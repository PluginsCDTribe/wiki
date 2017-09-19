Dynmap 是一个像谷歌地图一样的、为 Minecraft 服务器设计的地图插件，让你可以在浏览器查看地图。你可以使用 Dynmap 的集成的网络服务器立即上手，也可以将其部署到 Apache 等现有的网络服务器，易于使用。Dynmap 可以使用不同的渲染器渲染你的地图，有的适用于高性能，而有的可以展示更详细的细节。

原始的项目是由 k-red 开发。

# 联系 #
* [Bukkit 论坛](http://forums.bukkit.org/threads/misc-dynmap-v0-12-1-realtime-minecraft-maps-314.489/)
* [BukkitDev 项目页面](http://dev.bukkit.org/server-mods/dynmap/)
* IRC: irc://irc.esper.net/#dynmap ([在线](http://webchat.esper.net/?nick=Webuser&channels=dynmap&prompt=0))

# 用户 #

* [不使用内部服务器建立](/Setting-up-without-the-Internal-Web-Server.md)
* [在Linux下建立动态地图插件](/Setting-up-the-Dynamic-Map-plugin-under-Linux.md)
* [在Windows下建立动态地图插件](/Setting-up-the-Dynamic-Map-plugin-under-Windows.md)
* [通过托管服务建立Dynmap](/Setting-up-Dynmap-through-hosting-services.md)
* [配置](/Configuration.md)
    + [基础插件设定](/Base-Plugin-Settings.md)
    + [部件设定](/Component-Configuration.md)
    + [世界&模板设定](/World-and-template-settings.md)
    + [高分辨率地图设定](/HD-Map-Configuration.md)
    + [支持的基于Forge的Mod](/Support-for-MinecraftForge-based-mods.md)
    + [支持的服务端](/Support-for-Minecraft-Servers-other-than-CraftBukkit.md)
* [命令](/Commands.md)
    + [使用dmap配置地图和世界](/Configuring-Maps-and-Worlds-using-dmap.md)
* [权限](/Permissions.md)
    + [网页登录支持与权限](/Web-ui-login-support-and-permissions.md)
* [网页参数](/Web-UI-Parameters.md)
* [使用标记](/Using-markers.md)
* [自定义方块](/Custom-Block-Definitions.md)
* [导出世界为WavefrontOBJ格式](/Exporting-World-Data-in-Wavefront-OBJ-Format.md)

# 开发者 #
Dynmap 项目包含了多个部分，可以支持多个服务器平台，也可以帮助我们清楚地发布API。用来构建 'dynmap'（Bukkit 的 Dynmap 插件）的有以下几部分（按照构建顺序）：

* [DynmapCoreAPI](https://github.com/webbukkit/DynmapCoreAPI) - 这是无关平台的 Dynmap API：插件编写者可以使用这个接口来在任何平台使用 Dynmap（通过将插件转换为 `org.dynmap.DynmapCoreAPI` 示例）

* [DynmapCore](https://github.com/webbukkit/DynmapCore) - 这个服务器平台的 Dynmap 核心：几乎所有的网页和渲染都在这里（我们尽可能多的往里放）。在这里构建的结果是不可运行的 - 他们被放入 `dynmap` 的其他部分（比如，`DynmapSpout` 支持 Spout 平台）。

* [dynmap-api](https://github.com/webbukkit/dynmap-api) - Dynmap 的 Bukkit 部分的 API - 定义了 `org.dynmap.DynmapAPI` 接口，包括了 Bukkit 的调用，通过配合 DynmapCoreAPI（DynmapAPI 继承），将插件实例转为 `org.dynmap.DynmapAPI` 来使用公布的接口。

* [dynmap](https://github.com/webbukkit/dynmap) - 真正的 Dynmap Bukkit 的部分，包括了那些与服务器无关的代码。

[如何编译Dynmap](/How-to-compile-Dynmap.md)