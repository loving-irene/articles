#### @PathVariable说明

@PathVariable 映射 URL 绑定的占位符

如果有多个，需要指明

```java
@RequestMapping("/testPathVariable/{id}")
    public String testPathVariable(@PathVariable("id") Integer id)
    {
        System.out.println("testPathVariable:"+id);
        return SUCCESS;

```