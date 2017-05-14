# Composer

composer 是 PHP 的包管理工具。Drupal，Laravel 这类的应用都需要用到 Composer 。

安装 Composer，先进入到某个目录的下面：

```
cd ~
```

下载 Composer 的安装器：

```
curl -O https://getcomposer.org/installer
```

使用 Composer 安装器安装 Composer：

```
php installer
```

这样会下载一个 composer.phar ，这就是 Composer。这个文件可以放在系统环境变量的某个目录下面，这样你就可以在任何地方使用 Composer 了。

输出系统环境变量：

```
 echo $PATH
```

我决定把 Composer 放在 /usr/local/bin 这个目录的下面，执行：

```
 sudo mv composer.phar /usr/local/bin/composer
```

然后再试一下：

```
composer
```

会返回一些帮助信息：

       ______
      / ____/___  ____ ___  ____  ____  ________  _____
     / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
    / /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
    \____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                        /_/
    Composer version 1.4.1 2017-03-10 09:29:45

    Usage:
      command [options] [arguments]
      ...

想让 composer 安装的东西可以在全局范围使用的话，需要配置一下，编辑：

```
 vi ~/.bash_profile
```

原有：

```
PATH=$PATH:$HOME/.local/bin:$HOME/bin
```

在上面这行配置的结束添加 `:$HOME/.composer/vendor/bin`，像这样：

```
PATH=$PATH:$HOME/.local/bin:$HOME/bin:$HOME/.composer/vendor/bin
```

意思就是在用户主目录下的`.composer/vendor/bin` 里面的东西，我们可以在任何地方执行。

让配置生效，执行：

```
source ~/.bash_profile
```

Composer 安装器现在没用了，可以删除掉：

```
rm -rf installer
```



