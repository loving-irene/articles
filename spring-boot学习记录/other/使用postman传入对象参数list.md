#### 问题

需要使用 postman 传入数组，数组中为对象。

步骤
1. header中设置Content-Type:application/json
2. Body中使用raw，数组直接使用[]
3. 控制器中要使用 `@RequestBody` 来说明从请求体中拿取参数

示例，如果嵌套直接嵌套即可
```
{
    "category_id":368,
    "goods_params_list":[
        {
        "goods_id":1,
        "param_id":2,
        "param_name":"参数名称",
        "param_value":"121wfwefwe"
        }
    ]
}
```