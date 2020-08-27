ubuntu使用镜像安装之后未设 root 权限，需要先设置 root 的密码。

```
sudo passwd
之后输入root的密码

su root
切换成root账号
```

### 目录颜色设置

在用户目录编辑 .bash_profile
```
LS_COLORS=$LS_COLORS'di=01;33' （01：粗体，34蓝色，33黄色）

source .bash_profile 此命令重新加载文件使其生效
```