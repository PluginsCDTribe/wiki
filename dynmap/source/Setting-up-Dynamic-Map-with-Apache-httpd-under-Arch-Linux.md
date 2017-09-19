我们猜测：

* 你安装了 apache-httpd。
* 你的 www-root 目录在: `/srv/http/`。
* 你应该可以通过 *http://localhost:8123/* 成功访问Dynmap。

这个示例展示了如何将你的Dynmap部署在apache-httpd的 *http://mywebserver/dynmap/*。

* 先创建文件夹 `/srv/http/dynmap/`.
* 将 `web` 目录下的文件复制到 `/srv/http/dynmap/` 的zip包。

在 `/etc/httpd/conf/httpd.conf`，保证你在有以下几段，注意，这些语句不必相邻。

        LoadModule proxy_module modules/mod_proxy.so
        LoadModule proxy_http_module modules/mod_proxy_http.so
        LoadModule rewrite_module modules/mod_rewrite.so

接下来，我们必须将 `/dynmap/up/` 和 `/dynmap/standalone` 重定向到Dynmap的内部Web服务器。编辑以下内容到 `/etc/httpd/conf/httpd.conf` 的末尾：

```apache
    ...
    Alias /dynmap/tiles /opt/minecraft_server/plugins/dynmap/web/tiles/

    RewriteEngine on
    RewriteRule /dynmap/up/(.*) http://localhost:8123/up/$1 [P,L]
    RewriteRule /dynmap/standalone/(.*) http://localhost:8123/standalone/$1 [P,L]

    <Directory /opt/minecraft_server/plugins/dynmap/web/tiles/>
        Order allow,deny
        Allow from all
    </Directory>

    <Proxy http://localhost:8123/*>
        Order deny,allow
        Allow from all
    </Proxy>
```

注意这会对所有的VirtualHost生效，如果你有多个虚拟主机，那么推荐你将这些代码放入。

重启Apache/httpd (`sudo /etc/rc.d/httpd restart`)

现在应该在 *http://mywebserver/dynmap/* 显示在线玩家了。