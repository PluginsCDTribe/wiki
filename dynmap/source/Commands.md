# 命令 #
## 隐藏/显示玩家 ##

* `/dynmap hide`: 将此玩家从地图隐藏。
* `/dynmap hide thedude`: 将玩家 _thedude_ 从地图隐藏。
* `/dynmap show`: 将此玩家重新从地图显示。
* `/dynmap show thedude`: 将玩家 _thedude_ 重新从地图显示。

## 渲染 ##

* `/dynmap render`: 渲染你的位置的一个tile。
* `/dynmap fullrender`: 尝试从你的位置开始渲染整个世界的全部地图（如果从控制台使用则从世界中心开始）。
* `/dynmap fullrender world`: 尝试从你的位置开始渲染 `world` 世界的全部地图（如果从控制台使用则从世界中心开始）。
* `/dynmap fullrender world:surface`: 尝试从你的位置开始渲染 `world` 世界的 `surface` 地图（如果从控制台使用则从世界中心开始）。
* `/dynmap radiusrender radius`: 尝试从你的位置开始渲染半径为 `radius` 的所有方块的区域。
* `/dynmap radiusrender radius mapname`: 尝试从你的位置开始渲染半径为 `radius` 的所有方块的区域的 `mapname` 地图。
* `/dynmap radiusrender world x z radius`: 尝试从 (x,64,z) 开始渲染 `world` 世界半径为 `radius` 的所有方块的区域。
* `/dynmap updaterender`: 尝试从你的位置开始渲染 所有需要更新的tiles，到地图的边缘或是没有需要更新的tiles停止。
* `/dynmap updaterender mapname`: 尝试从你的位置开始渲染 `mapname` 地图所有需要更新的tiles，到地图的边缘或是没有需要更新的tiles停止。
* `/dynmap updaterender world x z`: 尝试从 (x,64,z) 开始渲染 `world` 世界所有需要更新的tiles，到地图的边缘或是没有需要更新的tiles停止。
* `/dynmap updaterender world x z mapname`: 尝试从 (x,64,z) 开始渲染 `world` 世界 `mapname` 地图所有需要更新的tiles，到地图的边缘或是没有需要更新的tiles停止。
* `/dynmap cancelrender world`: 取消指定世界所有激活的渲染任务。
* `/dynmap purgequeue`: 清除tile更新队列
* `/dynmap purgeworld world`: 清除 'world' 世界的所有地图文件
* `/dynmap purgemap world map`: 清除 'world' 世界的 'map' 地图文件
* `/dynmap pause all`: 暂停所有的渲染（更新和全部/范围渲染）
* `/dynmap pause none`: 恢复所有渲染

## 统计 ##

* `/dynmap stats`: 显示所有世界的所有地图的渲染统计
* `/dynmap stats world` : 显示 _world_ 世界的所有地图的渲染统计
* `/dynmap triggerstats` : 显示所有世界的触发器的渲染统计
* `/dynmap resetstats` : 重置所有世界的所有地图的渲染统计
* `/dynmap resetstats world` : 重置 _world_ 世界的所有地图的渲染统计

## 记号 ##
这些命令只能在标记部件启用后使用（v0.22或之后的版本）。

* `/dmarker add <label> icon:<icon> set:<set-id>` : 在玩家的当前位置添加一个指定标签，可选的图标和可选的记号集的记号
* `/dmarker add id:<id> <label> icon:<icon> set:<set-id>` : 在玩家的当前位置添加一个指定标签和 ID，可选的图标和可选的记号集的记号
* `/dmarker add id:<id> <label> icon:<icon> set:<set-id> x:<x-coord> y:<y-coord> z:<z-coord> world:<Worldname>` : 在指定位置添加一个指定标签和 ID，可选的图标和可选的记号集的记号
* `/dmarker movehere <label>` : 将第一个匹配指定标签的记号移动至玩家的当前位置
* `/dmarker movehere id:<id>` : 将第一个匹配指定 ID 的记号移动至玩家的当前位置
* `/dmarker update <label> icon:<newicon> newlabel:<newlabel>` : 更新第一个匹配指定标签的记号的图标和/或标签
* `/dmarker update id:<id> icon:<newicon> newlabel:<newlabel>` : 更新第一个匹配指定 ID 的记号的图标和/或标签
* `/dmarker delete <label>` : 删除第一个匹配指定标签的记号
* `/dmarker delete id:<id>` : 删除第一个匹配指定 ID 的记号
* `/dmarker list` : 列出默认记号集中定义的所有记号的属性
* `/dmarker list set:<set-id>` : 列出指定记号集中定义的所有记号的属性
* `/dmarker icons` : lists the attributes of all the icons defined for use by markers
* `/dmarker addset <label> hide:<hide-by-def> prio:<priority> minzoom:<minzoom>` : 添加指定标签的新记号集 (ID = 标签)
* `/dmarker addset id:<id> <label> hide:<hide-by-def> prio:<priority> minzoom:<minzoom>` : 添加指定标签和 ID 的新记号集
* `/dmarker updateset <label> newlabel:<new-label> hide:<hide-by-def> prio:<priority> minzoom:<minzoom>` : 更新指定标签的记号集 (ID = 标签)
* `/dmarker updateset id:<id> newlabel:<new-label> hide:<hide-by-def> prio:<priority> minzoom:<minzoom>` : 更新指定 ID 的记号集
* `/dmarker deleteset <label>` : 删除指定标签的记号集
* `/dmarker deleteset id:<id>` : 删除指定 ID 的记号集
* `/dmarker listsets` : 列出所有的记号
* `/dmarker addicon id:<id> <label> file:"filename"` : 使用指定的文件添加指定 ID 和标签的新图标（路径相对于 MC 服务器文件夹）。
* `/dmarker updateicon id:<id> newlabel:<label> file:"filename"` : 使用指定的文件更新指定 ID 和标签的图标（路径相对于 MC 服务器文件夹）。
* `/dmarker deleteicon id:<id>` : 删除指定 ID 的图标
* `/dmarker addcorner` : 将目前的坐标作为一个角添加到列表
* `/dmarker addcorner <x> <z> <world>` : 将给定的坐标作为一个角添加到列表
* `/dmarker clearcorners` : 清除角列表
* `/dmarker addarea <label>` : 使用给定的标签和当前的角列表创建并添加新的区域
* `/dmarker addarea id:<id> <label>` : 使用给定的标签、ID 和当前的角列表创建并添加新的区域
* `/dmarker deletearea <label>` : 删除给定标签的区域
* `/dmarker deletearea id:<id> <label>` : 删除给定 ID 的区域
* `/dmarker listareas` : 列出所有区域的详细信息
* `/dmarker updatearea <label> <arg>:<value> ...` : 更新给定标签的区域的属性
* `/dmarker updatearea id:<id> <arg>:<value> ...` : 更新给定 ID 的区域的属性
* `/dmarker addline <label>` : 使用当前的角列表和给定的标签创建并添加新的线
* `/dmarker addline id:<id> <label>` : 使用当前的角列表和给定的 ID 创建并添加新的线
* `/dmarker deleteline <label>` : 删除给定标签的线
* `/dmarker deleteline id:<id> <label>` : 删除给定 ID 的线
* `/dmarker listlines` : 列出所有线的详细信息
* `/dmarker updateline <label> <arg>:<value> ...` : 更新给定标签的线的属性
* `/dmarker updateline id:<id> <arg>:<value> ...` : 更新给定 ID 的线的属性        

## 地图/世界配置命令 ##

* `/dmap worldlist` : 显示所有配置了的世界（启用或禁用）
* `/dmap worldset worldname enabled:<true|false>` : 设置 'worldname' 世界启用或禁用
* `/dmap worldset worldname center:<x/y/z|here|default>` : 设置 'worldname' 世界的地图中心
* `/dmap worldset worldname extrazoomout:<N>` : 设置 'worldname' 世界的额外缩小等级
* `/dmap worldset worldname title:<label>` : 设置 'worldname' 世界的标题名称
* `/dmap worldset worldname sendposition:<true|false> sendhealth:<true|false>` : 设置 'world' 世界的 sendposition 和 sendhealth 标签
* `/dmap worldset worldname order:<N>` : 设置 'worldname' 世界的顺序
* `/dmap worldreset worldname` : 重置 'worldname' 世界为模板设定
* `/dmap worldreset worldname templatename` : 设置 'worldname' 世界为 'templatename' 模板设定
* `/dmap maplist worldname` : 列出 'worldname' 世界的详细信息
* `/dmap mapdelete worldname:mapname` : 删除 'worldname' 世界的 'mapname' 地图
* `/dmap mapadd worldname:mapname attrib:val attrib:val` : 在世界 'worldname' 创建新的地图 'mapname'，使用所有给出的属性（所有的 'mapset' 属性都可用）
* `/dmap mapset worldname:mapname order:<N>` : 设置地图 'mapname' 在世界 'worldname' 中的顺序
* `/dmap mapset worldname:mapname prefix:<prefix>` : 设置世界 'worldname' 的地图 'mapname' 的文件前缀
* `/dmap mapset worldname:mapname title:<label>` : 设置世界 'worldname' 的地图 'mapname' 的标题
* `/dmap mapset worldname:mapname icon:<icon-file>` : 设置世界 'worldname' 的地图 'mapname' 的图标文件（相对于 'webpath' 目录）
* `/dmap mapset worldname:mapname mapzoomin:<N>` : 设置世界 'worldname' 的地图 'mapname' 的缩放等级
* `/dmap mapset worldname:mapname perspective:<perspective> shader:<shader> lighting:<lighting>` : 设置世界 'worldname' 的地图 'mapname' 的预设、光照和着色
* `/dmap mapset worldname:mapname img-format:<format>` : 设置世界 'worldname' 的地图 'mapname' 的图片格式
* `/dmap perspectivelist` : 列出所有的预设
* `/dmap shaderlist` : 列出所有的着色器
* `/dmap lightinglist` : 列出所有的光照

## 杂项 ##
其他的命令。

* `/dynmap sendtoweb message ...` : 向网页发送一条消息
* `/dynmap ids-for-ip ip-address` : 列出指定 IP 最近登录的所有玩家
* `/dynmap ips-for-id player-id` : 列出玩家的所有连接到服务器过的 IP 地址
* `/dynmap add-id-for-ip player-id ip-address` : 将指定玩家添加到指定 IP 的已知玩家列表中
* `/dynmap del-id-for-ip player-id ip-address` : 将指定玩家移除于指定 IP 的已知玩家列表中
* `/dynmap webregister` : 开始注册自己的网页登录账户
* `/dynmap webregister player-id` : 开始注册指定玩家的网页登录账户
