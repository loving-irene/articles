在使用 kafka 功能之前，需要先下载安装，直接在官网下载压缩包，然后使用`rz`上传比直接在服务器下载要来的快。

### 注意事项

如果碰到一些选项或者命令无效，可能是因为版本不匹配的原因，一般可能是当前使用版本过新，按照大版本回退到对应的版本应该就可以了。

### 概念说明

1.  消费者组（consumer group）
    >消费者组包括多个消费者实例，共享一个组ID，组内的所有消费者协调在一起来消费订阅主题的所有分区。每个分区只能由同一个消费组内的唯一一个消费者来消费。
2.  说明是 rebalance
    >rebalance 本质上是一个协议，解决的问题：规定了一个 consumer group 下的 consumer 实例如何达成一致来分配订阅 topic 的每个分区。比如一个 group 内有 20 个实例，订阅的 topic 有 100 个分区，这样要进行分配，一个实例分配 5 个分区。
3.  什么时候 rebalance
    1.  组成员发生变更
    2.  订阅主题数发生变更，使用正则表达式订阅
    3.  订阅主题的分区数发生变化
4.  

### 查看 kafka 版本

`kafka`的服务端使用`Scala`编写，下载的软件包中包含了两个版本号，`kafka_2.13-2.6.0.tgz`,2.13是`Scala`版本，2.6.0是`kafka`版本。

### 启动kafka server

如果和 zookeeper 配合使用，需要先启动 zookeeper。

`bin/kafka-server-start.sh config/server.properties`

### 启动 zookeeper

kafka 安装包中包含了 zookeeper 安装包，可以不单独下载，但是这样会缺少一些命令行脚本可用，最好是单独下载单独安装。

`bin/zookeeper-server-start.sh config/zookeeper.properties`

### 创建topic

`bin/kafka-topics.sh --create --topic topic_name --bootstrap-server localhost:9092`

### 查看topic list

`bin/kafka-topics.sh --zookeeper 127.0.0.1:2181 --list`

### 查看 consumer group 列表

旧版本使用`--zookeeper`，新版本使用`--bootstrap-server`选项，一个不行就换用另外一个

`bin/kafka-consumer-groups.sh --bootstrap-server 127.0.0.1:9092 --list`

### 查看 consumer group 详情

`bin/kafka-consumer-groups.sh --bootstrap-server 127.0.0.1:9092 --describe --group lx_test`

### 查看指定topic详情

`bin/kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092`

### 向 topic 中写入数据

`bin/kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092`

### 消费

`bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092`

### 关机顺序

先停掉`kafka`，然后再停掉`zookeeper`。