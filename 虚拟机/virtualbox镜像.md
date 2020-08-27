vagrant 官方提供了一些基础版的 box。可以在基础 box 上来构建自己的开发环境并进行打包，这样非常的方便。

使用原生的安装方式非常的缓慢，可以先下载下来 box，然后在本地进行关联。

```
vagrant box add name1 /path/to/download-box #这就是在本地进行关联，将 box 与下载的镜像进行关联

vagrant init name1
vagrant up
vagrant ssh  这样就完成了登录
```

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