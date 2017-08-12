# 变换式
变换式能够应用在笔刷上或在全局中，它可以修改方块变化的位置和方式。

又见： [这里](/Region_operations.mc#Deforming_regions)

----

### 用法
#### 多个变换式
使用半角逗号 (`,`) 来随机从列表中使用一个变换式，例如： `#offset[0][1][0],#pattern[wood]` (将方块向上偏移一个位置，或是将它变成木头)

使用这个符号 (`&`) 来为一个方块使用多个变换式，例如： `#offset[0][1][0]&#pattern[wood]` (将方块向上偏移一个位置，且将它变成木头)
#### 参数
变换式的参数应该写在方括号之中，例如： `#offset[0][1][0]`

----

### 设置变换式
#### `//gtransform [transforms...]`
权限： `worldedit.global-transform`    
描述： 设置全局变换式
#### `//transform [transform...]`
权限： `worldedit.brush.options.transform`    
描述： 设置笔刷的变换式（将多个变换式用空格 ` ` 或者半角冒号 `:` 分割）

### [`>> 点这里查看变换式的列表……`](/Commands.md#transform-commands-)