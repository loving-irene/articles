在`linux`中安装`java openJDK`，默认安装的只有`jre`，必须要继续安装`yum install java-1.8.0-openjdk-devel`，默认的安装路径在`/usr/lib/jvm`

校验方式
```
java -version
javac -version
```

### 环境配置

在安装完之后，还需要进行相关的环境配置

```
export JAVA_HOME=/usr/lib/jvm/java-1.8.0
export JRE_HOME=$JAVA_HOME/jre
export CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
export PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
```