## 总览
从图片中创建 命令可以用于从大型的高度图中生成地形。

高度图可以使用 WorldMachine 生成，或在网上找到。

示例：
[![CFI TEST](https://i.imgur.com/qUjm3hv.jpg)](https://i.imgur.com/qUjm3hv.jpg)
视频：
 - https://www.youtube.com/watch?v=pPR-w6cRNTc
 - https://www.youtube.com/watch?v=cJZk1GTig7A

前置插件：
 - PlotSquared （dev 构建版本）配置文件中 `enabled-components.worlds` 项设置为 true
 - 将任何带有你想要的材质的 jar 文件(例如你的 Minecraft 核心文件： `.minecraft/versions/<version>/<version>.jar`)放入  `FastAsyncWorldEdit/textures` 之中

## 命令用法     
 - `<arg>` - 一个必需参数     
 - `[arg]` - 一个可选参数     
 - `<arg1|arg2>` - 提供的多选一选项     
 - `<arg=value>` - 默认或建议你使用的值     

## 开始
要想开始你需要指定想要的高度图（图床链接）和你想要使用的世界。
 - 使用高度图： `/2 cfi <url>`
 - 使用固定大小： `/2 cfi <width> <length>`

查看下面这两条命令，在你完成之后请使用其中的一条：
 - /2 cfi done
 - /2 cfi cancel

## 修改世界
### 调色板
 - 地形能够通过使用图像染色。
 - 如果你想要使用颜色的话，你需要预先调整好调色板和其他设置。
##### `/2 cfi paletteComplexity <min=0> <max=100>`
 - 根据它们的对比度来过滤方块，测量材质中有多少适合那个方块的对比度的颜色。
 - 使用 `0 50` 分别作为最小值与最大值会使用最简单的方块的50%来染色。
##### `/2 cfi paletteRandomization <enabled=true>`
 - 默认是启用的，随机会为方块增加一些随机的颜色来匹配接近于给定图像上的颜色。
 - 如果禁用了的话，最接近于方块的颜色总是会被使用。 
##### `/2 cfi paletteBlocks <block-list|#clipboard>`
 - 仅允许某些方块能够用于染色
##### `/2 cfi paletteBiomePriority <percent=50>`
 - 在使用 `blockBiomeColor` 时你可以增加或减少生物群系的优先级。
 - 默认的值是 50 。
### 染色命令
##### `/2 cfi color <image-url>`
 - 仅使用方块为地形染色
##### `/2 cfi glass <image-url>`
 - 使用玻璃为地形染色（很奇特，但是从另一个角度来看也很奇怪）
##### `/2 cfi biomeColor <image-url>`
 - 使用生物群系为地形染色。

注意：使用生物群系染色不会改变方块：
 - 如果你将方块更改为除了草方块之外的别的方块你就什么都看不到了。
##### `/2 cfi blockBiomeColor <image-url>`
 - 使用方块和生物群系来为地形染色。
##### `/2 cfi biome [url|mask] <biome> [white=false]`
设置地图某些部分的生物群系。 
 - 如果使用图片了的话，生物群系有几率被设置，取决于像素点的色彩中白的程度（白色 #FFF = 100% 的几率）
 - 是否仅为白色参数决定着是否仅设置图片上的白色值
 - 如果使用了蒙版的话，生物群系在任何蒙版应用的地方都会被设置
### 高度设置
#### `/2 cfi height <url|height>`
 - 设置地形的高度，取决于高度图图片或数值。
#### `/2 cfi waterHeight <height=0>`
 - 改变水平面的生成高度。 
 - 默认水平面是禁用的（即值为0）
#### `/2 cfi waterId <number-id>`
 - 使用另外一种方块来代替水方块，例如你可能想使用岩浆。
### 杂项设定
#### `/2 cfi overlay [url|mask] <pattern> [white=false]`
 - 改变作为覆盖层的方块（默认：none）
#### `/2 cfi main [url|mask] <pattern> [white=false]`
 - 改变作为填充层的方块（默认：stone）
#### `/2 cfi floor [url|mask] <pattern> [white=false]`
 - 改变作为顶层的方块（默认：grass）
#### `/2 cfi column [url|mask] <pattern> [white=false]`
 - 改变顶层和主方块。
### 其他选项
#### `/2 cfi caves`
 - 生成洞穴
#### `/2 cfi ore[s]`
##### `/2 cfi addores`
 - 增加默认的 Minecraft 原版矿石。
##### `/2 cfi ore <mask> <pattern> <size> <frequency> <rarity> <min-Y> <max-Y>`
 - 使用给定的模板和设置来生成矿石。
#### `/2 cfi schem  [url] <mask> <file|folder|url> <rarity> <distance> <rotate>`
 - 在地形上使用schematic文件。 
 - 改变蒙版（例如：角蒙版）来仅在某些特殊的位置放置schematic文件中的内容。
 - 稀有程度是一个在 0 到 100 之间的值。