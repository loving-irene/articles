### transactional 说明

当标于类前时, 标示类中所有方法都进行事物处理。

#### 事务传播行为介绍：
@Transactional(propagation=Propagation.REQUIRED) ：如果有事务, 那么加入事务, 没有的话新建一个(默认情况下)
@Transactional(propagation=Propagation.NOT_SUPPORTED) ：容器不为这个方法开启事务
@Transactional(propagation=Propagation.REQUIRES_NEW) ：不管是否存在事务,都创建一个新的事务,原来的挂起,新的执行完毕,继续执行老的事务
@Transactional(propagation=Propagation.MANDATORY) ：必须在一个已有的事务中执行,否则抛出异常
@Transactional(propagation=Propagation.NEVER) ：必须在一个没有的事务中执行,否则抛出异常(与Propagation.MANDATORY相反)
@Transactional(propagation=Propagation.SUPPORTS) ：如果其他bean调用这个方法,在其他bean中声明事务,那就用事务.如果其他bean没有声明事务,那就不用事务

#### 事务隔离级别：
@Transactional(isolation = Isolation.READ_UNCOMMITTED)：读取未提交数据(会出现脏读, 不可重复读) 基本不使用
@Transactional(isolation = Isolation.READ_COMMITTED)：读取已提交数据(会出现不可重复读和幻读)
@Transactional(isolation = Isolation.REPEATABLE_READ)：可重复读(会出现幻读)
@Transactional(isolation = Isolation.SERIALIZABLE)：串行化

MYSQL: 默认为REPEATABLE_READ级别
SQLSERVER: 默认为READ_COMMITTED

#### 事务超时设置

@Transactional(timeout=30) //默认是30秒

脏读 : 一个事务读取到另一事务未提交的更新数据
不可重复读 : 在同一事务中, 多次读取同一数据返回的结果有所不同, 换句话说, 
后续读取可以读到另一事务已提交的更新数据. 相反, "可重复读"在同一事务中多次
读取数据时, 能够保证所读数据一样, 也就是后续读取不能读到另一事务已提交的更新数据
幻读 : 一个事务读到另一个事务已提交的insert数据