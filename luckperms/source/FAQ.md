# 常见问题
这些是我经常被问到的问题，我很高兴你在直接问我之前看了这些问题。

### 我在用 EssentialsChat 然后它不工作了
请确保你在使用最新版的 [EssentialsX](https://ci.drtshock.net/job/essentialsx/) 并且你安装了 [Vault](https://dev.bukkit.org/bukkit-plugins/vault/)。EssentialsX 的 X 是很重要的，老的版本不会工作。

### 我在哪里安装 LuckPerms 呢？
如果你在运行很多的服务器，你应该将 LuckPerms 放入每个服务器的 plugins 文件夹。

如果你想使用 BungeeCord 来应用权限，你需要将 LuckPermsBungee.jar 放入 BungeeCord 插件文件夹。

如果你选择只在 BungeeCord 安装 LuckPerms，他将不会影响任何 Spigot/Sponge 服务器的权限检查，如果你想要使用 LuckPerms，你必须将 LuckPerms 安装在这些服务器。


### 我可以只在 BungeeCord 安装 LuckPerms 吗？
在 BungeeCord 上的权限系统是完全独立于 Spigot/Sponge 服务器的。

如果你想让 Spigot/Sponge 的权限检查被 LuckPerms 处理的话，在每个 Spigot/Sponge 服务器都安装 LuckPerms。

如果你想让 BungeeCord 服务器的权限检查被 LuckPerms 处理，在 BungeeCord 服务器安装 LuckPerms。

你可以**只**在 BungeeCord 安装 LuckPerms，但是 Spigot/Sponge 服务器的权限检查将不会被 LuckPerms 处理。


### 我应该怎样在多个服务器中同步权限呢？
将每个 LuckPerms 连接到同一个 MySQL/MongoDB 服务器，你可以使用 /luckperms sync 来从数据库获得最后的权限更新。你也可以 [建立一个通讯服务](/Instant-Update-Propagation.md#messaging-services) 来立刻在你的服务器之间同步更改。


### LuckPerms 不能连接到我的 Redis 服务器
检查以下是否正常：

* 你正在使用正确的地址和端口
* 你的密码是正确的
* 没有防火墙规则阻拦了连接
* Redis 服务器正在运行

### LuckPerms 不能连接到我的 MySQL 服务器
检查以下是否正常：

* 你正在使用正确的地址和端口
* 你使用了正确的用户名 / 密码
* 数据库存在并且用户可以访问
* 该服务器在线并且接受连接
* 没有防火墙规则阻拦了连接
* MySQL 正确绑定了端口，并且安装 LuckPerms 的服务器可以访问
* 检查 MySQL 的连接限制没有超过，默认 LuckPerms 会使用 10 个连接，如果你有过多的插件连接了同一个服务器，你需要增加这个限制。

如果你得到了 `Communications link failure` 的错误，或者由于超时导致的错误，那么上面的有一条是不正常的。

给玩家 LuckPerms 表的权限，使用
```sql
GRANT ALL PRIVILEGES ON [databasename].* TO '[username]'@'[ipaddress]';
```
记得替换 [ ] 里的东西。

比如：
```sql
GRANT ALL PRIVILEGES ON luckperms.* TO 'luck'@'%';
```

接着当你完成这个更改后，使用
```sql
FLUSH PRIVILEGES;
```
