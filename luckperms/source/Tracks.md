虽然其他一些插件也提供了一些相似的功能，LuckPerms 插件拥有它自己独特的权限组路线系统。

请将“权限组路线”试做一种“梯子”或“晋升路线”。

### 示例 1
我创建了一个叫做“staff”的权限组路线，这权限树包括以下组：

**default :arrow_right: helper :arrow_right: mod :arrow_right: admin**

然后我就能使用权限组路线来为玩家升级或降级。

例如，玩家“Notch”在helper权限组里，我想将他升到“mod”组，我需要运行

`/luckperms user Notch promote staff`

### 示例 2
我又为赞助商新建了一个权限组路线，包括以下组：

**default :arrow_right: iron :arrow_right: gold :arrow_right: diamond**

当玩家购买了“权限组提升”这类的东西时，我能使用权限组路线为玩家晋升权限等级。

`/luckperms user Luck promote donator`

要想让玩家在某条权限组路线中降级的话，请使用降级命令。

## 创建权限组路线
请运行 `/luckperms createtrack <name>` 命令，然后使用 `/luckperms track <name> append <group>` 来将权限组加入路线中。

帮助编辑路线的命令也还有几条，你可以在命令使用页面找到。