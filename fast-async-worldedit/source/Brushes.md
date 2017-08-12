### 总览
FAWE 拥有能够让你在远处建筑或涂画的笔刷工具。当你启用了一个笔刷之后，笔刷就会绑定在你当前持有的物品上，你可以将不同的工具绑定在不同类型的物品上，单个物品最多绑定两个笔刷。

### 装备上你的笔刷：
绑定到任意点击上：
`/br <brush>`        
绑定到右键点击上：
`/br primary <brush>`    
绑定到左键点击上：
`/br secondary <brush>`    

### 修改笔刷设置
 - [`/mat <pattern>`](/WorldEdit-and-FAWE-patterns.md) - 修改放置方块的模型
 - [`/mask <mask>`](/WorldEdit---FAWE-mask-list.md) - 修改应该改变的方块的蒙版类型
 - [`/smask <mask>`](/WorldEdit---FAWE-mask-list.md) - 如果方块可以放置的话源模板的改变
 - [`/targetmask <mask>`](/WorldEdit---FAWE-mask-list.md) - 能够被笔刷作为目标的方块，默认值是 `!air`     
 - [`/transform <transform>`](/Transforms.md) - 放置方块处的变换式
 - `/range <range>` - 你能够使用笔刷的距离
 - `/size <size>` - 你的笔刷的大小（如：半径为10的球体）    
 - `/none` - 取消工具的绑定
使用 `-h` 标志来改变你副手中笔刷的相关设定。

### 改变笔刷的目标位置
你可以改变笔刷对目标定位的相关设置来符合在不同区域建筑的需要（空气，墙，地面等等）
改变 `//brush range` 也会很有用。 
`/br target <0-3>`      
 - 0 = 定位方块
 - 1 = 定位直接指向的方块，距离由 Pitch 决定
 - 2 = 定位一点，距离由自地面算起的高度决定
 - 3 = 定位方块的面

### 增加笔刷行为
使用你的鼠标滚轮来改变笔刷表现
 - `/br scroll clipboard <file|folder|asset url>`      
 - `/br scroll mask <mask1> <mask2...>`      
 - `/br scroll pattern <mat1> <mat2...>`      
 - `/br scroll range`      
 - `/br scroll size`      
 - `/br scroll target`      

### 重设笔刷
潜行（`shift`）然后点击来重设笔刷。
这将会，举个例子，清除你的粘贴笔刷的剪切板，或者重设你的曲线笔刷的相关点。

### 显现笔刷的范围
使用 FAWE 你能够显现出笔刷将会怎么改变方块：
`/br vis <0-2>`    
 - 0 = 不显现
 - 1 = 显现单个点
 - 2 = 所有将会改变的方块全部显现    

视频： https://www.youtube.com/watch?v=xX-MTSLoNXw    
图片： https://i.imgur.com/J2g6Qfn.jpg    

### 笔刷：
[要想列出所有笔刷的话，请查看命令页面。](/Commands.md#brush-commands-)