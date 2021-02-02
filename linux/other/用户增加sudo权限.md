
###### 打开sudoer文件

root 用户执行命令 `visudo`，编辑的是`/etc/sudoers`文件

##### 修改文件
找到 `root ALL=(ALL) ALL`
在其下面增加一行
`user-name ALL=(ALL) ALL`

如果不想每次都输出密码，可以进行配置，在定义下面增加一行
`Defaults:user-name timestamp_timeout=-1,runaspw`


![照片](https://i.ibb.co/rF6gmZW/sudo.png)

[](https://blog.csdn.net/Dream_angel_Z/article/details/45841109)