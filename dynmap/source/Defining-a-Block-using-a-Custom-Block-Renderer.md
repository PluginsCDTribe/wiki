使用提供的模型定义自定义块可以前往此处[使用自定方块着色器](/Using-custom-block-renderers.md)，第一步是选择和配置渲染[模型定义文件](/Model-Definition-Files.md)。  在配置 'customblock:' 行中， 必须包含一个或多个方块的 ID （通过 *id* 识别）， 任何需要的元数据值 （通过 *data* 识别）和自定义渲染器类 （通过 *class* 识别)。  例如，砂岩台阶方块的定义如下：
```
     customblock:id=128,,data=*,class=org.dynmap.hdmap.renderer.StairBlockRenderer
```
此外，这些核心属性将由自定义渲染器提供一部分（可能需要）附加属性来帮助使用者正确配置渲染。 详情请在 'Attributes' 来查阅关于渲染器类提供的附加属性的细节。

接下来，材质参考资源需要被定义为自定义渲染器所支持的材质。 在 'Patches Requiring Textures' 的自定义渲染器的描述部分定义了 `patch\<N\>` 需要为方块提供的属性。 仔细阅读这些帮助，配置项 'block:' 行必须在材质定义文件中包含，以及在 'patchN' 设定每个补丁的显示属性。 例如，楼梯方块上所需要的的自定义渲染器需要三块：一个是方块边缘，一个是方块顶部，一个是方块底部：对于砂岩楼梯方块，提供以下示例：
```
     block:id=128,data=*,patch0=0:sandstone_normal,patch1=0:sandstone_top,patch2=0:sandstone_bottom,transparency=SEMITRANSPARENT
```
注意：大多数自定义渲染器定义的是不完整的方块, 不透明块, 所以 *方块透明度* 属性通常需要在 "block:" 行中配置。 对需要不遮挡其他方块的方块设置合适的透明度， 或设置为半透明的方块，防止光照被该方块所阻挡（例如石板和楼梯）。
