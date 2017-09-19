我们猜测

* 你的Minecraft服务器目录为 `/opt/minecraft_server/`。
* 你安装了最新的CraftBukkit
* 你的Minecraft服务器托管于 `localhost`。

安装并测试Dynmap：

* 将文件 `dynmap.jar` 和文件夹 `dynmap` 复制到 `/opt/minecraft_server/plugins/`。
* 重启你的Minecraft服务器。
* 加入你的Minecraft服务器。
* 放置一些方块。
* 开启浏览器。
* 前往 *http://localhost:8123/*。

你应该在左上方看到了你的地图和名字。一旦你点击了名称，地图会平移到你的位置，你应该能看见一部分生成的地图。

# 发布 #
如果你想让你的地图能被其他人访问，你需要做这两步：

* 将 TCP 端口 8123 转发。
* 将地图托管到大型Web服务器上，大型Web服务器必须能够访问Minecraft服务器，详细见下。

# 大型Web服务器 #
如果你正在托管一个 Apache 或者 Lighttpd 服务器，你可能想要让Dynmap地图可以被网页相同的URL访问，像 *http://www.yourwebsite.com/dynmap/* 而不是 *http://www.yourwebsite.com:8123/*。如果是这样，你可以在下方选择你的Web服务器。

* Debian/Ubuntu 上的 apache2: [在Debian下使用Apache建立Dynmap](/Setting-up-Dynamic-Map-with-apache2-under-Debian.md)
* Arch Linux 上的 apache/httpd: [在Arch Linux下使用apache/https建立Dynmap](/Setting-up-Dynamic-Map-with-Apache-httpd-under-Arch-Linux.md)
* Arch Linux 上的 lighttpd: [在Arch Linux下使用Lighttpd建立Dynmap](/Setting-up-Dynamic-Map-with-lighttpd-under-Arch-Linux.md)
* nginx [在Centos下使用Nginx建立Dynmap](/Setting-up-with-Nginx-server-on-Centos.md) (由 LukeHandle 提供)
