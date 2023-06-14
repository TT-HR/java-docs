RocketMQ 集群部署模式
- 多master模式：多个master节点组成的集群，单个master重启对应用没有影响，但是未被消费的消息在节点恢复之前不可用
- 多master多slave：maseter写slave读，未被消费的消息可以从slave消费。主从节点同步方式可能出现消息丢失
- 多maseer多slave同步双写：解决上面所有问题，发送消息时间变长。同步刷盘性能较低

rocketmq防止消息丢失
- rocketmq自带的消息事务机制发送消息
- 同步刷盘模式
- 主从机构，需要同步消息

消息堆积
- 增加消费者
- 关注单个消费者消费情况，提高单个消费能力
- mq的堆积监控告警

rocketMq和kafaka
- rocketMQ数据可靠性高，支持同步刷盘
- kafaka写入性能强，主要用于日志场景。rocketMQ倾向于业务
- rocketMQ使用长轮询，消息延迟低
- rocketMQ消费失败重试机制
- rocketMQ能保证全局顺序消费
- rocketMQ支持分布式事务消息
- rocketMQ支持消息查询
