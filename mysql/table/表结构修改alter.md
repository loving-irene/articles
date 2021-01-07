表结构修改，如新增字段，已有字段类型变更等。


#### 删除表字段

`alter table table_name drop field`
`ALTER TABLE testalter_tbl  DROP i`

#### 向表中添加字段

默认添加到表中最后一列
`alter table table_name add field_name type`
`ALTER TABLE testalter_tbl ADD i INT`

添加到第一列
`ALTER TABLE testalter_tbl ADD i INT FIRST`

添加到指定列之后
`ALTER TABLE testalter_tbl ADD i INT AFTER c`

#### 修改字段类型及名称

`ALTER TABLE testalter_tbl MODIFY c CHAR(10)`

另外的一种写法，使用 CHANGE
`ALTER TABLE testalter_tbl CHANGE i j BIGINT`
`ALTER TABLE testalter_tbl CHANGE j j INT`