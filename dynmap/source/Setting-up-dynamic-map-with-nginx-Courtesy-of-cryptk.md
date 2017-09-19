这里介绍了如何使用Nginx作为外部Web服务器搭建Dynmap 网页服务（非代理服务器）。 
我们推测你已经完成了以下步骤：

- 你所安装的 Dynmap 根目录在 /srv/dynmap
- 你正确地安装了 Nginx 服务，并且懂得如何使用它来搭建一台PHP在线聊天系统
- 你所安装的 Dynmap 和内置网页服务器已经正确运行在 8123 端口

以下展示出 Dynmap 运行在Nginx时的默认配置文件。为了更好的进行数据处理，我特意将Nginx中的php-fpm配置命名为 "php5-fpm.sock"。

```
server {
    listen       80;
    server_name  minecraft.example.com;
    root         /srv/dynmap/;

    index index.html;

    access_log /var/log/nginx/minecraft.example.com-access_log;
    error_log /var/log/nginx/minecraft.example.com-error_log;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        try_files $uri =404;
        fastcgi_index index.php;
        fastcgi_pass php5-fpm-sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include /etc/nginx/fastcgi_params;
    }
}
```

这些配置会运用到 Dynmap 下所有的URL行中。如果你想使用 MultiCraft 作为 Dynmap 的后台管理系统也是极好的。 以下是使用Nginx搭建 Dynmap 时使用 MultiCraft 管理的配置：

```
server {
    listen       80;
    server_name  minecraft.example.com;
    root         /srv/dynmap/;

    index index.html;

    access_log /var/log/nginx/minecraft.example.com-access_log;
    error_log /var/log/nginx/minecraft.example.com-error_log;

    location / {
        try_files $uri $uri/ =404;
    }

    location /admin {
        alias /srv/multicraft/;
        index index.php;
    }

    location ~ ^/admin/(.*\.php)$ {
        alias /srv/multicraft/$1;
        fastcgi_pass php5-fpm-sock;
        fastcgi_param SCRIPT_FILENAME $request_filename;
        include /etc/nginx/fastcgi_params;
    }

    location ~ \.php$ {
        try_files $uri =404;
        fastcgi_index index.php;
        fastcgi_pass php5-fpm-sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include /etc/nginx/fastcgi_params;
    }
}
```

你需要在确保以上所有步骤正确完成以及配置项无误后，你还需要给 Dynmap 和网页服务器对 *standalone/dynmap_webchat.json* 文件赋予足够的读写权限用于网页在线聊天系统。

如果你们有关于Nginx+PHP5 FPM等的非 Dynmap类问题，可以前往 [原作者的博客](http://www.cryptkcoding.com/2011/08/running-wordpress-with-nginx-php-fpm-apc-and-varnish/) 进行详细的提问。
