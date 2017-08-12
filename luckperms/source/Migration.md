LuckPerms 有内置的支持其他的权限插件轻松迁移到 LuckPerms 的功能。

## 开始之前
需要注意的是这个系统还不是那么的完美，在绝大多数情况下，它在转变数据时相当不错，但是不是所有的数据都是相同的，并且有时我可能没有考虑这么多。

LuckPerms 有和其他权限插件相同的地方，但是有些部分从根本上不同，有些迁移运用了一些技巧。

另外，让插件迁移你的所有的数据意味着你没有机会学习任何一个 LuckPerms 命令，这可能会是一个麻烦的地方，如果你是从 PermissionsEx 或者 GroupManager 迁移来的数据，你应该看看 [GM PEX 的等同命令](/GM-&-PEX-Command-Equivalents.md)

如果你使用了老版本的权限插件，或者你根本不喜欢的，现在可能是一个机会来重新构建清理，顺便学习 LuckPerms 的命令！

不？！就喜欢你现在的权限插件？让我们来迁移。

   
## 目前支持的插件

| Bukkit / Spigot       | BungeeCord            | Sponge                |
|-----------------------|-----------------------|-----------------------|
| GroupManager          | BungeePerms           | PermissionsEx         |
| PermissionsEx         |                       | PermissionManager     |
| zPermissions          |                       |                       |
| PowerfulPerms         |                       |                       |
| bPermissions          |                       |                       |


# 如何
迁移的处理很简单，但是每个平台可能有不同。

1. 将 LuckPerms jar 文件放入你的服务器文件夹。
2. 保证两个权限插件的文件夹在同一个文件夹里（现在还不要卸载）
3. 开启服务器，你可以在活跃的服务器来进行这个操作，但是我建议在没有人的服务器上进行。

**运行一下命令: `lp migration <插件名>`**

有些插件需要你填写额外的选项/标签，如果需要，你会在迁移之前被通知。

接着只需要让 LuckPerms 处理剩下的事了！你将会被提示迁移进度，完成时也会被提示。

当处理完成，停止服务器，移除其他权限插件的 jar，再次开启你的服务器。

控制台的输出一定是冗长繁杂的，以 "(LP) LOG" 开头的命令都可以忽略，但是栈堆信息不应该忽略（一般表示出现了什么问题）。如果你的迁移输出含有栈堆信息，请反馈给我，更多的信息在这一个页面的底部。


## PowerfulPerms
处理 PowerfulPerms 的过程更加复杂。

玩家的信息只有在加入服务器时才被加载，插件 API 没有方法一次性获得所有的玩家的数据。

这意味着我们在导入数据时，我们必须得查询 PowerfulPerms MySQL 表来获得所有玩家的信息。

命令使用将会不同。

`/luckperms migration powerfulperms [address] [database] [username] [password] [db table]`

解释：
* address = MySQL 服务器的 IP 地址，比如 127.0.0.1:3306
* database = PowerfulPerms 插件使用的数据库的名称
* username = SQL 服务器登入需要的用户名
* password = SQL 服务器登入需要的密码
* db table = 存储玩家数据的表名（尽管我们只关注 UUID 列表）

默认的表名，据我所知，是 "players"，但是如果你添加了表名的前缀，你需要添加他们。

比如如果我的表的前缀是 "pp_"，那么 db table = "pp_players"（不需要引号）

比如: `/luckperms migration powerfulperms 127.0.0.1:3306 minecraft root passw0rd players`

# 错误
如果这个命令不存在，请检查这个插件是否正确加载。

如果处理没有完成，并且打印了错误消息，请在 GitHub 提交 issue 或者 [在这里联系我](https://github.com/lucko/LuckPerms/wiki#cant-find-something)，我将尽力尽可能快的回复你。
