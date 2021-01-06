git 仓库存在，但是在本地使用 git clone，报错仓库不存在。

原因：
之前使用 git clone 时缓存了账户和密码，缓存的账户和密码没有当前项目的权限，所以连输入框都没有弹出。

查看是否缓存了用户名和密码
`git config -l` 查看返回值中是否存在 `credential.helper=`，如果有，则说明缓存了

清除缓存的账号和密码
`git credential-manager uninstall`