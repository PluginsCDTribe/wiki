长方体块只是一个简单的立方体块，在其一个或多个轴上被截。  其结果是一个矩形棱柱形，否则有材质，以同样的方式作为一个[简单的方块](/Defining-a-Simple-Block.md)也会得到同样的结果。

定义一个长方体快，首先应该添加"boxblock:" 行在[材质定义文件](/Texture-Definition-Files.md)中。 在[定义长方体模型](/Defining-cuboid-models.md)获取更详细的介绍。

这是一个木制压力板（需要三维的裁剪）的模型定义的示例：
```
     boxblock:id=72,data=*,xmin=0.0625,xmax=0.9275,ymax=0.0625,zmin=0.0625,zmax=0.9275
```
接下来，方块的材质被定义为一个简单的实心方块：只需用 "block:" 行设定6个方向所引用的材质即可。在[定义一个简单的方块](/Defining-a-Simple-Block.md)获取更详细的介绍。  相应的木质压力板（如上）的材质定义是：
```
     block:id=72,allfaces=0:planks_oak,stdrot=true,transparency=TRANSPARENT
```
注意：大多数适合作为长方体块渲染的块将要求 *透明属性* 设置为透明，不阻止对其他方块的光照，或半透明的块阻止光照（如半砖或楼梯）。
