6.8 版本的 homestead 安装了多个版本的 PHP。

**php安装路径**

`/usr/share/php`

**配置文件路径**

包含了 cli 和 fpm 两个不同的配置文件。
`/etc/php/7.3/cli/php.ini/`

**在homestead中如何切换PHP版本**

在 .yaml 中直接配置即可切换PHP的版本。
也可以直接执行 php72，以这样的命令来直接进行切换。

**切换root**

先要生成 root 账号及其密码，`sudo passwd root`，然后填入 root 密码，一般使用 root。