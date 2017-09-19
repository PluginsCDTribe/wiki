材质定义文件（*-texture.txt 文件）提供了数据的三个关键设置：
* 需要什么材质文件，以及他们怎么被读取
* 每个自定义方块的每个面应用什么材质，伴随着的还有这些材质如何被使用（例如：根据生物群系的不同来进行染色，旋转，添加覆盖层，等等）
* 在Mod提供自定义生物群系时，附加属性需要决定怎样提供生物群系敏感的材质

## 定义材质文件
在历史之中，Minecraft使用了很多定义材质的方法，并且这些方法变化了好几次（特别是在1.5版本，1.6版本又变了一次）。要想处理这些不同之处的话，你需要指定一些定义标志。

### 为1.6.x和之后的服务器定义材质
至于 Minecraft v1.6.0，大多数嵌入的材质都包括在 assets/minecraft/textures/blocks 路径（在Minecraft客户端的Jar文件中，或者在资源包的ZIP文件中）下找到的单个文件。对于 v1.6.x 和晚些的Minecraft Forge Mod，材质资源需要在给予的Mod文件（ZIP或JAR）中找到，路径为 assets/\<modname\>/textures/blocks （其中 \<modname\> 是用小写表示的Mod名字）。

要想指定加载材质所使用的相对路径，'texturepath:' 这一行应该被包括在材质文件之中。在设置之后，给予的路径可以用来读取任何指定的材质（或者，至少直到加载下一个 texturepath: 行——在这一点上，它的路径可以用来加载额外的材质）。举个例子，Minecraft V1.6.x ，或更晚版本的 BiomesOPlenty Mod 的材质应该为：

     texturepath:assets/biomesoplenty/textures/blocks/

只要路径制定好了，材质文件需要渲染单独需要渲染的方块，使用 'texture:' 行。这些行的格式像下面那样：

     texture:id=<texture-id>

其中 <texture-id> 不仅用来表明它会用于定义文件中定义材质，它也是文件名的基础部分，用于读取材质文件（通过向texturepath中加入<texture-id>，然后加入一个“.png”扩展名 —— 举个例子，ID为“test123”会读取材质资源 assets/biomesoplenty/textures/blocks/tes123.png ，这里使用之前的 texturepath 示例）。如果ID需要与文件名不同的话，你可以指定全名：

     texture:id=<texture-id>,filename=<full-filename>

举个例子：

     texture:id=test123.id,filename=assets/biomesoplenty/textures/blocks/tes123.png

对于一个材质文件包含多于一个材质的情况而言，材质的数目横向（X的数目）和纵向（Y的数目）可以被指定：

     texture:id=<texture-id>,xcount=<xcount>,ycount=<ycount>

在这种情况之下，文件被读取然后分成指定的网格。分开的材质通过行序指数来排列：\<column-base-zero\> + \<xcount\>*\<row-base-zero\> : 所以，第一个材质，即网格的左上角的材质，指数为0，它右面的那个材质指数为1，以此类推，直到下一行的第一个材质为止（这些都是指数，即X数目）。对于单个材质文件而言（默认情况），只会使用指数为0的那一个。

一些材质文件可以特别格式化： 材质定义的位置在文件之中，而不是网格（举个例子，箱子，玩家或怪物的材质文件）。遇到这些情况时，查看[特殊材质文件种类](/Special-texture-file-types.md)来获得支持的类型的有关信息。遇到这些情况时，“format”属性可以用于定义文件的布局。

     texture:id=<texture-id>,format=<file-format>

### 为 1.5.x 定义材质
为 Minecraft v1.5.x定义的材质的处理方式与1.6.x的处理方式有一点类似，但是有一些关键性的不同之处：
* 原版的材质的路径为客户端JAR或材质包的 textures/blocks 路径之中
* 对于Minecraft Forge Mod的材质通常可以在Mod的ZIP或JAR文件中的mods/\<modname\>/textures/blocks 路径找到

对于v1.5.x的Mod而言， 'texturemod:' 行可以用来指定材质路径的特殊名字（'mods/<modname>/textures/blocks' 中 \<modname\> 的名字）。如果没有指定的话， \<modname\> 默认会使用提供在文件中 'modname:' 这一行的Mod名字。所以，对于v1.5.x格式的Mod，请使用这行字：

     texturemod:<modname>

它就相当于使用这行字

     texturepath:mods/<modname>/textures/blocks/

另外，材质的指数和格式和v1.6.x及以后的版本相同。注意：使用 'texturepath:' 行结果会使定义文件中的所有 'texturemod:' 行全部被忽略。

### 为v1.4.x或更早的版本定义材质
Minecraft v1.4.7 和更早版本中的材质几乎都在包括网格的16x16的材质文件之中（这相当于X数量为16，Y数量为16）。对于这些文件而言，你经常要使用 'texturefile:' 行。 'texturefile:' 行几乎可以说完全等于 'texture:' 行，只是默认的X数量为16，Y数量为16而已（针对 'texture:' 中的单个材质来说，等于X数值为1，Y数值为1）。

在 v1.5.x之前，Minecraft Forge Mod定义材质资源没有统一的方法，所以 'texturepath:' 命令，或者文件名的 'texturefile:' 或 'texture:' 属性行通常是必需的。

## 材质的参考系
只要所需的材质读取之后，不同的指令就可以用来指定Mod中不同方块不同面的材质。在所有的情况下，某个特殊材质的参考是通过结合材质文件中的指数（单个材质的材质文件通常是0）和'texture:' 或 'texturefile:'行中 'id' 属性的值实现的。总的来说，格式如下：

     <index>:<texture-id>

在所有方块定义行中，又能够指定默认材质ID，可用于所有缺失 ":\<texture-id\>" 后缀的参考系： 'txtid=' 属性。通过指定 'txtid=\<texture-id\>' 属性，对于 '\<index\>' 的参考变得等价于 '\<index\>:\<texture-id\>'。材质指数值限制在0至999之间，包含这两个数。

除了选择使用的材质之外，材质参考系也能够做出一系列修改功能，这会影响材质在渲染时的处理过程。这些修改功能通过为材质增加一系列特殊值来实现（都是1000的倍数），加入的位置为 \<index\> 。这些修改的定义值为：

* 1000 : 材质使用生物群系使用的草方块的颜色进行染色(assets/minecraft/textures/colormap/grass.png ，版本为v1.6.x 或更晚)

* 2000 : 材质使用生物群系使用的树叶方块的颜色进行染色(assets/minecraft/textures/colormap/foliage.png，版本为v1.6.x 或更晚)

* 3000 : 材质使用生物群系使用的水方块的颜色进行染色(通过 MCPatcher/Optifine - assets/minecraft/mcpatcher/colormap/water.png ，版本为v1.6.x 或更晚).

* 4000 : 材质顺时针旋转90度

* 5000 : 材质顺时针旋转180度

* 6000 : 材质顺时针旋转270度

* 7000 : 材质横向镜面翻转（左面变为右面）

* 8000 : 材质向下偏移50%高度

* 9000 : 材质向下偏移50%高度，且横向镜面翻转

* 10000 : 材质被转换用于倾斜火把（特殊情况）

* 11000 : 材质是草方块一边（对于生物群系染色和雪颜色两者兼容的特殊情况）

* 12000 : 材质在代表内表面，且接近其他相同类型的方块时透明（例如玻璃和水方块的内部）

* 13000 : 材质使用云杉树叶的颜色着色

* 14000 : 材质使用白桦树叶的颜色着色

* 15000 : 材质使用睡莲的颜色着色

* 17000 : 材质使用 colorMult 属性的值或 custColorMult 属性类定义的值着色（特别分出来一条）

* 18000 : 相当于270度旋转 (6000) 和草的色调 (1000)

* 19000 : 相当于270度旋转 (6000) 和树叶的色调 (2000)

* 20000 : 相当于270度旋转 (6000) 和水的色调 (3000)

* 21000 : 相当于多色调和 (17000) 和内部透明 (12000)

* 22000 : 相当于树叶色调 (2000) 和多色调 (17000)

## 方块 ID 数值
某个特殊方块的材质的定义需要定义给定的方块类型要使用哪个方块ID。内置的Minecraft基础方块当前拥有修复后的方块ID数值，但是Minecraft Forge Mod的所有方块ID是通过他们的配置文件来控制的。这些ID通过"cfgfile:"行来读取（请查看 [材质和模型文件的基础特性](/Common-Features-for-Texture-and-Model-Definition-Files.md) 获得关于这一行的更多信息，以及配置文件中一些有用的内容的设置）在所有方块定义行之中，方块ID通过 'id=' 属性来指定。 'id=' 属性的值可以是数值（必须连续不间断），根据Mod的配置文件中定义的符号名称，或是展示名称的组合，加号 (\+)，和数值。在所有情况中，如果ID的值是0或附属的话，这个ID值就会被忽略（允许禁用方块，忽略更简单）。
## 定义方块材质地图
* 要想定义简单的正方体方块，查看 [定义一个简单的方块](/Defining-a-Simple-Block.md)
* 要想定义长方体方块，查看 [定义长方体方块](/Defining-a-Cuboid-Block.md)
* 要想定义以自定义方块着色器为基础的方块，查看 [自定义方块着色器](/Defining-a-Block-using-a-Custom-Block-Renderer.md)
* 要想定义根据不定体积的方块模型的话，请查看 [使用立体方块模型](/Defining-a-block-using-a-volumetric-block-model.md)

