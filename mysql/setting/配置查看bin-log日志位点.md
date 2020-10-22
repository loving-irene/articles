### 查看binlog日志位点

```
select unix_timestamp();show master status;
```

### 获取 binlog 文件列表

`show binary logs;`

### 查看当前正在写入的 binlog 文件

`show master status\G;`

### 查看指定binlog文件的内容

`show binlog events in 'mysql-bin.000002';`

### 使用 mysqlbinlog 工具查看

本地查看

1.  基于开始/结束时间
`mysqlbinlog --start-datetime='2013-09-10 00:00:00' --stop-datetime='2013-09-10 01:01:01' -d 库名 二进制文件`
2. 基于 pos 值
`mysqlbinlog --start-postion=107 --stop-position=1000 -d 库名 二进制文件`

远程查看
`mysqlbinlog -u username -p password -hl-db1.dba.beta.cn6.qunar.com -P3306 --read-from-remote-server --start-datetime='2013-09-10 23:00:00' --stop-datetime='2013-09-10 23:30:00' mysql-bin.000001 > t.binlog`

### 报错 unknown variable 'default-character-set=utf8mb4'

原因是`my.cnf`文件中加入了该配置，可以变更配置，也可以增加选项`--no-defaults`