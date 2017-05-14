# 配置 PHP-FPM

如果网站要写入某个目录，在我们搭建的环境里，你要确保运行 PHP-FPM 的用户对这个要写入的目录拥有写入权限。一般目录的拥有者对目录都有可以写入的权限。我们可以把运行 PHP-FPM 的用户修改成跟运行 NGINX 一样的用户，这样更好记一些。

先查看一下进程，看看运行 NGINX 的用户叫什么：

```
ps aux | grep nginx
```

显示，运行 nginx: worker process 的用户是 `nginx`，再查看一下运行 PHP-FPM 的用户是谁：

```
ps aux | grep php
```

显示，运行 php-fpm: pool www 的用户是 `php-fpm`，下面我们可以把运行 PHP-FPM 的用户修改成 nginx。

PHP 的配置文件是在：

```
/etc/php-fpm.d
```

这里有个 `www.conf`，编辑这个配置文件，把：

```
user = php-fpm
group = php-fpm
```

修改成：

```
user = nginx
group = nginx
```

重载 PHP-FPM 服务：

```
sudo systemctl reload php-fpm
```

这样运行 PHP-FPM 的用户就变成了 `nginx`，现在，我们可以把需要写入权限的目录的拥有者修改成 `nginx`，这样 PHP-FPM 就可以写入内容到这个目录了。

存储 session 文件的地方，`session.save_path`，值是：

```
/var/lib/php/fpm/session
```



```
chown -R nginx:nginx /var/lib/php/fpm
```











