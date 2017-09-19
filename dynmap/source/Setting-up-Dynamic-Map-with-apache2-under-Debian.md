我们猜测：

* 你安装了 Apache2。
* 你的 www-root 目录在: `/srv/http/`。
* 你应该可以通过 *http://localhost:8123/* 成功访问Dynmap。

这个示例展示了如何将你的Dynmap部署在Apache的 *http://mywebserver/dynmap/*。

* 先创建文件夹 `/srv/http/dynmap/`.
* 将 `web` 目录下的文件复制到 `/srv/http/dynmap/` 的zip包。

首先，我们需要开启需要的模组，输入以下命令：
```bash
    sudo a2enmod rewrite proxy_http
```

首先我们必须重定向 `/dynmap/up/` 和 `/dynmap/standalone/` 到Dynmap的内部Web服务器。请保证你在 `/etc/apache2/sites-available/default` 后有这一段内容：

```apache
    ...
        Alias /dynmap/tiles /opt/minecraft_server/plugins/dynmap/web/tiles/
    
        RewriteEngine on
        RewriteRule /dynmap/up/(.*) http://localhost:8123/up/$1 [P,L]
        RewriteRule /dynmap/standalone/(.*) http://localhost:8123/standalone/$1 [P,L]
    </VirtualHost>
    
    <Directory /opt/minecraft_server/plugins/dynmap/web/tiles/>
        Order allow,deny
        Allow from all
    </Directory>
    
    <Proxy http://localhost:8123/*>
        Order deny,allow
        Allow from all
    </Proxy>
```

重启Apache2 (`sudo /etc/init.d/apache2 restart`).

现在应该在 *http://mywebserver/dynmap/* 显示在线玩家了。