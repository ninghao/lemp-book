## 配置 NGINX

NGINX 相关的配置可以单独写一本书，不过一开始，我们不会用到太多的配置选项。这本书主要介绍搭建一个 LEMP 环境的流程，你可以在相关资源里找到扩展学习的课程与资料。

先去看一下 NGINX 配置文件所在地。

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

`conf.d` 是个目录，这个目录上面的 .conf 文件都会被 NGINX 使用，因为在 NGINX 的主配置文件：`nginx.conf` 里面，用了一条指令包含了 `conf.d` 目录下的所有的 .conf 文件。

在 conf.d 下面很可能已经有了一个配置文件：default.conf，如果有你可以先备份一下这个配置文件：

```
sudo mv default.conf default.conf.bak
```

**然后自己配置一个配置文件：**

```
sudo vi default.conf
```

**配置文件里的内容是：**

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

这个配置文件里用了一个 `server` 区块，定了一个服务器。在它里面设置了监听的端口号， `root` 指令指定了网站的根目录是 `/mnt/web`，配置里有两个 `location` 区块。第二个 `location` 区块里设置了怎么处理对 php 文件的请求，这种请求交给了 PHP-FPM 服务（`127.0.0.1:9000`），`include` 载入了一个 fastcgi 的参数配置文件：`fastcgi_params`，这个文件是在 NGINX 配置目录下面。

**现在去创建网站的根目录：**

```
mkdir -p /mnt/web
```

**在网站根目录下面创建一个 php 文件：**

```
echo "<?php phpinfo(); ?>" >> /mnt/web/phpinfo.php
```

**重载 NGINX 可以让配置生效：**

```
sudo systemctl reload nginx
```

**访问：**

```
http://192.168.33.10/phpinfo.php
```

如果一切正常你应该会看到一个页面显示了环境里的 PHP 相关的信息。如果报错：403 Forbidden / File not found. / Access denied ，很可能是 SELinux 引起的，你需要关掉 SElinux。

