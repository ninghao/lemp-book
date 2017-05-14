# Git

git 可以为项目做版本项目。连接到服务器以后，我们先去搜索一下要安装的 git  ..  yum search git  ..

这里你会看到一些带 git2u 这个前缀的包 .. 这是 ius 仓库里提供的 git  ..  2 是 git 的版本号 .. 后面的 u 是 ius 仓库的一个前缀 .. 

下面我们去安装一下它 ..  sudo  yum install git2u -y

出现了一个冲突的提示，引起冲突的包是这个 git-core  ..   这是因为我们系统里可能安装了 git  ..  输入 git --version  ..  会显示当前安装的 git 的版本 ..

我们可以先删除掉有冲突的包 ..  sudo yum remove git-core -y

然后再去安装一下新版本的 git  .  完成以后查看一下现在的 git 的版本 ..   你会看到是 2.x 版本的 git  ..

下面我们可以再做一点简单的配置，告诉 git 我们是谁 ..

```
 git config --global user.name "wanghao8080"
```

这是用户的名字 ..  再设置一下邮件的地址 ..

```
 git config --global user.email "117663444@qq.com"
```



