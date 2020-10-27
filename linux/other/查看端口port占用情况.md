`linux`查看端口占用情况可以使用`lsof`,`netstat`命令。

### lsof

查看指定端口
`lsof -i:端口号`

查看当前用户下的所有端口，管理员可以看所有
`lsof -i`

显示开启文件 abc.txt 的进程
`lsof abc.txt`

显示 abc 进程现在打开的文件
`lsof -c abc`

显示进程号为 1234 的进程所打开的文件
`lsof -c -p 1234`

显示归属 gid 的进程情况
`lsof -g gid`

### netstat

`netstat -tunlp`用于显示 tcp,udp 的端口和进程等相关情况

`netstat`查看端口占用语法格式：
`netstat -tunlp | grep 端口号`