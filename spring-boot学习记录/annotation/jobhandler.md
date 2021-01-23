#### @JobHandler 说明

xxl-job 集成到 spring-boot 中

开发步骤：
1.  继承"IJobHandler"：“com.xxl.job.core.handler.IJobHandler”；
2.  注册到Spring容器：添加“@Component”注解，被Spring容器扫描为Bean实例；
3.  注册到执行器工厂：添加“@JobHandler(value="自定义jobhandler名称")”注解，注解value值对应的是调度中心新建任务的JobHandler属性的值
4.  执行日志：需要通过 "XxlJobLogger.log" 打印执行日志