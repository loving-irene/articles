#### 获取指定tag的代码

```
// 获取代码库的tag标识
git tag

// 切换到指定tag
git checkout tag_name
```

tag 相当于仓库的一个的快照标识，如果需要编辑指定 tag 下的代码，需要单独拉出来一个分支，在指定分支上修改编辑
```
将 tag 为 v1.6 的代码拉到分支 v1.6 上进行处理
git checkout -b us v1.6
```