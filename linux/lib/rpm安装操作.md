Linux 下几乎所有的软件都可以通过 RPM 来进行安装，RPM 有5种操作模式：安装、卸载、升级、查询和验证。

### 安装

`rpm -ivh example.rpm` 安装包并在安装过程中显示正在安装的文件信息及安装进度

### 查询

`rpm -qa|grep tomcat4` 查看`tomcat4`是否被安装

查询还有很多其他的选项

### 卸载

`rpm -e tomcat4`

### 升级

`rpm -Uvh example.rpm`

### 验证

`rpm -Vf /etc/tomcat4/tomcat4.conf`