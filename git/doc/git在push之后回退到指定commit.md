命令格式：

```
git reset --soft 版本号

git reset --hard 版本号
```

`soft`和`hard`之间的区别在于，`soft`并不会改变本地的代码，只会改变提交的指向，`hard`不仅会改变指向，还会将本地的代码回退到指定版本下。

一般来讲，使用`soft`模式就可以。