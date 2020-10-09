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
|tar -zxvf filename.tar.gz|解压||
|tar -cf package_name file_name|将指定文件打包||
|ps -efl|显示进程相关信息|有很多的参数，具体查资料|

<br>

### 永久设置环境变量
对所有用户生效，改 /etc/profile，在里面加入 export PATH="$PATH:/bin/path"

### 查询日志套餐
cat xxx | grep -A 20 'pattern' 往后20
cat xxx | grep -B 20 'pattern' 往前20
cat xxx | grep -C 20 'pattern' 前后各20

fuser xxx 指定文件在被哪个 PID 使用
top -p pid 查看指定 PID 情况

### 解压缩
