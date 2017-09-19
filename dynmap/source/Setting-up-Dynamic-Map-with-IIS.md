这个页面猜测：

* 你的Web服务器的地址为 `C:\Inetpub\wwwroot\`。
* 你的 IIS 和 CraftBukkit 在同一台机器运行。
* 你的 IIS 开启了 ASP.NET <http://support.microsoft.com/kb/315122>。

开始：

* 创建目录 `C:\Inetpub\wwwroot\dynmap\`。
* 创建目录 `C:\Inetpub\wwwroot\dynmap\tiles\`。
* 将仓库找到的'web'文件夹下的内容放入 C:\Inetpub\wwwroot\dynmap\。

你现在应该有这个文件 `C:\Inetpub\wwwroot\dynmap\up.aspx`。

* 前往 `minecraft_server/plugins/dynmap/configuration.txt` 并确保你将 `tilespath` 设置为 `C:\Inetpub\wwwroot\dynmap\tiles\`：

        # The path where the tile-files are placed.
        tilespath: C:\Inetpub\wwwroot\dynmap\tiles

* 重启你的Minecraft服务器
* 加入你的Minecraft服务器，随机放置一些方块，激活Dynmap生成tiles。

如果一切正常，你应该能在 `C:\Inetpub\wwwroot\dynmap\tiles\` 找到一些新的 'PNG' 文件。你也可以前往 *http://yourwebserver/dynmap/* 。这时候应该显示地图，并且也会显示不能更新（玩家位置和地图更新）的错误。

创建或打开 `C:\Inetpub\wwwroot\dynmap\standalone\config.js` 文件，将内容替换为如下：

        var config = {
          url: {
            configuration: 'up.aspx?path=configuration',
            update: 'up.aspx?path=world/{world}/{timestamp}',
            sendmessage: 'up.aspx?path=sendmessage',
            login: 'up.aspx?path=login',
            register: 'up.aspx?path=register',
            tiles : 'tiles/',
            markers : 'tiles/'
          }
        };

现在刷新你的浏览器。现在应该在 *http://mywebserver/dynmap/* 显示在线的玩家。

### 故障排除 ###

前往你的Web服务器，开启一个浏览器。前往 *http://localhost/dynmap/up.aspx?path=configuration*。这里**应该**显示一些代表你的 `configuration.txt` 中配置的文本，如果显示的是一些错误，那么分析这些错误。如果你不确定要怎么做，请在 IRC 联系我们或者前往论坛求助。

有些版本的（7.x）的IIS不会自动给Dynmap需要的 *.json 文件分配正确的MIME类型（导致加载这些文件时出现406或者404错误，比如 Markers API）。解决这个问题，请按照[这里](http://support.microsoft.com/kb/942050)的指示，来将MIME类型 'application/json' 定义为 'json' 文件拓展。

更多让IIS6和IIS7正确处理 JSON 的细节，请查看 <http://www.sencha.com/forum/showthread.php?33266-Some-Problem-with-JSON&p=229858&viewfull=1#post229858>