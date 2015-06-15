# Hadoop
Hadoop

系统瓶颈：存储容量，读写速度，计算效率...

基于系统瓶颈就诞生了,谷歌（Google）MapReduce.BigTable.GFS技术。 降低了成本，软件保证可靠性，简化并行分布是计算，无须控制节点同步和数据交换。 Hadoop是模仿谷歌大数据技术的开源实现。

Hadoop是什么？
Hadoop是一个开源的分布式存储和分布式计算平台。

是Apache开源项目：网站http://hadoop.apache.org。

Hadoop的组成 两个核心组成： HDFS：分布式文件系统，存储海量的数据。 MapReduce :并发处理框架，实现任务分解和调度。

Hadoop可以用来做什么呢？ 可以用来搭建大型数据仓库，PB级数据的存储、处理、分析、统计等业务。 常用于用于搜索引擎、商业智能、日志分析以及数据挖掘。

好处优势： 1，高扩展。 2，低成本。 3，很多辅助工具。

Hadoop开源工具介绍

Hive（蜜蜂） Hadoop的开源工具。 用SQL语句----hive----转化成-----Hadoop任务执行。

HBase 存储结构化数据的分布式数据库。

HBase和关系数据库的区别：放弃事务特性，追求高扩展。 HBase和HDFS区别： 提供数据的随机读写和实时访问，实现对表数据的读写功能。

ZooKeeper(动物管理员):监控Hadoop集群里的每个节点的状态，管理整个集群的配置，维护数据节点之间的一致性...

ver1.2稳定版本，对于初学者来说更容易上手

Hadoop安装

1、准备liunx环境； 两种方式：1，安装虚拟机 2，用云主机

2、安装JDK； $ ls $ javac $ apt-get install jdk文件 $ vim /etc/profile

export JAVA_HOME=jdk安装目录 export JRE_HOME=$JAVA_HOME/jre export CLASSPATH=$JAVA_HOME/lib;$JRE_HOME/lib:$CLASSPATH export PATH=$JAVA_HOME/lib;$JRE_HOME/lib:$PATH

$ source /etc/profile

3、配置hadoop；
