操作命令

`redis-cli -h r-7xvnvfs9tx9ugd5tx4pd.redis.rds.aliyuncs.com -p 6379 -a 1qaz@WSX keys "/PC/*" | xargs redis-cli -h r-7xvnvfs9tx9ugd5tx4pd.redis.rds.aliyuncs.com -p 6379 -a 1qaz@WSX del`

其中 "/PC/*" 用来匹配符合要求的key。