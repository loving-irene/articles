**virtualbox ip地址为 10.0.2.15**

因为 virtual box 的默认网络连接方式为网络地址转换，将其变更为桥接模式。

**无法联网**

/etc/sysconfig/network-scripts/ifcfg-ens33【ens33位置就是网卡的名字，找到对应网卡的配置文件】 

设置 BOOTPROTO = DHCP 和 ONBOOT = yes 即可（service network restart）

**centos7开启防火墙**

防火墙未开启，报错 unit is masked，防火墙被锁定 
解锁命令 
systemctl unmask firewalld 

启动防火墙 
systemctl start firewalld 


**虚拟机增强现实功能**
安装 Centos 时，安装增强现实功能报错，需要将本地的 VBoxGuestAdditions.iso 上传到服务器上，然后在服务器上安装它。

第一步挂载，然后执行
```
mount -o loop /path/to/VBoxGuestAdditions.iso /path/to/new/folder
cd /path/to/new/folder
./VBoxLinuxAdditions.run
```
在这个过程中，可能会报错，`Could not find the X.Org or XFree86 Window System, skipping.`，这里就需要安装相关的依赖

```
yum install -y xorg-x11-drivers xorg-x11-utils
使用这种方式之后还需要安装其他的包，最后卡在 libXt.so.6 上，这里主要是版本问题，需要指定64位版本，默认会安装32位，可用 yum list 报名来查看有哪些可安装包，然后选择安装对应的包
```