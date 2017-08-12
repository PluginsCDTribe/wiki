LuckPerms 提供了一个命令来帮助执行大量的权限编辑，这个命令应该小心使用，因为很容易破坏你的所有信息。

在执行这个命令之前做一个备份可能是个明智的选择，或者是给你的数据库做个备份，或者使用 export 命令。

命令的设计基于 SQL 格式，这意味着命令可以直接转换为一条 SQL 查询语句，或者在 YAML 或者 JSON 文本编辑。那些对 SQL 语句有经验的人可能会发现在数据库服务器直接写入查询比使用命令更简单。

这些命令**只能在控制台使用**。这是因为这些命令可能会对你的服务器造成极大的伤害。在执行之前，你会被要求输入一个确认码，用于防止 "sudo" 来通过这些命令获得权限。

命令用法如下...

## `/lp bulkupdate <data type> <action> [action field] [action value] [constraint...]`

一开始有点令人害怕，我知道，拆开来看...

| 参数 | 描述 |
|----------|-------------|
| `data type` | 更改的数据 (可以是 "all", "users" 或者 "groups") |
| `action` | 对数据执行的操作 (可以是 "update" 或者 "delete") |
| `action field` | 只可用于 update 操作 (可以是 "permission", "server" 或 "world") |
| `action value` | 替换的值，只可用于 update 操作 |
| `constraint` | update 的约束 |

`data type` 是最简单的，只是简单的告诉了 LuckPerms 这个操作应该影响什么数据。

`action` 是对数据执行的操作。可以是 "update" 或 "delete"。delete 就是简单的删除满足约束的所有的记录。Update 将会将原来的值替换为新的值。

`action field` 和 `action value` 参数是可选的，因为只对 update 有效。field 是用来更新的东西，而 value 是用来替换的东西。

`constraints` 参数与 update 的限制有关，只有权限（或者条目）匹配约束才会被影响。

### 约束
约束分为 3 部分，`field`, `comparison` 和 `value`。

可用的 `fields` 是 `permission`, `server` 和 `world`。权限就只是存储在文件中的权限节点（记住甚至组的关系和前缀都是存储在前缀的）。server 和 world 与 permission 应用的世界和服务器有关。如果权限没有他们的值，那么就是全局。

`value` 部分的约束是需要的 field，用于比较。

有四种比较的方式。

| 比较符号          | 比较的名称      | 描述        |
|-------------------|-----------------|-------------|
| `==`              | 等于        | 两个值相同（忽略大小写） |
| `!=`              | 不等于    | 两个值不相同（忽略大小写） |
| `~~`              | 相似      | 两个值相似，与SQL的 `LIKE` 关键字相同 |
| `!~`              | 不相似  | 两个值不相似，与SQL的 `LIKE` 关键字相同 |

更多的有关相似的信息可以在[这里](https://www.w3schools.com/sql/sql_like.asp)和[这里](https://www.tutorialspoint.com/sql/sql-like-clause.htm)找到。

基础的大概是这样的：
* `%` - 百分号代表 0 到多个字符
* `_` - 下划线代表一个字符

##### 一些示例
* `server ~~ hub_` 匹配 "hub1", "hub2", "hub3" 等
* `permission !~ group.%` 匹配任何不以 group 开头的权限
* `world == nether` 匹配世界名为 nether

当在命令中使用约束，必须使用 `" "` 引号包围。

### 命令示例
#### `/lp bulkupdate all update permission group.mod "permission == group.moderator"`
更新所有的条目，替换所有的 "group.moderator" 为 "group.mod"（效率重命名）。

#### `/lp bulkupdate user delete "server ~~ hub%" "world == nether"`
删除任何分配给以 "hub" 开头的服务器，并且世界是 "nether" 的玩家的权限。

#### `/lp bulkupdate all delete "permission == essentials.fly"`
删除所有 "essentials.fly" 的权限

#### `/lp bulkupdate all update server global "server == factions"`
更改所有服务器 "factions" 条目为 "global"。

希望你理解了这个意思，如果你不确定如何构建一个你想要应用的命令，请随意使用 Wiki 主界面的联系方式联系我。