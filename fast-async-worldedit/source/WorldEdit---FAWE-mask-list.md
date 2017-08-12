# `蒙版`
蒙版是限制方块什么时候能够放置出来的，举个例子：只在石头下方放置方块。

全局蒙版会应用于所有编辑中，笔刷蒙版只会应用于当前笔刷上。

----

### 用法
#### 方块
使用方块的名字或ID（例如： `stone`）。要想获得更多信息请查看 [方块数据用法](http://wiki.sk89q.com/wiki/WorldEdit/Block_data_syntax)
#### 多个蒙版
使用 `,`(或) 或者 `&`(和) 来分割多个蒙版，举个例子： `grass,$desert`
#### 参数
蒙版的参数应该写在方括号之中，例如： `#offset[0][5][3]`

----

### 设置蒙版
#### `//gmask [masks...]`    
权限： `worldedit.global-mask`
描述： 全局目标蒙版，应用到你做的所有编辑中，蒙版跟目标方块有关（即世界中的方块）。
#### `//gsmask [masks...]`
权限： `worldedit.global-mask`    
描述： 全局资源蒙版，应用到你做的所有编辑中，蒙版跟资源方块有关（例如：你剪切板中的方块）    
#### `//mask [masks...]`
权限： `worldedit.brush.options.mask`    
描述： 设置笔刷的目标蒙版
#### `//smask [masks...]`
权限： `worldedit.brush.options.mask`    
描述： 设置笔刷的资源蒙版

### [`>> 点这里来查看所有蒙版……`](/Commands.md#mask-commands-)