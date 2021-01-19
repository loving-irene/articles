使用 yum 安装依赖包之后，可以这样查找到安装的路径信息。

以 Redis 安装为例

1. 安装

`yum install redis`

2. 查看具体的安装包

`rpm -qa|grep redis`

```
redis-3.2.10-2.el7.x86_64
```

3. 查找安装包的路径

`rpm -ql redis-3.2.10-2.el7.x86_64`

然后就可以拿到安装的路径。