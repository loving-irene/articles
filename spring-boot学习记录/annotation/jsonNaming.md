#### @JsonNaming

可配置选项：

value（Class<? extends PropertyNamingStrategy>）：属性名序列化与反序列化的命名风格，默认PropertyNamingStrategy.clas，即LOWER_CAMEL_CASE(aaBbCc)。


#### 配置可选值：

SNAKE_CASE：下划线连接单词 （aa_bb_cc,大小写不分）

UPPER_CAMEL_CASE：驼峰式（AaBbCc）

LOWER_CAMEL_CASE：驼峰式（aaBbCc）

LOWER_CASE：无论什么格式，转换成小写输出

KEBAB_CASE： 短横线连接单词（aa-bb-cc）


#### 配置的位置

类