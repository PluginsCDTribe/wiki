这个页面包含了一些使用 `@Inject` 注释的目的以及如何使用的指南。

- [目的](#purpose)
  - [控制反转](#控制反转)
  - [依赖注入](#依赖注入)
- [注入方法](#注入方法)
  - [构造注入](#构造注入)
  - [字段注入](#字段注入)
  - [`@Inject` 获得单实例](#@Inject 获取单实例)

# 目的

`@Inject` 允许我们更容易使用控制反转。

## 控制反转

简要地说，控制反转意味着我们将一个类需要的服务从外部传递进来，而不是实例化这个类或者主动调用获得（`getInstance()`）该服务。这使得依赖显式化（我们更清楚我们的依赖是什么），并且在未来更方便更换组件，而且方便了单元测试。

### 示例

考虑以下类
```java
public class MessageTask {

    public void setTask(String name) {
        if (PlayerCache.getInstance().isAuthenticated(name) && LimboCache.getInstance().hasLimboPlayer(name)) {
            LimboCache.getInstance().getLimboPlayer(name).initMessageTask();
        }
    }
}
```

应用控制反转后，这个类看起来像这样：
```java
public class MessageTask {

    private final PlayerCache playerCache;
    private final LimboCache limboCache;

    public MessageTask(PlayerCache playerCache, LimboCache limboCache) {
        this.playerCache = playerCache;
        this.limboCache = limboCache;
    }

    public void setTask(String name) {
        if (playerCache.isAuthenticated(name) && limboCache.hasLimboPlayer(name)) {
            limboCache.getLimboPlayer(name).initMessageTask();
        }
    }
}
```

第二种版本里，我们立刻看到了 `MessageTask` 需要一个 `LimboCache` 和 `PlayerCache` 实例。我们可以很简单的传递模拟实现来测试这个类，而第一种情况下，我们不可能来更换实现。

## 依赖注入

### 没有依赖注入的情况

使用「控制反转」的一个缺点是，我们很清楚的知道了实例化这个类需要两个实例作为依赖。考虑一下代码：

```java
 private CommandHandler initializeCommandHandler(PermissionsManager permissionsManager, Messages messages,
                                                 PasswordSecurity passwordSecurity, NewSetting settings) {
    HelpProvider helpProvider = new HelpProvider(permissionsManager, settings.getProperty(HELP_HEADER));
    Set<CommandDescription> baseCommands = CommandInitializer.buildCommands();
    CommandMapper mapper = new CommandMapper(baseCommands, permissionsManager);
    CommandService commandService = new CommandService(
        this, mapper, helpProvider, messages, passwordSecurity, permissionsManager, settings);
    return new CommandHandler(commandService);
}
```
我们想要实例化一个 `CommandHandler`。我们需要像其传递一个 `CommandService` ，所以我们需要先实例化这个。然而，它又需要一个 `CommandMapper` ，一个 `HelpProvider`... 一共四个实例。这让我们必须解决一大堆的类之后（CommandService, CommandMapper, 等.）才能 - 而我们只是想要一个 `CommandHandler` 实例而已。

### 依赖注入的目的

依赖注入允许我们避免大量的实例化代码块，而是通过 _注入_ 依赖。我们可以像这样简单的从注入器请求一个类： 
```java
CommandHandler handler = injector.getSingleton(CommandHandler.class);
```
注入器会扫描 CommandHandler 类来查找依赖，实例化他们并传递给我们。基本来说，它自动做到了上面一大堆的代码块。我们需要小小的帮助一下注入器，通过使用 `@Inject` 注释对应的类来告诉注入器应该注入什么。

# 注入方法

依赖可以通过很多不同的方法传递给一个类。重要的是每个类只能使用一个。

## 构造方法注入

构造方法可以使用 `@Inject` 注释。这告诉注入器这个构造方法的参数需要被注入。考虑第一个例子中的 `MessageTask` 类。我们住需要添加一个注释来启用构造器注入：

```java
public class MessageTask {

    private final PlayerCache playerCache;
    private final LimboCache limboCache;

    @Inject
    MessageTask(PlayerCache playerCache, LimboCache limboCache) {
        this.playerCache = playerCache;
        this.limboCache = limboCache;
    }

    public void setTask(String name) {
        if (playerCache.isAuthenticated(name) && limboCache.hasLimboPlayer(name)) {
            limboCache.getLimboPlayer(name).initMessageTask();
        }
    }
}
```

现在一个 MessageTask 实例可以通过 `injector.getSingleton(MessageTask.class)` 来获得。这个注入器将会注意到 `PlayerCache` 和 `LimboCache` 需要传递给构造方法。

## 字段注入

另一种方法，字段可以使用 `@Inject` 注释：

```java
public class MessageTask {

    @Inject
    private PlayerCache playerCache;
    @Inject
    private LimboCache limboCache;

    public void setTask(String name) {
        if (playerCache.isAuthenticated(name) && limboCache.hasLimboPlayer(name)) {
            limboCache.getLimboPlayer(name).initMessageTask();
        }
    }
}
```
再一次的，注入器将会检测到字段上的注释，然后就会给这些字段赋值。这些字段可以是 private 的，或者是任何其他的可见性。字段注入需要一个无参构造方法存在。

## @Inject 获取单实例

无论是你使用构造方法注入或者字段注入，很重要的一点就是要理解实例被传递，并且注入器每次都会传递相同的类实现。举个例子，如果你在某些类里有 `@Inject private LimboCache limboCache` ，另一个类里有另一个 `@Inject private LimboCache limboCache` ，两个字段都会有相同的 `LimboCache` 对象（即 `limboCache == limboCache` 为 true）。