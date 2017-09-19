我们猜测：

* 你安装了 lighttpd。
* 你的 www-root 目录在: `/srv/http/`。
* 你应该可以通过 *http://localhost:8123/* 成功访问Dynmap。

开始

* 先创建文件夹 `/srv/http/dynmap/`.
* 将 `web` 目录下的文件复制到 `/srv/http/dynmap/` 的zip包。

这个示例展示了如何将你的Dynmap部署在lighthttpd的 *http://mywebserver/dynmap/*。

在 `/etc/lighttpd/lighttpd.conf`，保证以下模块开启：

```lighttpd
    server.modules = ( "mod_access",
    "mod_rewrite",
    "mod_proxy",
    "mod_fastcgi"
    )
```

现在我们需要让Web服务器的tiles可用，并且将代理 `/dynmap/up/`重定向至Dynmap的内部服务器。将以下内容添加至 `/etc/lighttpd/lighttpd.conf` 的末尾：

```lighttpd
alias.url += ( "/dynmap/tiles/" => "/home/minecraft/minecraft_server/plugins/dynmap/web/tiles/" )

url.rewrite-once += ( 
        "^/dynmap/up/(.*)" => "/up/$1",
        "^/dynmap/standalone/(.*)" => "/standalone/$1"
)

$HTTP["url"] =~ "^/up/" {
        proxy.server = ( "" => (( "host" => "127.0.0.1", "port" => 8123 )) )
}
$HTTP["url"] =~ "^/standalone/" {
        proxy.server = ( "" => (( "host" => "127.0.0.1", "port" => 8123 )) )
}
```

重启 lighttpd (`sudo /etc/rc.d/lighttpd restart`)

现在应该在 *http://mywebserver/dynmap/* 显示在线玩家了。