# 配置 SELinux

如果你发现配置了 NGINX ，指定了网站的目录，提示没有权限访问。这很可能是 SELinux 的原因，你可以把它关掉。先查看一下系统的 SELinux 的运行状态：

```
sestatus
```

**返回：**

```
SELinux status:                 enabled
SELinuxfs mount:                /sys/fs/selinux
SELinux root directory:         /etc/selinux
Loaded policy name:             targeted
Current mode:                   enforcing
Mode from config file:          enforcing
Policy MLS status:              enabled
Policy deny_unknown status:     allowed
Max kernel policy version:      28
```

`Current mode` 是 `enforcing` ，表示 SELinux正在运行，临时关掉它可以执行：

```
setenforce 0
```

想永久关掉 SELinux，需要修改一个配置文件：

```
sudo vi /etc/sysconfig/selinux
```

找到：

```
SELINUX=enforcing
```

设置成：

```
SELINUX=disabled
```

关掉了 SELinux 可以再去查看一下之前配置好的 NGINX 服务器。

![](/assets/phpinfo.png)







