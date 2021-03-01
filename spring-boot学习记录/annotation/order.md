#### @order 说明

order 支持集合的注入时，指定集合中 bean 的顺序，将多个 bean 注入到集合时，bean 在集合中的顺序受 order 影响。

order 并不能影响 bean 的加载顺序，也就是往 Ioc容器中注入 bean 时是不受 order 影响的。

@order 不写数字时，默认为最小值，int 类型的最大值，order 的值越小优先级越高。