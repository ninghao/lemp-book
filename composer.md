# Composer

composer 是 PHP 的包管理工具。

https://getcomposer.org/download/

在 composer 的官方网站的 download 页面上，你会看到一段安装 composer 用的脚本  ..  复制一下它 .. 回到终端 .. 登陆到服务器 ..

因为安装 composer 的脚本里面用到了 php 命令 ..  所以在我们的 php 环境里需要再去安装一下 php-cli  ..  sudo yum install php70u-cli -y    注意你需要安装跟自己现有的 php 相同版本的 php-cli  ..

完成以后，把安装的代码粘贴过来执行一下 ...  如果环境符合安全就会安装成功 ..

在当前的目录里面，会下载一个 composer.phar  ..  使用它的时候可以这样 php composer.phar  ...

我们可以把它放在环境变量的某个目录的下面，这样就可以在任何地方去使用 composer 了 ..  先查看一下环境变量 ..

```
 echo $PATH 
```

比如我要把它放在 /usr/local/bin 目录的下面 ..   移动一下这个文件  ..

```
 sudo mv composer.phar /usr/local/bin/composer
```

想让 composer 安装的东西可以在全局范围使用的话，我们需要再去配置一下 .. 先编辑一个文件 ..

```
 vi ~/.bash\_profile
```

在这个 PATH 里面再添加一个目录的位置 .. 用 : 号分隔一下 .. $HOME/.composer/vendor/bin  ..  $HOME 表示用户的主目录 ..

意思就是在用户主目录下的 .composer/vendor/bin 里面的东西，我们可以在任何地方执行 ..

要让这个配置生效，再执行一下  source ~/.bash\_profile  ..

