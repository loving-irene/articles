##### @Resource说明

@Resource 和 @Autowired 用法类型，都是用来进行依赖注入。

如果对象的属性上面有 @Resource 注解，在启动 spring 容器时会找到 @Resource 注解，进行如下的匹配步骤
1.  查看@Resource括号中的name是否为空，如果不为空，看name的属性值与 bean id是否一致，不一致则匹配失败
2.  上一步为空，spring容器中的bean id与@Resource注解的变量名是否相同
3.  上一步如果不相同，spring容器中 bean 的 id 对应的类型是否与 @Resource 注解的那个变量属性对应的类型相同，如果到这一步还不相同，则匹配失败