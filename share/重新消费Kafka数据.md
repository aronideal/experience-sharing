
## 在Kafka服务器查找offset：

### 找到kafka服务的server.properties

### 找到log.dirs的值，即kafka索引和日志文件的所在目录

### 在(kafka partitionId)0/1/2所属目录的log文件里查找丢失数据的所在索引位，确定是哪个分区，0/1/2

### 在文件上查找offset。如0000000000123456.log的ffset是123456

## 停止kafka消费端服务程序

## 在Zookeeper服务器设置offset：

    zkCli.sh  -server  localhost:2181

### 查看ZooKeeper上offset值:

    get /consumers/[groupId]/offsets/[topic]/[partitionId]

### 设置ZooKeeper上offset值:

    set /consumers/[groupId]/offsets/[topic]/[partitionId] 123456

## 启动afka消费端服务程序

