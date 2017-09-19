一个简单的方块是一个固体立方体，填充整个立方体。这是最简单的一种方块形式，最好尽可能的使用（无论是简化实现还是性能）。由于固体立方体是默认的**模型**，这些方块不需要在[模型定义文件](/Model-Definition-Files.md)中有对应的模型。方块的材质通过 'block:' 行设置。

一个简单的方块有 6 个面，有很多的等效的属性：

* *top* 或 *face1* 或 *patch4* （方块顶部）

* *bottom* 或 *face0* 或 *patch1* （方块底部）

* *north* 或 *face4* 或 *patch0* （方块西面，负 X 轴方向）

* *south* 或 *face5* 或 *patch3* （方块东面，正 X 轴方向）

* *west* 或 *face3* 或 *patch5* （方块南面，负 Z 轴方向）

* *east* 或 *face2* 或 *patch2* （方块北面，正 Z 轴方向）

通过以下方式设置对应的属性来提供材质引用，需要添加 'id='：
```
   block:id=<block-id>,<side>=<index-plus-function>:<texture-id>,<side>=<index-plus-function>:<texture-id>,...
```
每一个常见的面的组合也有方便设置的属性，这允许你将相同的材质应用到多个面：

* *allfaces* （六个面使用相同的材质）

* *allsides* （所有的侧面使用相同的材质）

* *topbottom* （顶面和底面使用相同的材质）

由于遗留的问题，标准的方块也需要设置属性 `stdrot=true`，否则顶部和底部的材质将会使用错误的旋转(90度)。

如果相同的材质映射应用于所有的元数据，那么应该设置属性 `data=`（尽管当没有其他的 `data=` 存在时这是默认值）。如果有只有特定的元数据使用给定的材质映射，那么应该提供多个 `data=<数字>` 属性。

如果多个方块的 ID 使用相同的材质，则可以同一个 `block:` 行指定多个 `id=` 属性。

如果需要，可以指定以下其他的特殊属性：

* *txtid* - 此选项允许在没有 `: texture-id ` 后缀的 `block:` 定义中指定默认的材质。

* *transparency* - 这将会影响方块照明的计算。如果设置为 OPAQUE（默认），那么方块的表面亮度将会基于相邻方块的亮度计算，如果设置为 TRANSPARENCY，方块的亮度基于自身的光线亮度，如果设置为 SEMITRANSPARENT，方块的亮度为两种情况混合的特殊情况（一般由阻挡光线但没有完全填充的立方体使用，如台阶和半砖）。如果设置为 LEAVES，那么使用特殊的照明情况（通常与 TRANSPARENCY 相同，除了某些版本的 Spout）。

* *colorMult* - 这会影响使用 `multiplier-tinting` 选项的任何材质（17000, 21000），由 6 位的十六进制组成：RRGGBB，RR 是红色分量（00-FF），GG 是绿色分量（00-FF），BB 是蓝色分量（00-FF）。

* *customColorMult" - 这会影响使用 `multiplier-tinting` 选项的任何材质（17000, 21000），由一个着色器类名组成，目前有这些值： 
     + `org.dynmap.hdmap.colormult.TFBandedWoodColorMultiplier` - 针对暮色森林 Mod 的 banded wood 的特殊的着色器类
     + `org.dynmap.hdmap.colormult.TFMagicLeafColorMultiplier` - 针对暮色森林 Mod 的银树叶（Magic Tree Leaves）的特殊的着色器类
     + `org.dynmap.hdmap.colormult.TFSpecialLeafColorMultiplier` - 针对暮色森林 Mod 的特殊的树叶（Special Leaves）的特殊的着色器类

* *layer&lt;M&gt;* 或 *layer&lt;M&gt;-&lt;N&gt;* - 此选项允许材质被"堆叠" - 如果某个面的材质是透明的，那么下一层的材质将被应用于那些部分。layer&lt;M&gt; 或 layer&lt;M&gt;-&lt;N&gt; 属性的值是对应的 `patch<序数>` 定义的索引，用于下一层的对应 patch&lt;M&gt; 的材质或者在 patch&lt;M&gt; 和 patch&lt;N&gt; 之间的材质。对于标准的长方体，标准的面使用 patch0 到 patch6，所以任何附加的覆盖层材质应该使用 patch6 或者更高的值。

* *patch&lt;M&gt;* 或 *patch&lt;M&gt;-&lt;N&gt;* - 此选项允许这是附加的材质引用，基于超过 6 的（patch0 到 patch5，或之前指定的其他别名）。对于简单的立方体，这里只需要定义覆盖的材质。这里的值是一个材质引用，应用到第 M 个 patch 或者 M 到 N 之前的所有 patch。
