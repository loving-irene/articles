### HttpSecurity 说明

java 类配置文件完全就是对 xml 文件的映射，根本还是理解 xml 文件。

举例：这是一个 security 配置的写法，对应的 xml 文件如下
```java
protected void configure(HttpSecurity http) throws Exception {
    http
        .authorizeRequests()
            .anyRequest().authenticated()
            .and()
        .formLogin()
            .and()
        .httpBasic();
}
```

```xml
    <http>
        <intercept-url pattern="/**" access="authenticated"/>
        <form-login />
        <http-basic />
    </http>
```

这样对照着看就会明白，各个方法名究竟是什么意思。

and() 相当于 xml 的关闭标签。

#### 1.指定 url 关闭用户名密码校验

```java
protected void configure(HttpSecurity http) throws Exception {
    http
        .authorizeRequests()  //1
            .antMatchers("/resources/**", "/signup", "/about").permitAll() //2
            .antMatchers("/admin/**").hasRole("ADMIN") //3
            .antMatchers("/db/**").access("hasRole('ADMIN') and hasRole('DBA')")            4
            .anyRequest().authenticated()  //5
            .and()
        // ...
        .formLogin();
}

1.http.authorizeRequests()方法有多个子节点，每个macher按照他们的声明顺序执行。
2.我们指定任何用户都可以访问的多个URL模式。任何用户都可以访问URL以 "/resources/",开头的URL ,以及"/signup", "/about".
3.以"/admin/" 开头的URL只能由拥有 "ROLEADMIN"角色的用户访问. 请注意我们使用HasRole方法，没有使用ROLE前缀。
4.任何以/db/开头的URL需要用户同时具有"ROLEADMIN" 和 "ROLE_DBA". 和上面一样我们的hasRole方法也没有使用ROLE前缀。
5.尚未匹配的任何URL要求用户进行身份验证
```

#### 2.关闭token

现阶段，在完成登录之后会使用 token 来代替用户名密码，后面还需要关闭指定 URL 对 token 的校验



### 方法说明

addFilterBefore
> 如果携带了 token，则进行 token 验证，通过自定义的过滤器。