有很多用于控制地图和界面的可配置的设置，大多数都可以使用模板设置 - 这是很正常的，因为模板本质上是用来设置世界没有指定的某些设置的集合。

按道理来说，任何定义的世界都应该有一些默认的设置，按照他们的环境（普通、地狱、空岛）分为不同的模板 - 设置继承于默认的与环境名称相同的模板。如果 **deftemplatesuffix** 设置，模板的名称将变成环境加 '-' 加上设置的后缀。所以设置 **deftemplatesuffix** 为 **hires** 让普通的世界使用 **normal-hires** 模板，而地狱使用 **nether-hires** 模板。

除了这些由模板继承的设置，给定的设置可以通过在 **worlds:**（在 **worlds.txt**，或者 **configuration.txt**） 部分指定选项来给出自定义的设置。当给定世界的选项在配置文件出现，任何在配置中提供的设置将会覆盖对应的继承自模板的设定。

除了世界的**名称**和**地图**以外，所有的世界设定都是可选的，并且拥有默认的值，**地图**通常由模板提供。因此，在**worlds:**部分下的设定只能包含世界名称：

    worlds:
      - name: world1
      - name: world2

这可以用来控制世界的顺序，因为定义的世界总是根据这里的顺序排列。

一份更加复杂的示例世界设置如下：

    worlds:
      - name: world
        title: "My Great World"
        enabled: true
        template: mycustomtemplate
        sendposition: true
        sendhealth: true
        fullrenderlocations:
          - x: 100
            y: 64
            z: 2000
        visibilitylimits:
          - x0: -1000
            z0: -1000
            x1: 1000
            z1: 1000
        hiddenlimits:
          - x0: 100
            z0: 0
            x1: 200
            z1: 0
        hidestyle: stone
        center:
          x: 0
          y: 64
          z: 0
        bigworld: false
        extrazoomout: 0
        maps:
          - class: org.dynmap.flat.FlatMap
          ....

可用的设定如下

- _name_ : 设置世界的名称，必须独一无二，不能从模板继承。

- _title_ : 如果设置，此字符串为世界的标签，默认留空。

- _enabled_ : 如果启用（设置为 **true**），将会启用该世界的地图，或者禁用（设置为 **false**）。所有的世界都是默认启用的，所以将其设置为 false 只能防止生成地图和显示在网页上。

- _template_ : 如果设置，此选项覆写模板的默认世界设置。如果没有设置，那么将会使用基于世界环境的模板的设置（普通、地狱或空岛），如果设置了 **deftemplatesuffix**，还会在后面跟上 -**deftemplatesuffix**。这个设定不能由模板继承而来。

- _sendposition_ : 如果设置为 **false**，这将导致该世界的所有玩家的位置信息全部隐藏，设置此属性为 **true** 时，如果全局 _sendposition_ 设置为 **false**，那么仍然不显示位置信息。如果没有设置此选项，默认为 **true**。

- _sendhealth_ : 如果设置为 **false**，这将导致该世界的所有玩家的生命信息全部隐藏，设置此属性为 **true** 时，如果全局 _sendhealth_ 设置为 **false**，那么仍然不显示生命信息。如果没有设置此选项，默认为 **true**。

- _fullrenderlocations_ : 如果设置，这组世界坐标列表（每个坐标由**x**，**y**和**z**坐标组成）定义了一组附加位置（如果一个**/dynmap fullrender**命令由游戏玩家发出，那么为除了x=0，y=64，z=0，或玩家的当前位置的坐标）来开始一次完全渲染。讲道理，fullrender 就像画图软件中的油漆桶一样 - 如果地图在区块之间有间隙，比如地图使用传送门或者传送来探索，那么从一个点开始的完全渲染可能无法到达地图生成的全部区块： 添加到 _fullrenderlocations_ 中的坐标点也会使这些区块被渲染。

- _visibilitylimits_ : 如果设置，那么这个列表代表的矩形能够用来限制渲染的区域：矩形外的区域将不会被精确呈现，而是使用某种形式填充（见下 _hidestyle_）。如果列表为空，那么将没有限制，地图将会渲染到生成的所有区块的边缘位置。每个矩形由两个坐标对 - **x0**, **z0**, 和 **x1**, **z1** 组成。从 1.5-alpha-3 开始，可以使用 **x**, **z** 作为圆心， **r** 作为半径的原型区域。

- _hiddenlimits_ : 如果设置，那么这个列表代表的矩形与 `visibilitylimits` 相反 - 定义了隐藏的世界特定区域（使用 _hidestyle_ 的设置来填充）。如果定义了 'visibilitylimits' 和 'hiddenlimits'，那么首先使用 'visibilitylimits'（确定可见区域），然后使用 'hiddenlimits' 来进一步限制渲染的区域。每个矩形由两个坐标对 - **x0**, **z0**, 和 **x1**, **z1** 组成。从 1.5-alpha-3 开始，可以使用 **x**, **z** 作为圆心， **r** 作为半径的原型区域。

- _hidestyle_ : 如果 _visibilitylimits_ 和/或 _hiddenlimits_ 设置限制了世界的可见区域，则 _hidestyle_ 设置用于控制如何显示这些无法显示的区块。有以下 3 种设置：**stone**，用石块填满隐藏区域，**ocean**，用海填满隐藏的地区，或 **air**，使隐藏区域为空（如世界地图的生成部分的边缘）。默认值为**stone**。

- _center_ : 如果设置，此选项提供该世界的地图的视点中心。该坐标包括了 **x**, **y** 和 **z** 的坐标。如果没有设置，则使用世界的出生点坐标。

- _bigworld_ : 如果设置，则将使用 FlatMap 或 KzedMap 地图种类的替代的文件结构，这个结构更加适合拥有数万数十万的 tiles 的大型世界。HDMap 始终使用这种结构，不会被此设置影响。默认为 **false**，当使用 **true** 则启用这种文件结构。如果更改了此设置，则需要使用 **/dynmap fullrender** 开初始化全新的地图。

- _extrazoomout_ : 如果设置，那么这将指定地图默认的缩小等级。这能让地图查看器提供更多的缩放等级，也能生成其他的缩放等级的 tiles（基于原始的tiles）：每一级将会缩小两倍的大小，每一级 4 个tiles将会缩小为 1 个tiles。启用此设置将会增加tiles文件数量和磁盘使用量的 25% - 33%，但是可以在大型世界更高的找到方位。默认为 **0**（无附加的缩小）。

- _maps_ : 如果设置，那么 _maps_ 部分提供了按地图查看器显示的顺序用于渲染世界的所有的设置，如果在 **worlds:** 部分设置，则替换世界模板提供的地图设置。有关地图定义的详细信息，参见[地图配置](/README.md)和[高解析度地图配置](/HD-Map-Configuration.md)。
