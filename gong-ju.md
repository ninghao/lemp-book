# Git

Git 可以为项目做版本控制项目。先搜索一下：

```
yum search git
```

我看到一些 `git2u` 这个前缀的包，这应该是 ius 仓库提供的。安装 Git：

```
sudo yum install git2u -y
```

如果出现冲突的提示，是因为你的系统里已经包含了 Git，需要先删除掉系统里的 Git 才能继续安装。

再做一点简单的配置，告诉 Git 我们是谁：

```
 git config --global user.name "wanghao8080"
```

再告诉 Git 我们的邮件地址：

```
 git config --global user.email "117663444@qq.com"
```



