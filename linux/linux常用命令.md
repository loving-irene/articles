<!--
 * @Author: your name
 * @Date: 2020-06-11 15:16:30
 * @LastEditTime: 2020-06-11 19:10:26
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \articles\linux\linux常用命令.md
--> 

|命令|说明|备注|
|-|-|-|
|echo $PATH|输出环境变量||
|export PATH=$PATH:/bin/path|将指定命令临时设置为环境变量||

#### 永久设置环境变量
对所有用户生效，改 /etc/profile，在里面加入 export PATH="$PATH:/bin/path"