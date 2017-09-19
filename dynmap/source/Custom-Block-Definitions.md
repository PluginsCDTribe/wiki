Dynmap 支持数据驱动的方法来支持对新的 Minecraft 方块的支持，比如通过某些插件和客户端 Mod 提供的新方块。这些定义对 Dynmap 的内部光线追踪非常敏感，并且可能在以后的版本没有任何通知就过时了 - 实际上会避免这一点，但是如果你要在这之上花费太多的经历之前请务必了解。

## 方块是如何被渲染的

Dynmap 的方块的渲染通过很多独特的机制完成，这些机制用于对不同的方块和 Mod 的需求。在所有情况下，方块的渲染由两个核心元素组成：一个**模型**用于定义方块的形状，一组**材质**来应用颜色到不同的表面。因为 Minecraft 的"方块"的特质，大多数的方块就是一个简单的立方体：所以大多数方块不需要自定义模型，可以被认为是一个简单的实体方块。

附加 Mod 的对自定义方块的支持文件是通过对每个 Mod 定义两个文件来实现的：一个定义纹理贴图（按照命名约定 `*-texture.txt`，放在 'renderdata' 文件夹（或者该文件夹下的子目录）），一个用于定义不是简单立方体的方块的模型（按照命名约定 `*-models.txt`，放在 'renderdata' 文件夹（或者该文件夹下的子目录））。对那些只有简单方块的 Mod，不需要 `*-models.txt` 文件（没有定义模型的方块全部处理为简单立方体）。

## 创建材质和模型定义文件
* [材质和模型文件的基础特性](/Common-Features-for-Texture-and-Model-Definition-Files.md)
* 查看[材质定义文件](/Texture-Definition-Files.md)的细节
* 查看[模型定义文件](/Model-Definition-Files.md)的细节

## 定义方块
* 定义一个简单的立方体，查看[定义一个简单的方块](/Defining-a-Simple-Block.md)
* 定义一个长方体方块，查看[定义长方体方块](/Defining-a-Cuboid-Block.md)
* 定义基于自定义的方块渲染器的方块，查看[自定义方块着色器](/Defining-a-Block-using-a-Custom-Block-Renderer.md)
定义一个基于立体模型的方块，查看[使用立体方块模型](/Defining-a-block-using-a-volumetric-block-model.md)
