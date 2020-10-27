以`php-fpm`为例
`ps -ef|grep php-fpm|grep -v grep|grep master|awk '{print $2}'`

获取`alibaba/canal`的`pid`
`ps aux|grep otter-cannal|grep -v grep|awk '{print $2}'`