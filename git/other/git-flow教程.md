### git flow 使用说明

[教程](https://www.git-tower.com/learn/git/ebook/cn/command-line/advanced-topics/git-flow/)


#### 开始一个新功能

`git flow feature start rss-read`[这里的 feature 也可以切换成其他的]

#### 完成一个功能

`git flow feature finish rss-read`

这个命令会将 `rss-read` 分支下的开发内容整合到 `develop` 分支中去并删除当前分支，切换到 `develop` 分支。

#### 创建 release

`git flow release start 1.1.5`

`develop` 分支已经完成了测试等工作，可以发布了，就建立这样的一个分支

#### 完成 release

`git flow release finish 1.1.5`

这个命令将 `release` 分支上的内容整合到本地的 `master` 和 `develop` 分支，且拉取远程分支，保证目前是最新版本。之后，删除该分支，切换到 `develop` 分支。

本地 `master` 分支上的变动需要手动 `push` 才行。


#### 创建 hotfix

`git flow hotfix start missing-link`

这个是对产品代码的修复，基于本地 `master` 分支。

#### 完成 hotfix

`git flow hotfix finish missing-link`

完成的改动合并到 `master` 同时也会更新 `develop` ，然后删除分支，切换到 `develop`