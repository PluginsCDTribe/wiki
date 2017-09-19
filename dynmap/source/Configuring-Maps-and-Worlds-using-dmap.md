从 v0.31 开始，Dynmap 提供了通过管理员权限使用控制台命令或者玩家命令来配置世界和地图的功能的选项。当使用任何编辑命令时，现有的设置将被输出到 worlds.txt 文件中（无论是现有的还是基于模板）。新的世界仍然会使用模板进行初始化，但是将设置迁移至 worlds.txt 后任何模板的更改不会影响现有的世界。另外，所有的地图编辑指令仅限于 HDMap，原来的 KzedMap 和 FlatMap 不能通过 /dmap 命令编辑。

开始之前，你要知道在地图渲染进行时，任何 /dmap 命令都是无法使用的（除了 /dmap worldlist, /dmap maplist, /dmap perspectivelist, /dmap shaderlist, 或 /dmap lightinglist 命令）。所以开始之前需要使用 `/dynmap pause all` 命令，这将暂停所有的渲染处理。 - **不要忘记使用 `/dynmap pause none` 来恢复所有的处理，如果你忘记了，这将堆积越来越多的渲染任务，和相关的内存使用**.

渲染暂停后，/dmap 命令可以用于添加、移除、渲染或编辑已有的地图定义。顺序和很多的世界设定都可以控制，以下是一些示例：

* 关闭/隐藏一个世界：`/dmap worldset _worldname_ enabled:false`

* 重置某世界或地图的设定为默认模板设定：`/dmap worldreset _worldname_`

* 重置某世界或地图的设定为指定模板设定：`/dmap worldreset _worldname_ _templatename_`

* 将世界设置为世界列表的第一个：`/dmap worldset _worldname_ order:1`

* 设置世界的标题：`/dmap worldset _worldname_ title:_"title string"_`

* 隐藏某世界的玩家的位置和生命显示：`/dmap worldset _worldname_ sendposition:false sendhealth:false`

* 设置世界的中心位置为玩家的当前位置：`/dmap worldset _worldname_ center:here`

* 设置世界的中心位置为指定位置：`/dmap worldset _worldname_ center:X/Y/Z`

* 设置世界的额外缩放等级为 N：`/dmap worldset _worldname_ extrazoomout:N` 

* 显示指定世界的地图：`/dmap maplist _worldname_`

* 删除指定世界的某地图：`/map mapdelete _worldname_:_mapname_`

* 给指定世界添加新地图（指定标题、预设、阴影和光照）：`/dmap mapadd _worldname_:_mapname_ title:_"map-title"_ perspective:_perspective-id_ shader:_shader-id_ lighting:_lighting-id_`

* 编辑世界中的某地图的顺序为 N：`/dmap mapset _worldname_:_mapname_ order:_N_`

* 编辑某地图的标题：`/dmap mapset _worldname_:_mapname_ title:_"new-title"_`

* 更改某地图的预设：`/dmap mapset _worldname_:_mapname_ perspective:_perspective-id_`

* 更改地图的文件前缀名：`/dmap mapset _worldname_:_mapname_ prefix:_prefix_`

* 设置地图的图标文件（相对于 'wenpath'）：`/dmap mapset _worldname_:_mapname_ icon:images/block_skylands.png`

* 设置地图缩放等级为 N：`/dmap mapset _worldname_:_mapname_ mapzoomin:_N_`

* 更改地图使用的默认图片格式：`/dmap mapset _worldname_:_mapname_ img-format:jpg`

* 更改末日呢的洞穴视图为新的材质洞穴视图：`/dmap mapset _worldname_:_mapname_ shader:stdtexture-cave`

* 显示所有可用的预设：`/dmap perspectivelist`

* 显示所有可用的着色器：`/dmap shaderlist`

* 显示所有可用的光照：`/dmap lighinglist`

* 设置地图与其他的地图同行显示：`/dmap mapset _worldname_:_mapname_ append-to-world:_another_worldname_`

注意：任何 mapset 可用的属性都可以使用 mapadd 命令创建新地图。

这些地图的更新编辑大多都需要进行一次完全渲染。

完成编辑以后请务必记住**运行 `/dynmap pause none` 命令来恢复正常的渲染处理**。


