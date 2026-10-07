

## 大数据在电子医疗中的作用

![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_171_0.png)

图 8.15 单节点-单代理节点 [40]。

可以使用以下过程安装 Kafka：

- *验证 Java 安装*
- 已安装 ZooKeeper 框架
  i. 下载 ZooKeeper
  ii. 解解 tar 文件
  iii. 创建配置文件
  iv. 启动 ZooKeeper 服务器
  v. 启动 CLI

![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_171_1.png)

图 8.16 单节点-多代理节点 [40]。

## 医疗健康物联网

- - 已安装 Apache Kafka
  i. 下载 Kafka
  ii. 解解 tar 文件
  iii. 启动 Kafka 服务器

在安装 ZooKeeper 和 Kafka 之后，可以通过以下步骤实现单节点-单代理节点：

- - 启动 ZooKeeper
- 配置单节点-单代理节点
  i. 获取主题列表
    命令：bin/kafka-topics.sh -list -zookeeper localhost:2181
  ii. 发送消息
    命令：bin/kafka-console-producer.sh -broker-list localhost:9092 -topic topic-name
  iii. 接收消息
    命令：bin/kafka-console-consumer.sh -zookeeper localhost:2181 -topic topic-name -from-beginning
- 单节点-多代理节点系统可以类似配置
- 部分主题选项：
  i. 修改主题
    命令：bin/kafka-topics.sh -zookeeper localhost:2181 -alter -topic name -partitions count
    示例：bin/kafka-topics.sh -zookeeper localhost:2181 -alter -topic Hello-kafka -partitions 2
  ii. 删除主题
    命令：bin/kafka-topics.sh -zookeeper localhost:2181 -delete -topic _name
    示例：bin/kafka-topics.sh -zookeeper localhost:2181 -delete -topic Hello-kafka

用户通过编写交互式查询并生成结果与 Kafka 进行交互。该系统分析了具有 I/O 路径的可能数据分析策略，并能够在特定情况下克服数据移动问题。

Flex Analytics [24] 系统提高了项目平台的灵活性和扩展性，适用于数据预处理、运行时数据分析以及大规模数据传输。可以从 kafka.apache.org 下载 Kafka，其设置通常包括一些现代技术，如应在系统中安装的 Java 等其他内容。随着技术的不断进步和企业对市场上最佳系统的追求，Kafka 不断证明了它的存在价值。Kafka 的概览见图 8.17。

## 大数据在电子医疗中的作用

![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_173_0.png)

图 8.17 Kafka 概览 [24]。

### 8.2.7 Hive

Hive 在 Hadoop 中用作数据仓库基础设施，处理结构化数据。它存在于 Hadoop 之上以处理大数据，使查询和分析变得简单。Facebook（一家公司）在初始阶段开发了 Hive；Apache 软件基金随后将其宣布为开源，并命名为 Apache Hive。[34] 对 Hive 和 HiveQL 进行了详细研究。Hive 是为了联机分析处理（OLAP）设计的。它以 SQL 查询（即 HiveQL，或 HQL）的形式将架构存储在数据库中，并将数据处理到 HDFS 中。Hive 的特点是快速、可扩展、熟悉且可扩展的。

Hive 的工作原理如下：

- - **执行查询：** 它包含作为命令行或 Web UI 的 Hive 界面，向驱动（任何数据库驱动，如 JDBC、ODBC 等）查询执行。
- **获取元数据：** 编译器向任何 Metastore（数据库）发送元数据请求。
- **获取计划：** 驱动程序利用查询编译器，将相同的查询解析为查询的语法、计划和需求。
- **发送计划：** 此外，编译器检查需求然后将计划重新传回驱动程序以完成并解析查询。
- **发送元数据：** 负责作为编译器的响应传输元数据。
- **执行计划：** 驱动程序将执行计划传输给执行引擎。
- **元数据操作：** 在执行期间，执行引擎与 Metastore 执行元数据操作。
- **执行作业：** 在内部，执行作业过程是一个 MapReduce 作业。执行引擎将作业传输到位于 Name Node 的 JobTracker 并分配。
- **获取并发送结果：** 执行引擎从数据节点接收结果。执行引擎将这些结果值发送到驱动程序；驱动程序将结果发送到 Hive 界面。

## 医疗健康物联网

![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_174_0.png)

```
@@ sal@sal-vb:-$ hive
sal@sal-vb:-$ hive
Logging Initialized using configuration in jarfile:/home/sal/bigdata/apache-hive-2.1.1-bin/lib/hive-2.1.1.jar/hive-log4j2.properties Async: true
Hive-onMN 在 Hive 2 中已弃用，在未来的版本中可能不再可用。使用不同的执行引擎使用 Hive
hive> _
```

**图 8.18**

可以使用以下步骤安装 Hive：

- - 验证 Hadoop 安装
  - 命令：jps
- - 已安装 Derby
  - 下载 Hive
  - 解解 tar 文件
  - 配置数据库
  - 启动 Hive

## Hive 的优点

- - 高级查询语言
- 比 Pig 更低
- 支持外部表
- 构建在 Hadoop 之上

## Hive 的缺点

- - 不可以实时处理
- 高延迟
- 更新和修改较为困难

## 8.3 医疗保健领域中的大数据

正如第 8.2 节讨论的关于大数据的结构和功能，大数据对海量数据产生了奇效。许多企业（无论是公共还是私立）关注存储、分析和生成数据以预防人类。医疗的主要组成部分是医生、护士、药店等。

## 大数据在电子医疗中的作用

![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_175_0.png)

图 8.19 医疗保健中的大数据 [44]。

通过了解病史来治愈患者。在过去，患者的记录写在记事本或任何文件中。现在，记录以电子化的形式维护。随着时间的推移，数据变得海量，处理海量数据是一项困难的任务。然后医疗行业转向大数据，通过数据仓库的概念处理大量数据。电子健康记录（EHR）和电子医疗记录（EMR）等共同改进了健康记录，提高了人们的健康状况。图 8.19 显示了医疗大数据的作用，医疗提供者数据（如 EMR、药品处方和保险记录）以及基因组驱动的实验（如基因分型、基因表达）以及从智能物联网（IoT）获取的其他数据 [44]。

## 8.4 结论

许多应用程序或生物识别传感器产生大量与健康相关的数据。生成生成数据并克服这些生成数据非常重要。在本章中，我们讨论了处理大数据的最常用技术，从旧的人工分析方法到先进技术如 Spark、Kafka 等。其中某些技术（如人工分析和 MRP 系统）已被取代。每家大公司和

