#### mysql命令导入

这种方式导入的是整个库。

```
# mysql -uroot -p123456 < runoob.sql
```

#### source命令导入

```
mysql> create database abc;      # 创建数据库
mysql> use abc;                  # 使用已创建的数据库 
mysql> set names utf8;           # 设置编码
mysql> source /home/abc/abc.sql  # 导入备份数据库
```

如果已经创建了库，先要选中库，然后再导入。