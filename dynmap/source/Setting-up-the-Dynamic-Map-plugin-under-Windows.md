我们猜测：

* 你的Minecraft服务器目录位于`D:\minecraft_server\`。
* 你安装了最新的 CraftBukkit
* 你的Minecraft服务器托管在 `localhost`。

安装并测试Dynmap：

* 将 `dynmap.jar` 和文件夹 `dynmap` 复制到 `D:\minecraft_server\plugins\`.
* （重新）启动你的Minecraft服务器
* 加入你的Minecraft服务器。
* 放置几个方块。
* 开启浏览器。
* 前往 *http://localhost:8123/*。

你应该看到了你的地图的名字显示在左上角。当你点击名字后，地图将会平移到你的位置，并且你应该看到了已经生成的一部分的世界。

# 发布 #
如果你想让地图能被其他的人访问，你需要做以下几步：

* 将 TCP 端口 8123 转发。
* 将地图托管到大型Web服务器上，大型Web服务器必须能够访问Minecraft服务器，详细见下。

# 大型Web服务器 #
如果你正在托管一个 Apache 或者 Lighttpd 服务器，你可能想要让Dynmap地图可以被网页相同的URL访问，像 *http://www.yourwebsite.com/dynmap/* 而不是 *http://www.yourwebsite.com:8123/*。如果是这样，你可以在下方选择你的Web服务器。

* IIS: [使用IIS的URL重写和ARR模块建立Dynmap](/Setting-up-dynamic-map-with-iis-using-url-rewrite-and-applicationrequestrouting.md)(感谢Kekec852的帮助!)
* IIS: [使用IIS建立Dynmap](/Setting-up-Dynamic-Map-with-IIS.md)

(这还不是一个列表啊！如果你使用了其他的服务器，并且你知道如何配置它们，请将其添加至Wiki)