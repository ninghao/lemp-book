# SELinux

如果你发现配置了 nginx ，指定了网站的目录，提示没有权限访问。这很可能是 selinux 的原因，你可以把它关掉。先查看一下你的系统的 selinux 的状态：

```
sestatus
```

上面命令会返回：

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

Current mode 是 enforcing ，表示 selinux 正在运行，你可以临时关掉它：

```
setenforce 0
```

永久关掉 selinux，你可以编辑一下它的配置文件：

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

![](/assets/phpinfo.png)

