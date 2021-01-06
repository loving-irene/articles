### 创建库

语法：
`create {database|schema} [if not exists] db_name [create_specification]...`

说明：
语法中{}表示必填，A|B 意味着在 A 和 B 中二选一，[] 表示有可无
create_specification 提供这些选项

* [default] character set [=] charset_name
* [default] collate [=] collation_name
* default encryption [=] {'Y'|'N'}

实例:

```
    #创建数据库 test，使用默认配置
    create database test;

    #创建数据库 test2，使用自定义配置，character set 配置数据库字符编码，collate 指定排序规则
    create database test2 character set = xxx collate = xxx
``