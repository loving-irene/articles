#### java数值转换

![转换图片](https://i.ibb.co/hM1sJTk/java.png)

实线表示无精度损失，虚线表示有可能损失精度。


#### 强制类型转换

```java
double x = 9.97;
int nx=(int) x;
```

强制转换可以是显式操作，也存在隐式执行的情况。比如

```java
int a += 3.5
```