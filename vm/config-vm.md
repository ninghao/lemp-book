# 配置虚拟机

打开命令行，执行：

```
cd ~/desktop
mkdir ninghao-lemp
cd ninghao-lemp
mkdir app
vagrant init centos/7
```

用编辑器打开 ninghao-lemp 目录，编辑 Vagrant 配置文件：Vagrantfile

**macOS：**

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "./app", "/mnt", type: 'nfs'
end
```

**Windows：**

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "./app", "/mnt", type: 'smb',
    owner: "nginx", group: "nginx"
end
```

启动并连接到虚拟机：

```
vagrant up
vagrant ssh
```



