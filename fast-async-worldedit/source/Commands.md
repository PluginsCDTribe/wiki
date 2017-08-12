## 总览
本页面是由资源文件生成的。点击下列指令旁边的编辑（edit）按钮来直接修改命令的类。

你需要找到跟帮助文档对应的命令的相关部分。

命令的帮助文档与游戏中可使用的命令是一致的。

要想在游戏中查看这些信息的话请使用 `//help [类型|命令]`
## 命令的用法   
 - `<arg>` - 一个必需参数     
 - `[arg]` - 一个可选参数     
 - `<arg1|arg2>` - 提供的多选一选项     
 - `<arg=value>` - 默认或建议你使用的值     
 - `-a` - 一条命令的标记，如 `//<command> -a [命令的标记的值]`
## 也请看看
 - [Masks](/WorldEdit---FAWE-mask-list.md)
 - [Patterns](/WorldEdit-and-FAWE-patterns.md)
 - [Transforms](/Transforms.md)

## 目录
点击类型的名字去查看该类型下命令的列表，或者点击 `更多信息` 获取更多详细信息
 - [`World Edit 命令`](#world-edit-命令-编辑回到顶部)  （更新，信息，调试以及帮助命令）
 - [`工具命令`](#utility-命令-编辑回到顶部)  （一些工具的命令： [更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Utilities)）
 - [`区域命令`](#region-命令-编辑回到顶部)  （一些对区域起作用的命令： [更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Region_operations)）
 - [`选区命令`](#selection-命令-编辑回到顶部)  （变更你的选取点，模式或是查看你当前选区的有关信息： [更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Selection)）
 - [`历史命令`](#history-命令-编辑回到顶部)  （撤销，反撤销，清除历史记录的有关命令： [更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Features#History)）
 - [`Schematic 命令`](#schematic-命令-编辑回到顶部)  （跟 schematic 文件有关的命令）
 - [`剪切板命令`](#clipboard-命令-编辑回到顶部)  （跟复制和粘贴方块有关的命令： [更多信息](https://goo.gl/z2ScQR)）
 - [`生成命令`](#generation-命令-编辑回到顶部)  （创建结构或特性： [更多信息](https://goo.gl/KuLFRW)）
 - [`生物群系命令`](#biome-命令-编辑回到顶部)  （改变，列出或检查生物群系）
 - [`Anvil 命令`](#anvil-命令-编辑回到顶部)  （操纵超大量的方块： [更多信息](/Anvil-API.md)）
 - [`超级镐子命令`](#super-pickaxe-命令-编辑回到顶部)  （超级镐子命令： [更多信息](https://goo.gl/aBtGHo)）
 - [`导航命令`](#navigation-命令-编辑回到顶部)  （关于让玩家在地上移动的命令： [更多信息](https://goo.gl/uQTUiT)）
 - [`快照命令`](#snapshot-命令-编辑回到顶部)  （列出，读取或查看有关快照的更多信息）
 - [`快照功能命令`](#snapshot-util-命令-编辑回到顶部)  （[更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Snapshots)）
 - [`脚本命令`](#scripting-命令-编辑回到顶部)  （运行 craftscripts 脚本： [更多信息](https://goo.gl/dHDxLG)）
 - [`区块命令`](#chunk-命令-编辑回到顶部)  （[旧版] 检索区块：[更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Chunk_tools)）
 - [`选项命令`](#options-命令-编辑回到顶部)  （玩家切换，设置与显示物品信息）
 - [`笔刷选项命令`](#brush-options-命令-编辑回到顶部)  （工具命令）
 - [`工具命令`](#tool-命令-编辑回到顶部)  （将某些功能绑定到持有的物品上： [更多信息](https://goo.gl/xPnPxj)）
 - [`笔刷命令`](#brush-命令-编辑回到顶部)  （能够从远处建筑的命令。 [更多信息](https://git.io/vSPYf)）
 - [`/Masks`](#/masks-编辑回到顶部)  （帮助设立蒙版。 [更多信息](https://git.io/v9r4K)）
 - [`/Patterns`](#/patterns-编辑回到顶部)  （对一些模板很有帮助。 [更多信息](https://git.io/vSPmA)）
 - [`/Transforms`](#/transforms-编辑回到顶部)  （对一些改造很有帮助。 [更多信息](https://git.io/v9KHO)）

#### 未分类的命令
| 别称 | 权限 | 标记 | 使用方法 |
| --- | --- | --- | --- |
| //cancel | fawe.cancel | | 取消你当前正在进行的任务 |
| /plot replaceall | plots.replaceall | | 替换地皮世界中所有的方块 |
| /plot createfromimage | plots.createfromimage | | 从一张高度图图片开始世界生成： [更多信息](/CreateFromImage.md) |

---
### **World Edit 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/WorldEditCommands.java)`]`
> （更新，信息，调试与帮助命令）    

---

#### `/we threads `
**权限**： `worldedit.threads`    
**描述**： 显示出所有的线程堆栈    
#### `/we version `
**描述**： 获取当前 WorldEdit / FAWE 插件的版本信息
#### `/we help [<command>]`
**权限**： `worldedit.help`    
**描述**： 显示出 FAWE 插件的命令帮助信息    
#### `/we debugpaste `
**权限**： `worldedit.debugpaste`    
**描述**： 将调试信息上传到 hastebin.com    
#### `/we changelog `
**权限**： `worldedit.changelog`    
**描述**： 查看 FAWE 插件的更新日志    
#### `/we reload `
**权限**： `worldedit.reload`    
**描述**： 重载插件配置    
#### `/we tz [timezone]`
**描述**： 设置你的快照的时间区域    
#### `/we cui `
**描述**： 完成 CUI 信息交换（内部开发使用）    

---

### **Utility 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/UtilityCommands.java)`]`
> (一些功能命令： [更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Utilities))    

---

#### `/remove <type> <radius>`
**权限**： `worldedit.remove`    
**描述**： 移除所有指定类型的实体    
#### `//fill <block> <radius> [depth]`
**权限**： `worldedit.fill`    
**描述**： 填充一块洞    
#### `//help [<command>]`
**描述**： 显示 WorldEdit 插件的帮助命令    
#### `//drain <radius>`
**权限**： `worldedit.drain`    
**描述**： 排开一片池塘内的水   
#### `//removenear <block> [size]`
**权限**： `worldedit.removenear`    
**描述**： 移除你附近的方块    
#### `//fillr <block> <radius> [depth]`
**权限**： `worldedit.fill.recursive`    
**描述**： 递归填充周围的洞    
#### `//removeabove [size] [height]`
**权限**： `worldedit.removeabove`    
**描述**： 移除你头上方的方块    
#### `//fixlava <radius>`
**权限**： `worldedit.fixlava`    
**描述**： 让岩浆静止   
#### `//removebelow [size] [height]`
**权限**： `worldedit.removebelow`    
**描述**： 移除你脚下方的方块   
#### `//fixwater <radius>`
**权限**： `worldedit.fixwater`    
**描述**： 让水静止   
#### `//green [radius] [-f]`
**权限**： `worldedit.green`    
**描述**： 绿化半径中的区域  
#### `//replacenear <size> <from-id> <to-id> [-f]`
**权限**： `worldedit.replacenear`    
**描述**： 替换附近的方块  
#### `//snow [radius]`
**权限**： `worldedit.snow`    
**描述**： 模仿下雪  
#### `/butcher [radius] [-p] [-l] [-a] [-n] [-g] [-b] [-t] [-f] [-r]`
**权限**： `worldedit.butcher`    
**描述**： 击杀附近的怪物，根据半径，如果没有特别给出半径的话则使用配置文件中的默认半径。<br />可用的标记：<br />  -p 也击杀宠物<br />  -n 也击杀 NPC<br />  -g 也击杀铁傀儡<br />  -a 也击杀动物。<br />  -b 也击杀中立生物<br />  -t 也击杀带有名字的怪物<br />  -f 相当于这以前所有标记的混合<br />  -r 也击杀盔甲架<br />  -l 目前啥都不能干
#### `//ex [radius]`
**权限**： `worldedit.extinguish`    
**描述**： 熄灭周围的火 
#### `//thaw [radius]`
**权限**： `worldedit.thaw`    
**描述**： 使周围的区域中的雪与冰熔化  
#### `//calc <expression>`
**权限**： `worldedit.calc`    
**描述**： 求一个数学表达式的值  
#### `//confirm `
**描述**： 确认一条命令   

---

### **Region 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/RegionCommands.java)`]`
> (一些对区域起作用的命令： [更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Region_operations))    

---

#### `//replace [from-mask] <to-pattern> [-f]`
**权限**： `worldedit.region.replace`    
**描述**： 用给定的方块替换选区中所有另一给定的方块
#### `//stack [count] [direction] [-s] [-a] [-m]`
**权限**： `worldedit.region.stack`    
**描述**： 重复选区中的内容<br />标记：<br />  -s 将上一堆叠的选取换挡为最终选区<br />  -a 跳过空气方块
#### `//set [pattern]`
**权限**： `worldedit.region.set`    
**描述**： 将选取设置为给定方块    
#### `//fall [replace] [-m]`
**权限**： `worldedit.region.fall`    
**描述**： 让选区中的方块掉落<br />-m 标记仅会让方块在竖直位置上下落。   
#### `//faces <block>`
**权限**： `worldedit.region.faces`    
**描述**： 建造出选区的墙壁，天花板和地板
#### `//center <block>`
**权限**： `worldedit.region.center`    
**描述**： 设置出选区的中心方块
#### `//hollow [<thickness>[ <block>]]`
**权限**： `worldedit.region.hollow`    
**描述**： 挖空本区域中的物体<br />你可定义挖空的部分用什么方块填充<br />厚度用曼哈顿距离来计算。
#### `//smooth [iterations] [-n]`
**权限**： `worldedit.region.smoothsnow`    
**描述**： 平滑化区域的陡峭程度。<br />-n 标记互让它仅更改自然生成的方块。<br />-s 标记让它只更改雪方块。
#### `//nbtinfo `
**权限**： `worldedit.nbtinfo`    
**描述**： 查看一个方块的NBT信息    
#### `//setskylight `
**权限**： `worldedit.light.set`    
**描述**： 设置一个选区的天空亮度    
#### `//line <block> [thickness] [-h]`
**权限**： `worldedit.region.line`    
**描述**： 在长方体选择区域的两个角落划出一条对角线线段。<br />仅能够在长方体选区中使用。<br />可用的标记：<br />  -h 仅会生成外形
#### `//getlighting `
**权限**： `worldedit.light.fix`    
**描述**： 获取某位置的亮度信息    
#### `//overlay <block>`
**权限**： `worldedit.region.overlay`    
**描述**： 在给定区域的顶层方块上方覆盖给定方块    
#### `//wea `
**权限**： `fawe.admin`    
**描述**： 跳过区域检测限制    
#### `//wer `
**权限**： `fawe.worldeditregion`    
**描述**： 选择你当前允许的区域    
#### `//fixlighting `
**权限**： `worldedit.light.fix`    
**描述**： 修复某位置的光照    
#### `//removelight `
**权限**： `worldedit.light.remove`    
**描述**： 移除某位置的光照    
#### `//curve <block> [thickness] [-h]`
**权限**： `worldedit.region.curve`    
**描述**： 过选择的点画一条曲线。<br />只能在使用凸多面体选区类型时才能使用。<br />Flags:<br />  -h 仅会生成外形    
#### `//naturalize `
**权限**： `worldedit.region.naturalize`    
**描述**： 顶层覆盖3层泥土，下面为石头    
#### `//walls <block>`
**权限**： `worldedit.region.walls`    
**描述**： 围上选区的四边    
#### `//setblocklight `
**权限**： `worldedit.light.set`    
**描述**： 设置选区中的方块亮度    
#### `//lay <block>`
**权限**： `worldedit.region.overlay`    
**描述**： 设置选区的顶层方块    
#### `//move [count] [direction] [leave-id] [-s]`
**权限**： `worldedit.region.move`    
**描述**： 将选区中的内容移动。.<br />  -s 标记会将选区换挡到目标位置。<br />  -b 也会复制生物群系<br />  -e 忽略实体<br />  -a 忽略空气<br />自动使用 <leave-id> 填充旧区域。    
#### `//forest [type] [density]`
**权限**： `worldedit.region.forest`    
**描述**： 在区域内生成森林    
#### `//flora [density]`
**权限**： `worldedit.region.flora`    
**描述**： 在区域内生成植物群
#### `//deform <expression> [-r] [-o]`
**权限**： `worldedit.region.deform`    
**描述**： 使用给定的表达式使区域变形<br />表达式对每个方块都会执行，它可以<br />将方块的x，y，z修改到新方块的位置<br />来实现。也请看看 tinyurl.com/wesyntax。    
#### `//regen [biome] [seed]`
**权限**： `worldedit.regen`    
**描述**： 重新生成当前选区中的内容。<br />这条命令也有可能影响选区外的东西，<br />如果它们在相同区块中的话。

---

### **Selection 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/SelectionCommands.java)`]`
> (改变你选区的点，选取模式或是查看关于你的选区的信息： [更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Selection))    

---

#### `//count <block> [-d]`
**权限**： `worldedit.analysis.count`    
**描述**： 为当前选区中某种类型的方块计数    
#### `//size  [-c]`
**权限**： `worldedit.selection.size`    
**描述**： 获取当前选区的信息    
#### `//expand <amount> [reverse-amount] <direction>`
**权限**： `worldedit.selection.expand`    
**描述**： 延展选区区域    
#### `//shift <amount> [direction]`
**权限**： `worldedit.selection.shift`    
**描述**： 移动选区区域    
#### `//sel [cuboid|extend|poly|ellipsoid|sphere|cyl|convex] [-d]`
**描述**： 选择选区类型    
#### `//contract <amount> [reverse-amount] [direction]`
**权限**： `worldedit.selection.contract`    
**描述**： 缩小选区区域    
#### `//pos1 [coordinates]`
**权限**： `worldedit.selection.pos`    
**描述**： 设置选取点1    
#### `//pos2 [coordinates]`
**权限**： `worldedit.selection.pos`    
**描述**： 设置选取点2   
#### `//chunk [x,z coordinates] [-s] [-c]`
**权限**： `worldedit.selection.chunk`    
**描述**： 将选取设置为当前你所在的区块。<br />写入 -s 标记你当前的选区会被延展<br />来包括所有为它的部分的区块。<br /><br />也可以使用给定的坐标，这会替代你的<br />当前位置。使用-c来指定区块坐标，<br />否则就会使用全局坐标。<br />（举个例子，坐标5,5和 -c 0,0 是一样的） 
#### `//hpos1 `
**权限**： `worldedit.selection.hpos`    
**描述**： 将选取点1设置为目标方块   
#### `//wand `
**权限**： `worldedit.wand`    
**描述**： 获取魔杖物品  
#### `/toggleeditwand `
**权限**： `worldedit.wand.toggle`    
**描述**： 切换编辑魔杖的功能启用与否   
#### `//hpos2 `
**权限**： `worldedit.selection.hpos`    
**描述**： 将选取点2设置为目标方块   
#### `//outset <amount> [-h] [-v]`
**权限**： `worldedit.selection.outset`    
**描述**： 使用给定的数值，在所有方向上延展选区。<br />可用标记：<br />  -h 仅会延展横向<br />  -v 仅会延展纵向    
#### `//distr  [-c] [-d]`
**权限**： `worldedit.analysis.distr`    
**描述**： 获得选区内方块的分布情况。<br /> -c 标记会获得你剪切板内容的分布情况。<br /> -d 标记会将方块用数据分割    
#### `//inset <amount> [-h] [-v]`
**权限**： `worldedit.selection.inset`    
**描述**： 使用给定的数值，在所有方向上缩小选区。<br />可用标记：<br />  -h 仅会缩小横向<br />  -v 仅会缩小纵向    

---

### **History 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/HistoryCommands.java)`]`
> (能够撤销操作，反撤销操作，清除历史的相关命令： [更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Features#History))    

---

#### `//redo [times] [player]`
**权限**： `worldedit.history.redo`    
**描述**： 反撤销上个操作（从历史记录中）   
#### `//clearhistory `
**权限**： `worldedit.history.clear`    
**描述**： 清除你的历史记录   
#### `//undo [times] [player]`
**权限**： `worldedit.history.undo`    
**描述**： 撤销上个操作    
#### `//frb <user=Empire92> <radius=5> <time=3d4h>`
**权限**： `worldedit.history.rollback`    
**描述**： 撤销某个给定的操作。  - 时间使用以下单位： s（秒）, m（分钟）, h（小时）, d（天）, y（年）。<br /> - 从硬盘中导入： /frb #import    

---

### **Schematic 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/SchematicCommands.java)`]`
> (跟 schematic 文件有关的命令)    

---

#### `/schematic load [<format>] <filename>`
**权限**： `worldedit.clipboard.load`, `worldedit.schematic.load`, `worldedit.schematic.upload`, `worldedit.schematic.load.other`    
**描述**： 将某个schematic文件导入到你的剪切板中    
#### `/schematic delete <filename>`
**权限**： `worldedit.schematic.delete`    
**描述**： 将某个schematic文件从文件列表中移除   
#### `/schematic list [mine|<filter>] [page=1] [-d] [-n] [-p]`
**权限**： `worldedit.schematic.list`    
**描述**： 列出所有schematic路径下的可用文件<br /> -p <页码数> 能够列出指定页面的文件<br /> -f <format> 启用格式限制   
#### `/schematic save [<format>] <filename>`
**权限**： `worldedit.clipboard.save`, `worldedit.schematic.save`, `worldedit.schematic.save.other`    
**描述**： 使用你的剪切板的内容储存到schematic文件中  
#### `/schematic remap `
**权限**： `worldedit.schematic.remap`    
**描述**： 将剪切板在MCPE/PC的值之间交换 
#### `/schematic formats `
**权限**： `worldedit.schematic.formats`    
**描述**： 列出所有可用的格式  
#### `/schematic loadall [<format>] <filename|url>`
**权限**： `worldedit.clipboard.load`, `worldedit.schematic.load`, `worldedit.schematic.upload`    
**描述**： 读取多个剪切板<br /> -r 标记可以应用随机旋转位置 

---

### **Clipboard 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/ClipboardCommands.java)`]`
> (跟复制和粘贴方块有关的命令： [更多信息](https://goo.gl/z2ScQR))    

---

#### `//copy  [-e] [-m]`
**权限**： `worldedit.clipboard.copy`    
**描述**： 将选区中的内容复制到剪切板中<br />可用标记：<br />  -e 跳过复制实体<br />  -m 设置资源蒙版，蒙版外的方块会作为空气复制<br />  -b 也会复制生物群系<br />警告：实体的粘贴不能被撤销！    
#### `//flip [<direction>]`
**权限**： `worldedit.clipboard.flip`    
**描述**： 沿着复制发生时的那个点为剪切板中的内容进行镜面翻转。   
#### `//rotate <y-axis> [<x-axis>] [<z-axis>]`
**权限**： `worldedit.clipboard.rotate`    
**描述**： 不会有破坏性的旋转剪切板中的内容。<br />角度需要输入度数，正数会进行顺时针旋转。你也可以堆叠进行多次旋转。插值是不被接受，且没有任何作用的，所以角度的度数应该是90的倍数。  
#### `//lazycopy  [-e] [-m]`
**权限**： `worldedit.clipboard.lazycopy`    
**描述**： 将选区中的内容延迟复制到剪切板中<br />可用标记：<br />  -e 跳过复制实体<br />  -m 设置资源蒙版，蒙版外的方块会作为空气复制<br />  -b 也会复制生物群系<br />警告：实体的粘贴不能被撤销！    
#### `//place  [-s] [-a] [-o]`
**权限**： `worldedit.clipboard.place`    
**描述**： 不应用任何变化（例如：旋转）放置剪切板的内容。<br />可用参数：<br />  -a 跳过空气方块<br />  -o 粘贴在原位置<br />  -s 在粘贴之后将选区定在粘贴区域        
#### `//cut [leave-id] [-e] [-m]`
**权限**： `worldedit.clipboard.cut`    
**描述**： 将选区剪切到粘贴板之中<br />可用参数：<br />  -e 跳过复制实体<br />  -m 设置资源蒙版，蒙版外的方块会作为空气复制<br />  -b 也会复制生物群系<br />警告：实体的粘贴不能被撤销！ 
#### `/download `
**权限**： `worldedit.clipboard.download`    
**描述**： 通过配置的网页接口下载剪切板的内容   
#### `/asset [category]`
**权限**： `worldedit.clipboard.asset`    
**描述**： 将你的剪切板的内容保存到网页资源接口中   
#### `//paste  [-s] [-a] [-o]`
**权限**： `worldedit.clipboard.paste`    
**描述**： 粘贴剪切板的内容。<br />可用参数：<br />  -a 跳过空气方块<br />  -b 跳过粘贴生物群系<br />  -e 跳过粘贴实体<br />  -o 粘贴到原位置<br />  -s 在粘贴之后将选区定在粘贴区域     
#### `//lazycut  [-e] [-m]`
**权限**： `worldedit.clipboard.lazycut`    
**描述**： 将选区中的内容延迟剪切到剪切板之中<br />可用参数：<br />  -e 跳过复制实体<br />  -m 设置资源蒙版，蒙版外的方块会作为空气复制<br />  -b 也会复制生物群系<br />警告：实体的粘贴不能被撤销！    
#### `/clearclipboard `
**权限**： `worldedit.clipboard.clear`    
**描述**： 清除你的剪切板    

---

### **Generation 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/GenerationCommands.java)`]`
> (创建结构或特性： [更多信息](https://goo.gl/KuLFRW))    

---

#### `//image <imgur> [randomize=true] [complexity=100]`
**权限**： `worldedit.generation.image`    
**描述**： 创建一张图片  
#### `//generate <block> <expression> [-h] [-r] [-o] [-c]`
**权限**： `worldedit.generation.shape`    
**描述**： 根据表达式创建结构，表达式返回的值<br />应该是正数（返回true，如果选择点在结构内的话）<br />可选地，你可以设置目标方块的类型或数据。<br />可选参数：<br />  -h 创建凹下去的结构<br />  -r 使用原版Minecraft坐标<br />  -o 与 -r 相似，但使用相对坐标。<br />  -c 与 -r 相似，但相对坐标的中心不同。<br />如果你既没有没有输入 -r ，也没有输入 -o 的话，选区会自动映射为 -1..1<br />详见 tinyurl.com/wesyntax。    
#### `//cyl <block> <radius>[,<radius>] [height] [-h]`
**权限**： `worldedit.generation.cylinder`    
**描述**： 生成圆柱体。<br />通过指定用逗号分隔的两个半径，<br />你能够创建椭圆体。<br />第一个参数指定南北距离，第二个参数指定东西距离。    
#### `//sphere <block> <radius>[,<radius>,<radius>] [raised?] [-h]`
**权限**： `worldedit.generation.sphere`    
**描述**： 生成内部填充的球。<br />通过指定用逗号分隔的三个半径，<br />你能够创建椭球体。椭球体半径的距离的指定顺序为：<br />南北，上下，东西。    
#### `//ore <mask> <pattern> <size> <freq> <rarity> <minY> <maxY>`
**权限**： `worldedit.generation.ore`    
**描述**： 生成矿物    
#### `//caves [size=8] [freq=40] [rarity=7] [minY=8] [maxY=127] [sysFreq=1] [sysRarity=25] [pocketRarity=0] [pocketMin=0] [pocketMax=3]`
**权限**： `worldedit.generation.caves`    
**描述**： 生成网状的洞穴结构    
#### `//hcyl <pattern> <radius>[,<radius>] [height]`
**权限**： `worldedit.generation.cylinder`    
**描述**： 生成中空的圆柱体。<br />通过指定用逗号分隔的两个半径，<br />你能够创建椭圆体。<br />第一个参数指定南北距离，第二个参数指定东西距离。     
#### `//ores `
**权限**： `worldedit.generation.ore`    
**描述**： 生成矿物    
#### `//hsphere <block> <radius>[,<radius>,<radius>] [raised?]`
**权限**： `worldedit.generation.sphere`    
**描述**： 生成中空的球体。<br />通过指定用逗号分隔的三个半径，<br />你能够创建椭球体。椭球体半径的距离的指定顺序为：<br />南北，上下，东西。   
#### `/forestgen [size] [type] [density]`
**权限**： `worldedit.generation.forest`    
**描述**： 生成森林    
#### `//hpyramid <block> <size>`
**权限**： `worldedit.generation.pyramid`    
**描述**： 生成中空的金字塔    
#### `/pumpkins [size]`
**权限**： `worldedit.generation.pumpkins`    
**描述**： 生成南瓜群   
#### `//pyramid <block> <size> [-h]`
**权限**： `worldedit.generation.pyramid`    
**描述**： 生成填充过的金字塔    
#### `//generatebiome <biome> <expression> [-h] [-r] [-o] [-c]`
**权限**： `worldedit.generation.shape`, `worldedit.biome.set`    
**描述**： 根据表达式创建结构，表达式返回的值<br />应该是正数（返回true，如果选择点在结构内的话）<br />可选地，你可以设置目标方块的类型或数据。<br />可选参数：<br />  -h 创建凹下去的结构<br />  -r 使用原版Minecraft坐标<br />  -o 与 -r 相似，但使用相对坐标。<br />  -c 与 -r 相似，但相对坐标的中心不同。<br />如果你既没有没有输入 -r ，也没有输入 -o 的话，选区会自动映射为 -1..1<br />详见 tinyurl.com/wesyntax。    

---

### **Biome 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/BiomeCommands.java)`]`
> (改变，列出或检查生物群系)    

---

#### `//setbiome <biome> [-p]`
**权限**： `worldedit.biome.set`    
**描述**： 设置区域的生物群系。<br />默认生成的生物群系会使用你选区中所有的方块构成。<br />-p 会使用你当前所在的区块。   
#### `/biomeinfo  [-p] [-t]`
**权限**： `worldedit.biome.info`    
**描述**： 获取区块的生物群系。<br />默认获取的生物群系会检测你选区中所有的方块。<br />-t 使用你正在看着的那个区块。<br />-p 会使用你当前所在的区块。   
#### `/biomelist [page]`
**权限**： `worldedit.biome.list`    
**描述**： 获取所有可用的生物群系。    

---

### **Anvil 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/boydti/fawe/command/AnvilCommands.java)`]`
> (Manipulate billions of blocks: [更多信息](https://github.com/c7w/FastAsyncWorldedit/wiki/Anvil-API))    

---

#### `/anvil count <ids> [-d]`
**权限**： `worldedit.anvil.count`    
**描述**： 为选区中的方块计数    
#### `/anvil replace [from-block] <to-block>`
**权限**： `worldedit.anvil.replace`    
**描述**： 用一种方块替换选区中的所有另一种方块    
#### `/anvil replaceall <folder> [from-block] <to-block> [-d] [-f]`
**权限**： `worldedit.anvil.replaceall`    
**描述**： 用另一种方块替换选区中的所有方块<br /> -d 标记会禁用通配符的匹配    
#### `/anvil copy `
**权限**： `worldedit.anvil.copychunks`    
**描述**： 将区块延迟复制到你的anvil剪切板中    
#### `/anvil paste  [-c]`
**权限**： `worldedit.anvil.pastechunks`    
**描述**： 从anvil剪切板将内容粘贴出来。<br /> -c 标记会调整将内容粘贴到区块中。  
#### `/anvil distr `
**权限**： `worldedit.anvil.distr`    
**描述**： 用另一种方块替换选区中的所有方块   
#### `/anvil trimallplots `
**权限**： `worldedit.anvil.trimallplots`    
**描述**： 修剪地皮世界中的区块<br />未认领的区块会被删除<br />未修改的区块会被删除<br />使用 -v 来删除没有人去过的区块    
#### `/anvil countall <folder> [hasSky] <id> [-d]`
**权限**： `worldedit.anvil.countall`    
**描述**： 为世界中的方块计数    
#### `/anvil clear `
**权限**： `worldedit.anvil.clear`    
**描述**： 清除选区的区块（不整理磁盘碎片就删除）    
#### `/anvil removelayers <id>`
**权限**： `worldedit.anvil.removelayer`    
**描述**： 如果某一区块的顶层方块全部都匹配提供的方块类型的话，就移除顶层方块。   
#### `/anvil replacepattern [from-mask] <to-pattern>`
**权限**： `worldedit.anvil.replace`    
**描述**： 移除选区内所有匹配模型的方块    
#### `/anvil remapall <folder>`
**权限**： `worldedit.anvil.remapall`    
**描述**： 将世界在MCPE和PC的存档格式之间转换    
#### `/anvil deletealloldregions <folder> <time>`
**权限**： `worldedit.anvil.deletealloldregions`    
**描述**： 移除一段时间内没有人进入的区域<br />你可以使用秒 (s), 分钟 (m), 小时 (h), 天 (d), 周 (w),和 年 (y) 来计算时间<br />(请注意：月份不是计算时间的单位)<br />举个例子： 8h5m12s    
#### `/anvil replaceallpattern <folder> [from-block] <to-pattern> [-d] [-m]`
**权限**： `worldedit.anvil.replaceall`    
**描述**： 将选区中所有的方块替换成另一种    
#### `/anvil deleteallunvisited <folder> <age-ticks> [file-age=60000]`
**权限**： `worldedit.anvil.deleteallunvisited`    
**描述**： 移除所有加载时间没有到指定整数刻的区块(20t = 1s) and <br />在创建文件后的文件持续时间 `file-duration` (ms) 内不能访问<br />没有在过去的 `chunk-inactivity` (ms)中使用。自动保存的间隔推荐是 `file-duration` 和 `chunk-inactivity`   的值  

---

### **Super Pickaxe 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/SuperPickaxeCommands.java)`]`
> (超级镐子相关命令： [更多信息](https://goo.gl/aBtGHo))    

---

#### `/sp recur <radius>`
**权限**： `worldedit.superpickaxe.recursive`    
**描述**： 启用递归超级镐子模式    
#### `/sp area <radius>`
**权限**： `worldedit.superpickaxe.area`    
**描述**： 启用区域超级镐子模式    
#### `/sp single `
**权限**： `worldedit.superpickaxe`    
**描述**： 启用单个方块的超级镐子模式    

---

### **Navigation 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/NavigationCommands.java)`]`
> (关于玩家在地面上移动的相关命令： [更多信息](https://goo.gl/uQTUiT))    

---

#### `/descend [# of floors]`
**权限**： `worldedit.navigation.descend`    
**描述**： 向下降一层    
#### `/ascend [# of levels]`
**权限**： `worldedit.navigation.ascend`    
**描述**： 向上升一层    
#### `/thru `
**权限**： `worldedit.navigation.thru.command`    
**描述**： 穿过墙壁    
#### `/jumpto [world,x,y,z]`
**权限**： `worldedit.navigation.jumpto.command`    
**描述**： 传送到某一位置    
#### `/ceil [clearance] [-f] [-g]`
**权限**： `worldedit.navigation.ceiling`    
**描述**： 去天花板上    
#### `/up <block> [-f] [-g]`
**权限**： `worldedit.navigation.up`    
**描述**： 向上移动一段距离    
#### `/unstuck `
**权限**： `worldedit.navigation.unstuck`    
**描述**： 在卡在方块中的情况下逃脱    

---

### **Snapshot 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/SnapshotCommands.java)`]`
> (列出，读取快照以及查看跟快照有关的信息)    

---

#### `/snapshotlist [num]`
**权限**： `worldedit.snapshots.list`    
**描述**： 列出某一快照    
#### `/snapshotafter <date>`
**权限**： `worldedit.snapshots.restore`    
**描述**： 选择距离一个时间最近的快照，快照发布时间在该时间之后    
#### `/snapshotbefore <date>`
**权限**： `worldedit.snapshots.restore`    
**描述**： 选择距离一个时间最近的快照，快照发布时间在该时间之前    
#### `/snapshotuse <snapshot>`
**权限**： `worldedit.snapshots.restore`    
**描述**： 选择要使用的快照    
#### `/snapshotsel <index>`
**权限**： `worldedit.snapshots.restore`    
**描述**： 选择根据列表ID排序的某一快照    

---

### **Snapshot Util 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/SnapshotUtilCommands.java)`]`
> ([更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Snapshots))    

---

#### `/restore [snapshot]`
**权限**： `worldedit.snapshots.restore`    
**描述**： 从某一快照恢复选区    

---

### **Scripting 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/ScriptingCommands.java)`]`
> (执行 CraftScript 脚本 [更多信息](https://goo.gl/dHDxLG))    

---

#### `/cs <filename> [args...]`
**权限**： `worldedit.scripting.execute`    
**描述**： 执行一个 CraftScript 脚本    
#### `/.s [args...]`
**权限**： `worldedit.scripting.execute`    
**描述**： 执行上一个 CraftScript 脚本    

---

### **Chunk 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/ChunkCommands.java)`]`
> ([旧版] 检索区块： [更多信息](http://wiki.sk89q.com/wiki/WorldEdit/Chunk_tools))    

---

#### `/chunkinfo `
**权限**： `worldedit.chunkinfo`    
**描述**： 获得你当前所在的区块的有关信息    
#### `/listchunks `
**权限**： `worldedit.listchunks`    
**描述**： 列出你的选取包括的区块    
#### `/delchunks `
**权限**： `worldedit.delchunks`    
**描述**： 已过期，请使用 anvil 命令    

---

### **Options 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/OptionsCommands.java)`]`
> (玩家切换设置和物品信息)    

---

#### `//searchitem <query> [-b] [-i]`
**描述**： 搜索某个物品。<br />Flags:<br />  -b 仅搜索方块<br />  -i 仅搜索物品    
#### `//gtransform [transform]`
**权限**： `worldedit.global-trasnform`    
**描述**： 获取全局变换式    
#### `//toggleplace `
**描述**： 在你当前位置和第一个选取点直接切换位置    
#### `//tips `
**描述**： 切换FAWE提示是否开启    
#### `//gsmask [mask]`
**权限**： `worldedit.global-mask`    
**描述**： 能够应用给你的所有编辑的全局资源蒙版，你做出的资源性更改符合本蒙版（例如：剪切板中的方块）    
#### `//gmask [mask]`
**权限**： `worldedit.global-mask`    
**描述**： 能够应用给你的所有编辑的全局目标蒙版，你所有的目标性更改都符合本蒙版（例如：世界中的方块）   
#### `//fast [on|off]`
**权限**： `worldedit.fast`    
**描述**： 切换FAWE插件能否进行撤销操作    

---

### **Brush Options 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/BrushOptionsCommands.java)`]`
> (工具命令)    

---

#### `/target [mode]`
**描述**： 在不同的目标模式之间切换    
#### `/size [pattern]`
**权限**： `worldedit.brush.options.size`    
**描述**： 设置笔刷大小    
#### `//listbrush [mine|<filter>] [page=1] [-d] [-n] [-p]`
**权限**： `worldedit.brush.list`    
**描述**： 列出所有笔刷路径下的笔刷<br /> -p <页码数> 会列出指定页面    
#### `/mask [mask]`
**权限**： `worldedit.brush.options.mask`    
**描述**： 设置笔刷的目标蒙版    
#### `/range [pattern]`
**权限**： `worldedit.brush.options.range`    
**描述**： 设置笔刷的范围    
#### `/transform [transform]`
**权限**： `worldedit.brush.options.transform`    
**描述**： 设置笔刷的变换式    
#### `/mat [pattern]`
**权限**： `worldedit.brush.options.material`    
**描述**： 设置笔刷的材料    
#### `/patterns [page=1|search|pattern]`
**描述**： 模型可以决定哪些方块被放置<br /> - 使用[括号]来输入参数<br /> - 使用 , 来代表 或 的分割<br />举个例子： #surfacespread[10][#existing],andesite<br />更多信息: https://git.io/vSPmA    
#### `/savebrush [name]`
**权限**： `worldedit.brush.save`    
**描述**： 保存你当前的笔刷<br />使用 -g 标记来做出全局储存    
#### `/loadbrush [name]`
**权限**： `worldedit.brush.load`    
**描述**： 读取笔刷    
#### `/transforms [page=1|search|transform]`
**描述**： 变换方块被放置的方式<br /> - 使用[括号]来输入参数<br /> - 使用 , 来代表 或 的分割<br /> - 使用 & 来表示 和 的分割<br />更多信息: https://git.io/v9KHO    
#### `/primary [brush arguments]`
**描述**： 设置右键点击激活的笔刷    
#### `// [on|off]`
**权限**： `worldedit.superpickaxe`    
**描述**： 切换超级镐子功能    
#### `/targetmask [mask]`
**描述**： 设置目标蒙版     
#### `/none `
**描述**： 从当前物品上解除绑定功能    
#### `/visualize [mode=0]`
**描述**： 在不同的预览模式之间进行切换<br />0 = 没有预览<br />1 = 预览单个目标方块<br />2 = 用玻璃预览所有将会改变的方块    
#### `/scroll [none|clipboard|mask|pattern|range|size|visual|target]`
**描述**： 在不同的目标模式之间进行切换    
#### `/secondary [brush arguments]`
**描述**： 设置左键点击激活的笔刷    
#### `/smask [mask]`
**权限**： `worldedit.brush.options.mask`    
**描述**： 设置笔刷的资源蒙版    
#### `/masks [page=1|search|mask]`
**描述**： 能够决定方块能否被放置的蒙版<br /> - 使用[括号]来输入参数<br /> - 使用 , 来代表 或 的分割<br /> - 使用 & 来表示 和 的分割<br />举个例子： >[stone,dirt],#light[0][5],$jungle<br />更多信息: https://git.io/v9r4K    

---

### **Tool 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/ToolCommands.java)`]`
> (将某些功能绑定到持有的物品之上： [更多信息](https://goo.gl/xPnPxj))    

---

#### `/tool tree [type]`
**权限**： `worldedit.tool.tree`    
**描述**： 生成树的工具    
#### `/tool repl <block>`
**权限**： `worldedit.tool.replacer`    
**描述**： 方块替换工具    
#### `/tool info `
**权限**： `worldedit.tool.info`    
**描述**： 方块信息工具    
#### `/tool lrbuild <leftclick block> <rightclick block>`
**权限**： `worldedit.tool.lrbuild`    
**描述**： 大范围建筑工具    
#### `/tool cycler `
**权限**： `worldedit.tool.data-cycler`    
**描述**： 方块数据值循环工具    
#### `/tool deltree `
**权限**： `worldedit.tool.deltree`    
**描述**： 移除漂浮的树的工具    
#### `/tool inspect `
**权限**： `worldedit.tool.inspect`    
**描述**： 选择检查笔刷    
#### `/tool floodfill <pattern> <range>`
**权限**： `worldedit.tool.flood-fill`    
**描述**： 池塘填充工具    
#### `/tool farwand `
**权限**： `worldedit.tool.farwand`    
**描述**： 远程选区工具    

---

### **Brush 命令** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/BrushCommands.java)`]`
> (从远程建筑与涂画的工具。 [更多信息](https://git.io/vSPYf))    

---

#### `/brush copypaste [depth=5]`
**权限**： `worldedit.brush.copy`    
**描述**： 左键点击一个物体的底座来复制。<br />右键点击来粘贴<br /> -r 标记能够在粘贴时应用随机旋转<br />注意：能和剪切板滚动一起搭配使用<br />视频： https://www.youtube.com/watch?v=RPZIaTbqoZw    
#### `/brush command <radius> [cmd1;cmd2...]`
**权限**： `worldedit.brush.command`    
**描述**： 在点击的位置执行一条命令。<br /> - 你的选区会延展到包括该点<br /> - 可用的变量： {x}, {y}, {z}, {world}, {size}    
#### `/brush populateschematic <mask> <file|folder|url> [radius=30] [points=5] [-r]`
**权限**： `worldedit.brush.populateschematic`    
**描述**： 选择分散型schematic笔刷。<br /> -r 标记能够应用随机旋转    
#### `/brush scmd <scatter-radius> <points> <cmd-radius=1> <cmd1;cmd2...>`
**权限**： `worldedit.brush.scattercommand`    
**描述**： 在表面的随机一点执行命令<br /> - 分散的半径是每个点之间的最小距离<br /> - 你的选区会延展到包括该点<br /> - 可用的变量： {x}, {y}, {z}, {world}, {size}     
#### `/brush erode [radius=5]`
**权限**： `worldedit.brush.erode`    
**描述**： 侵蚀地形    
#### `/brush pull [radius=5]`
**权限**： `worldedit.brush.pull`    
**描述**： 将地形推向你    
#### `/brush blendball [radius=5]`
**权限**： `worldedit.brush.blendball`    
**描述**： 平滑化，混合化地形<br />图片： https://i.imgur.com/cNUQUkj.png -> https://i.imgur.com/hFOFsNf.png    
#### `/brush stencil <pattern> [radius=5] [file|#clipboard|imgur=null] [rotation=360] [yscale=1.0]`
**权限**： `worldedit.brush.stencil`    
**描述**： 使用高度图来画出地形表面。<br /> -w 标记仅会应用于最大饱和度<br /> -r 标记会应用随机旋转    
#### `/brush splatter <pattern> [radius=5] [seeds=1] [recursion=5] [solid=true]`
**权限**： `worldedit.brush.splatter`    
**描述**： 设置物体表面为随机方块。<br />图片： https://i.imgur.com/hMD29oO.png<br />使用示例： /br splatter stone,dirt 30 15<br />注意：种子决定着会有多少斑点，递归次数决定着其大小，solid决定着模型是按照每个种子应用还是每个方块应用。    
#### `/brush cylinder <block> [radius=2] [height=1] [-h]`
**权限**： `worldedit.brush.cylinder`    
**描述**： 创建圆柱体。<br /> -h 标记会创建空心的圆柱体。    
#### `/brush shatter <pattern> [radius=10] [count=10]`
**权限**： `worldedit.brush.shatter`    
**描述**： 创建将地形分成多个部分的不均匀的线<br />图片： https://i.imgur.com/2xKsZf2.png    
#### `/brush circle <pattern> [radius=5]`
**权限**： `worldedit.brush.sphere`    
**描述**： 围绕着你看向的方向创建一个圆。<br />注意：无视笔刷的半径，并且启用预览可以帮助你看到将要放置的东西    
#### `/brush smooth [size=2] [iterations=4] [-n]`
**权限**： `worldedit.brush.smooth`    
**描述**： 选择地形平滑化笔刷。<br /> -n 标记会只让它更改自然生成的方块。    
#### `/brush ex [radius=5]`
**权限**： `worldedit.brush.ex`    
**描述**： 火焰熄灭笔刷的快捷方式    
#### `/brush gravity [radius=5] [-h]`
**权限**： `worldedit.brush.gravity`    
**描述**： 这个笔刷会模仿重力的作用。<br /> -h 标记能够让它从世界的最大Y坐标开始计算，而不是点击方块的Y坐标。    
#### `/brush sspl <pattern> [size=0] [tension=0] [bias=0] [continuity=0] [quality=10]`
**权限**： `worldedit.brush.surfacespline`    
**描述**： 在地面上创建一条曲线。<br />视频： https://www.youtube.com/watch?v=zSN-2jJxXlM    
#### `/brush spline <pattern>`
**权限**： `worldedit.brush.spline`    
**描述**： 点击一些物体，然后再次点击相同的方块来让你的物体之间进行连接。<br />笔刷半径设置过小，或是点击位置错误或导致变形。形状必须是简单的线条或者封闭的环形。<br />图片： http://i.imgur.com/CeRYAoV.jpg -> http://i.imgur.com/jtM0jA4.png<br />图片2： http://i.imgur.com/bUeyc72.png -> http://i.imgur.com/tg6MkcF.png    
#### `/brush surface <pattern> [radius=5]`
**权限**： `worldedit.brush.surface`    
**描述**： 使用高度图来画出表面。<br /> -w 标记仅会应用于最大饱和度<br /> -r 标记会应用随机旋转    
#### `/brush layer <radius> [color|<pattern1> <patern2>...]`
**权限**： `worldedit.brush.layer`    
**描述**： 使用覆盖层来替换地形。<br />示例：/br layer 5 95:1 95:2 35:15 - 会在地面上放置一些覆盖层<br />图片： https://i.imgur.com/XV0vYoX.png    
#### `/brush sphere <pattern> [radius=2] [-h]`
**权限**： `worldedit.brush.sphere`    
**描述**： 创建一个球体。<br /> -h 标记能够创建中空的球体。    
#### `/brush clipboard `
**权限**： `worldedit.brush.clipboard`    
**描述**： 选择剪切板笔刷。<br /> -a 标记会使其不会粘贴空气方块。<br />不输入 -p 标记，粘贴后的内容的中心会出现在目标位置。输入该标记后，粘贴内容所在的位置就会根据你在复制内容时所站的位置而定义了。   
#### `/brush recursive <pattern-to> [radius=5]`
**权限**： `worldedit.brush.recursive`    
**描述**： 设置所有连接起来的方块。<br /> -d 标记会应用深度优先的顺序<br />注意：设置蒙版可以递归指定的方块    
#### `/brush scatter <pattern> [radius=5] [points=5] [distance=1] [-o]`
**权限**： `worldedit.brush.scatter`    
**描述**： 在地面上随机放置方块，每两个方块之间有某种距离的联系。<br />  -o 标记会覆盖原方块<br />视频： https://youtu.be/RPZIaTbqoZw?t=34s    
#### `/brush line <pattern> [radius=0] [-h] [-s] [-f]`
**权限**： `worldedit.brush.line`    
**描述**： 创建线段。<br /> -h 标记仅会创建外壳<br /> -s 标记在创建之后会选择点击的点。<br /> -f 标记会创建平坦的线段。    
#### `/brush height [radius=5] [file|#clipboard|imgur=null] [rotation=0] [yscale=1.00] [-h]`
**权限**： `worldedit.brush.height`    
**描述**： 这个笔刷可以使地形上升或下降。<br /> -  `-r` 标记启用随机坐标旋转<br /> -  `-l` 标记也会在某些雪层中工作<br /> -  `-s` 标记禁用平滑<br />注意！注意！如果你要降低地形的话请将yscale的值设置为负数<br />雪的图片： https://i.imgur.com/Hrzn0I4.png    
#### `/brush butcher [radius=5] [-p] [-l] [-a] [-n] [-g] [-b] [-t] [-f] [-r]`
**权限**： `worldedit.brush.butcher`    
**描述**： 击杀在指定的半径内的怪物。<br />可用的标记：<br />  -p 也击杀宠物<br />  -n 也击杀 NPC<br />  -g 也击杀铁傀儡<br />  -a 也击杀动物。<br />  -b 也击杀中立生物<br />  -t 也击杀带有名字的怪物<br />  -f 相当于这以前所有标记的混合<br />  -r 也击杀盔甲架<br />  -l 目前啥都不能干    
#### `/brush flatten [radius=5] [file|#clipboard|imgur=null] [rotation=0] [yscale=1.00] [-h]`
**权限**： `worldedit.brush.height`    
**描述**： 平坦笔刷，可以使地形平坦<br /> -  `-r` 标记启用随机坐标旋转<br /> -  `-l` 标记也会在某些雪层中工作<br /> -  `-s` 标记禁用平滑    
#### `/brush cliff [radius=5] [file|#clipboard|imgur=null] [rotation=0] [yscale=1.00] [-h]`
**权限**： `worldedit.brush.height`    
**描述**： 这个笔刷可以平坦地形且创建悬崖。<br /> -  `-r` 标记启用随机坐标旋转<br /> -  `-l` 标记也会在某些雪层中工作<br /> -  `-s` 标记禁用平滑   

---

### **/Masks** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/MaskCommands.java)`]`
> (Help for the various masks. [更多信息](https://git.io/v9r4K))    
蒙版决定了方块能否被放置
 - 使用 [brackets] 来输入参数
 - 使用 , 来代表 或 的分割
 - 使用 & 来代表 和 的分割
例如： >[stone,dirt],#light[0][5],$jungle
更多信息: https://git.io/v9r4K    

---

#### `#offset <dx> <dy> <dz> <mask>`
**描述**： 使蒙版偏移    
#### `% <chance>`
**描述**： 百分比的几率    
#### `#id `
**描述**： 限制初始ID   
#### `#data `
**描述**： 限制初始数据值    
#### `{ <min> <max>`
**描述**： 限制方块与初始方块的距离范围    
#### `#existing `
**描述**： 设置为非空气方块    
#### `$ <biome>`
**描述**： 在特殊的生物群系中，要想列出所有的生物群系请使用 //biomelist    
#### `#surface `
**描述**： 限制为地面（任何接触空气的固体方块    
#### `! <mask>`
**描述**： 使其他蒙版反向    
#### `= <expression>`
**描述**： 表达式蒙版    
#### `#region `
**描述**： 在某个提供的选取内部    
#### `\ <min> <max>`
**描述**： 限制为特殊的地形角度<br /> -o 标记仅仅会覆盖，举个例子： /[0d][45d]<br />作用解释：能够选出任何对角线在0-45度之间的方块<br />示例：/[3][20]<br />作用解释：能够选出任何对角线在3-20度之间的方块    
#### `#dregion `
**描述**： 在玩家的选取之中    
#### `#xaxis `
**描述**： 限制为特殊的x轴位置   
#### `#yaxis `
**描述**： 限制为特殊的y轴位置    
#### `#opacity <min> <max>`
**描述**： 限制为指定的不透明度等级    
#### `#light <min> <max>`
**描述**： 限制为指定的光亮等级    
#### `#blocklight <min> <max>`
**描述**： 限制为指定的方块亮度等级    
#### `#haslight `
**描述**： 限制为方块是否拥有光照（天空或环境）    
#### `~ <mask> [min=1] [max=8]`
**描述**： 邻近的其他方块的数量    
#### `#brightness <min> <max>`
**描述**： 限制指定的方块光照等级    
#### `#nolight `
**描述**： 限制方块需要没有光亮（天空或环境）    
#### `#skylight <min> <max>`
**描述**： 限制需要指定天空光亮等级    
#### `#simplex <scale=10> <min=0> <max=100>`
**描述**： 使用噪声算法作为蒙版    
#### `#zaxis `
**描述**： 限制为特殊的z轴位置    
#### `> <mask>`
**描述**： 在某一指定方块的上面    
#### `#wall `
**描述**： 限制为墙壁（任意方块，东西南北任意一面为空气）    
#### `| <mask> <min> <max>`
**描述**： 旁边位置拥有指定数量的其他方块    
#### `#iddata `
**描述**： 限制指定的方块ID与数据值    
#### `< <mask>`
**描述**： 在某一指定方块之下    
#### `#solid `
**描述**： 如果是固体方块    

---

### **/Patterns** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/PatternCommands.java)`]`
> (对于某些模板信息的帮助。 [更多信息](https://git.io/vSPmA))    
模板决定着放置什么方块
 - 使用 [brackets] 输入参数
 - 使用 , 来代表 或 的分割
举个例子： #surfacespread[10][#existing],andesite
更多信息: https://git.io/vSPmA    

---

#### `#offset <dx> <dy> <dz> <pattern>`
**描述**： 使模板偏移    
#### `#mask <mask> <pattern-true> <pattern-false>`
**描述**： 根据蒙版应用模板    
#### `#id <pattern>`
**描述**： 只改变方块ID    
#### `#spread <dx> <dy> <dz> <pattern>`
**描述**： 随机扩散方块    
#### `#buffer <pattern>`
**描述**： 只有当模板在使用时才放置方块<br />如果你不想点击某些地方两次时，用它和笔刷搭配    
#### `#clipboard `
**描述**： 使用你剪切板中的方块作为模板    
#### `#relative <pattern>`
**描述**： 将模板偏移到你所点击的位置    
#### `#data <pattern>`
**描述**： 只会改变方块的数据值    
#### `#biome <biome>`
**描述**： 设置生物群系   
#### `#existing `
**描述**： 使用已经存在的方块    
#### `= <expression>`
**描述**： 表达式模板： http://wiki.sk89q.com/wiki/WorldEdit/Expression_syntax    
#### `#simplex <scale=10> <pattern>`
**描述**： 使用噪声算法来随机放置方块    
#### `#averagecolor <color> [randomize=true] [max-complexity=100]`
**描述**： 在已经存在的方块和颜色之间平均化    
#### `#desaturate [percent=100] [randomize=true] [max-complexity=100]`
**描述**： 减小已经存在的方块的颜色的饱和度    
#### `#darken [randomize=true] [max-complexity=100]`
**描述**： 使已经存在的方块变暗    
#### `#fullcopy [schem|folder|url=#copy] [rotate=false] [flip=false]`
**描述**： 将你全部的剪切板放置在每个方块上    
#### `#buffer2d <pattern>`
**描述**： 只有在一列中的模板在使用时才会放置方块    
#### `#lighten [randomize=true] [max-complexity=100]`
**描述**： 使已存在的方块变亮    
#### `#saturate <color> [randomize=true] [max-complexity=100]`
**描述**： 增加已经存在的方块的颜色的饱和度    
#### `#anglecolor [randomize=true] [max-complexity=100]`
**描述**： 依靠于地形偏角的较暗的方块    
#### `#iddatamask <bitmask=15> <pattern>`
**描述**： 使用模板的ID和提供的蒙版的已存在的方块数据<br /> - 用于替换半砖，数据值需要换挡而不是设置    
#### `#angledata `
**描述**： 根据已存在的地形偏角的方块数据    
#### `#!x <pattern>`
**描述**： 本模板不会提供z轴的信息。<br />举个例子： #!x[#!z[#~[#l3d[pattern]]]]    
#### `#!y <pattern>`
**描述**： 本模板不会提供y轴的信息    
#### `#linear <pattern>`
**描述**： 从列表的模板中循序设置方块    
#### `#!z <pattern>`
**描述**： 本模板不会提供z轴的信息    
#### `#surfacespread <distance> <pattern>`
**描述**： 随机改变地面上一个方块的位置    
#### `#linear3d <pattern>`
**描述**： 使用 x,y,z 坐标选定一个来自列表中的方块    
#### `#solidspread <dx> <dy> <dz> <pattern>`
**描述**： 随机传播固体方块    
#### `#color <color>`
**描述**： 使用接近于指定颜色的方块    

---

### **/Transforms** `[`[`编辑`](https://github.com/c7w/FastAsyncWorldedit/edit/master/core/src/main/java/com/sk89q/worldedit/command/TransformCommands.java)`]`
> (Help for the various transforms. [更多信息](https://git.io/v9KHO))    
变换式会修改方块怎么被放置
 - 使用 [brackets] 来输入参数
 - 使用 , 来代表 或 的分割
 - 使用 & 来代表 和 的分割
更多信息: https://git.io/v9KHO    

---

#### `#offset <dx> <dy> <dz> [transform]`
**描述**： 偏移变换式    
#### `#rotate <rotateX> <rotateY> <rotateZ> [transform]`
**描述**： 所有的变化都会被绕着指定位置旋转   
#### `#scale <dx> <dy> <dz> [transform]`
**描述**： 所有的变化都会依比例决定    
#### `#pattern <pattern> [transform]`
**描述**： 总是使用给定的模板    
#### `#spread <dx> <dy> <dz> [transform]`
**描述**： 随机偏移变换式    
#### `#linear <transform>`
**描述**： 从变换式列表中顺序选择变换式    
#### `#linear3d <transform>`
**描述**： 使用 x,y,z 坐标选定一个来自列表中的变换式   

---

