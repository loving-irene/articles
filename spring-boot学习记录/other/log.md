#### spring中输入日志的颜色已经占位符使用

```java
logger.error("发送短信参数异常,请检查phone={} ,vcode={} ,param={} ", phone, vcode, param);

占位符在string中为 {}
```

##### 输入的日志颜色

一般来说在 `resource/logback.xml` 文件中进行定义

```xml
<Pattern>%yellow(%d{ISO8601}) %highlight(%-5level) [%blue(%t)] %yellow(%logger) : %msg%n%throwable</Pattern>

%yellow
```
![日志颜色种类](https://i.ibb.co/j6JMWLr/screenshot-logback-qos-ch-2021-01-23-15-33-10.png)