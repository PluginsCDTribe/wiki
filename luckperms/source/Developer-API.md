## 简介
LuckPerms API 允许你更改大量的插件内部编程，并且能够轻松地将 LuckPerms 深度集成到你的插件和系统里。

大多数的其他的权限要么没有 API，要么有很差的 API，或者是有很差的文档的 API，而且里面的方法和类可能随机在不同版本里消失或是移动。Vault 项目就是一个很好的接口，并且是将大量插件一次性集成的很好的方法，可惜他的功能实在是太少了。

LuckPerms 遵循 Semantic 版本控制，也就是意味着一个不向后兼容的新的 API 出现时，主版本会增加这个 API，你可以放心你的集成不会因为版本的不同而崩溃，主要的版本是保持不变的。

## 如何在项目里使用 API
LuckPerms 的 API 包是 [`me.lucko.luckperms.api`](https://github.com/lucko/LuckPerms/tree/master/api/src/main/java/me/lucko/luckperms)

我的 Nexus 服务器可以在这里找到 [https://nexus.lucko.me/](https://nexus.lucko.me/)，你在你的构建脚本里需要的仓库在 [https://repo.lucko.me/](https://repo.lucko.me/)

#### 其他有用的链接
* [JavaDocs](https://luckperms.lucko.me/javadocs/)
* [CI Server](https://ci.lucko.me/job/LuckPerms/)

### Maven
````xml
<repositories>
    <repository>
        <id>luck-repo</id>
        <url>https://repo.lucko.me/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>me.lucko.luckperms</groupId>
        <artifactId>luckperms-api</artifactId>
        <version>3.2</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
````

### Gradle
```gradle
repositories {
    maven {
        name "luck-repo"
        url "https://repo.lucko.me/"
    }
}

dependencies {
    compile ("me.lucko.luckperms:luckperms-api:3.2")
}
```

## 使用指南
使用 API，你需要获得 LuckPermsApi 接口的实例，这可以通过几个方法完成。

```java
// 所有平台 (抛出 IllegalStateException 如果 API 没有被加载)
final LuckPermsApi api = LuckPerms.getApi();

// 或者可选的
Optional<LuckPermsApi> provider = LuckPerms.getApiSafe();
if (provider.isPresent()) {
    final LuckPermsApi api = provider.get();
}

// Bukkit/Spigot
ServicesManager manager = Bukkit.getServicesManager();
if (manager.isProvidedFor(LuckPermsApi.class)) {
    final LuckPermsApi api = manager.getRegistration(LuckPermsApi.class).getProvider();
}

// Sponge
Optional<LuckPermsApi> provider = Sponge.getServiceManager().provide(LuckPermsApi.class);
if (provider.isPresent()) {
    final LuckPermsApi api = provider.get();
}
```

### 线程安全的警告
所有 LuckPerms 内部，包括 API 都是线程安全的，你可以在异步线程任意调用 API 而不用担心发生错误。

但是，请注意一些操作，（尤其是存储类）是阻塞的。[CompletableFuture](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/CompletableFuture.html) 就是用于这种情况：防止由于较差的处理导致的增加的错误，当出现 IO 时主线程等待处理完成。注意在添加 Callback 时指定正确的处理器。

### 我想将 LuckPerms 作为依赖项
在 Bukkit/Bungee，你需要在你的 plugin.yml 添加以下信息

```yml
depend: [LuckPerms]
```

在 Sponge, 在你的插件声明添加这些。
```java
@Plugin(
        id = "myplugin",
        dependencies = {
                @Dependency(id = "luckperms")
        }
)
public class MyPlugin {
    ...
}
```

### 事件
LuckPerms 有一个完整的读写API，也有一个事件监听系统。由于插件的多平台的原因，我们使用了内部的事件系统，而不是每个平台已经使用的事件系统（举个例子，Bukkit Event API）。这意味着简单的注册你的平台的监听器将不会生效。

所有的事件都是**异步触发**的。这意味着不应该在监听器里交互或者调用任何不是线程安全的方法。

值得注意的是，大多数的 Bukkit/Sponge 都不是线程安全的，并且只应该使用主服务器线程来交互。你应该使用调度器来访问 LuckPerms 的监听器。

### 我怎样才能监听一个事件
所有的事件接口都可以在 [me.lucko.luckperms.api.event](https://github.com/lucko/LuckPerms/tree/master/api/src/main/java/me/lucko/luckperms/api/event) 包里找到，它们都继承了 [LuckPermsEvent](https://github.com/lucko/LuckPerms/blob/master/api/src/main/java/me/lucko/luckperms/api/event/LuckPermsEvent.java) 类。

监听事件应该获得 [EventBus](https://github.com/lucko/LuckPerms/blob/master/api/src/main/java/me/lucko/luckperms/api/event/EventBus.java) 实例，使用 [LuckPermsApi#getEventBus](https://github.com/lucko/LuckPerms/blob/master/api/src/main/java/me/lucko/luckperms/api/LuckPermsApi.java#L68)即可。

为你的监听器创建另一个类常常是个好想法，这是一个你可以用来参考的类。

```java
package me.PluginsCDTribe.test;

import me.PluginsCDTribe.luckperms.api.event.EventBus;
import me.PluginsCDTribe.luckperms.api.event.log.LogPublishEvent;
import me.PluginsCDTribe.luckperms.api.event.user.UserLoadEvent;
import me.PluginsCDTribe.luckperms.api.event.user.track.UserPromoteEvent;

public class TestListener {
    private final MyPlugin plugin;

    public TestListener(MyPlugin plugin, LuckPermsApi api) {
        this.plugin = plugin;

        EventBus eventBus = api.getEventBus();

        // use a lambda
        eventBus.subscribe(LogPublishEvent.class, e -> e.getCancellationState().set(true));
        eventBus.subscribe(UserLoadEvent.class, e -> {
            System.out.println("User " + e.getUser().getName() + " was loaded!");
            if (e.getUser().hasPermission("some.perm", true)) {
                // Do something
            }
        });

        // use a method reference
        eventBus.subscribe(UserPromoteEvent.class, this::onUserPromote);
    }

    private void onUserPromote(UserPromoteEvent event) {
        Bukkit.getScheduler().runTask(plugin, () -> {
            Bukkit.broadcastMessage(event.getUser().getName() + " was promoted to" + event.getGroupTo().get() + "!");

            Player player = Bukkit.getPlayer(event.getUser().getUuid());
            if (player != null) {
                player.sendMessage("Congrats!");
            }
        });
    }

}
```

[EventBus#subscribe](https://github.com/lucko/LuckPerms/blob/master/api/src/main/java/me/lucko/luckperms/api/event/EventBus.java#L43) 返回一个 [EventHander](https://github.com/lucko/LuckPerms/blob/master/api/src/main/java/me/lucko/luckperms/api/event/EventHandler.java) 实例，可以用来在插件停止的时候取消注册监听器。

## 示例用法
下面就是一些简短的实例，使用了一些基本的 API 功能。

### 获得玩家的组
如果你只是想找到一个玩家的组，我非常建议你使用以下的方法（你甚至不需要使用 API）。

```java
public static String getPlayerGroup(Player player, List<String> possibleGroups) {
    for (String group : possibleGroups) {
        if (player.hasPermission("group." + group)) {
            return group;
        }
    }
    return null;
}
```
记住将你的组排列为优先级的顺序（比如组长在前，成员在后）。

### 为一个玩家添加权限

```java
LuckPermsApi api = null; // See above for how to get the API instance.

Optional<User> user = api.getUserSafe(uuid);
if (!user.isPresent()) {
    return false; // The user isn't loaded in memory.
}

// Build the permission node we want to set
Node node = api.getNodeFactory().newBuilder(permission).setValue(true).build();

// Set the permission, and return true if the user didn't already have it set.
try {
    user.get().setPermission(node);

    // Now we need to save the user back to the storage
    api.getStorage().saveUser(u);

    return true;
} catch (ObjectAlreadyHasException e) {
    return false;
}
```

### 为（可能的）离线玩家添加权限

CompletionStage API 可以用来轻松交互插件的存储，查看[这里](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/CompletionStage.html) 和 [这里](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/CompletableFuture.html) 来查看这两个类的详细信息。

```java
LuckPermsApi api = null; // See above for how to get the API instance.

// load the user in from storage. we can specify "null" for their username,
// since it's unknown to us.
api.getStorage().loadUser(uuid, "null").thenComposeAsync(success -> {
    // loading the user failed, return straight away
    if (!success) {
        return CompletableFuture.completedFuture(false);
    }
    
    // get the user instance, they're now loaded in memory.
    User user = api.getUser(uuid);

    // Build the permission node we want to set
    Node node = api.getNodeFactory().newBuilder(permission).setValue(true).build();

    // Set the permission, and return true if the user didn't already have it set.
    try {
        user.setPermission(node);
        
        // now we've set the permission, but still need to save the user data
        // back to the storage.
        
        // first save the user
        return api.getStorage().saveUser(user)
                .thenCompose(b -> {
                    // then cleanup their user instance so we don't create
                    // a memory leak.
                    api.cleanupUser(user);
                    return CompletableFuture.completedFuture(b);
                });
        
    } catch (ObjectAlreadyHasException e) {
        return CompletableFuture.completedFuture(false);
    }
    
}, api.getStorage().getAsyncExecutor());
```

### 获得玩家的前缀
LuckPerms 有一个（复杂的）缓存系统，用于非常快速的权限/信息查询。这些类都在 API 里，并且可以在可能的地方使用。


```java
LuckPermsApi api = null; // See above for how to get the API instance.

// Get the user, or null if they're not loaded.
User user = api.getUserSafe(uuid).orElse(null);
if (user == null) {
    return Optional.empty(); // The user isn't loaded. :(
}

// Now get the users "Contexts". This is basically just data about the players current state.
// Don't worry about it too much, just know we need it to get their cached data.
Contexts contexts = api.getContextForUser(user).orElse(null);
if (contexts == null) {
    return Optional.empty();
}

// Ah, now we're making progress. We can use the Contexts to get the users "MetaData". This is their cached meta data.
MetaData metaData = user.getCachedData().getMetaData(contexts);

// MetaData#getPrefix returns null if they have no prefix.
return metaData.getPrefix();
```

### 获得玩家请求的权限
我们也可以使用这个缓存系统来获得一个包含用户权限的 Map 实例，包含了基础的权限查询。

```java
// All retrieved in the same way as shown above.
User user;
Contexts contexts;

PermissionData permissionData = user.getCachedData().getPermissionData(contexts);
Map<String, Boolean> data = permissionData.getImmutableBacking();
```

### 寻找权限
你可以使用 Java 8 的流轻松过滤并返回一个用户请求的权限

```java
public boolean hasPermissionStartingWith(UUID uuid, String startingWith) {
    // Get the user, if they're online.
    Optional<User> user = api.getUserSafe(uuid);

    // If they're online, perform the check, otherwise, return false.
    return user.map(u -> u.getPermissions().stream()
            .filter(Node::getValue)
            .filter(Node::isPermanent)
            .filter(n -> !n.isServerSpecific())
            .filter(n -> !n.isWorldSpecific())
            .anyMatch(n -> n.getPermission().startsWith(startingWith))
    ).orElse(false);
}
```

### 创建新的组并分配权限
这个方法不是阻塞的，所以可以安全的在主线程调用，一旦操作完成，回调会异步运行。

```java
api.getStorage().createAndLoadGroup("my-new-group").thenAcceptAsync(success -> {
    if (!success) {
        return;
    }

    Group group = api.getGroup("my-new-group");
    if (group == null) {
        return;
    }

    Node permission = api.buildNode("test.permission").build();

    try {
        group.setPermission(permission);
    } catch (ObjectAlreadyHasException ignored) {}

    // Now save the group back to storage
    api.getStorage().saveGroup(group);
}, api.getStorage().getAsyncExecutor());
```

## 版本控制
在 2.0 版本里，LuckPerms 遵循了 Semantic 版本控制。

唯一不同的是 patch 号不包含在任何地方，除了 pom，并且每次构建都会计算，基于上次提交后的提交数量。（每个新的小版本都会创建新的标签）

这意味着 API 版本不再有 patch 号（在 patch 里没有 API 的变化），API 版本会是 x.y，每个不同的 LuckPerms 构建都会遵循 x.y.z。

### 变更日志
* 版本 2.x 保持了几个月的稳定，没有任何向后不兼容的变更，但是在之后的版本里很多的方法变为弃用状态，并且事件 API 的确应该重写一遍。
* 版本 3.x 包含了以下的向后不兼容的变化。
https://gist.github.com/lucko/fdf6ae4b2d9e466d8103dd9c68e5db9e