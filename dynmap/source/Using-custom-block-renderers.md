一些类型的方块相比较于将静态模型直接赋予指定ID和数据值的方块这种简单的方法而言，其渲染的逻辑更加复杂。这包括依照相邻方块而做出改变的方块（红石线，栅栏，围墙，玻璃板和楼梯等等），同时它们的模型也依赖于TileEntity数据和其他信息（例如头颅，RailCraft的铁轨，和Immibis' Microblocks等等）。

要想使用自定义方块渲染器定义模型的话，你需要提供"customblock:" 文本行。这一行应该包括这些基础属性：

* *id* - 本模型所用于的方块ID。你最少提供一个 *id* 属性，但是只要你需要的话可以有无限多——这允许相同的模型可以作用于多个方块。查看[方块ID数字](/Texture-Definition-Files.md#block-id-numbers)来获得定义方块ID的有关细节。

* *data* - 这项提供模型应用于的方块的数据值。默认地，*data=\** 代表所有*id*属性中的方块的所有数据值。另外，你也可以提供多个 *data=number* 属性，这用于为模型选择多个数据值。

* *class* - 这项提供自定义方块渲染器所使用的类的类名，同时这一项也是必需的。

"customblock:" 行可能也有其他的属性，这些属性可以标识出指定的自定义方块渲染器。

自定义方块渲染器总是会创建渲染面（即材质被应用的那个表面）的序列。相应的渲染面的序列通过自定义方块渲染器而定义。材质的参考内容通过[材质定义文件](/Texture-Definition-Files.md)提供，你需要在相应的"block:"文本行中指定 *patch&lt;N&gt;* 属性。

## 创建自定义方块渲染器
下面的自定义方块渲染器都是由Dynmap所提供的，它们可以用来渲染适当的自定义方块。
* [org.dynmap.hdmap.renderer.BoxRenderer 类](/Class-org.dynmap.hdmap.renderer.boxrenderer.md) - 用于实现[立方体模型](/Defining-cuboid-models.md) 的渲染器
* Class org.dynmap.hdmap.renderer.CTMVertTextureRenderer
* [org.dynmap.hdmap.renderer.FenceWallBlockRenderer类](/Class-org.dynmap.hdmap.renderer.FenceWallBlockRenderer.md) - 用于栅栏和围墙的渲染器
* Class org.dynmap.hdmap.renderer.FrameRenderer
* Class org.dynmap.hdmap.renderer.ImmibisMicroRenderer
* [org.dynmap.hdmap.renderer.PaneRenderer 类](/Class-org.dynmap.hdmap.renderer.PaneRenderer.md) - 用于玻璃板和铁栅栏的渲染器
* Class org.dynmap.hdmap.renderer.RailCraftSlabBlockRenderer
* Class org.dynmap.hdmap.renderer.RailCraftTrackRenderer
* [org.dynmap.hdmap.renderer.RedstoneWireRenderer 类](/Class-org.dynmap.hdmap.renderer.RedstoneWireRenderer.md) - 用于红石线的渲染器
* Class org.dynmap.hdmap.renderer.RotatedBoxRenderer
* Class org.dynmap.hdmap.renderer.RotatedPatchRenderer
* Class org.dynmap.hdmap.renderer.RPMicroRenderer
* Class org.dynmap.hdmap.renderer.RPRotatedBoxRenderer
* Class org.dynmap.hdmap.renderer.RPSupportFrameRenderer
* [org.dynmap.hdmap.renderer.SkullRenderer 类](/Class-org.dynmap.hdmap.renderer.SkullRenderer.md) - 用于渲染原版头颅的渲染器
* [org.dynmap.hdmap.renderer.StairBlockRenderer 类](/Class-org.dynmap.hdmap.renderer.StairBlockRenderer.md) - 用于渲染普通楼梯方块的渲染器
* Class org.dynmap.hdmap.renderer.TFCLooseRockRenderer
* Class org.dynmap.hdmap.renderer.TFCSupportRenderer
* Class org.dynmap.hdmap.renderer.TFCWoodRenderer
* Class org.dynmap.hdmap.renderer.ThaumFurnaceRenderer