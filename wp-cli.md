# WP-CLI

wp-cli 是管理 wordpress 项目用的命令行工具。 下面去安装一下这个工具 ..  先把它下载下来 ..  



curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar  .. 



完成以后，会下载一个 wp-cli.phar 文件  ..  想让它可以执行需要给它添加一个执行的权限 ..



chmod +x wp-cli.phar



想在任何地方都可以执行它的话，可以把它放到系统的环境变量目录里 ..  先查看一下环境变量 



echo $PATH 



可以把它放在 /usr/local/bin 这个目录的下面 ..



sudo mv wp-cli.phar /usr/local/bin/wp



现在我们就可以在任何地方，使用 wp 这个命令去管理 WordPress 项目了 .. 





