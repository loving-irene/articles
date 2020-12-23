操作命令

`redis-cli -h r-2zetbdoijtgwdy3c0hpd.redis.rds.aliyuncs.com -p 6379 -a 1qaz@WSX keys "/PC/*" | xargs redis-cli -h r-2zetbdoijtgwdy3c0hpd.redis.rds.aliyuncs.com -p 6379 -a 1qaz@WSX del`

其中 "/PC/*" 用来匹配符合要求的key。