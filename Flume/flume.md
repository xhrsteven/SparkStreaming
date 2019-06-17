## 业务现状分析

You have lots of servers and systems

A. Network devices B. operating systems C. Web Servers D. Applications

You want to move the logs to Hadoop Clusters

如何解决我们的数据从其他的server上移动到Hadoop上

shell cp 

WebServer /Application Server 分散到各个机器上

日志如何收集到Hadoop平台上

## Flume 概述

flume.apache.org

FLume is a distributed, realiable and available service for efficiently collecting, aggregating and moving large amounts of log data.

webServer ===> Flume ====> HDFS

flume 是由Apache提供的一个分布式、高可靠、高可用的服务，用于分布式的海量日志的高效收集、聚合、移动系统

设计目标：
    可靠性，扩展性，管理性

业界同类产品的对比：
    (***)Flume：Cloudera/Apache Java 开发

    Scribe: FaceBook C/C++开发 不在维护了

    Chukwa: Yahoo/Apache Java开发 不在维护

    Kafka: LinkedIn 

    (***)Logstach: ELK 

## Flume架构及核心组件





## Flume 环境部署

