这教程包括如何使用LuckPerms插件设置和管理玩家的前缀，后缀以及元数据。

如果你已经对这些概念很熟悉了，或是只想查看本插件如何实现更改，你应该阅读[命令使用](/Command-Usage.md#meta---lp-user-user-meta---lp-group-group-meta-) 页面的 “section” 小节。

# 关键术语
### 前缀/后缀
Minecraft服务器上的前缀和后缀代指你聊天用户名前后的文本。

举个例子，在下列的聊天中：
```
[Admin] Luck the great: Hello!
```
玩家的前缀是`"[Admin] "`部分，玩家的后缀是`" the great"`部分。

### 元数据
有时元数据指“选项”或“变量”，元数据是跟权限组有关的额外数据部分。与权限不同的是，元数据分成两部分，一部分是“关键字”，另一部分是“值”。

关键字就是元数据的名字，值就是关键字所代表的数据。

举个例子，我的用户有下列的元数据，这元数据代表我最多能设置5个家，然后我的用户名应该是蓝色的。
```
max-homes = 5
username-color: blue
```

## 是谁提供了对这些的支持？
一般来说，提供服务器管理权限的插件就有能够让你设置，管理和储存玩家的前缀，后缀和元数据的功能，这对于LuckPerms插件来说也一样。、

有时，提供这些设置的权限插件也能够直接在游戏中应用这些值。但是这对于LuckPerms来说不是它能做到的任务，你需要安装另一款额外的插件来在游戏聊天中应用，关于这点我们稍后详述。

## 前缀/后缀/元数据是怎么存储的
LuckPerms 插件将前缀和后缀转换成权限节点来存储。你可能会注意到当你给一位用户或一个权限组添加权限的恶化，他们的权限信息中会多出一条跟你设置的值相同的权限数据。为什么要这样做呢？好的，从编程的角度来说，让所有东西都储存在一个地方，用相同的格式，这样做更简单。这也意味着你能够简单的更改前缀和后缀，就像你改权限的方式一样。

前缀和后缀分成了两部分
* **Weight** —— 这是决定着前缀和后缀优先级的数值，较大的数代表着较大的优先级。
* **Value** —— 这是真正的前缀的值。

例如一个叫做 "[Admin] " 的前缀，优先级设置为100，转换成权限就是： `"prefix.100.[Admin] "`。

对于元数据来说所使用的系统也相似，元数据组合 `favourite-color = red` ，转换成权限就是：`"meta.favourite-color.red"`.

## 前缀和后缀的优先级是怎么工作的
前缀和后缀和权限一样，也能够继承。这意味着LuckPerms插件需要决定，当需要显示前缀或后缀时，真正为玩家显示哪一个。

当另外一款插件请求玩家的前缀或后缀时，LuckPerms插件会：
* 收集玩家的所有前缀与后缀，包括继承的
* 根据他们的优先级来进行分类，高的优先级数值代表高的优先级
* 然后决定出最高优先级的前缀或后缀来为玩家展示

如果发现了两个相同优先级的前缀或后缀的话，最接近于用户的那一个会被使用，接近的意思就是插件在搜索继承数据时最先找到的那一个。

## 我怎么为玩家设置前缀或后缀
举个例子，如果我想让admin权限组的玩家拥有 "&c[Admin] " 前缀，在mod权限组的玩家拥有 "&d[Mod] " 前缀的话，我需要运行：

* /lp creategroup admin
* /lp creategroup mod
* /lp group admin parent add mod
* /lp group admin meta addprefix 100 "&c[Admin] "
* /lp group mod meta addprefix 90 "&d[Mod] "

然后如果我决定想要将admin用户组的称号改为使用 "&4" 这个颜色代码的话，要想删除之前设定的值，我需要运行：
* /lp group admin meta removeprefix 100

这会将所有设定给admin权限组的，优先级为100的前缀全部移除，然后我就能重新设置新的前缀值了。

对于临时设定用户前缀或后缀的方法和增加临时权限或临时权限组的方法差不多。

所有的权限使用方法可以在[**权限使用页面**](/Command-Usage.md#meta---lp-user-user-meta---lp-group-group-meta-)找到。增加和移除元数据的方法也列在了那里。

## 我怎么查看一位玩家或一个用户组所有的前缀或后缀
解决前缀或后缀相关问题最简单的方式就是使用info命令。

举个例子： `/lp user Luck meta info`。这会将用户所有的前缀，后缀和元数据，以及继承的相关信息列举出来。

按照优先级来排序，所以你就能很清楚的看到目前应用的值是哪一个。

另外一条有趣的命令就是玩家的全局信息命令： `/lp user Luck info`。

如果玩家在服务器上在线的话，这会直接给你展示所提供给要读取LuckPerms信息的插件的前缀或后缀。

## 展示前缀和后缀
就像早些时候提到的那样，LuckPerms插件不会为你处理任何的聊天格式相关信息。

你需要安装额外的插件来做到这个。

下面为你列出了一些推荐的聊天管理插件。

### Bukkit/Spigot
LuckPerms 目前已经支持**所有**能够从 [Vault](https://dev.bukkit.org/projects/vault) 插件读取信息的聊天管理插件了。

你需要在你的服务器上安装Vault来让其工作。

如果你发现某款插件所获取的数据不正确的话，请确保 `/vault-info` 插件输出的信息展示的数据是从LuckPerms插件处读取的。

一些较为受欢迎的，且支持Vault的聊天管理插件包括：
* [EssentialsXChat](https://ci.drtshock.net/job/EssentialsX/) —— 原来的Essentials插件的升级复刻版本。（“X” 是很重要的！）
* [ChatEx](https://dev.bukkit.org/projects/chatex)
* [DeluxeChat](https://www.spigotmc.org/resources/deluxechat.1277/) —— 你能够使用Vault或LuckPerms所提供的Placeholder变量。
* [ChatControl](https://www.spigotmc.org/resources/10258/) —— 也支持其他选项的设置来帮助管理聊天。

列举出所有可用的插件没有任何意义，再说一遍，所有支持Vault的聊天管理插件都支持LuckPerms！


### BungeeCord
* [gChat](https://github.com/lucko/gChat) (我写的 :wink:)
* [MultiChat](https://www.spigotmc.org/resources/multichat.26204/)
* [BungeeChat](https://www.spigotmc.org/resources/bungee-chat.12592/)

### Sponge
* [Nucleus](http://nucleuspowered.org/) —— 就像是“Essentials”一样的插件，包括 [聊天管理模块](http://nucleuspowered.org/docs/modules/chat.html).