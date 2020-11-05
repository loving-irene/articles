在配置 `nginx` 做 `web` 服务器时，和`php-fpm`的交互方式，可以设置端口模式，也可以使用 `socket`。

查询`php-fpm.cnf`配置，查询`listen`。

```
listen=127.0.0.1:9000

listen=/tmp/php-cgi.sock
```

根据`php-fpm`的配偶来调整`nginx`的配置
```
fastcgi_pass unix:/tmp/php-cgi.sock

or

fastcgi_pass 127.0.0.1:9000
```