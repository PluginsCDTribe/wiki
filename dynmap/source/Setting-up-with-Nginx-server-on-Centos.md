# 在 CentOS 6.X 使用 Nginx 建立 Dynmap

## 介绍

之前我们介绍了使用Nginx（或者Apache）来建立你的Dynmap而不是内置的Jetty服务器，如果你正在托管你自己的网站（并且已经开放了80端口），那么这将允许你将你的地图建立在 http://map.example.com/ 而不是 http://map.example.com:8123/ (设置DNS记录超出了本文的讨论范围)。

注意：这篇文章猜测你的Web服务器与Minecraft服务器是分离的，这个例子里，我使用 192.168.1.2 建立Minecraft服务器而使用 192.168.1.3 建立Nginx服务器。如果你选择在同一个服务器运行，那么请在配置里将192.168.1.2更改为127.0.0.1 - 只是记住这可能不是最好的解决方式（这时候代理可能有用？）。

## CentOS

为什么是 CentOS? 来自 Wikipedia: 
> CentOS（Community Enterprise Operating System）是Linux发行版之一，它是来自于Red Hat Enterprise Linux依照开放源代码规定发布的源代码所编译而成。由于出自同样的源代码，因此有些要求高度稳定性的服务器以CentOS替代商业版的Red Hat Enterprise Linux使用。

从安装的时候，我选择了'最小安装'的ISO，接着安装任何我可能需要的模块。我推荐安装尽可能少的东西，接着添加缺少的东西而不是一次性安装所有的东西。CentOS ISO镜像都在[这里](http://www.centos.org/modules/tinycontent/index.php?id=30)。 x86\_64 最小安装 ISO 在 `/6.X/isos/x86\_64/CentOS-6.X-x86_64-minimal.iso`，这与你使用的镜像相关（X替换为最近的版本 - 本文写作的时候 - 6.4 - 翻译的时候已经7.4了）。

安装CentOS并在安装的时候设置好网络而不是启动时手动设置 `/etc/sysconfig/network-scripts/ifcfg-eth0` 来配置你的网络。一个静态的IP地址是非常重要的，或者使用DHCP服务器（经常是路由器）。你可能需要配置SSHd，但这不是必须的。

## 安装 Nginx, PHP 和 PHP-FPM

按照[这里或者网上](http://howtounix.info/howto/nginx-php-5-3-10-and-php-fpm-on-centos-5-7-6-2)的指示安装Nginx。这样如果你安装了 x86\_64 CentOS 你就可以在root登陆下使用以下命令。

`rpm -ivh http://mirror.yandex.ru/epel/6/x86_64/epel-release-6-7.noarch.rpm`

`rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm`

在 "配置 Nginx" 部分，我个人使用了 /var/www/map.example.com/public_html 和 /var/www/map.example.com/logs，但这决定于你。

Note: Also create a folder for the cache eg. /var/www/cache and run `chown nginx:nginx /var/www/cache`.

## 设置"站点"

在 /etc/nginx/sites-available/map.example.com 的文件处，更改为以下信息。

```
    proxy_cache_path  /var/www/cache levels=1:2 keys_zone=map:8m max_size=1g inactive=24h;
server {
    server_name map.example.com;
    access_log /var/www/map.example.com/logs/access.log;
    error_log /var/www/map.example.com/logs/error.log;
    root /var/www/map.example.com/public_html;

    location / {
        proxy_pass                  http://[IP OF MINECRAFT SERVER]:9999/;
        proxy_set_header            Host $host;
        proxy_cache                 map;
        proxy_cache_key "$host$uri";
        proxy_cache_valid  200 302  60m;
        proxy_cache_valid  404      10m;
        proxy_cache_use_stale       error timeout invalid_header updating http_500 http_503 http_504;
        proxy_connect_timeout 10;
    }
}
```

将 `proxy_pass` 更改为你的Dynmap服务器的IP和端口。

## 完成

运行这个命令：
`service nginx reload` 来重载命令

保证 80 端口被防火墙（iptables）开放，并且公共IP有一个DNS的A记录连接到 map.example.com 域名。

打开 http://map.example.com