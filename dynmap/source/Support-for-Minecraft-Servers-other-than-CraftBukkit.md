Dynmap 包括了除了 CraftBukkit 的其他版本。其他的最新的版本可以在[这里](http://www.minecraftforum.net/topic/1543523-dynmap-dynamic-web-based-maps-for-minecraft/)找到。目前有 3 个Dynmap主要的平台：

* [Bukkit Dynmap](https://github.com/webbukkit/dynmap/)
* [DynmapForge](https://github.com/webbukkit/DynmapForge/)
* [DynmapSpout](https://github.com/webbukkit/DynmapSpout/)

# Spigot
Spigot 通过 Bukkit Dynmap 被完全支持。

# MinecraftForge
很多版本的 MinecraftForge 都是支持的，可以使用 DynmapForge 项目。所有的 Forge 版本的 Dynmap 都需要特定的 Forge 版本，升级 Forge 版本也需要升级到对应的 DynmapForge 版本。你应该按照如下的方法来安装或者升级：
* 下载对应的 ZIP 文件，对应 MC 版本。
* 解压整个 ZIP 文件，包括子目录，至服务器的根目录。
* 如果是升级，那么删除 'mods' 下老的 'Dynmap-x.y.zip'。

# MCPC+
目前 MCPC+ 的版本(v1.4.7 或之后) 只被 DynmapForge mods 支持对应的 Forge 版本。CraftBukkit 版本不被支持。安装请按照以下步骤。
你可以使用 DynmapCBBridge 来兼容使用的 Bukkit 的插件的数据（可以在[这里](http://www.minecraftforum.net/topic/1543523-dynmap-dynamic-web-based-maps-for-minecraft/)找到）。这是一个 Bukkit 插件，所以应该放在 'plugins' 目录，并且只支持那些基于 Forge 的 Bukkit 服务器上。

# BukkitForge
BukkitForge mod，一个基于 Forge 的 Mod，添加了Bukkit 的 API，是不被 Dynmap 的 Bukkit 版本支持的。可以使用 DynmapForge 版本，并且搭配 DynmapCBBridge 插件。安装过程与上方的 MCPC+ 相同。

# Tekkit Classic
Tekkit Classic，和更老的 MCPC （没有+ - v1.2.5），被 DynmapBukkit 支持。

# Tekkit-Lite
Tekkit-Lite 被 DynmapForge 支持，而不是 Bukkit Dynmap。按照上方 Forge 的安装方式安装 Dynmap。

# Spout
Spout 服务器被 DynmapSpout 的实验项目支持（Spout 进行的重构使对其进行支持不切实际）。安装至 Spout 与 Bukkit 相同（解压到 plugins 目录）。注意：这个项目是给 Spout 服务器使用而不是 Bukkit 上的 Spout 插件。Spout插件可以使用 Bukkit Dynmap。

# 从 Bukkit Dynmap 迁移到 Forge Dynmap
将 Bukkit Dynmap 迁移到 Forge Dynmap 可以按照以下方式进行：
* 将 &lt;base&gt;/plugins/dynmap 目录（包括所有数据和子目录）移动到 Forge 服务器上的 &lt;base&gt;/dynmap 目录。
* 编辑 configuration.txt: 替换 'render-triggers' 为以下信息：
```yaml
      render-triggers:
        - blockupdate
        #- blockupdate-with-id
        #- lightingupdate
        - chunkpopulate
        - chunkgenerate
        #- none
```

* 删除 &lt;base&gt;/plugins/dynmap.jar
* 按照安装对应 Forge 版本的方法安装。

