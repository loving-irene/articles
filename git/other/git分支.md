### 不指定分支

`git clone  http://10.1.1.11/service/tmall-service.git`

默认拉取的是仓库设置的默认分支，如果没有特别设置，一般都是master分支

### 指定分支

`git clone -b dev_jk http://10.1.1.11/service/tmall-service.git`

### 将远程 git 仓库里的指定分支拉取到本地（本地不存在的分支）

`git checkout -b 本地分支名 origin/远程分支名`

如果出现提示
```
fatal: Cannot update paths and switch to branch 'dev2' at the same time.
Did you intend to checkout 'origin/dev2' which can not be resolved as commit?
```

先执行 `git fetch`，然后再执行上面的命令。

### 本地检出一个新的分支并推送到远程仓库

```
git checkout -b 新的分支名

# 推送新分支到远程仓库
git push --set-upstream origin 分支名
```