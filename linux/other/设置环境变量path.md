### 对所有用户永久生效

在`/etc/profile`中新增新的位置，在修改之后，`source /etc/profile`之后才能立即生效，不然要重新登录才能生效。

### 单一用户永久生效

在用户目录下的`.bash_profile`文件中增加变量，`source`才能立即生效。

### 直接运行 export 命令

这样操作只对当前 `shell` 有效。

`export 变量名=变量值`