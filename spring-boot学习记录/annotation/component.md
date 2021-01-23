#### @Component 说明

@Component作用在类上
@Component注解作用域默认为singleton
使用注解配置和类路径扫描时，被@Component注解标注的类会被Spring扫描并注册为Bean
@Component使用在不确定哪一个层的时候使用，可以作用在任何层次，把普通pojo实例化到spring容器

不推荐使用@Component注解，而应该使用它的扩展，如@Service、@Repository