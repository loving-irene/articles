### 自定义注解的操作说明

需要自定义两个类
1.  注解类

上面有4个元注解，其中 `@Constraint(validatedBy = {RedirectTypeValidator.class})` 指明用哪个具体的类实现校验

```java
@Constraint(validatedBy = {RedirectTypeValidator.class})
@Documented
@Target( {ElementType.PARAMETER,ElementType.FIELD})
@Retention(RetentionPolicy.RUNTIME)
public @interface RedirectType {

    String message() default "不正确的跳转类型";

    Class<?>[] groups() default {};

    Class<? extends Payload>[] payload() default {};
}
```

2.  注解校验类

需要实现接口 ConstraintValidator<RedirectType, String>，泛型里面的参数是注解类和参数类型。

function initialize 进行一些初始化操作

function isValid 进行校验动作
```java
public class RedirectTypeValidator implements ConstraintValidator<RedirectType, String> {

    private final String[] ALL_STATUS = {"APPLET_PAGE","APPLET_TAB","EXT_APPLET_PAGE","EXT_APPLET_TAB","H5_PAGE","APPLET_CHAT","GOODS_ID","GOODS_CATEGORY","LIVE"};

    @Override
    public void initialize(RedirectType status) {

    }

    @Override
    public boolean isValid(String value, ConstraintValidatorContext context) {
        return Arrays.asList(ALL_STATUS).contains(value);
    }
}
```


[网页说明1](https://blog.csdn.net/qq_38439885/article/details/81227063)

