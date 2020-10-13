以`php-fpm`为例
`ps -ef|grep php-fpm|grep -v grep|grep master|awk '{print $2}'`

