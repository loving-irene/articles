#### linux中安装ftp服务器

[1](https://www.cnblogs.com/chenmh/p/5365274.html)
[2](https://blog.csdn.net/xietansheng/article/details/84145618)

安装ftp服务器
`yum -y install vsftpd`

配置文件目录
`/etc/vsftpd/`

启动服务
`service vsftpd start`

```
sudo service vsftpd start             # 启动 vsftpd 服务
sudo service vsftpd stop              # 关闭 vsftpd 服务
sudo service vsftpd restart           # 重新启动 vsftpd 服务
sudo service vsftpd status            # 查看 vsftpd 服务状态
```


设置用户只能ftp不能登入
`usermod -s /sbin/nologin ftpuser`

linux默认带有安全机制，使用普通的 ftp 21 端口无法连接到服务器，使用 sftp就可以，修改配置文件需要重启服务器

`vim /etc/sysconfig/selinux`
改成selinux=disabled

不重启服务器的方法
setenforce 0

setenforce 1 ：设置SELinux 成为enforcing模式
setenforce 0 ：设置SELinux 成为permissive模式

查看 SELinux 状态
/usr/sbin/sestatus -v

#### 错误记录
[ip4和ip6同时监听](http://blog.ilc.edu.tw/blog/index.php?op=printView&articleId=456809&blogId=25793)
IP4 和 IP6 不能同时监听，在配置文件中
```
listen
listen_ipv6
不能同时为YES
```
