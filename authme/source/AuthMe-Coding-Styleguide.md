- 使用 4 个空格作为缩进（而不是 TAB）
- 总是将类似 `if`, `while` 的结构使用花括号包起来（永远不要 `if (isTrue) doThis();`）
- 字段不应该是 public 的 - 使用更适合的 getter 和 setter。
- 最大行宽度：120 个字符

Java 日常规范：
- 类名应该是大驼峰式的（CamelCase）
- 方法名、字段名和变量应该是小驼峰式的（camelCase）

## Exception handling

不要「吞」掉一个异常，除非它以另一种预期的场景中被处理了。否则你可以简单的使用 `ConsoleLogger` 来记录这个异常：

```java
try {
    Files.write(configFile, settings);
} catch (IOException e) {
    ConsoleLogger.logException("Could not write to config file:", e);
}
```

这将输出类似： `[WARN] Could not write to config file: [IOException] File is read-only` 的东西到控制台和日志文件。记录异常有助于 debug 和检测日后可能出现的问题。

## 复杂性

试着创建 "bite-sized" 的元素：一个方法应该只做一件事情，每个类应该只解决一个主要问题。如果一个方法中做了太多的事情，那么人们就必须花掉更多的脑子来理解你想要在这个方法里干什么，你就不能获得更好的概览 - 这会帮助你找到逻辑中的性能提升以及逻辑的破绽。

## 可维护性

为观众编程 - 让他人从你花费时间解决的努力中获益，你可以为不是非常明确的代码添加注释和 Javadocs：

```java
// 让这个任务稍后执行，这样就不会和背包的处理冲突
scheduler.scheduleSyncTaskLater(new LoginTask());
```

类似的，在问题跟踪器中创建一个问题，而不是仅仅写一个 TODO 注释。TODO 注释如果没有积极地处理，最后一定会被忘掉。

## JavaDoc

使用第三人称（"Gets the player's name"）或者祈使的语气（"Get the player's name"）；整个类中都应该这么写。Javadocs 应该简要的解释这个方法是干什么的，并向开发者提供进一步的信息。 

在 `@param` 和描述之间留一个空行。

示例：
```java
    /**
     * 添加执行此命令需要的权限节点
     *
     * @param permissionNode 添加的权限节点
     * @return true 则成功，false 则失败
     */
    public boolean addPermissionNode(String permissionNode)
```
