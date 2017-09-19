按照他们对 v0.20 版本的介绍，HDMap提供了一种新的】更加灵活的，并且（按理说）更加复杂的用来在服务器上定义和自定义地图的方式。一些HDMap如何定义和架构的细节旨在抵消一些额外的复杂性 - 但是理解HDMap定义后的"操作理论"也是很重要的，这能让你知道你需要做些什么才能得到想要的地图（而不用做出任何不必要的努力就能得到想要的结果）。

## 迅速上手：启用HDMap的模板

Dynmap包括了3种模板，每种都提供了如何定义不同种类的世界（普通、地狱、末地）。编辑 **configuration.txt** 来在这些模板之间选择，并且更改 _deftemplatesuffix_ 的设置（可以在 **configuration.txt** 的顶部找到）。现在定义的值包括了这些：

* _deftemplatesuffix: ""_ : 这让Dynmap使用"经典"的默认模板 - 那些低解析度并且渲染非常快速，但是远没有让人满意的地图种类。这种模式使用的模板的文件可以在 **templates/normal.txt**, **templates/nether.txt**, 和 **templates/the_end.txt** 找到。这在 0.23 以及之前的版本都是默认设置。

* _deftemplatesuffix: vlowres_ : 这是 "very-low-res"（非常低解析度） 的高清地图。这些地图跟'经典'的默认地图（表面地图，东南方地图，洞穴地图），但是是使用高解析度地图渲染器渲染的。并且，默认的Minecraft材质将会用于方块着色，用于更加准确的表现地图。使用的模板文件在**templates/normal-vlowres.txt**, **templates/nether-vlowres.txt**, 和 **templates/the_end-vlowres.txt**。在 0.24 版本，这些是默认的模板。

* _deftemplatesuffix: lowres_ : 这是 "low-res"（低解析度）高清地图，这些地图跟'经典'的默认地图（表面地图，东南方地图，洞穴地图），但是是使用高解析度地图渲染器渲染的与经典地图相比高 2-3 倍分辨率的地图。并且，默认的Minecraft材质将会用于方块着色，用于更加准确的表现地图。渲染这些地图的时间比经典地图长大约 4-6 倍，存储空间使用也会多 4 倍。使用的模板文件在**templates/normal-lowres.txt**, **templates/nether-lowres.txt**, 和 **templates/the_end-lowres.txt**。

* _deftemplatesuffix: hires_ : 这是 "high-res"（高解析度）的高清地图。这些地图跟 _lowres_ 高清地图相似，除了 _surface_ 地图（直观图）使用了更加高的分辨率（比 _lowres_ 高 4 倍。比_经典_高8倍），并且在更低的观察角度渲染（水平的 30 度而不是 60 度）。渲染的结果是非常棒的，但是会消耗相当的时间进行渲染（约低清晰度的 16 倍时间，经典地图的 64 倍时间），并且会使用更多的磁盘（比低清晰度多 16 倍，比经典地图多 64 倍）。使用的模板文件在 **templates/normal-hires.txt**, **templates/nether-hires.txt**, 和 **templates/the_end-hires.txt**。

当选择了一个模板集之后，地图就可以通过编辑模板文件来达到更高的自定义效果。以下部分描述了完全的地图设置方法。

## 基础：如何将高清地图添加到模板或世界

设置 HDMap 与其他现有的地图是相同的，和其他地图一同，HDMap 的配置模板在 _maps:_ 部分提供（configuration.txt 或者相应的文件夹）或者在世界配置的 _worlds:_ 部分（ **configuration.txt** 或者 **worlds.txt** 文件）。接下来是 HDMap 的一份示例配置：

    maps:
      - class: org.dynmap.hdmap.HDMap
        name: myhdmap
        title: "My HD Map"
        prefix: hdm1
        perspective: iso_S_90_lowres
        shader: stdtexture
        lighting: default

与其他的地图相似，HDMap 需要 3 个基本的参数：

- _class:_ 设置 - 此选项设置了地图的类型，HDMap 为 `org.dynmap.hdmap.HDMap`

- _name:_ 设置 - 此选项设置了此地图的独一无二的名称（与其他给出的世界的地图名称不同）。此名称用于识别地图，包括在 _defaultmap_ 设定选择默认地图时和使用网页的参数时。

- _prefix:_ 设置 - 如果没有提供， _name_ 设置将被用作此项。这项用于存储地图的文件和目录名称 - 所以也需要区别于其他世界的地图的 _prefix_ 值、

现在，接下来的设定控制 HDMap 将怎样绘制：

- 我们怎么确定看到的内容？

- 我们决定如何着色？

- 照明对我们看到的颜色有什么影响？

使用 HDMaps，这些问题的答案由接下来的 3 个选项所决定：

- _perspective:_ 设置决定我们查看地图使用的透视种类。透视控制着物体的投射（目前只有等距投射），查看地图的方向（南北角度，水平角度），和查看视图的缩放（每一格边界有多少像素）。

- _shader:_ 设置提供了用于着色地图的渲染器 - 决定透视的着色。这可以包括使用特定的Minecraft材质的着色器，使用老式颜色主题的着色器（就像 FlatMap 和 KzedMap 一样），使用生物群系着色的着色器，或者洞穴着色器。

- _lighting:_ 设置提供了用于更改地图着色的光照系统，基于光照条件。这可以包含阴影渲染，夜视渲染或二者皆可。

Dynmap使用几个提前设定好的预设来简化配置的过程，这些预设，有必要时可以修改，或是在创建新的配置时作为参考。

### 预设

你可以在 _perspectives.txt_ 很多的预设，预设的名称按照严格的命名规则，这样可以使其更加浅显易懂：

_投影_ _ _方向_ _ _角度_ _ _缩放_

其中：

- _projection_ 是观察点的类型：目前只有 **iso** （等距）支持。

- _direction_ 是观察的方向：这八个方向都支持 (**N**, **NE**, **E**, **SE**, **S**, **SW**, **W**, **NW**)

- _angle_ 是观察的水平角度： **30** (30 度) 和 **60** (60 度) 支持所有的观察角度，**90** (90 度 - 自上而下) 用于 **N** (北), **S** (南), **E** (东) 和 **W** (西) 的观察角度。

- _scale_ 是视图的缩放倍数或细节程度：**vlowres** 对应每个方块两个像素的宽度（与 KzedMap 解析度相似），**lowres** 对应每个方块 4 个像素的宽度（KzedMap 的两倍解析度），**medres** 对应每个方块 8 个像素的宽度，**hires** 对应每个方块 16 个像素的宽度。

[所有可用的预设](/Full-list-of-predefined-perspectives.md)

### 预设着色器

预设的着色器设定（可在 **shaders.txt** 找到）包括了以下内容：

- **default** : 默认的着色器，使用标准Minecraft材质包渲染地图。

- **defaultscheme** : 使用 'default' 颜色主题（在 **colorschemes/default.txt** 中设定）渲染地图。

- **ovocean** : 使用 'ovocean' 颜色主题（在 **colorschemes/ovocean.txt** 中设定）渲染地图。

- **flames** : 使用 'flames' 颜色主题（在 **colorschemes/flames.txt** 中设定）渲染地图。

- **sk89q** : 使用 'sk89q' 颜色主题（在 **colorschemes/sk89q.txt** 中设定）渲染地图。

- **biome** : 使用生物群系种类渲染地图。

- **temperature** : 使用环境温度数据来渲染地图。

- **rainfall** : 使用生物群系雨水/湿度数据来渲染地图。

- **no_transparency** : 使用默认的颜色主题（在 **colorschemes/default.txt** 中设置）渲染地图，关闭所有的透明处理（水、玻璃，树叶为实体）。

- **cave** : 使用"洞穴视图"渲染 - 显示空气与非空气之间的界限，使用基于深度的从绿色到蓝色渲染。

- **stdtexture** : 使用标准Minecraft材质包（在 **texturepack/standard/**）渲染地图。

- **stdtexture-nobiome** : 使用标准Minecraft材质包（在 **texturepack/standard/**）渲染地图，但是关闭基于生物群系的彩色草地和树叶。

- **topo** : 创建基于颜色的地形图，从 128 格生成世界。

- **topo256** : 创建基于颜色的地形图，从 256 格生成世界。

- **topo-noplants** : 创建基于颜色的地形图，从 128 格生成世界，隐藏普通的树和植被。

- **topo256-noplants** : 创建基于颜色的地形图，从 256 格生成世界，隐藏普通的树和植被。

### 预设光照

预设的光照配置可以在 **lightings.txt** 找到，包含以下设置：

- **default** : 默认无特殊处理，无阴影，完全白天

- **shadows** : 使用完全白天的设置，但是启用阴影处理。

- **night** : 使用标准的月夜的设置，启用阴影处理。

- **brightnight** : 使用更加明亮的月夜的设置（使不明显的地形更加明显），启用阴影处理。

- **nightandday** : 渲染两组 tiles，一组用于白天渲染（基于 **shadows** 设置），另一组用于夜晚渲染（基于 **night** 设置），将会对应对应世界的白天和夜晚设置。

- **brightnightandday** : 与 **nightandday** 相同，但是使用 **brightnight** 相同的设置来渲染夜晚。

预设的选择对最终渲染地图的大小和质量的影响是非常明显的，特殊的， -scale- 将会明显影响渲染地图的大小，因为渲染的tiles的数量随着 -scale- 上升而上升。**lowres** 地图将会比 KzedMap 的 tiles 多 4 倍（水平垂直都多2倍解析度 - 2x2=4）。**medres** 又多了两倍的解析度，所以就是 4 倍的tiles（或者说比 KzedMap 多 16 倍） 。**hires** 又多了两倍的解析度，所以就是 4 倍的tiles（或者说比 KzedMap 多 64 倍）！-hires- 的地图看起来非常赞，但是在第一次完全渲染的时候准备花上一些时间（几个小时，如果地图更大可能要一天）。低的观察视角（**30** 度角）会让地图多一些tiles渲染（低的视角意味着观察的视线会包含更多的区块 - 相比垂直视角）。其他的设置 - -shader- 和 -lighting- 基本对地图文件的大小没有影响，并且对地图渲染的时间有可以忽略的影响。

### 自定义预设，着色器，光照

查看一下页面获得关于自定义预设、着色器、光照的详细信息：

[自定义预设](/Defining-custom-perspectives.md)

[自定义着色器](/Defining-custom-shaders.md)

[自定义光照](/Defining-custom-lightings.md)

定义自定义预设、着色器、光照之后，地图就可以按照使用预设配置一样使用这些自定了。

## 附加高解析度地图设置

HDMap 支持很多可选的附加选项，用于设置用户的使用。这些设置包含：

- _title_ : 此选项控制网页的地图的标题。

- _icon_ : 此选项允许控制地图图标的文件图片的 URI 地址。如果没有设置，此选项使用 **images/block_**_name_**.png**。

- _background_ : 此选项提供了地图的背景颜色。颜色的值为经典的 CSS 格式的颜色代码：#rrggbb。如果没有设置则为黑色(#000000)。

- _backgroundday_ : 此选项提供了白天时地图的背景颜色 - 当设置后并且为白天，此选项覆盖 _background_ 设置，只能在开启了白天夜晚的地图使用。

- _backgroundnight_ : 此选项提供了夜晚时地图的背景颜色 - 当设置后并且为夜晚，此选项覆盖 _background_ 设置，颜色的值为经典的 CSS 格式的颜色代码：#rrggbb。只能在开启了白天夜晚的地图使用。

- _mapzoomin_ : 此选项控制原始地图的放大步数。放大的等级可以在不需要更多地图数据的情况下拉伸地图 - 相同的像素会变得更大（1步数=2x，2步数=4x，等等）。默认为 2 （允许两个额外的放大，对应 2x 和 4x）。

- _image-format_ : 此选项控制生成的tiles的格式，默认为PNG，是一种无损的图像形式，但是大小最大，会使用明显的带宽。JPG 是一种有损的压缩形式，牺牲质量来减少文件大小。最好的 JPG 文件仍然明显比 PNG 小（一般是 2 倍），质量少了一点。更低的质量等级仍然可以得到很好地地图质量，并且文件大小将减少很多（6 - 10 倍）。支持的值如下：

    + _png_ : 无损（但可能有点大）PNG（默认）

    + _jpg_ : 质量很好的 JPG (85% 质量) - 与 jpg-q85 相同

    + _jpg-q75_ : 质量还行的 JPG (75% 质量)

    + _jpg-q80_ : 质量还行的 JPG (80% 质量)

    + _jpg-q85_ : 质量很好的 JPG (85% 质量)

    + _jpg-q90_ : 质量很好的 JPG (90% 质量)

    + _jpg-q95_ : 质量非常好的 JPG (95% 质量)

    + _jpg-q100_ : 质量非常好的 JPG (100% 质量)

注意：JPEG 不支持透明（透过的背景颜色）。如果 _backgroundday_ 或 _backgroundnight_ 的颜色更改，所有的tiles都将被重新渲染。并且，如果白天和夜晚的颜色不同，开启了 _night-and-day_ 选项（比如 _nightandday_ 或 _brightnightandday_ 光照）必须生成两组tiles（每一组对应白天和夜晚）。
