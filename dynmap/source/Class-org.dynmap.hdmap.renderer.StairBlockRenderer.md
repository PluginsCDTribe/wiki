StairBlockRender 类定义了一个用于渲染标准台阶方块的渲染器。当使用时，他应该处理台阶方块的所有元数据。渲染器处理所有的台阶连接、转角和方位（倒置或其他）的信息。

渲染器可以选择台阶每个表面使用的材质，通过以下方法：
* 普通情况（非 TileEntity 方块），通过打包提供的材质（一个侧面，一个顶部，一个底部）。
* 对基于 TileEntity 的方块，通过读取 TileEntity 的特殊字段，通过一个映射寻找来查看每个表面使用什么材质。

###属性
* *textureindex* - 此可选的参数用于指定包含一个数字或字符串的 TileEntity 属性能用于选择渲染方块使用的材质。
* *texturecnt* - 此可选的参数仅与 *textureindex* 参数相关，此参数指定了映射的材质的数量用于确定 *textureindex*：通过 'textmap*(texturecnt-1)*' 确定 'textmap0'。
* *textmap&lt;N&gt;* - 每个从 N=0 到 N=(*texturecnt*-1)，包含了 TileEntity 字段通过 *textureindex* 标记的应该使用 'patch&lt;N&gt;' 的台阶材质。

###材质补丁

如果 *textureindex* 没有被设置：
* *patch0* - 使用于侧面的（垂直面）方块的材质
* *patch1* - 使用于顶部的方块的材质
* *patch2* - 使用于底部的方块的材质

如果 *textureindex* 被设置：
* *patch0* - 当方块的 TileEntity 的 *textureindex* 字段与 *textmap0* 属性相同时用于渲染侧面的材质。此选项也用于如果 *textureindex* TileEntity 字段没有匹配任何 *textmap&lt;N&gt;* 属性的情况。
* *patch1* - 当方块的 TileEntity 的 *textureindex* 字段与 *textmap1* 属性相同时用于渲染侧面的材质。
* *patch&lt;N&gt;* - 当方块的 TileEntity 的 *textureindex* 字段与 *textmap&lt;N&gt;* 属性相同时用于渲染侧面的材质。

