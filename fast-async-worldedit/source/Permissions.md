### 要想获得跟指令相关的权限请： [查看这里](/Commands.md)
# 权限：
### 管理员权限：
 - `fawe.admin` （允许通过使用 `/wea` 命令来跳过检测）
 - `fawe.bypass` （自动跳过 WorldEdit 的区域限制）
 - `worldedit.anyblock` （跳过 WorldEdit 插件的 `disallowed-blocks` 的限制）
 - `worldedit.inventory.unrestricted` （当背包限制启用时，跳过该限制）

### 用户权限：
 - `fawe.limit.<限制组名>` （给予玩家给定组的限制）
 - [`fawe.permpack.basic`](https://github.com/c7w/FastAsyncWorldedit/blob/master/bukkit/src/main/resources/plugin.yml#L29) （对于创造服来说可以使用的一堆 WorldEdit 权限）
 - `worldedit.navigation.jumpto.tool` （能够使用 jumpto 魔杖的权限）
 - `worldedit.navigation.thru.tool` （能够使用 thru 魔杖的权限）

### 区域权限：
>FAWE 模式是被区域所限制的，这对于想给予普通玩家 WorldEdit 权限的服务器来说是很有用的。要想起用区域限制，将配置文件中的 `region-restrictions` 设置设置为 true，然后给予玩家对应的区域权限。如果你想让管理员在任何地方都可以使用 WorldEdit 的话，请使用  `//wea` 命令，给予他们 `fawe.admin` 权限。

 - `fawe.factions`
 - `fawe.plotsquared`
 - `fawe.plotsquared.member` - 允许地皮的成员（`/plot add`）使用 WorldEdit 
 - `fawe.griefprevention`
 - `fawe.plotme`
 - `fawe.preciousstones`
 - `fawe.residence`
 - `fawe.towny`
 - `fawe.towny.*`
 - `fawe.worldguard`
 - `fawe.worldguard.member`

### 延展的 WorldEdit 命令：
 - `worldedit.schematic.load.other` （在每个玩家的schematic储存文件分离时，允许玩家读取主schematic文件夹下的所有文件）
 - `worldedit.schematic.save.other` （在每个玩家的schematic储存文件分离时，允许玩家储存文件到主schematic文件夹下）