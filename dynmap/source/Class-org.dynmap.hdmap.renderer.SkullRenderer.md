SkullRenderer 类用于渲染头颅。渲染器使用 TileEntity 字段用于确定头部方向（"Rot"），并确定头颅类型（"SkullType"）。每个头颅需要 6 个材质 -  来自 'SKIN' 种类的采指纹键（包含人体模型的纹理文件）。你必须使用正确的 'texturefile:' 来加载此文件 - 比如僵尸头颅就是这样的：

     texturefile:id=zombie,filename=mob/zombie.png,format=SKIN

使用 SkullRender 连接到 "block:" 需要提供 6 中材质引用给 SkullType 的每个定义的值：patch0 到 patch5 为第一个索引 (0)，patch6 到 patch11 为第二个 (1)，等等。

###属性
无

###材质补丁
SkullType 的每个值对应 N=0 到 N=最大值：
* *patch&lt;6 x N&gt;* - 头颅底部 (SKIN 材质索引 5)
* *patch&lt;6 x N + 1&gt;* - 头颅顶部 (SKIN 材质索引 4)
* *patch&lt;6 x N + 2&gt;* - 头颅后面 (SKIN 材质索引 1)
* *patch&lt;6 x N + 3&gt;* - 头颅前面 (SKIN 材质索引 0)
* *patch&lt;6 x N + 4&gt;* - 头颅侧面 (SKIN 材质索引 2)
* *patch&lt;6 x N + 5&gt;* - 头颅侧面 (SKIN 材质索引 3)
