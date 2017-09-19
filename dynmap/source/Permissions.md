# 权限 #

基于 SuperPerms 权限控制，包括了对 PermissionsEx, BukkitPermissions, bPermissions, 和经典的 Permissions 的支持、有以下的权限节点：

* `dynmap.render` - 允许使用 /dynmap render 命令
* `dynmap.show.self` - 允许使用 /dynmap show （自己）
* `dynmap.show.others` - 允许使用 /dynmap show &lt;player&gt;
* `dynmap.hide.self` - 允许使用 /dynmap hide 自己
* `dynmap.hide.others` - 允许使用 /dynmap hide &lt;player&gt;
* `dynmap.fullrender` - 允许使用 /dynmap fullrender 或 /dynmap fullrender &lt;world&gt;
* `dynmap.radiusrender` - 允许使用 /dynmap radiusrender
* `dynmap.updaterender` - 允许使用 /dynmap updaterender
* `dynmap.cancelrender` - 允许使用 /dynmap cancelrender &lt;world&gt;
* `dynmap.pause` - 允许使用 /dynmap pause
* `dynmap.reload` - 允许使用 /dynmap reload
* `dynmap.stats` - 允许使用 /dynmap stats 或 /dynmap stats &lt;world&gt; 或 /dynmap triggerstats
* `dynmap.resetstats` - 允许使用 /dynmap resetstats 或 /dynmap resetstats &lt;world&gt;
* `dynmap.sendtoweb` - 允许使用 /dynmap sendtoweb
* `dynmap.purgequeue` - 允许使用 /dynmap purgequeue
* `dynmap.ids-for-ip` - 允许使用 /dynmap ids-for-ip
* `dynmap.ips-for-id` - 允许使用 /dynmap ips-for-id
* `dynmap.add-id-for-ip` - 允许使用 /dynmap add-id-for-ip
* `dynmap.del-id-for-ip` - 允许使用 /dynmap del-id-for-ip
* `dynmap.marker.add` - 允许使用 /dmarker add
* `dynmap.marker.movehere` - 允许使用 /dmarker movehere
* `dynmap.marker.update` - 允许使用 /dmarker update
* `dynmap.marker.delete` - 允许使用 /dmarker delete
* `dynmap.marker.list` - 允许使用 /dmarker list
* `dynmap.marker.icons` - 允许使用 /dmarker icons
* `dynmap.marker.addset` - 允许使用 /dmarker addset
* `dynmap.marker.updateset` - 允许使用 /dmarker updateset
* `dynmap.marker.deleteset` - 允许使用 /dmarker deleteset
* `dynmap.marker.listsets` - 允许使用 /dmarker listsets
* `dynmap.marker.addicon` - 允许使用 /dmarker addicon
* `dynmap.marker.updateicon` - 允许使用 /dmarker updateicon
* `dynmap.marker.deleteicon` - 允许使用 /dmarker deleteicon
* `dynmap.marker.addarea` - 允许使用 /dmarker addarea
* `dynmap.marker.updatearea` - 允许使用 /dmarker updatearea
* `dynmap.marker.deletearea` - 允许使用 /dmarker deletearea
* `dynmap.marker.listareas` - 允许使用 /dmarker listareas
* `dynmap.marker.addline` - 允许使用 /dmarker addline
* `dynmap.marker.updateline` - 允许使用 /dmarker updateline
* `dynmap.marker.deleteline` - 允许使用 /dmarker deleteline
* `dynmap.marker.listlines` - 允许使用 /dmarker listlines
* `dynmap.dmap.worldlist` - 允许使用 /dmap worldlist
* `dynmap.dmap.worldset` - 允许使用 /dmap worldset
* `dynmap.dmap.worldreset` - 允许使用 /dmap worldreset
* `dynmap.dmap.mapdelete` - 允许使用 /dmap mapdelete
* `dynmap.dmap.mapset` - 允许使用 /dmap mapset
* `dynmap.dmap.mapadd` - 允许使用 /dmap mapadd
* `dynmap.dmap.perspectivelist` - 允许使用 /dmap perspectivelist
* `dynmap.dmap.shaderlist` - 允许使用 /dmap shaderlist
* `dynmap.dmap.lightinglist` - 允许使用 /dmap lightinglist
* `dynmap.webregister` - 允许使用 /dynmap webregister
* `dynmap.webregister.other` - 允许使用 /dynmap webregister player-id
* `dynmap.webchat` - 允许通过网页发送聊天消息（需要登录或 ID-IP 映射）
* `dynmap.playermarkers.showall` - 允许用户查看隐藏的玩家的记号
* `dynmap.world.<世界名>` - 如果世界被设置为保护，允许用户查看指定世界的地图
* `dynmap.map.<世界名>.<地图名>` - 如果地图被设置为保护，允许用户查看指定世界的指定地图
