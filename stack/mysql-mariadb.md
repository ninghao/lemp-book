# MySQL / MariaDB

MySQL 与 MariaDB 是常用的数据库管理系统，所以网站应用都需要这种数据库。在网站运行环境里你可以选择 MySQL ，也可以选择 MariaDB。

我要安装 MariaDB，搜索可用的软件包：

```
sudo yum search mariadb
```

返回的结果里我看到了一些包含 mariadb 的软件包，mariadb100u，mariadb101u。这里的 100u 与 101u 表示的 ius 仓库里的特定版本的软件包。结尾带 u 是为了跟其它仓库里提供的同样的软件包区分开。

**安装：**

```
sudo yum install mariadb101u-server -y
```

**报错：**

```
--> Finished Dependency Resolution
Error: mariadb101u-config conflicts with 1:mariadb-libs-5.5.52-1.el7.x86_64
```

因为原系统里自带 MariaDB 软件包，得先删除原来的低版本的 MariaDB，根据冲突提示，可以判断要删除的包的名字，用 yum remove 可以删除指定的软件包。执行：

```
sudo yum remove mariadb-libs -y
```

删除以后，再次执行安装新版本的 MariaDB，成功！

**启动：**

```
sudo systemctl start mariadb
```

**配置开机自启动：**

```
sudo systemctl enable mariadb
```

## 安全配置

再做点安全相关的配置，比如删除掉测试用的数据库，为 `root` 用户设置密码等等。执行：

```
mysql_secure_installation
```

做几个选择填空题：

```
# 输入当前 root 用户密码
Enter current password for root (enter for none): 

# 想设置 root 用户密码吗？
Set root password? [Y/n] Y

# 输入新密码
New password: 

# 再次输入新设置密码
Re-enter new password: 

# 要去掉匿名用户吗？
Remove anonymous users? [Y/n] Y

# 要禁止 root 用户远程登录吗？
Disallow root login remotely? [Y/n] Y

# 要删除掉 test 数据库吗？
Remove test database and access to it? [Y/n] Y

# 要重载权限表吗？
Reload privilege tables now? [Y/n] Y
```

**完整的对话：**

```
NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MariaDB
root user without the proper authorisation.

Set root password? [Y/n] Y
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] Y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] Y
 ... Success!

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] Y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] Y
 ... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!
```



