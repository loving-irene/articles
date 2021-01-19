### long与Long的区别
java 数据类型分为两种，基本类型以及对象类型

#### 基本类型
byte(8),short(16),int(32),long(64),float(32),double(64),char(16),boolean(1)

#### 对象类型
Byte,Short,Integer,Long,Float,Double,Character,Boolean

对象类型的值进行比较时不能直接使用，>，=，<，而是需要使用方法来取值。

对于=
.equals()

对于>,<
.longValue()

### long 转换 Long

对应的，将 long 转换为 Long 即可。
```java
int n = 10;
Integer in = new Integer(100);

//将int类型转换为Integer类型
Integer in1 = new Integer(n);

//将Integer类型的对象转换为int类型
int m = in.intValue();
```