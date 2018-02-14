此页面是一个描述 AuthMe 的命令是如何注册并处理的技术性文章。

### 概览

以下概览展示了命令处理中最重要的一些部分。

![Command handling overview](http://s33.postimg.org/t45b4jxbj/Untitled_Diagram.png)

### 命令注册

我们使用 `CommandDescription` 对象来定义 AuthMe 中可用的命令。这些对象不含有任何命令的逻辑，但是含有所有执行此命令必须的信息：使用命令的 label（比如必须使用 `/authme register` 或者 `/authme reg`），参数的长度，以及一个到实际命令实现的引用。 

### 映射输入的命令

当一个命令被执行时，Bukkit（或者 Spigot）将插件的信息传递给插件，使用这些参数 `String commandLabel, String[] args`。Bukkit 命令的 label 只含有命令的第一个「词」（比如 `authme` 之于 `/authme reload`）以及剩下的参数。

在 AuthMe 中，我们称 _labels_ 为命令的第一个单词，所以在 `/authme register billy pass123` 中，label 为 `authme, register` 因为他们指向了管理员注册的命令。在一开始，我们还不知道哪个是 label 哪个是参数，所以我们直接以 _命令部分_ 代指它们。

第一件事是决定哪个_部分_是 _labels_ 抑或 _参数_ 。如果这一部分可以映射到一个命令描述对象（`CommandDescription`）并且参数的长度是正确的，我们就称之为一个成功的映射。比如，`/authme register billy pass123` 指向了对于管理注册的命令的描述，并且剩下了两个参数 `billy, pass123` 。这个命令描述定义了两个强制的参数，所以参数匹配，我们成功地进行了一次映射。

**安全推测：** 在编程中，假定最多两个 label 就能够访问某个命令（比如 `/authme register`，又比如说 `/authme user register` - 这有三个 label，是不可能发生的）。任何更多的参数都可能复杂化我们的命令结构和代码结构。有一个测试检测我们的命令描述（`CommandDescription`）初始化为大于两个参数。尽管如此，你仍然可以自行编写处理命令的逻辑，如果不是太复杂的话。

### 权限检查

有关权限的逻辑在 `permission` 包中处理。CommandHandler 类将命令发送者和命令描述传递给 PermissionsManager 来查询用户是否可以执行此命令。

### 命令的执行

如果权限检查成功，命令就可以被执行。每个命令描述都有一个名为 `ExecutableCommand` 的子类，与之关联，用于真正的处理命令逻辑。参数将会传递给这个类。

一个 `ExecutableCommand` 实例可能调用更多的对象，尤其是使用数据库的异步处理也包含其中。在这种情况下，这个 `ExecutableCommand` 常常做一些不需要 I/O 的操作（比如：检查密码正确与否？玩家是否在线？）接着讲数据传递给一个异步任务，用于处理与数据库的交互。

**安全猜测：** 在 `ExecutableCommand` ，我们推断对应的命令描述中，所有的强制参数都是存在的。命令处理器不会在参数不匹配的情况下执行一个命令。