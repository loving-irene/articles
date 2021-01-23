#### swagger配置说明

#### 配置分组

如下是一个分组的范例

```java
@Bean
public Docket wechat() {
    return new Docket(DocumentationType.SWAGGER_2)
        .groupName("微信")
        .apiInfo(apiInfo())
        .select()
        .apis(RequestHandlerSelectors.basePackage("com.enation.app.javashop.api.buyer"))
        .paths(PathSelectors.ant("/wechat/**"))
        .build().globalOperationParameters(this.buildParameter()).directModelSubstitute(Region.class, Integer.class);
}

private ApiInfo apiInfo() {
    return new ApiInfoBuilder()
        .title("买家Api文档")
        .description("买家中心API接口")
        .version("7.0")
        .contact(new Contact("Javashop", "http://www.javamall.com.cn", "service@javashop.cn"))
        .build();
}
```

其中 `PathSelectors.ant("/wechat/**")` 用来过滤出符合条件的接口
`PathSelectors`支持4种模式
1.  any 不限制
2.  none 都不行
3.  regex   符合正则要求的
4.  ant 符合要求的