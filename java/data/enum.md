#### enum说明

枚举的作用是建立数字与文本之间的关系，在程序中直接使用名称而不是使用数字，这样来增加程序的可读性。


```java
基本用法

public enum demo {
    A,
    B
}

获取枚举集合
demo.values()

for(demo item:demo.values())，item 为集合的单项

获取名称
item.name()

获取原始下标
item.ordinal()

---------------
升级用法
这样就可以用上自定义的值，item 增加新的方法 getValue

public enum demo {
    A(20),
    B(30);

    private int value;

    demo(int value) {
        this.value = value;
    }

    public int getValue() {
        return value;
    }
}

上面拥有的方法都拥有，增加了一个方法

获取自定义的下标
item.getValue()
```