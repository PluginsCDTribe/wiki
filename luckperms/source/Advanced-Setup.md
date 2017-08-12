## 简介：
LuckPerm总体来说虽然是相对简单的..
你可以利用插件的一些特点与内部规则来制定一个适合你服务器情况的高等权限系统！

## 分服务器权限&分世界权限：
LuckPerm本来是针对群组服的情况来工作的，
但是你可以自定义一些只在特定子服/特定世界才生效的权限。

#### 配置中一些重要的选项说明：
```yml
# The name of the server, used for server specific permissions. Set to 'global' to disable.
server: global
```
该项为设置服务器的名称，如果要想设置特定服务器的权限，则需要通过修改server项来命名服务器。
如果你愿意，同一个群组服是可以一起使用相同的服务器名的。

```yml
# If users on this server should have their global permissions/groups applied.
include-global: true
```
include-global选项也是非常重要的。

LuckPerm有两种体现方式，一是特定服务器的权限，二则是直接应用全局权限设置。

如果这个选项被设置为 false，只有指定在此服务器的权限才会被应用。

如果上方的 "server" 选项设置为 global，请不要将其设置为 **false**。更多的有关服务器指定的权限可以在这里找到。
通过编辑更改这两个选项，你可以灵活的为每个服务器的权限组/权限做出意想不到的配合效果

### 示例
#### 示例 1
```yml
server: global
include-global: true
```
* /luckperms user Luck set minecraft.command.gamemode true **将应用**
* /luckperms user Luck set minecraft.command.gamemode true factions **不应用**

#### 示例 2
```yml
server: lobby
include-global: true
```
* /luckperms user Luck set minecraft.command.gamemode true **将应用**
* /luckperms user Luck set minecraft.command.gamemode true lobby **将应用**

#### 示例 3
```yml
server: bungeecord
include-global: false
```
* /luckperms user Luck set minecraft.command.gamemode true **不应用**
* /luckperms user Luck set bungeecord.command.alert true bungeecord **将应用**

#### 示例 4
```yml
server: global
include-global: false
```
**没有任何权限将会应用！**

如果没有设置服务器名字（server项设置为global）且全局设置未开启（include-global项设置为flase），
将不会有任何权限可以应用到服务器上！

## 权限计算
### 权限是根据优先级进行计算的，如下所示
* **服务器特定的权限是会覆盖通用/全局权限设置的**

例如：有一个玩家，我们姑且叫他海螺，他拥有一个全局的“fly.use”（允许飞行）权限，
然后在“factions”这个服务器上，取消了“fly.use”权限，服务器的特定权限设置将会覆盖全局设置。
即，这个海螺在“factions”服务器上是无法使用“fly.use”权限的，他就不能够上天了，
前提是海螺现在正在“factions”服务器上。

* **世界特定的权限也是会覆盖通用/全局权限设置的**

例如：上文我们说的玩家“海螺”，他现在任然有一个全局的“fly.use”权限，
然后在“world_nether”（地狱）世界，取消了“fly.use”权限，世界的特定权限设置将会覆盖全局设置。
即，这个海螺在地狱就无法上天了（只要海螺在地狱世界）。

* **临时权限将会覆盖非临时权限**

例如：如果玩家海螺本来关闭了一个权限“test.node”，
以此为基础，服务器给海螺设置新的临时权限“test.node”，
海螺的临时权限则会覆盖本身关闭的权限，即海螺会在特定时间（临时权限）获得“test.node”权限。

* **如果同时有两个节点相同、但时长不同的临时权限，时间较长的会覆盖时间较短的**


* **更加具体的通配符权限将覆盖不具体的通配符权限**

例如：一个用户拥有权限“luckperms.*”并且设置为true，但是“luckperms.user.*”权限却设置为false，
那么所有玩家的权限都将被设置为false！
因为尽管“luckperm.*”有更加通用的通配符，但是他没有“luckperms.user.*”具体。

* **继承权限将由对象自己的权限来重写**

例如：一个玩家是默认权限组的成员，默认权限组有“some.thing.perm”权限，
但是这个玩家又被以用户形式给予了权限“some.thing.perm”，
继承而来的权限将会被玩家自己的权限给覆盖。

## 临时权限
临时权限每间隔3s会检查一遍，检查临时权限的时限是否到期，
不论同步间隔设置的怎么样，这个检查都会照常工作，这意味着你可以安全的设置临时权限在几秒后过期，
他们将会在时限到期时被删除。

## 速记权限
LuckPerms有他自己的速记权限系统，在这一点上，它非常类似PermissionsEx，
它允许你使用速记格式来设置权限。

### 示例
#### 示例 1
使用LuckPerm的允许节点来作为例子，比如说，你想让一个用户组与用户权限设置/取消允许节点，

如果没有速记，你就必须键入下面四个节点。
```
luckperms.user.setpermission
luckperms.user.unsetpermission
luckperms.group.setpermission
luckperms.group.unsetpermission
```
但是，你要是使用速记，你就可以应用以下节点：

`luckperms.(user|group).(setpermission|unsetpermission)`

你可以使用括号来让一个节点成为一个速记的权限组，然后用 `|` 来分隔他们

#### 示例 2
你可以使用“-”来创建字符范围，如果没有使用速记，则必须键入以下四个节点：
```
coolkits.kit.a
coolkits.kit.b
coolkits.kit.c
coolkits.kit.d
```
然而，使用了速记方法，你只需应用下面的节点：

`coolkits.kit.(a-d)`

#### 示例 3
你可以使用“-”来创建字符范围，如果没有使用速记，则必须键入以下四个节点：
```
prisonmines.teleport.1
prisonmines.teleport.2
prisonmines.teleport.3
prisonmines.teleport.4
```
不过，你只要使用速记方法，这一切都会变得简单许多！你只需要应用下面的节点：

`prisonmines.teleport.(1-4)`

## 正则表达式
LuckPerms支持使用正则表达式来定义权限节点与服务器/世界的名字，
当使用正则表达式的时候，必须添加前缀“R=”。
所以LuckPerm才会知道将它是作为正则表达式来输出，而不是作为普通的字符串来输出。

例如：你希望玩家可以创建两个组与权限系（tracks），通常只需要添加两个权限节点。
然而使用正则表达式，你只需要添加一个权限节点 `luckperms\.create.*` 。
记住，转为任何字符，例如一个点，都将作为一个节点被系统解析。
