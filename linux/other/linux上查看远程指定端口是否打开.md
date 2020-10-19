使用`netcat`（简称`nc`）命令来确定远程主机上的端口是否可以打开/访问。

使用`netcat`命令可以：打开TCP连接、侦听任意TCP和UDP端口、发送UDP数据包、在IPv4和IPv6进行端口扫描。

### 检查远程指定端口是否打开

```
nc -zv 192.168.1.15 22

可以使用hostname
nc -zv baidu.com 22
```
