自定义着色器可以用于更改标准的着色器设置，在 **shaders.txt** 中直接更改或者在 **custom-shaders.txt** 中添加都是可以的。

现在有这么几个基础的着色器，任何一个都可以用来设置自定义着色器：

- **org.dynmap.hdmap.DefaultHDShader** - 用来支持 FlatMap 和 KzedMap 的颜色模型，包括了颜色主题、几种生物群系的着色

- **org.dynmap.hdmap.CaveHDShader** - 支持基于洞穴的颜色主题

- **org.dynmap.hdmap.TexturePackHDShader** - 支持使用 Minecraft 材质包，包括客户端的默认材质

- **org.dynmap.hdmap.TopoHDShader** - 根据方块的高度调节颜色的着色器

## 设置一个自定义的 DefaultHDShader 着色器
DefaultHDShader 类支持以下设置：
```
    shaders:
      - class: org.dynmap.hdmap.DefaultHDShader
        name: myshadername
        colorscheme: ovocean
```
和其他的相同， _name_ 属性是必需的，并且要独一无二。如果自定义着色器在  **custom-shaders.txt** 文件中拥有和标准着色器相同的名称，标准着色器将会被替换。

以下属性可选：

- _colorscheme_ : 设置渲染使用的颜色主题。对应的文件可以在 **colorschemes/** 文件夹找到，包括了 **default**, **ovocean**, **flames**, 和 **sk89q**。这些文件定义如何渲染普通方块以及基于生物群系的渲染设置。默认为 **default**。

- _biomecolored_ : 设置渲染使用的生物群系数据，默认包括 **none** （默认，方块将会被渲染为默认的颜色）， **biome** （会给予生物群系渲染）， **temperature** （基于原始生物群系的温度数据渲染），或是 **rainfall** （基于原始生物群系的湿度数据渲染）。

- _transparency_ : 控制是否使用透明度设置。默认为 **true**（正常处理透明） 或  **false** （所有方块视作不透明）。

## 设置一个自定义的 CaveHDShader 着色器
CaveHDShader 目前没有任何属性，使用这个着色器也不会有任何目的。将来的 Dynmap 更新可能会添加定义洞穴渲染使用的颜色设定。

## 设置一个自定义的 TexturePackHDShader 着色器

TexturePackHDShader 类更像用于自定义的着色器，因为必须使用附加的材质包文件。此着色器支持标准材质包的特性，也可以使用 MCPatcher 客户端的材质包，包括了高解析度的材质，自定义水和岩浆，自定义的群系树叶草地过渡。

示例的典型设置如下：
```
    shaders:
      - class: org.dynmap.hdmap.TexturePackHDShader
        name: mytexturepackshader
        texturepack: my-favorite-texturepack-v2.1.zip
        biomeshaded: true
        better-grass: false
        grid-scale: 0
```
设定包括以下：

- _name_ : 着色器名称

- _texturepack_ : 材质包文件的名称或者包含解压的材质包的目录名称。这些文件必须放在 **plugins/dynmap** 下的 **texturepacks** 文件夹。

- _biomeshaded_ : 此设置控制基于生物群系数据（温度和湿度）的草地和树叶颜色。如果设置为 **true** （默认），群系过渡将被启用。如果设置为 **false**，所有的草和树叶的颜色都是基于 **misc/grasscolor.png** 和 **misc/foliagecolor.png#** 文件的颜色。

- _better-grass_ : 此设置控制是否渲染草地方块和雪方块的侧面，就像 BetterGrass Mod 一样。如果没有设置，将会使用 **configuration.txt** 中的 _better-grass_ 设定值。

- _grid-scale_ : 是否在地图上渲染网格，如果设置为 16 ，每个方块的边缘都有白色网格。

## 设置一个自定义的 TopoHDShader 着色器

默认的 TopoHDShader 设置如下：
```
    shaders:
      - class: org.dynmap.hdmap.TopoHDShader
        name: topo
        color127: "#FFFFFF"
        color111: "#8B4513"
        color95: "#D2B48C"
        color79: "#FFFF00"
        color63: "#008000"
        color47: "#228B22"
        color31: "#104010"
        color15: "#6B8E23"
        color0: "#696969"
        linecolor: "#000000"
        watercolor: "#0000FF"
        hiddenids: [ 0 ]
```
选项包括：

- _name_ : 着色器的名称

- _linecolor_ : 高度的区域边框的 #RRGGBB 颜色，不设置则没有颜色

- _watercolor_ : 水方块使用的 #RRGGBB 颜色，如果设置，此颜色覆盖同纬度的水方块的颜色，如果没有设置，将会和其他方块相同渲染

- _colorN_ : N 从 0 - 255，对应 Y 轴。每个值都会提供用于渲染当前高度的方块的颜色，默认 _color0_ 为 #000000 且 _color255_ 为 #FFFFFF。没有提供的值将会取最近两个定义的值的插值。

- _hiddenids_ : 可选的参数，提供生成拓扑地图时隐藏的方块列表，默认只有空气 - [ 0 ]。此设置应为逗号分隔的一串数字，方括号包围（如`[ 6, 17, 18, 31, 32, 37, 38, 39, 40, 50, 55, 78, 81, 83, 86, 99, 100, 103, 104, 105, 111, 115 ]`）。

