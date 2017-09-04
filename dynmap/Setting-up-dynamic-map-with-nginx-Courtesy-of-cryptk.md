Here is an nginx configuration that gets dynmap properly serving through an nginx web server using an external web server (not proxying to dynmap).  This information assumes the following:

- Your document root for dynmap is at /srv/dynmap
- You have nginx properly installed and you know how to make it serve PHP content (for web chat)
- You have already verified that dynmap is working properly over port 8123 with the built in web server

Here is the nginx configuration that I am using to serve dynmap.  My particular nginx setup uses php-fpm with an upstream defined named "php5-fpm.sock" to connect to php-fpm for the php processing.

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

That config will get dynmap running through the root of the URL defined on the server_name line (adjust accordingly).  On my particular server I am also running the (really excellent) multicraft web admin panel to control my servers with the web panel portion located at /srv/multicraft/ .  Here is the full nginx config I use to also serve multicraft through a sub-URI of /admin/

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

You need to make sure all of the standard external web server configs are done, that the user minecraft is running as has write permissions to the dynmap document root and that the web server has write permissions to the standalone/dynmap_webchat.json file (for webchat to work).

If you need details on how to get nginx up and running with php5-fpm I have a blog article I wrote on running wordpress with nginx, php5-fpm, apc and varnish.  Just skip the wordpress and varnish portions and you will have nginx and php5-fpm (assuming you are on an ubuntu server).  That article is located here http://www.cryptkcoding.com/2011/08/running-wordpress-with-nginx-php-fpm-apc-and-varnish/
