### 单表编辑操作

<hr>

本章节主要介绍对单表记录的更新操作。仅做最实用的说明，详情可参看官方源文档。

[Mysql源文档](https://dev.mysql.com/doc/refman/8.0/en/update.html)

**语法：**
```
UPDATE table_reference 
    SET assignment_list 
    [WHERE where_condition] 
    [ORDER BY ...] 
    [LIMIT row_count]
```

**说明：**
```
    assignment:
        col_name = value
    
    assignment_list:
        assignment [,assignment] ...
```

<br>
<br>

### 常规编辑

<hr>

更新指定字段的值，使用 `student` 表演示。

|id|name|age|tag|
-|-|-|-
1|t1|10|1|
2|t2|11|1|
3|t3|12|2|

<br>

```
    # 更新单个字段
    update student set name = 'new name' where id = 1;

    更新之后的表为
    -----------------------------
    |id | name      | age | tag |
    ------------------------
    |1  | new name  |  10 |  1  |
    -----------------------------

    # 更新多个字段
    update student set name = 'back',age = 20 where id = 1;

    更新之后的表为
    ------------------------
    |id | name | age | tag |
    ------------------------
    |1  | back |  20 |  1  |
    ------------------------
```

<br>
<br>

### 非常见用法

<hr>

这部分列举出一些不常见的示例，了解即可。

```
    # 在已有值的基础之上进行处理
    update student set age = age + 1;

    # 如果不使用 order by 声明从大王小变更，按照正常顺序会报错。正常 id：1,2 先处理 1 ，就会有两个 2
    update student set id = id + 1 order by id desc;
```

<br>
<br>