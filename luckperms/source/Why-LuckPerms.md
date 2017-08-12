<!--- https://paste.lucko.me/HWn0fZKoJn -->
## 这是另外一款全新的权限插件？
是的，我认为LuckPerm相比其他权限插件还有很大的发展空间。

LuckPerm是一款先进、高等的权限插件，仅仅以**快速**、**稳定可靠**、**灵活多变**的特点，
便可以替代现有的许多权限插件，例如PermissionsEX、GroupManagerX、z/bPermissions、BungeePerms等主流权限插件。
LuckPerms这个插件的计划，本来是围绕着两个主要特点来制作的：高性能、强大且广泛的功能，
填补其他同类插件的功能缺陷、并且建立在同类现有功能上更进一步的优化功能。
LuckPerms还包括了非常广泛的API支持，这是为开发人员的添加的，
并且，luckperms还兼容各式各类Minecraft服务器软件&支持多种数据存储的选择。

## 我已经使用某插件很长一段时间了，它对我的帮助很大，我也很熟悉它了，为什么我要更换它而选择LuckPerm呢？
现在主流的权限插件大多数都是老牌插件了，并且都是在Bukkit早期就被创造出来了。
虽然，这可能意味着它们非常的稳定可靠，但通常也意味着它们被原作者抛弃，并且一般不会再有任何更新、修复，
但LuckPerm却任然是一个需要成长、需要磨砺的插件！

我会尽力及时查看并回复所有的bug报告、问题，以及可实现的新功能建议

## 你说的不错，但是我更加偏爱某插件，因为仅凭它就完成了我需要的一切
这没关系，我完全理解你的这种心态，我并不是想要说你**必须**用LuckPerm来作为你服务器的权限插件。
当然还有更多适合你服务器权限插件，但是LuckPerm确实是个很棒的选择，不是么？

## 来吧兄弟，告诉我，我为什么要使用LuckPerm？
LuckPerm能做很多事情，至少单在技术层面，LuckPerm就胜过大部分同类插件。
我认为这不取决于我制作插件的水平，而是取决于我在LuckPerm上面花费的精力与时间。

LuckPerm是我在2016年开始准备编写的插件，但因为Bukkit变得流行起来，许多同一时期的插件都变成了老牌稳定插件，
不过，这也为我编写LuckPerm提供的很好的参考帮助，因为我可以避免其它同类插件的缺陷，
并且明白它们哪些地方做的特别出色，我可以在其基础之上进一步优化，使那部分功能变得更加引人瞩目。

记着，如果你对LuckPerm技术性方面的内容感兴趣，我推荐你从[命令使用](/Command-Usage.md)部分开始阅读
或者看看wiki列出的其他部分内容，在本节的其余部分，我会将阅读重点放到LuckPerm一些全新的特色功能上面。

这些内容是你不太可能从其他插件中找到的，专属luckPerm的特色功能！

### Verbose（权限查看系统）
LuckPerm有一套完整的权限查看系统，是的，它叫做[verbose](/Verbose.md)。
他可以实时监视并检测其他插件所需的权限，就像下面示例的动态图那样：

[![](https://thumbs.gfycat.com/FearlessVelvetyBellfrog-size_restricted.gif)](https://gfycat.com/FearlessVelvetyBellfrog)

[![](https://thumbs.gfycat.com/DistortedMetallicLabradorretriever-size_restricted.gif)](https://gfycat.com/DistortedMetallicLabradorretriever)

你也可以把录像上传到网上，方便查看、分析和阅读：
[https://git.io/vQitM](https://git.io/vQitM)

### 权限树系统
LuckPerm允许你在服务器所有已知权限上建立编写"权限树"。
权限树上的数据是由你所有的插件在服务器注册的权限构成的。

随着你服务器运营时间的增长，因为服务器添加了许多插件，它们都会注册权限，这些数据都会被纳入权限树中。

这是个清真的例子 [https://git.io/vQiti](https://git.io/vQiti)。
你看到的权限树的颜色，代表了你的玩家是否拥有对应的权限，这一机制很方便的让你查阅到服务器的相应权限。

这还是那个清真的例子 [https://git.io/vQiti](https://git.io/vQiti)

### 指令界面&TAB补全
LuckPerm的指令系统被我设计的尽可能便捷、易用、人性化，
这样一来，你除了查阅LuckPerm的[大量相关帮助文档](/Command-Usage.md)，还可以在游戏中查看指令用法、以及指令列表。

![](http://i.imgur.com/XIVPP6P.png)

LuckPerm的所有指令皆可使用TAB补全功能，这就意味着，你可以通过输入更少的指令来完成你的工作！
这是不是在一定程度极大地提高了你的工作效率呢？就像下面那样：

[![](https://zippy.gfycat.com/AnnualYoungKoi.gif)](https://gfycat.com/AnnualYoungKoi)

### 网站编辑器
除了使用指令来编辑服务器权限相关，LuckPerm还提供了更加便捷的编辑方式，
你可以使用Web网站编辑器来对服务器的权限数据进行快速更改，
任何人都能够使用网站编辑器，不论你使用了哪种存储方式！

网站编辑功能非常容易使用，且易于上手

[![](https://thumbs.gfycat.com/MeanThatChinesecrocodilelizard-size_restricted.gif)](https://gfycat.com/MeanThatChinesecrocodilelizard)

### 行为记录仪
为了防止服务器中出现心存不轨的管理员，想要私自给自己添加权限，
LuckPerm详细的记录了服务器各类权限的微小变化，
你可以通过行为记录仪来搜索每个人的详细操作。

![](http://i.imgur.com/Jfu8XCI.png)

你也可以查看所有东西的详细历史。