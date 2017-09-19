这个页面猜测：

* 你基本了解如何配置和管理IIS服务器。
* Web服务器的根目录位于 C:\Inetpub\wwwroot\。
* 你的 IIS 和 CraftBukkit 在同一台机器运行。
* 你安装了[URL Rewrite](http://www.iis.net/downloads/microsoft/url-rewrite)和[ApplicationRequestRouting](http://www.iis.net/downloads/microsoft/application-request-routing)模块。

开始

* 创建目录 C:\Inetpub\wwwroot\dynmap\。
* 将仓库找到的'web'文件夹下的内容放入 C:\Inetpub\wwwroot\dynmap\。

有两种选择：

* 创建文件夹 `C:\Inetpub\wwwroot\dynmap\tiles\` 并且编辑 `configuration.txt` 并且保证你的 **tilespath** 设置设置为 `C:\Inetpub\wwwroot\dynmap\tiles\`。

```
# The path where the tile-files are placed.
tilespath: C:\Inetpub\wwwroot\dynmap\tiles
```

**或者**

* 在IIS中创建虚拟文件夹，通过在IIS中右键Dynmap文件夹并点击 `Add Virtual Directory` 命名为 `tiles` (别名) 然后 `Physical path` 指向 `dynmap插件文件夹/web/tiles`

接着是重写的部分

* 在IIS中选择Dynmap文件夹。点击URL Rewrite图标，接着 `Add rule(s)`；选择 `Reverse proxy`。在入站规则（inbound rule）中输入 `127.0.0.1:8123` 并且点击ok。在询问是否启用反向代理（reverse proxy）时选择 `Yes`。
* 打开你的Web文件夹 (`C:\Inetpub\wwwroot\dynmap\`) 开启 `web.config` 然后将内容更改为：

```
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <clear />
                <rule name="ReverseProxyInboundRule1" stopProcessing="true">
                    <match url="up/(.*)" />
                    <action type="Rewrite" url="http://127.0.0.1:8123/up/{R:1}" />
                </rule>
				<rule name="ReverseProxyInboundRule2" stopProcessing="true">
                    <match url="standalone/(.*)" />
                    <action type="Rewrite" url="http://127.0.0.1:8123/standalone/{R:1}" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
```

有些版本的（7.x）的IIS不会自动给Dynmap需要的 *.json 文件分配正确的MIME类型（导致加载这些文件时出现406或者404错误，比如 Markers API）。解决这个问题，请按照[这里](http://support.microsoft.com/kb/942050)的指示，来将MIME类型 'application/json' 定义为 'json' 文件拓展。

更多让IIS6和IIS7正确处理 JSON 的细节，请查看 <http://www.sencha.com/forum/showthread.php?33266-Some-Problem-with-JSON&p=229858&viewfull=1#post229858>