<!--
 * @Author: your name
 * @Date: 2020-06-09 14:18:24
 * @LastEditTime: 2020-06-09 14:30:50
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \git_articles\articles\框架\yii2\activeRecord.md
--> 
##### 前言

本篇文章介绍 `yii2` 中的 `activeRecord` 模型的相关知识。

##### 简介

active record 类与数据库表关联。Active Record 实例对应于该表的一行，Active Record 实例的属性表示该行中特定列的值。

```
$customer=new Customer();
$customer->name = 'qiang';
$customer->save();

$db->createCommand('Insert into `customer` (`name`) values(:name)',[':name'=>'qiang'])->execute();
```

yii\db\ActiveRecord 继承了模型 yii\base\Model，它就拥有所有模型特性，比如说属性，验证规则，数据序列化，等等。

##### 类继承及其依赖关系

