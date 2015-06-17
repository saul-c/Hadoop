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

Hadoop配置
1，下载Hadoop安装包 
地址：http://mirror.bit.edu.cn/apache/hadoop/common/hadoop-1.2.1/hadoop-1.2.1.tar.gz

$ wget http://mirror.bit.edu.cn/apache/hadoop/common/hadoop-1.2.1/hadoop-1.2.1.tar.gz

2、解压到指定目录下；
$ mv 文件 /opt
解压
$ tar -zxvf hadoop-1.2.1.tar.gz

3、配置hadoop-env.sh、core-site.xml、hdfs-site.xml、mapred-site.xml四个文件；
进入conf下 $ cd conf/
$ vim hadoop-env.sh 打开 配置Javahome
配置<configuration>

4、编辑/etc/profile文件，配置hadoop相关的环境变量；
5、第一次使用hadoop先进行格式化：
$ hadoop namenode -format；
6、启动hadoop:start-all.sh；
7、检查进程：jps；

HDFS系统

HDFS设计架构
1，块（block）:
HDFS的文件被分为块进行存储（默认65MB），块是文件存储处理的逻辑单元。
2，NameNode（管理节点）
存放的元数据
1，文件与数据快的映射表
2，数据快与数据节点的映射表

3，DateNode（工作节点）
存放数据块
就是真正的数据

MapReduce框架
每台机架上有多个数据块节点，每个节点数据块有三个副本备份，至少有一个备份副本分配到别的机架上，这样做为了每个节点会发生故障，保证数据容错，数据的丢失，有些许数据冗余，避免挂机了数据丢失。

心跳检测，同步做备份，一旦发生故障，备份就会替换。

HDFS 的特点：
1）数据冗余，硬件容错
2）流水线式的数据访问
3）存储大文件	
4）适用性和局限性：
适合数据批量读写，吞吐量高
不适合交互式应用，低延迟很难需求满足
适合一次读写多次读取，顺序读写
不支持多用户并发写相同的文件

HDFS使用：它提供了 shell 接口，可以用Linux命令行操作
hadoop namenode -format #格式化namenode
hadoop fs -ls / #打印目录文件列表
hadoop fs -mkdir input #创建目录
hadoop fs -put hadoop-env.sh input/ #上传文件
hadoop fs -get input/abc.sh hadoop-envcomp.sh #下载文件
hadoop dfsadmin -report #dfs报告
