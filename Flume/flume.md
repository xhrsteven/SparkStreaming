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

1) Source 收集

2) Channel 聚集
Memory Channel \Kafka Channel \File Channel

3) Sink 输出
HDFS Sink \ Hive Sink \ Logger Sink \Avro Sink \ HBase Sink \ Kafka Sink \

## Flume 环境部署

前置条件： Java Runtime Environment - Java 1.8 or later;
Memory - Sufficient memory for configurations used by sources, channels or sinks;
Disk Space - Sufficient disk space for configurations used by channels or sinks;
Directory Permissions - Read/Write permissions for directories used by agent;

####  下载解压
[hadoop@hadoop01 software]$ wget http://archive.cloudera.com/cdh5/cdh/5/flume-ng-1.6.0-cdh5.7.0.tar.gz
[hadoop@hadoop01 software]$ tar -zxvf flume-ng-1.6.0-cdh5.7.0.tar.gz -C ~/app/

#### 配置环境变量（使用root用户）
[root@hadoop01 ~]# vi /etc/profile
export FLUME_HOME=/home/hadoop/app/apache-flume-1.6.0-cdh5.7.0-bin
export PATH=$FLUME_HOME/bin:$PATH
[root@hadoop01 ~]# source /etc/profile

#### 修改配置文件
[hadoop@hadoop01 software]$ cd ~/app/apache-flume-1.6.0-cdh5.7.0-bin/
[hadoop@hadoop01 apache-flume-1.6.0-cdh5.7.0-bin]$ cp conf/flume-env.sh.template conf/flume-env.sh
[hadoop@hadoop01 apache-flume-1.6.0-cdh5.7.0-bin]$ vi conf/flume-env.sh
export JAVA_HOME=/usr/java/jdk1.8.0_45

#### 验证安装完成
[hadoop@hadoop000 ~]$ flume-ng version
Flume 1.6.0-cdh5.7.0
Source code repository: https://git-wip-us.apache.org/repos/asf/flume.git
Revision: 8f5f5143ae30802fe79f9ab96f893e6c54a105d1
Compiled by jenkins on Wed Mar 23 11:38:48 PDT 2016
From source with checksum 50b533f0ffc32db9246405ac4431872e
[hadoop@hadoop000 ~]$
--------------------- 

#### 使用Flume的关键就是写配置文件

A） 配置Source
B） 配置Channel
C） 配置Sink
D） 把以上三个组件串起来