
问题1：
com.alibaba.rocketmq.client.exception.MQClientException: Send [1] times, still failed, cost [150586]ms, Topic: INSERT_USER_010000006043, BrokersSent: [broker-a, null, null, null, null, null] See https://github.com/alibaba/RocketMQ/issues/50 for further details. at com.alibaba.rocketmq.client.impl.producer.DefaultMQProducerImpl.sendDefaultImpl(DefaultMQProducerImpl.java:578) at com.alibaba.rocketmq.client.impl.producer.DefaultMQProducerImpl.send(DefaultMQProducerImpl.java:1031) at com.alibaba.rocketmq.client.impl.producer.DefaultMQProducerImpl.send(DefaultMQProducerImpl.java:1025) at com.alibaba.rocketmq.client.producer.DefaultMQProducer.send(DefaultMQProducer.java:95) at
... more
java.lang.Thread.run(Thread.java:748) Caused by: com.alibaba.rocketmq.remoting.exception.RemotingTimeoutException: wait response on the channel <10.0.6.39:10911> timeout, 150000(ms) at com.alibaba.rocketmq.remoting.netty.NettyRemotingAbstract.invokeSyncImpl(NettyRemotingAbstract.java:375) at com.alibaba.rocketmq.remoting.netty.NettyRemotingClient.invokeSync(NettyRemotingClient.java:622) at com.alibaba.rocketmq.client.impl.MQClientAPIImpl.sendMessageSync(MQClientAPIImpl.java:309) at com.alibaba.rocketmq.client.impl.MQClientAPIImpl.sendMessage(MQClientAPIImpl.java:292) at com.alibaba.rocketmq.client.impl.producer.DefaultMQProducerImpl.sendKernelImpl(DefaultMQProducerImpl.java:679) at com.alibaba.rocketmq.client.impl.producer.DefaultMQProducerImpl.sendDefaultImpl(DefaultMQProducerImpl.java:500)
... more

解决办法：
暂无
