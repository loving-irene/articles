### 依赖关系

maven 定义了几种依赖关系，`compile`,`test`,`runtime`,`provided`

|scope|说明|备注|
|-|-|-|
|compile|编译时需要用到该 jar 包，默认||
|test|编译test时需要用到该 jar 包||
|runtime|编译时不需要，运行时需要||
|provided|编译时需要用到，但运行时由 JDK 或某个服务器提供||


### 中央仓库

所有的依赖管理器的运作原理都是类似，都会有一个中央仓库，需要将依赖包上传之后，才能使用依赖管理器来进行依赖管理。

除了从中央仓库下载之外，还可以从镜像下载。

### 查看依赖包

直接在 [查找依赖包](https://search.maven.org/) 中搜索关键字，来确定 `groupId` 等。


### 镜像配置

在用户主目录下进入 `.m2` 目录，创建一个`settings.xml`配置文件

```
<settings>
    <mirrors>
        <mirror>
            <id>aliyun</id>
            <name>aliyun</name>
            <mirrorOf>central</mirrorOf>
            <!-- 国内推荐阿里云的Maven镜像 -->
            <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
        </mirror>
    </mirrors>
</settings>
```

### 唯一ID

maven 需要3个变量，用来唯一确定某个 jar 包：
-   groupId:属于组织的名称
-   artifactId:该 jar 包自身的名称，类似于 java 的类名
-   version:依赖包的版本

### 命令行编译

在命令中，进入到 `pom.xml` 所在目录，执行命令

`mvn clean package`

### 启动服务

`mvn spring-boot:run`

### 常用命令

```
mvn package #打包

mvn jar:jar #只打jar包

mvn test #运行测试

-DskipTests   不执行测试用例，但编译测试用例生成相应的class文件
-Dmaven.test.skip=true  不执行测试用例，也不编译测试用例

mvn install #安装项目到本地


```