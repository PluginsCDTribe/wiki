在 Dynmap v1.9.3 中，我们支持了将地图生成并导出为 Wavefront OBJ 格式的文件，这个特性由 [jmc-2-obj](http://jmc2obj.net/) 工具启发而来，允许管理员（或控制台）选择并导出他们的部分世界为模型文件，用于其他支持 Wavefront OBJ 格式的建模软件的导入 - 包括了 Blender（一个免费开源的渲染和动画套件），Cinema 4D，Maya，3D Studio Max 和其他的软件。这些导出的模型可以用于 Dynmap 不支持的高级渲染（保举哦了更高级的光照和反射）。由于 Dynmap 导出的 OBJ 格式文件与 jmc-2-obj 软件产生的非常相似，所以针对 jmc-2-obj 的模型的导入和处理与 Dynmap 的 OBJ 导出非常相似。

导出和处理使用新的 /dynmapexp 命令完成，此命令可以设置一些属性来控制导出：

* x0, y0, z0 : 这些是最小的 X, Y, 和 Z 轴的长方体/矩形棱柱的值
* x1, y1, z1 : 这些是最大的 X, Y, 和 Z 轴的长方体/矩形棱柱的值
* world : 用于导出的世界的名称
* byChunk : 如果设置为 true，这将会生成整个区块的所有方块的对象
* byBlockID : 如果设置为 true，这将会生成所有给定方块ID的对象
* byBlockIDData : 如果设置为 true，这将会生成所有给定方块ID和方块元数据的对象
* byTexture : 如果设置为 true，这将会生成所有给定材质的方块的对象
* shader : 指定用于导出的使用的材质的着色器，默认情况下使用 `stdtexture`，只有基于材质包的着色器才支持

/dynmapexp 的子命令包括了：

* /dynmapexp set <attribute> <value> : 允许设置导出的属性（如上），附加的属性可以在同一个命令使用，如 `/dynmapexp set x0 0 y0 0 z0 100`。
* /dynmapexp radius <value> : 只能由一个游戏中的玩家使用：此命令会指定导出的世界为玩家所在的世界，并设置半径为玩家所在位置的半径，Y 轴为 0-255 的所有方块。
* /dynmapexp info : 显示当前导出的属性
* /dynmapexp pos0 : 此命令只能由玩家在游戏中使用：设置导出范围的第一个点
* /dynmapexp pos1 : 此命令只能由玩家在游戏中使用：设置导出范围的第二个点
* /dynmapexp reset : 重置导出属性为默认值
* /dynmapexp export <name> : 初始化一个导出，创建一个叫 <name>.zip 的文件（默认在 dynmap 文件夹下的 export  文件夹，可以在 exportpath 中设置）。导出是异步处理的，并且会耗费几分钟完成，用时取决于选区的大小
* /dynmapexp purge <name> : 删除上一个导出

完成后，ZIP文件中将会包含以下内容：

* 一个 minecraft.obj 文件，包含导出的模型（可能非常大）
* 一个 <shadername>.mtl 文件，包含材质列表（对应每个minecraft材质）
* 一个 <shadername> 目录，包含使用的材质文件

解压文件并将 minecraft.obj 导入到渲染/建模软件

