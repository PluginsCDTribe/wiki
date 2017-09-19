编译 Dynmap 使用 [Maven](http://maven.apache.org/)。使用 Maven 的 `mvn install` 命令你就可以将项目安装在你的 Maven 仓库，这样就可以用于编译其他需要用此项目作为依赖的项目。基本的方法为，使用 `git clone` 下载代码，使用 `mvn install` 编译代码。

Dynmap 的核心系统基本不需要依赖项，核心用于实现特殊的框架，比如 Bukkit 和 Spout。在你编译某平台的框架之前，你应该复制并按顺序编译这些项目：

* [DynmapCoreAPI](https://github.com/webbukkit/DynmapCoreAPI) - git://github.com/webbukkit/DynmapCoreAPI.git
* [DynmapCore](https://github.com/webbukkit/DynmapCore) - git://github.com/webbukkit/DynmapCore.git

# Dynmap for Bukkit #
复制并按顺序编译这些项目来编译 Bukkit 的 Dynmap：

* [dynmap-api](https://github.com/webbukkit/dynmap-api) - git://github.com/webbukkit/dynmap-api.git
* [dynmap](https://github.com/webbukkit/dynmap) - git://github.com/webbukkit/dynmap.git

或者将以下复制进你的终端：

	git clone git://github.com/webbukkit/DynmapCoreAPI.git && (cd DynmapCoreAPI && mvn install)
	git clone git://github.com/webbukkit/DynmapCore.git && (cd DynmapCore && mvn install)
	git clone git://github.com/webbukkit/dynmap-api.git && (cd dynmap-api && mvn install)
	git clone git://github.com/webbukkit/dynmap.git && (cd dynmap && mvn install)

包含 Dynmap 的 ZIP 文件位于 `dynmap/target/dynmap-*-bin.zip`.

# Dynmap for 原版Spout #
复制并按顺序编译这些项目来编译 Spout 原版服务器的 Dynmap：

* [SpoutAPI](https://github.com/SpoutDev/SpoutAPI) - git://github.com/SpoutDev/SpoutAPI.git
* [SpoutVanilla](https://github.com/SpoutDev/Vanilla) - git://github.com/SpoutDev/Vanilla.git
* [DynmapSpout](https://github.com/webbukkit/DynmapSpout) - git://github.com/webbukkit/DynmapSpout.git

或者将以下复制进你的终端：

	git clone git://github.com/webbukkit/DynmapCoreAPI.git && (cd DynmapCoreAPI && mvn install)
	git clone git://github.com/webbukkit/DynmapCore.git && (cd DynmapCore && mvn install)
	git clone git://github.com/SpoutDev/SpoutAPI.git && (cd SpoutAPI && mvn install)
	git clone git://github.com/SpoutDev/Vanilla.git && (cd Vanilla && mvn install)
	git clone git://github.com/webbukkit/DynmapSpout.git && (cd DynmapSpout && mvn install)

包含 Dynmap 的 ZIP 文件位于 `DynmapSpout/target/DynmapSpout-*-bin.zip`.