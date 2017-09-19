Dynmap 支持添加数据到地图的机制，这些数据统称为**Markers**标记，由记号（标记图标），区域标记和折线标记构成。

### 标记组

标记的收集和组织被称为**Marker Sets**标记集，每个标记集是一个图层，可以使用网页的层选择器选择，每个标记都包含在特定的标记集中。默认情况下，总有一个标签为 _Markers_ 的标记集，用于包括没有被手动分配的标记。删除标记集将会删除集合中的所有标记。

新的标记集可以通过使用 `/dmarker addset <markerset-label>` 或 `/dmarker addset id:<markerset-id>` 命令来创建，这个命令可以添加其他的参数： `prio:<N>` 用于控制图层的相对于其他的标记集的优先度顺序；`hide:<true|false>` 用于控制默认情况下是否可见（选中）或不可见（未选中）；`minzoom:<N>` 用于控制标记集可见的最小的缩放程度，如果为达到此缩放将不会可见。

对已有标记集的设置可以通过使用 `/dmarker updateset <markerset-label>` 或 `/dmarker updateset id:<markerset-id>` 命令，可以使用 `prio:<N>`，`hide:<true|false>` 或 `newlabel:<new-label>` 参数。

在 0.32 版本，选项 `showlabels:<true|false|null>` 被加入支持。此选项为 _true_ 或 _false_ 时，将会启用或禁用标记集的标签的可见性（禁用时，如果鼠标悬浮在某标记上，标签仍然会显示）。值 _null_ 将会使用全局设置（由 _configuration.txt_ 中的 _markers_ 部件的 _showlabels_ 设置指定）。

标记集（除了默认的 _Markers_ 集合）可以使用  `/dmarker deleteset <markerset-label>` 或 `/dmarker deleteset id:<markerset-id>` 命令删除。

### 记号

记号是最常见的地图标记 - 简单的图标和一些描述性的标签和弹出窗口。每个记号都有一个在世界中的坐标（X Y Z 和世界 ID），一个记号图标 ID，一个标签，和一个可选的描述。记号图标 ID 可以是标准记号 ID（本页底部） 中的一个，也可以对应安装的图标（查看下方的 _记号图标_ 部分）。

记号可以通过以下方法添加：

* `/dmarker add <marker-label> icon:<icon-id> set:<markerset-id>` - 此命令必须由一个在线的玩家使用，这将在玩家的位置添加一个记号，如果 _set_ 没有被提供，那么记号将会创建于默认的标记集。如果 _icon_ 没有被提供，那么将会使用默认的记号图标（_default_，一个房子）。

* `/dmarker add id:<marker-id> <marker-label> icon:<icon-id< set:<markerset-id>` - 与上方相同，但需要提供 独立 ID。

* `使用牌子` - 如果 _markers_ 部件的 _enablesigns_ 设定被弃用，那么拥有对应权限的用户可以使用特殊标签的牌子来创建记号。牌子的第一行必须是 `[dynmap]`，之后，除了格式为 `set: <标记集ID>` 或 `icon:<图标ID>`（允许设置为特殊的图标，如果没有设置，那么将使用默认的 _sign_ 图标）的行数都将被包含在此记号的标签中。如果记号被成功创建，牌子的 **[dynmap]**，**set:**，**icon:** 行都会被删除。如果这个牌子之后被破坏，那么地图上对应的记号将被删除。

创建后，记号可以使用以下的命令编辑：

* `/dmarker movehere <marker-label> set:<markerset-id>` 或 `/dmarker movehere id:<marker-id> set:<markerset-id>` - 此命令将会移动指定的记号到玩家的位置，注意：如果要选择不在默认集中的记号，那么 _markerset-id_ 是必要的。

* `/dmarker update <marker-label> set:<markerset-id> icon:<icon-id> newlabel:<new-label>` 或 `/dmarker update id:<marker-id> set:<markerset-id> icon:<icon-id> newlabel:<new-label>` - 注意：如果要选择不在默认集中的记号，那么 _markerset-id_ 是必要的。

记号可以使用 `/dmarker delete <marker-label> set:<markerset-id>` 或 `/dmarker delete id:<marker-id> set:<markerset-id>` 命令来删除。

可以使用 `/dmarker list set:<markerset-id>` 命令来列出所有已有的记号和属性。

### 记号图标

记号图标是用于给记号提供图标的图像，Dynmap 提供了一些默认的标准图标，全部都在下方的图片中，它们是预设的，并且不可以被删除。可以使用 `/dmarker icons` 命令来列出所有可用的图标。

新的图标可以通过以下几步来安装：

* 将 PNG 格式的图像文件复制进 Bukkit 的服务器文件夹，图片应该为 8x8，16x16 或 32x32 的大小。

* 运行命令 `/dmarker addicon id:<icon-id> <icon-label> file:<path-to-image-file>` - 如果成功，图片文件将被导入（所以不用放在第一次复制的地方）。

更新已有的图标的图片可以使用 `/dmarker updateicon id:<icon-id> newlabel:<new-label> file:<path-to-image-file>` 命令。

删除已有的图片可以使用 `/dmarker deleteicon id:<icon-id>` 命令。

![标准图标列表，感谢 Blankplanet](http://mikeprimm.com/images/Markers.png)

### 区域记号

区域标记用于在地图上方式 3D 或者 2D 的轮廓，区域标记由 2 个或者更多个的 X Z 坐标点序列组成的长方形（如果是两个点则是矩形的对角）或者多边形（如果是三个或者更多的点，则是多边形的有序的角序列，从第一个连接到最后一个再连回第一个点）。可选的，你可以设置设置最小和最大的 Y 值，将二维模型拓展为三维模型（顶部和底部是平坦的）。

可以设置颜色属性（#RRGGBB）和线段重量（0-N）和透明度（0.0-1.0）控制填充区域的颜色和外观。

创建一个区域之前必须提供一组角，可以通过以下步骤完成：

* 运行 `/dmarker addcorner` 命令来将玩家的当前位置添加为一个角

* 运行 `/dmarker addcorner <x> <y> <z>` 或 `/dmarker addcorner <x> <y> <z> <world>` 命令来添加指定的坐标点为一个角

添加的角可以使用 `/dmarker clearcorners` 命令来清除。

添加角之后，可以使用 `/dmarker addarea <area-label> set:<markerset-id>` 或 `/dmarker addarea id:<area-id> <area-label> set:<markerset-id>` 命令来创建一个区域标记。可以使用这些命令来设置附加的属性，或者使用 `/dmarker updatearea id:<area-id> set:<markerset-id>` 或 `/dmarker updatearea <area-label> set:<markerset-id>` 命令来更新已有的区域的属性。可用的选项包括：

* `color` - 轮廓颜色 (#RRGGBB 格式)

* `fillcolor` - 填充颜色 (#RRGGBB 格式)

* `opacity` - 轮廓的不透明度 (0.0 = 透明, 1.0 = 实体)

* `fillopacity` - 填充的不透明度 (0.0 = 透明, 1.0 = 实体)

* `weight` - 轮廓的重量（0=最小，越大越粗）

* `ytop` - 区域最大的 Y 轴高度 (默认=64)

* `ybottom` - 区域最小的 Y 轴高度 (默认=64)

注意：现有的区域无法更新，必须删除后重新创建新的区域。另外，当使用 `/dmarker addarea` 命令创建区域后，当前的角列表将会重置。

你可以使用 `/dmarker deletearea id:<area-id> set:<markerset-id>` 命令删除一个区域标记。

已经存在的区域和他们的属性可以使用 `/dmarker listareas set:<markerset-id>` 命令显示。

### 圆形标记

圆形标记用于在地图上放置二维圆形（或椭圆）轮廓，此区域使用圆形的轮廓，通过一个中心点（XYZ）和一个半径（圆形）或 X 和 Z 半径（椭圆）来创建。

轮廓边缘的外观可以通过设置颜色属性（#RRGGBB），线条重量（0-N）和透明度（0.0-1.0）来设置。

圆形标记可以通过使用 `/dmarker addcircle <circle-label> set:<markerset-id>` 或 `/dmarker addcircle id:<circle-id> <circle-label> set:<markerset-id>` 命令来创建。可以使用这些命令来设置附加的属性，或者使用 `/dmarker updatecircle id:<circle-id> set:<markerset-id>` 或 `/dmarker updatecircle <circle-label> set:<markerset-id>`命令来更新已有的圆形标记的属性。可用的选项包括：

* `x` - 中心的 X 坐标（默认为使用命令的玩家的坐标点 X 坐标）

* `y` - 中心的 Y 坐标（默认为使用命令的玩家的坐标点 Y 坐标）

* `z` - 中心的 Z 坐标（默认为使用命令的玩家的坐标点 Z 坐标）

* `radius` - 圆的半径（默认为 1）

* `radiusx` - 椭圆的 X 轴半径（默认为 1）

* `radiusz` - 椭圆的 Z 轴半径（默认为 1）

* `world` - 中心的世界（默认为使用命令的玩家的世界）

* `color` - 轮廓颜色 (#RRGGBB 格式)

* `fillcolor` - 填充颜色 (#RRGGBB 格式)

* `opacity` - 轮廓的不透明度 (0.0 = 透明, 1.0 = 实体)

* `fillopacity` - 填充的不透明度 (0.0 = 透明, 1.0 = 实体)

* `weight` - 轮廓的重量（0=最小，越大越粗）

使用 `/dmarker deletecircle id:<circle-id> set:<markerset-id>` 删除一个圆形标记。

已经存在的圆形标记和他们的属性可以使用 `/dmarker listcircles set:<markerset-id>` 命令显示。

### 折线标记

折线标记将连接的线段放置在地图上，每个折线标记由一个或多个 XYZ 坐标构成。以及可选的描述弹出窗口，重量和透明度设置。

轮廓边缘的外观可以通过设置颜色属性（#RRGGBB），线条重量（0-N）和透明度（0.0-1.0）来设置。

创建一个折线之前必须提供一组角，可以通过以下步骤完成：

* 运行 `/dmarker addcorner` 命令来将玩家的当前位置添加为一个角

* 运行 `/dmarker addcorner <x> <y> <z>` 或 `/dmarker addcorner <x> <y> <z> <world>` 命令来添加指定的坐标点为一个角

添加的角可以使用 `/dmarker clearcorners` 命令来清除。

添加角之后，可以使用 `/dmarker addline <line-label> set:<markerset-id>` 或 `/dmarker addline id:<line-id> <line-label> set:<markerset-id>` 命令来创建一个折线标记。可以使用这些命令来设置附加的属性，或者使用 `/dmarker updateline id:<line-id> set:<markerset-id>` 或 `/dmarker updateline <line-label> set:<markerset-id>` 命令来更新已有的折线的属性。可用的选项包括：

* `color` - 轮廓颜色 (#RRGGBB 格式)

* `opacity` - 轮廓的不透明度 (0.0 = 透明, 1.0 = 实体)

* `weight` - 轮廓的重量（0=最小，越大越粗）

注意：现有的折线无法更新，必须删除后重新创建新的折线。另外，当使用 `/dmarker addline` 命令创建折线后，当前的角列表将会重置。

你可以使用 `/dmarker deleteline id:<line-id> set:<markerset-id>` 命令删除一个折线标记。

已经存在的折线和他们的属性可以使用 `/dmarker listlines set:<markerset-id>` 命令显示。