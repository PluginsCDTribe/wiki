我们猜测

* 你对你正在使用的独立Web服务器有相当的经验
* 你的Web服务器与CraftBukkit运行在同一台机器上
* 你的Web服务器支持PHP (仅用于Web到Minecraft的聊天)
* 如果你在使用Linux，你应该知道如何使用终端和 `chmod`。

将以下信息：

      - class: org.dynmap.InternalClientUpdateComponent
        sendhealth: true
        allowwebchat: true
        webchat-interval: 5
      #- class: org.dynmap.JsonFileClientUpdateComponent
      #  writeinterval: 1
      #  sendhealth: true
      #  allowwebchat: false


更改为

      #- class: org.dynmap.InternalClientUpdateComponent
      #  sendhealth: true
      #  allowwebchat: true
      #  webchat-interval: 5
      - class: org.dynmap.JsonFileClientUpdateComponent
        writeinterval: 1
        sendhealth: true
        allowwebchat: false

关闭内部更新机制并开启json文件更新机制，这将在 `writeinterval` 的间隔后在你的web路径写入文件 `standalone/dynmap_world.json`。

将 `plugins/dynmap/web` 中的文件复制进你的Web服务器中的某个文件夹，将 `configuration.txt` 的指向 `tilespath` 和 `webpath` 更改至你放置Web文件的地方。

Linux

    # tile文件放置的路径
    tilespath: /path/to/web/server/dynmap/web/tiles

    # web文件放置的路径
    webpath: /path/to/web/server/dynmap/web

或 Windows

    # tile文件放置的路径
    tilespath: c:\\path\\to\\web\\server\\dynmap\\web\\tiles

    # web文件放置的路径
    webpath: c:\\path\\to\\web\\server\\dynmap\\web

现在**重启**你的Minecraft服务器。加入你的服务器并（随机）放置一些方块来激活Dynmap给你的地图生成tiles。
你也可以输入 `dynmap fullrender worldname` 于你的服务器控制台来渲染整个 `worldname` 世界。

现在刷新你的浏览器，应该在 *http://mywebserver/dynmap/* 显示你的在线人数，保持更新。

## 故障排除 ##

**如果你没有在地图看见任何tiles**，检查tiles目录来查看他们是否已经被生成。如果没有任何tiles，那么可能Minecraft没有在web路径写入tiles的权限，或者你没有正确填写 `tilespath` 。

**如果你没有看见任何玩家或者他们没有移动**，前往 *http://mywebserver/standalone/dynmap_world.json* ( *world* 是世界的名称)。你应该能看见一些代码，并且随着时间流逝刷新能看见代码的改变、 如果没有这个文件或者这个文件没有更新，那么你可能填写了错误的 `webpath` 。

在 Linux，**如果web到Minecraft的聊天没有工作**，你应该 `chmod` 'standalone' 文件夹到 775 或者 777：

    $ chmod -R 775 standalone

这允许 `sendmessage.php` 创建json文件。这一步是必须的，因为是你的Web服务器创建文件而不是Minecraft服务器。

**如果在IIS web到Minecraft的聊天没有运行**，你可能要安装PHP。
