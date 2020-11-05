### curl 命令使用

### GET 方法请求

`curl -v localhost:8080/employees`

### POST 方法发送请求

`curl -X POST localhost:8080/employees -H 'Content-type:application/json' -d '{"name":"bob","role":"student"}'`