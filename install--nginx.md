# NGINX

用户对某个地址发出请求，服务器上如果安装了 Web 服务器就可以接收这种请求，并且会把请求的内容发送给发出请求的用户。NGINX 就是一种 Web 服务器。

创建仓库文件

```
/etc/yum.repos.d/nginx.repo
```

稳定版仓库

```
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/7/$basearch/
gpgcheck=0
enabled=1
```

Mainline 版仓库

```
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/mainline/centos/7/$basearch/
gpgcheck=0
enabled=1
```

安装：

```
sudo yum install nginx -y
```

启动：

```
sudo systemctl start nginx
```

开机自启动：

```
sudo systemctl enable nginx
```

测试访问：

```
http://192.168.33.10
```

看到 NGINX 欢迎界面，证明成功。

