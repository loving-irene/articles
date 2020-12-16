### 创建表

> MySQL创建表存在大量的可选项，本文不会一一列举说明，感兴趣的可看源文档说明，本文只列举说明常用的选项,下文的说明部分并未100%展示源文档，同样只选择展示了部分内容，如下的 create_difinition 的说明只选择了常用的部分，源文档链接如下

[mysql源文档-创建表](https://dev.mysql.com/doc/refman/8.0/en/create-table.html)
<hr>

**语法：**
`create table [if not exists] tb_name {create_definition} [table_options] [partition_options]`

**说明：**
* create_definition
    *   表字段定义
    ```
    create_definition:
        col_name column_definition
        | {index|key} [index_name] [index_type] (key_part,...]) [index_option] ...
        | {fulltext|spatial} [index|key] [index_name] (key_part,...) [index_option] ...

    column_definition:
        data_type [not null | null] [auto_increment] [unique [key]] [[primary] key] [comment 'string']
    ```
* table_options
    * 表参数设置，如制定该表字符编码等
    
* partion_options
    * 表分区设置


**实例：**
```
    #使用默认设置创建 user 表，包括 name,age 字段
    create table if not exists user(
        name char(25),
        age int(9)
    );

    #使用一些 column_definition 设置来创建 user 表
    create table if not exists user(
        id int(9) not null auto_increment primary comment '主键',
        name char(25) unique
    );

    #使用一些 table_option 来创建表
    create table if not exists user(
        name char(25),
        age tinyint(3)
    ) charset = utf8 comment '用户表';
```

**注意点：**
1. 在命名时，使用 \`\` 包裹 `table` 和 `column`
2. 数据类型`type`在使用时，给出精确定义，如`int(10)`而不是`int`，后面这种方式可能报