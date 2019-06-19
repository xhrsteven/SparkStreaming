# Kafka概述--消息队列
kafka.apache.org

A distributed streaming platform

PUBLISH & SUBSCRBIE
:to streams of data like a messaging system

PROCESS
:streams of data efficiently and in real time

STORE
:streams of data safely in a distributed relicated cluster

Kafka is used for building real-time data pipelines and streaming apps. It's horizontally scalable, fault-tolearant, wicked fast, and runs in production in thousands of companies.

# Kafka架构及核心概念

Kafka is run as a cluster on one or more servers. The Kafka cluster stores streams of records in categories called topics. Each record consists of a key, a value and a timestamp.

Producer :
Producers publish data to the topics of their choice. The producer is responsible for choosing which record to assign to which partition within the topic

Consumer :
Consumers label themselves with a consumer group name, and each record published to a topic is delivered to one consumer instance within each subscribing consumer group

Broker 

Topic 

# Kafka部署

1）单节点单Broker部署/ 0.9.0.0
$KAFKA_HOME/conf/server.property/
broker.id/
listener 9092/
host.name/
log.dirs/
num.partitions/
zookeeper.connect/
启动Kafka ./bin/kafka-server-start.sh config/server.properties

创建topic：kafka-topic.sh --create --zookeeper hadoop000:2181 --replication-factor 1 --partition 1 --topic Hello_topic

查看所有topic：kafka-topic.sh --list --zookeeper hadoop000:2181

发送消息：broker/
kafka-console-producer.sh --broker-list hadoop000:9092 --topic hello_topic

消费消息：zk/
kafka-console-consumer.sh --zookeeper hadoop000:2181 --topic hello_topic --from beginning 

--from beginning 从头开始消费



2）单节点多Broker部署

3）多节点多Broker部署

# Kafka容错性测试


# Kafka API


