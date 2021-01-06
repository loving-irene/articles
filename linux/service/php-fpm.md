php 5.3 之后不再支持 php-fpm(start|stop|reload) 命令，新版本下需要使用信号量来进行控制。

master 进程可以理解的信号
1. INT,TERM 立刻终止
2. QUIT 平滑终止
3. USR1 重新打开日志文件
4. USR2 平滑重载所有 `worker` 进程并重新载入配置和二进制模块

### 简单的重启方法

先查看 `php-fpm` 的 `master` 进程号

```
# ps aux|grep php-fpm
root     21891  0.0  0.0 112660   960 pts/3    R+   16:18   0:00 grep --color=auto php-fpm
root     42891  0.0  0.1 182796  1220 ?        Ss   4月18   0:19 php-fpm: master process (/usr/local/php/etc/php-fpm.conf)
nobody   42892  0.0  0.6 183000  6516 ?        S    4月18   0:07 php-fpm: pool www
nobody   42893  0.0  0.6 183000  6508 ?        S    4月18   0:17 php-fpm: pool www
```

`kill -USR2 42891`

上面的这种方式适用于没有生成`pid`文件使用，如果生成了`pid`文件，`pid`文件地址一般在配置文件中有定义，配置文件地址可以在`ps`返回值中看到，`/usr/local/php/etc/php-fpm.conf`

在配置文件中查找`pid`，拿到对应配置的地址，这里举例为`run/php-fpm.pid`，下面有用

### 使用pid文件进行平滑重启

`kill -USR2 'cat /usr/local/php/var/run/php-fpm.pid'`

