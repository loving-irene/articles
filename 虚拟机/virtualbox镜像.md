vagrant 官方提供了一些基础版的 box。可以在基础 box 上来构建自己的开发环境并进行打包，这样非常的方便。

使用原生的安装方式非常的缓慢，可以先下载下来 box，然后在本地进行关联。

```
vagrant box add name1 /path/to/download-box #这就是在本地进行关联，将 box 与下载的镜像进行关联

vagrant init name1
vagrant up
vagrant ssh  这样就完成了登录
```

**打包**
基础库已经完成了一些基本设置，只需要将环境所需要的软件安装好就可以再次打包
```
vagrant halt #先停机
vagrant package --base 在virtualbox中显示的名字，看virtualbox --output 打包出来的名字
```

授权报错，这是因为基础 box ，ssh 使用的是 insercure key,在 vagrant up 时会去检测 key 是否安全，如果不安全，会生成新的key并删除之前不安全的key，如果build新的box给其他人用就会有问题，解决方案是在打包之前，用不安全的key将安全的key替换掉，也就是恢复最开始的原始状态
```
wget https://raw.githubusercontent.com/mitchellh/vagrant/master/keys/vagrant.pub -O .ssh/authorized_keys
chmod 700 .ssh
chmod 600 .ssh/authorized_keys
chown -R vagrant:vagrant .ssh
```

**配置**
```
关闭自动生成ssh key
config.ssh.insert_key=false

配置固定ip
config.vm.network "private_work",ip:"192.168.20.20"
```

**如何自己下载镜像完成配置**
官方文档有相关的配置说明以及一些讲解，下面是常规的一些要点

1.在国内下载速度太慢，一般的做法是使用迅雷下载远程镜像，然后在本地进行新增
```
vagrant box add choose_name /path/to/download_box

这里的 choose_name 自己随便起
```

2.初始化 Vagrantfile
```
如果想从官方远程下载资源，步骤1直接就不需要
vagrant init name

这里的 name 如果是官方搜索库中的 shortname，下一步启动时就会从远程下载资源并安装，如果是第一步中自己设置的名字，就会使用本地下载的镜像资源，而不是下载远程资源
```

3.安装并登陆
```
vagrant up
vagrant ssh

使用第二步的默认配置登陆之后，程序会自动生成新的 ssh key 并替换掉原来的 insecure key，如果你继续打包生成新 box，在使用时会报授权错误。   
```