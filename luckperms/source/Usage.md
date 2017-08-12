这篇教程是为之前从来没有使用过权限管理插件的人所准备的。
如果你已经很熟悉权限管理等相关概念了的话，我认为你应该就能够理解命令中的东西了。
这样我就推荐你去阅读[命令和权限](/Command-Usage.md)页面，这样更加“直奔主题”，你也能够更容易理解插件的工作方法。

如果你正在努力想弄明白权限管理相关概念的话，这篇教程就是你起步的最佳地方:)


# 关键术语
### 权限
在你的服务器上会有大量的**特性，命令和一些新功能**。
这其中的一些特性是服务器自带的，另一些是由“插件”所添加的。
与这些特性相联系的大多数行为都是由权限所控制的，因此你可以控制哪些用户可以使用你指定的特性或权限。
 
**权限仅仅是个字符串**，并且使用英文的句号（半角 → . ←）分成几部分。
举个例子， “minecraft.command.ban” 就是原版 /ban 命令所使用的权限。
显然我们不想让所有用户都能执行这个命令，所以我们只给我们信任的玩家这个权限。

代表特定行为的使用许可的字符串，我们就称之为权限，它又名“权限节点”，简称“权限”。

### 权限组

代替单独为每个用户设置权限，我们可以将**权限捆绑为一组**，然后直接将这一组**给予玩家**。

举个例子，在我设置的“admin”权限组中，我可能会添加使用ban和unban指令的权限，然后将玩家加入admin权限组中。
这意味着他们能够获得“admin”权限组所设置的所有权限和他们自身被设置的权限。


### 继承

用户和权限组能够**互相继承权限**。
举个例子，默认地，所有的用户都会从“default”权限组继承权限。
你可以为你自己的服务器设置你自己的权限组与继承方式，或是制作你自己独特的系统。

举个例子，我设置了三个权限组， “default”， “moderator” 和 “admin”。
我想让“moderator”权限组从“default”权限组继承所有权限，“admin”权限组从“moderator”权限组继承所有权限。

# 起步

如果你还没有将LuckPerms插件安装在你的服务器上的话，我们推荐你先阅读[安装](/Setup.md)有关的教程。

然后，请确保你在继续之前已经阅读了[选择数据存储类型](/Choosing-a-Storage-type.md)的有关章节。
虽然你在后期也能实现数据之间的转移，但第一次就将他们弄对位置是更好的。

## 给予修改权限的全部权限
你想做的第一件事情就是给你本插件的所有权限。
当本插件首次安装后，没有人能够使用LuckPerms插件的有关命令。

要想做到这个的话，你需要在服务器控制台输入 `/luckperms user Luck permission set luckperms.* true` 。
当然，请把我的名字换成你自己的（不用担心，这条命令的使用方法之后会详细讲解）

这应该就是运行的结果：
 ![](http://i.imgur.com/zaw4l7q.png)

实际上，这条命令起的效果，就是给了 `Luck` 用户 `luckperms.*` 权限。（或者说，为用户设置权限为 true）

你可能已经注意到了我们刚才在权限字符串的末端使用的 `*` 字符了。
这个字符叫做通配符，它会给玩家**所有**以 "luckperms" 为开头的权限。

## 创建第一个权限组
我们可以使用创建权限组命令来创建一个新的权限组。

让我们创建一个叫做“admin”的权限组，然后给它附加一条权限吧。

首先，运行 [`/luckperms creategroup admin`](/Command-Usage.md#lp-creategroup) 命令。
这会创建一个叫做“admin”的空权限组。

![](http://i.imgur.com/3mz08n1.png)

接下来，我们想为“admin”权限组增加一条权限。
用来修改权限组的命令是 [`/luckperms group <group>`](/Command-Usage.md#group---lp-group-group-)。
如果你执行这条命令的话，它会为你显示所有可用的子命令。

![](http://i.imgur.com/CPiZK5G.png)

你可能注意到了第一个子命令是“info”命令。它只会列举出一些权限组相关的信息。

我们可以运行 [`/luckperms group admin info`](/Command-Usage.md#lp-group-group-info) 来查看新建立的“admin”权限组的一些信息。

![](http://i.imgur.com/agliG4f.png)

接下来就是“permission”命令。这能够帮助你修改权限组的权限。
再一次，使用 [`/luckperms group admin permission`](/Command-Usage.md#permission---lp-user-user-permission---lp-group-group-permission-) 命令会列出所有可用的子命令。

![](http://i.imgur.com/T4P5YFy.png)

再一次，我们看到了更多我们可以执行的命令。
第一个就是另一个 "info" 子命令。
因为它是“permission”子命令下的又一子命令，它就会显示某一权限组所拥有的所有权限。

下面的命令是“set”子命令。

你还记得吗，之前我们使用相似的指令来给玩家 "luckperms.*" 权限。这里它也相同
只需要不加参数运行该命令就可以返回该命令的使用方法。举个例子：

![](http://i.imgur.com/8h16DV0.png)

举个例子，我想给我的“admin”用户组 "minecraft.command.ban" 权限。
因此我可以输入 [`/luckperms group admin permission set minecraft.command.ban true`](/Command-Usage.md#lp-usergroup-usergroup-permission-set) 。

![](http://i.imgur.com/McXI5Nx.png)

这条命令就会给予 `admin` 用户组 `minecraft.command.ban permission` 权限。
末端的true控制我们设置的权限的启用与否。
你可以将权限的启用与否设置为 `true` 或 `false` 。
为用户或权限组将权限设置为 true 能够让他们拥有该权限，设置为 false 即该权限无效。（指定他们没有该权限）

如果晚些时候我决定不再让“admin”用户组拥有这个权限了，我可以使用 unset 命令来移除该权限的设定。
输入 [`/luckperms group admin permission unset minecraft.command.ban`](/Command-Usage.md#lp-usergroup-usergroup-permission-unset) 。

![](http://i.imgur.com/x1ecIQo.png)

## 将玩家加入到权限组中
将用户加入到权限组中需要使用 "parent" 命令。（在我们的命令使用页我们经常用“permission”替换“parent”）

举个例子，把我自己加入“admin”权限组中，我需要使用 [`/luckperms user Luck parent add admin`](/Command-Usage.md#lp-usergroup-usergroup-parent-add) 。

![](http://i.imgur.com/eScw7gC.png)

这条命令会将用户 `Luck` 加入到 `admin` 权限组中。
这意味着任何“admin”权限组所拥有的权限我现在也继承下来了。

## 让一个权限组继承另一个权限组
就像用户能够继承一样，权限组也能够继承另一个权限组。

举个例子，想想下面这种情况的设置方法。（有些权限仅仅是为了演示而编造出来的）

| Admin | Mod | Default |
|-------|-----|---------|
| minecraft.command.ban | minecraft.command.mute | minecraft.command.say |
| minecraft.command.pardon | minecraft.command.unmute | minecraft.command.me |
| some.cool.admin.perm | some.cool.mod.perm | |
| someplugin.vanish | chatcolor.bold | |

我想让“admin”权限组中的用户拥有“mod”和“default”权限组的权限，同时“mod”权限组中的用户拥有“default”权限组中的权限。要想实现这个的话，我可以设置用户组之间的相互继承。

[`/luckperms group admin parent add mod`](/Command-Usage.md#lp-usergroup-usergroup-parent-add) 命令会让“admin”权限组继承所有“mod”权限组中的权限。

然后要想让“mod”继承“default”，同样的道理，我可以输入 `/luckperms group mod parent add default`。

![](http://i.imgur.com/tYcKGe6.png)

继承是可递归的，所以这样以后“admin”权限组就不仅仅继承了“mod”权限组，还继承了“default”权限组。
这意味着“admin”权限组中的玩家拥有“mod”**和**“default”两权限组中的权限了。

在“admin”组的一位用户因此拥有 `minecraft.command.ban`，`minecraft.command.mute` *和* `minecraft.command.say` 权限。

## 移除继承权限组
要想移除权限组间的继承关系只需要输入一个类似的命令就好了。

要想让我自己不再继承“admin”权限组，我只要输入 [`/luckperms user Luck parent remove admin`](/Command-Usage.md#lp-usergroup-usergroup-parent-remove) 就好了。

![](http://i.imgur.com/Fa4Mlgs.png)
