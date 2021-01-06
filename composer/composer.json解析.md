<!--
 * @Author: your name
 * @Date: 2020-06-12 18:00:12
 * @LastEditTime: 2020-06-12 18:09:06
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \git_articles\articles\composer\composer.json解析.md
--> 

#### 前言

介绍 composer.json 中各个字段的含义及作用。

#### 字段及其解释

|属性|含义|示例|备注|是否必备|
|-|-|-|-|-|
|name|包的名称，作者名称/项目名称|monolog/monolog|包名称可以包含任何字符，包括空格，并且不区分大小写|必备|
|description|描述|||必备|
|version|版本|1.0.0|必须遵循  X.Y.Z 或 vX.Y.Z，可选后缀 -dev, -patch ( -p ), -alpha ( -a ), -beta ( -b ) 或 -RC， patch, alpha , beta 和 RC 后缀也可以跟一个数字||
|type|包的类型||默认为library;composer支持四种类型:library,project,metapackage,composer-plugin||
|keywords|关键字||用于搜索和筛选包||
|homepage|项目网站的url地址||||
|readme|readme文档的绝对路径||||
|time|版本发布日期||||