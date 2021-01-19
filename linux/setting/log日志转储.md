`log`日志转储指的是`linux`提供服务来设置如何对日志进行管理。

使用的工具是`logrotate`，配置文件为`/etc/logrotate.conf`。日志轮替最主要的作用就是将旧有的日志移动并改名，同时建立新的空日志文件，当旧日志文件超出保存范围时就删除。

下面列举一个配置的例子
```
/home/vagrant/projects/kafka/logs/app.log{
    daily
    rotate 7
    dateext
}
```

需要特别注意的是，如果是一些使用安装包安装的服务，也就是日志是写入`rsyslog`服务配置文件的，新日志加入`logrotate`后，需要重启`rsyslog`服务。不然，虽然`logrotate`会生效，但是日志依然会写到旧文件中。

`prerotate`和`postrotate`主要用于日志轮替的同时执行特定的脚本，一般用于日志轮替之后重启服务。

[详细说明](http://c.biancheng.net/view/1106.html)