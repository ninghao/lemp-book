# 软件仓库

Linux 的软件仓库里包含了可以直接使用系统包管理工具安装的软件包。搭建环境需要用的软件包可能不包含在系统自带的软件仓库里，所以我们需要安装额外的软件仓库。

## ius

新版本的 php，mysql，mariadb，git，这些你都可以在 ius 仓库里找到。先去安装一下这个仓库：

```
sudo yum install https://centos7.iuscommunity.org/ius-release.rpm -y
```

ius 仓库依赖 epel-release 仓库，所以安装了 ius，也就安装了 epel-release 。ius 仓库可以用在 Redhat 或 CentOS 系统上，安装的时候也要注意适用的系统的版本。上面安装的是适合在 CentOS 7 上使用的 ius 仓库。

安装完以后可以查看系统里的仓库列表，执行：

```
yum repolist
```

你会看到安装的 epel 还有 ius 仓库的名字。

**仓库里可用的软件包列表：**

[https://dl.iuscommunity.org/pub/ius/stable/CentOS/7/x86\_64/repoview/](/h ttps://dl.iuscommunity.org/pub/ius/stable/CentOS/7/x86_64/repoview/)

