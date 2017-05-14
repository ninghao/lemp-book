![](/assets/lemp-book-cover.png)LEMP 是 PHP 网站应用的运行环境，也就是如果你打算在本地或者服务器上去运行一个用 PHP 语言写的网站应用，你需要为它搭建一个 LEMP 环境。 

L 表示 Linux ，它是一种操作系统，Linux 有很多种发行版本，比如 CentOS，Ubuntu 等等。本书会使用 CentOS 7 作为这套环境的操作系统。Linux 系统有很多相近的地方 ，了解了其中的一种，再去使用其它的 Linux 系统就会比较容易了。

E 表示的是 Nginx ，这个 E 取的是 Nginx 的读音（Engine X）。它是一种 Web 服务器，可以为网站应用提供 Web 服务，也就是接待用户访问的服务，用户请求资源，Nginx 提受用户的请求，处理一下，再把用户需要的资源发送给用户。

M 表示 MySQL 或者 MariaDB ，是网站应用使用的数据库管理系统。你可以在数据库管理系统里面创建很多的数据库，然后分配给网站应用去使用。MySQL 跟 MariaDB 可以相互兼容，现在开源社区推荐我们使用 MariaDB，你也可以选择 MySQL。

P，表示的是 PHP。它是解释 PHP 语言用的解析器，我们可以使用 PHP-FPM 跟 Web 服务相互沟通，也就是如果 Web 服务遇到对 PHP 资源的请求，会把请求交给 PHP-FPM ，它会去解释请求的 PHP，再把结果交给 Web 服务，然后 Web 服务器（比如：NGINX）会把最后的结果返回给用户。

[宁皓网出品](https://ninghao.net/?a=51729)



