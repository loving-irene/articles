#### 背景介绍

因为业务稳定性上面的考量，采用的安装方式是从服务器上打包，然后直接搬运到新服务器上解压使用。

在这个过程中，碰到了一些问题，本文做一些记录。
<br>

#### 安装过程

`Mysql` 有一个默认的安装路径，在 `mysql/support-files/mysql.server` 的注释中有说明，期望的安装路径是 `/usr/local/services/mysql`，如果不是安装在这个路径，就需要自己在 `my.cnf` 文件中进行配置。

`**.tar.gz` 解压之后的文件包括
```
# bin/ 带/表明这是一个目录
mysql/
    bin/
    data/
    docs/
    include/
    lib/
    man/
    mysql-test/
    scripts/
    share/
    sql-bench/
    supports-file/
    README
    my.cnf
    my.default.cnf
```
其中需要关注的有这么一些目录和文件
```
    bin/    #存储相关命令
    data/   #储存数据
    scripts/    #初始化脚本
    support-file/  #启动脚本
    my.cnf #配置文件
```

在 `.tar.gz` 解压之后，第一步是配置好 `my.cnf` 文件，接下来的初始化中，部分路径依赖配置文件中的数据，`mysql` 会默认先读取 `/etc/my.cnf` 文件，如果没有才是安装目录下的 `my.cnf`,初始化 OK 之后使用 `support-file/mysql.serve` 脚本以 `--user=mysql` 账户启动 `mysql`，这样就可以了。
<br>

#### 可能碰到的问题

1. 权限问题

    `mysql` 默认使用的用户和用户组都是 `mysql`，在 `linux` 下需要确保 `mysql` 用户和用户组是存在的，且涉及到 `mysql` 读写的文件目录需要变更所属用户和所属组，这里的文件目录一般就是 `mysql` 的安装目录以及 `mysql` 数据存储目录
<br>

2. 顺序问题

    在数据库初始化之前要配置好 `my.cnf` 文件，最佳实践是将安装目录下的 `my.cnf` 复制到 `/etc/my.cnf` 下
<br>

3. 配置文件条目
常规配置包括（其中的路径可以随意指定）：
    ```
    [mysqld]
    basedir = /usr/local/mysql
    datadir = /data/mysql
    socket = mysql.sock
    port = 3306
    pid-file = mysql.pid
    log-error = mysql.err
    ```

    **basedir**
    这是软件的安装路径，结合 1 中所说的权限问题，需要将 `/usr/local/mysql` 的所属用户和所属组变更为 `mysql:mysql`

    **datadir**
    这是数据库的数据存放地址，初始化生成的一些数据也会放置在该文件夹下

    **pid-file**
    `pid` 文件的路径是基于 `datadir` 的，如上，最终的 pid 文件路径会是：`/data/mysql/mysql.sock`
    `log-error` 也是一样
<br>

4. root 密码变更

    一般情况下，`mysql` 正常安装之后，可以使用 `root` 进行无密码登录。有的情况下会随机生成一个密码，存放在 `log` 文件中，在上诉的配置下，就是在 `/data/mysql/mysql.err` 中。除了这两种情况之外，还有一种新情况，生成了 `root` 密码但又找不到，类似于忘记了 `root` 密码。

    这样的情况下，需要先停掉 `mysql server` 然后在特定条件 `--skip-grant-tables` 下启动。
<br>

5. 停掉 mysql server 服务

    本文因为是直接使用自己打包的 `.tar.gz` 来安装，所以无法借助操作系统提供的便捷管理功能，比如 `service` 或者 `systemctl`。
    在这样的情况下，需要使用 `kill` 命令，手动的结束进程。`ps -A|grep mysql` 可以用来查找 `PID`，然后即可使用 `kill -9 PID` 命令。结束进程之后，重启 `mysql server`，使用 `/usr/local/mysql/bin/mysqld_safe --skip-grant-tables &` 重启服务，这个时候可以无密码进入，然后重设 `root` 密码。
