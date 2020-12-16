shell 字符串截取命令 cut,printf,awk,sed
[网页](https://www.cnblogs.com/farwish/p/4806018.html)
#### cut

语法：
    cut [options] 文件
    -c 列号     提取第几列
    -d 分隔符   使用指定分隔符来分隔

示例
```
tcp        0      0 0.0.0.0:7000            0.0.0.0:*               LISTEN      1/java

cut -c 1 -d " "
拿到：tcp
```

