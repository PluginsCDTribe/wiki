不同平台的 LuckPerms 的配置文件可以在这里找到。


| 平台          | 位置                                                                                                                      |
|---------------|-------------------------------------------------------------------------------------------------------------------------------|
| Bukkit/Spigot | [`/plugins/LuckPerms/config.yml`](https://github.com/PluginsCDTribe/LuckPerms/blob/master/bukkit/src/main/resources/config.yml)        |
| BungeeCord    | [`/plugins/LuckPerms/config.yml`](https://github.com/PluginsCDTribe/LuckPerms/blob/master/bungee/src/main/resources/config.yml)        |
| Sponge        | [`/config/luckperms/luckperms.conf`](https://github.com/PluginsCDTribe/LuckPerms/blob/master/sponge/src/main/resources/luckperms.conf) |

请注意配置文件不能在有新配置的时候自动添加，如果文件中没有找到任何东西，我们将使用默认选项。


## 索引
### 基础
* [`server`](#server)
* [`include-global`](#include-global)
* [`include-global-world`](#include-global-world)
* [`apply-global-groups`](#apply-global-groups)
* [`apply-global-world-groups`](#apply-global-world-groups)
* [`use-server-uuids`](#use-server-uuids)
* [`log-notify`](#log-notify)
* [`world-rewrite`](#world-rewrite)
* [`group-name-rewrite`](#group-name-rewrite)
* [`temporary-add-behaviour`](#temporary-add-behaviour)
* [`primary-group-calculation`](#primary-group-calculation)
### 权限计算
* [`apply-wildcards`](#apply-wildcards)
* [`apply-regex`](#apply-regex)
* [`apply-shorthand`](#apply-shorthand)
##### Bukkit
* [`apply-bukkit-child-permissions`](#apply-bukkit-child-permissions)
* [`apply-bukkit-default-permissions`](#apply-bukkit-default-permissions)
* [`apply-bukkit-attachment-permissions`](#apply-bukkit-attachment-permissions)
##### Bungee
* [`apply-bungee-config-permissions`](#apply-bungee-config-permissions)
##### Sponge
* [`apply-sponge-implicit-wildcards`](#apply-sponge-implicit-wildcards)
* [`apply-sponge-default-subjects`](#apply-sponge-default-subjects)
### 服务器管理员 / Vault (仅 Bukkit 版本)
* [`enable-ops`](#enable-ops)
* [`auto-op`](#auto-op)
* [`commands-allow-op`](#commands-allow-op)
* [`use-vault-server`](#use-vault-server)
* [`vault-server`](#vault-server)
* [`vault-include-global`](#vault-include-global)
* [`vault-ignore-world`](#vault-ignore-world)
* [`vault-debug`](#vault-debug)
### 存储
* [`storage-method`](#storage-method)
* [`watch-files`](#watch-files)
* [`split-storage`](#split-storage)
* [`data`](#data)
* [`pool-size`](#pool-size)
* [`table-prefix`](#table-prefix)
* [`sync-minutes`](#sync-minutes)
* [`messaging-service`](#messaging-service)
* [`auto-push-updates`](#auto-push-updates)
* [`redis`](#redis)


## 基础
___
### `server`

服务器的名称，用于制定服务器的权限。

如果设置为 "global" 这个设置将会被忽略，更多关于服务器指定的权限可以在[这里](/Advanced-Setup.md)找到。


##### 示例
```yaml
server: global
```

___
### `include-global`

这个服务器的玩家是否应该应用他们的全局权限。（没有指定服务器的权限）

如果这个选项被设置为 false，只有指定在此服务器的权限才会被应用。如果上方的 "server" 选项设置为 global，请不要将其设置为 false。更多的有关服务器指定的权限可以在[这里](/Advanced-Setup.md)找到。


##### 示例
```yaml
include-global: true
```

___
### `include-global-world`

与上方的选项相似，只是这个选项用于世界的设定。如果设置为 false，只有指定了世界的权限才会被应用至玩家。任何没有指定世界的权限都不会被应用。


##### 示例
```yaml
include-global-world: true
```

___
### `apply-global-groups`

这个选项与 "include-global" 选项类似，但是此选项更改了组的继承设定。

当计算玩家的权限时，插件将会给继承树设定范围，递归解析组成员关系。如果这个设置设置为 false，如果一个组没有被应用，那么它的父组都不会被计算，继承查询将会在此终止。

这意味着就算一个玩家没有在一个特定服务器直接继承一个组，如果这个组通过了一个没有指定服务器的组继承，这个组将不会被应用。

举个例子，当设置为 false，使用以下设置：

```
用户 "Luck" 继承自全局组 "admin"，admin 继承自某服务器的 "default" 组。
```

尽管 Luck 在指定服务器上继承了默认组，它将不会被应用，因为继承查询在 admin 停止。admin 的父组将不被考虑。


##### 示例
```yaml
apply-global-groups: true
```

___
### `apply-global-world-groups`

与上面的选项相似，但是这个选项用于世界的设定。如果设置为 false，只有指定了世界的组才会被分配，给用户解析。任何没有指定世界的组都不会被应用。


##### 示例
```yaml
apply-global-world-groups: true
```

___
### `use-server-uuids`

如果使用服务器的UUID，或者根据之前的连接的用户名来查询，那么这个设定应该使用 true，除非你很确定你在做什么。

一般的，当这个选项设置为 true 时，当玩家登入时，LuckPerms 将会使用服务器提供的用户名/UUID来标识玩家。这个在大多数的服务器都是适用的。

当设置为 false，LuckPerms 将会检查玩家是否曾经在服务器登录过，如果找到了一个玩家，那么之前映射的UUID将会被使用，否则将会回到默认的使用服务器的UUID的方法。

在离线模式（破解版）的服务器，玩家的UUID基于他们的用户名创建。

**重要**

如果你在运行一个 BungeeCord 服务器，你必须开启 IP forward 设置，这将让服务器使用正确的UUID。

[Spigot](https://www.spigotmc.org/wiki/bungeecord-ip-forwarding/) [Sponge](https://docs.spongepowered.org/stable/en/server/getting-started/bungeecord.html). SpongeForge 推荐使用 [HexaCord](https://github.com/HexagonMC/BungeeCord), 这是一个 BungeeCord 分支，支持 Forge 的 IP forwarding。

如果你的 BungeeCord 代理运行于离线模式并且你使用了 Spigot，你也应该像下方一样开启 IP forwarding，但是推荐你安装 [Paper](https://ci.destroystokyo.com/job/PaperSpigot/) 并设置 paper.yml 中的 `bungee-online-mode: false`。

如果还有什么原因导致了你无法设置 Ip forwarding，你可能需要将其设置为 false，请确保这样做之前你知道这样做的后果。


##### 示例
```yaml
use-server-uuids: true
```

___
### `log-notify`

当任何权限被修改后是否向玩家发送长的提醒。提醒将只发送给拥有正确权限的用户。

提醒可以在游戏中使用 `/lp log notify off` 临时关闭。


##### 示例
```yaml
log-notify: true
```

___
### `world-rewrite`

允许你给发送的世界设置别名，别名附加于真正的世界名，递归应用。


##### 示例
```yaml
world-rewrite:
  world_nether: world
  world_the_end: world
```

___
### `group-name-rewrite`

允许你设置组名的别名。它们是纯粹的显示名称，实际上的名称不会改变，只有命令/信息的输出会改变。


##### 示例
```yaml
group-name-rewrite:
  default: Member
```

___
### `temporary-add-behaviour`

控制临时的权限/父类/元数据，默认是 `deny`

* **`accumulate`** - 任何添加的节点将被添加
* **`replace`** - 临时的节点持续的最长的时间，其他的节点将被忽略
* **`deny`** - 如果你试图添加一个重复的临时节点命令将被拒绝


##### 示例
```yaml
temporary-add-behaviour: deny
```

___
### `primary-group-calculation`

LuckPerms 如何决定用户的主组，Bukkit/Bungee 默认的是 `stored`，Sponge 默认的是 `parents-by-weight`。

* **`stored`** - 使用存储的记录在文件/数据库的数据
* **`parents-by-weight`** - 使用用户权重最高的父组
* **`all-parents-by-weight`** - 像上面的一样，但是计算所有的继承，包括直接继承和间接继承


##### 示例
```yaml
primary-group-calculation: stored
```

___


## 权限计算
___
### `apply-wildcards`

插件是否应用带有通配符的权限。

如果插件的作者没有提供他们自己的通配符权限，那么开启这个选项将会让 LuckPerms 转换它们。Bukkit 尤其不认同这种做法，但是它们在管理员中间适用的相当普遍。在 Sponge，这个选项控制 "node.part.*" 类型的通配符是否生效。


##### 示例
```yaml
apply-wildcards: true
```

___
### `apply-regex`

插件是否转换正则表达式权限。

如果设置为 true，LuckPerms 将会检测任何正则表达式权限，正则表达式权限节点以 "r=" 开头，返回所有匹配这个节点的请求。如果你没有任何正则表达式权限的设置，开启这个将没有任何性能的影响。这个特点的更多信息可以在[这里](/Advanced-Setup.md#regex)找到。


##### 示例
```yaml
apply-regex: true
```

___
### `apply-shorthand`

是否允许GLOB风格的速记权限。

更多这个特性的信息可以在[这里](/Advanced-Setup.md#shorthand-permissions)找到。


##### 示例
```yaml
apply-shorthand: true
```

___
### `apply-bukkit-child-permissions`

插件是否应用Bukkit子权限。

插件的作者可以给他们的插件定义自定义权限结构，如果设置为 true，LuckPerms 将会使用他们。

这个选项是默认启用的，因为这是一个基础的Bukkit特性，大多数的服务器管理员都需要，但是如果你不希望使用这个系统，它将可以被安全关闭。


##### 示例
```yaml
apply-bukkit-child-permissions: true
```

___
### `apply-bukkit-default-permissions`

插件是否应该应用Bukkit的默认权限。

插件作者可以给所有的用户默认权限，或者设置应该/不应该给OP玩家。如果这个设置为 false，LuckPerms将会忽略这些默认权限。

这个选项是默认启用的，因为这是一个基础的Bukkit特性，大多数的服务器管理员都需要，但是如果你不希望使用这个系统，它将可以被安全关闭。


##### 示例
```yaml
apply-bukkit-default-permissions: true
```

___
### `apply-bukkit-attachment-permissions`

插件是否应该应用Bukkit的附加权限。

服务器的其他插件可以添加它们自身的"权限附加"到玩家，这允许大量的玩家附加权限持续到回话结束，或者被移除。如果这个设置被设置为 false，LuckPerms 在考虑玩家是否有某一特定的权限时，将不会包括这些附加的权限。

你在开启这个选项后可能会见到一个小的性能提升，关闭 OP 系统后，这个系统可以非常有效的阻止恶意插件给玩家任意权限的尝试。

这个选项是默认启用的，因为这是一个基础的Bukkit特性，大多数的服务器管理员都需要，但是如果你不希望使用这个系统，它将可以被安全关闭。


##### 示例
```yaml
apply-bukkit-attachment-permissions: true
```

___
### `apply-bungee-config-permissions`

插件是否应用 BungeeCord config.yml 里设置的权限和组。

如果设置为 false，LuckPerms 将会忽略这些值。

这个是默认关闭的，因为所有的权限都应该通过 LuckPerms 来设置，这样他们可以在游戏中查看和编辑。


##### 示例
```yaml
apply-bungee-config-permissions: false
```

___
### `apply-sponge-implicit-wildcards`

插件是否解析并应用Sponge的通配符集成系统的权限。

如果一个玩家获得了 `example`，那么他将自动获得 `example.function` 权限，`example.another`，`example.deeper.nesting` 等。

如果这个选项被设置为 false，系统将不会被应用。

这个选项是默认启用的，因为这是一个基础的Sponge特性，大多数的服务器管理员都需要，但是如果你不希望使用这个系统，它将可以被安全关闭。


##### 示例
```hocon
apply-sponge-implicit-wildcards=true
```

___
### `apply-sponge-default-subjects`

插件是否应用Sponge的默认权限。

插件将会授予玩家一组默认权限，如果设置为 false，那么插件将在考虑玩家是否拥有某权限时忽略这一组权限。

这个选项是默认启用的，因为这是一个基础的Sponge特性，大多数的服务器管理员都需要，但是如果你不希望使用这个系统，它将可以被安全关闭。


##### 示例
```hocon
apply-sponge-default-subjects=true
```


## Server Operator / Vault (Bukkit version only)
___
### `enable-ops`

是否使用原版的OP系统。

如果设置为 false，所有玩家都不是 op，op/deop 命令将被禁止。



##### 示例
```yaml
enable-ops: true
```

___
### `auto-op`

如果设置为 true，任何拥有 "luckperms.autoop" 权限的玩家将会自动设置为服务器OP。

这个权限可以被继承，或者设置在特定的服务器/世界，临时的等等。另外，设置此选项为 true 将会强制上方的选项 "enable-ops" 为 false。所有的用户都将被 deop 直到他们有了这个权限节点，并且 op/deop 命令将被禁止。

有一点需要注意的是，自动OP检测只有在玩家进入服务器和切换世界时生效，这意味着，简单的移除他们的权限并不会自动去除玩家的OP，玩家必须重新登陆才能使其生效。

推荐使用这个选项而不是简单的分配一个 "*" 权限。


##### 示例
```yaml
auto-op: false
```

___
### `commands-allow-op`

OP玩家是否有权限使用 LuckPerms 指令。

设置为 false 将只允许有命令指定的权限的玩家使用。


##### 示例
```yaml
commands-allow-op: true
```

___
### `use-vault-server`

下方的 `vault-server` 选项是否应该使用。

当这个选项设置为 false 时，"server" 值用于 Vault 操作。


##### 示例
```yaml
use-vault-server: false
```

___
### `vault-server`

Vault 操作中使用的服务器名称。

如果你不想让 Vault 操作为特定服务器，将其设置为 "global"。

只有当 `use-vault-server` 设置为 true 时生效。


##### 示例
```yaml
vault-server: global
```

___
### `vault-include-global`

玩家组接受元数据时是否考虑全局权限。


##### 示例
```yaml
vault-include-global: true
```

___
### `vault-ignore-world`

Vault 操作是否应该忽略提供的世界参数。

默认情况下，如果没有提供世界参数，权限将会设置在玩家当前的世界。（Vault 的设计给满分）。设置为 true 来更改这项操作的结果。


##### 示例
```yaml
vault-ignore-world: false
```

___
### `vault-debug`

LuckPerms 是否应当在一个插件使用了 Vault 的功能后打印 debug 信息。


##### 示例
```yaml
vault-debug: false
```


## Storage
___
### `storage-method`

插件应该使用哪个存储方法。

查看[这里](/Choosing-a-Storage-type.md)查看支持的所有类型。

**接受**： `mysql`, `mariadb`, `postgresql`, `sqlite`, `h2`, `json`, `yaml`, `mongodb`

如果你的 MySQL 支持，那么 `mariadb` 选项比 `mysql` 更好，`h2` 当然也比 `sqlite` 更好。


##### 示例
```yaml
storage-method: h2
```

___
### `watch-files`

当使用基于文件的存储系统，LuckPerms将会监视数据文件的变化，并在文件变化被检测到的时候自动规划更新数据、

如果不想让这个发生，那么将此选项设置为 false。


##### 示例
```yaml
watch-files: true
```

___
### `split-storage`

分离存储允许你为不用的数据类型使用不同的存储选项。

**不同类型的数据有：**
* **`user`** - 关于用户的数据，包含权限、父组和元数据
* **`group`** - 关于组的数据，包括了组权限、继承组和元数据
* **`track`** - 关于轨道的数据（或者说是梯子）
* **`uuid`** - LuckPerms 适用的 `uuid <-- --> username` 缓存，当 `/lp user` 使用的是用户名而不是 UUID
* **`log`** - LuckPerms 存储的日志
允许的数据类型在上方列出


##### 示例
```yaml
split-storage:
  enabled: true
  methods:
    user: mariadb
    group: yaml
    track: yaml
    uuid: mariadb
    log: mariadb
```

___
### `data`

此选项用于指定数据库的存储凭据。

* **`address`** - 数据库的地址，如果使用默认的端口可以不填写，如果使用了特定端口，请使用 `host:port`
* **`database`** - LuckPerms 应该使用的数据库
* **`username`** - 使用的用户名
* **`password`** - 使用的密码，留空则不使用验证



##### 示例
```yaml
data:
  address: localhost
  database: minecraft
  username: root
  password: ''
```

___
### `pool-size`

MySQL 连接池大小。

默认为 `10`，应该适合大部分服务器。只有你清楚你在干什么再更改这项设置。

查看[这里](https://github.com/brettwooldridge/HikariCP/wiki/About-Pool-Sizing)了解更多关于连接池大小的信息。


##### 示例
```yaml
data:
  pool-size: 10 # The size of the MySQL connection pool.
```

___
### `sync-minutes`

此选项控制 LuckPerms 多长时间进行一次同步任务。

同步任务将会刷新存储中的所有信息，保证插件使用的是最新的数据。

这个选项默认关闭，因为大多数的用户都是不需要这个功能的，但是如果你使用远程存储，又没有设置信息服务，那么你可能将其设置为像 3 这样的数值。

设置为 -1 来完全停用这个任务。


##### 示例
```yaml
data:
  sync-minutes: 3
```

___
### `messaging-service`

设置信息服务。

如果开启并且正确配置了，LuckPerms 可以使用消息系统来通知其他连接的服务器更改。使用命令 `/luckperms networksync` 来推送更改，使用这个服务不会存储数据，只是用于消息平台。

如果你决定开启这个功能，你应该设置 "sync-minutes" 为 -1，因为没有必要将数据推至数据库。

**可用的选项：**

* **`bungee`** - 使用插件的 messaging channel。必须在所有的子服务器开启才能使用，并且要在 Bungee 安装 LuckPerms。
* **`lilypad`** - 使用 LilyPad 的 pub sub 来推送更改。你需要安装 LilyPad-Connect 插件。
* **`redis`** - 使用 Redis 的 pub sub 来推送更改。
* **`none`** - 啥都没有！


##### 示例
```yaml
messaging-service: none
```

___
### `auto-push-updates`

LuckPerms 是否应该在命令执行后自动推送更改。


##### 示例
```yaml
auto-push-updates: true
```

___
### `redis`

Redis的设定。

* **`address`** - redis 使用的地址，默认使用默认端口（6379），如果你有特定的端口，请使用 `host:port`。
* **`password`** - 使用 Redis 需要的密码。留空则不使用验证。


##### 示例
```yaml
redis:
  enabled: true
  address: localhost
  password: 'passw0rd'
```
