## 配置 NGINX

NGINX 相关的配置可以单独写一本书，不过一开始，我们不会用到太多的配置选项。这本书主要介绍搭建一个 LEMP 环境的流程，你可以在相关资源里找到扩展学习的课程与资料。

**查看 NGINX 的配置：**

```
cd /etc/nginx
ls
```

**返回：**

```
conf.d          koi-utf  mime.types  nginx.conf   uwsgi_params
fastcgi_params  koi-win  modules     scgi_params  win-utf
```

备份

```
sudo mv default.conf default.conf.bak
```

创建

```
vi default.conf
```

内容

```
server {
  listen       80;
  server_name  localhost;
  root         /mnt/web;
  index        index.php index.html index.htm;

  location / {
     try_files $uri $uri/ /index.php?$query_string;
   }

 location ~ \.php$ {
   fastcgi_pass 127.0.0.1:9000;
   fastcgi_index index.php;
   fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
   include fastcgi_params;  
 }
}
```

创建

```
mkdir -p /mnt/web
```

创建

```
echo "<?php phpinfo(); ?>" >> /mnt/web/phpinfo.php
```

重载

```
sudo systemctl reload nginx
```

访问：

```
http://192.168.33.10/
```

报错：

```
403 Forbidden
```







