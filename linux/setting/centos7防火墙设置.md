查看防火墙状态
firewall-cmd --state
关闭防火墙
systemctl stop firewalld.service
禁止开机启动
systemctl disable firewalld.service
重启防火墙
firewall-cmd --reload

开启端口
firewall-cmd --zone=public --add-port=80/tcp --permanent
--zone 作用域
--add-port=80/tcp 添加端口，格式：端口/通讯协议
--permanent 永久生效，无此参数重启失效