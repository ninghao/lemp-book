## PHP

网站应用如果是用 PHP 语言编写的，对 PHP 文件的请求需要用到 PHP 的解释器，它跟 Web 服务器之间需要用到 PHP-FPM。Web 服务器会把请求转发给 PHP-FPM，PHP-FPM 会使用 PHP 解释器处理请求，把结果再交给 Web 服务器。

**搜索：**

```
yum search php
```

要安装的 PHP 的版本有很多选择，你得根据要运行的网站的需求，去安装网站应用推荐使用的 PHP。Drupal 8，WordPress，Laravel 都支持新版本的 PHP，我看到一些来自 ius 仓库的 php71u ，这是 PHP 7.1 版本的软件包。

PHP 有很多扩展，根据网站的需求，你可能需要在环境里安装不同的 PHP 扩展。

**安装：**

```
sudo yum install php71u-cli php71u-common php71u-fpm php71u-gd php71u-mbstring php71u-mcrypt php71u-mysqlnd php71u-json php71u-xml php71u-pecl-memcached -y
```

启动：

```
sudo systemctl start php-fpm
```

配置开机自启动：

```
sudo systemctl enable php-fpm
```



