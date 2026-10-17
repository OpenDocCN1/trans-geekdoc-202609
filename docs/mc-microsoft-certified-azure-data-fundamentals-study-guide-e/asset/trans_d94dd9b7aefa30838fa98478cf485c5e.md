

# 数据仓库

数据仓库是支持分析工作负载和商业智能（BI）活动的数据管理系统。数据仓库管理的数据源自多个来源，例如 OLTP 系统、Web API、IoT 设备和社交媒体网络。与 OLTP 系统不同，数据仓库使用经过读取优化的数据模型，因此针对其发出的分析查询可以高效地返回聚合计算，以支持业务决策。

如 [第 2 章](#c02.xhtml) 中所述，数据仓库使用非规范化数据模型，这些模型针对分析查询和读取密集型工作负载进行了优化。这种方法最常见的设计实践是星型模式。星型模式对业务数据进行非规范化处理，以最大限度地减少数据模型中的表数量。表由与这些实体相关的业务实体和可衡量事件组成。这种数据类别的划分由星型模式中定义的两种表表示：维度表和事实表。

维度表包含描述特定业务实体的信息。这些表通常非常宽，包含多个描述符列和一个作为唯一标识符的键列。一些作为维度表存储的常见实体包括日期、客户、产品类别和产品子类别信息。在所有这些情况下，可能只有相对较少的行，但有大量的列，以尽可能提供描述性信息。

事实表存储与维度表相关的可量化观测值。这些表可以增长到非常大，包含与特定可衡量事件相关的数百万行。一些事实表示例包括互联网销售、产品库存和天气指标。事实表还包括用于与维度表建立关系的外键列。这些关系确定分析查询在筛选事实表数据时可以使用的粒度级别。例如，按日期维度筛选互联网销售事实表的查询只能返回日期维度中包含的详细级别的时间片。

## 现代数据仓库的 Azure 服务

在 Azure 生态系统中，有几种服务可用于构建现代数据仓库解决方案。根据构建解决方案的工程师的场景和技能，大多数 Azure 服务都可以用于构建数据处理管道的不同组件。但是，有一组核心 Azure 数据服务专门设计用于处理大数据工作负载：

* Azure Data Factory
* Azure HDInsight
* Azure Databricks
* Azure Synapse Analytics

这些服务中的每一种都可以在数据处理管道中执行各种不同的功能。这种多功能性使它们能够用于 ETL 或 ELT 管道的各个阶段。它们可以管理各种不同格式的数据，并可以水平和垂直扩展，以处理非常大的数据量。

首先，让我们来看看 Azure HDInsight、Azure Databricks 和 ADF 在现代数据仓库解决方案中的使用方式。关于 Azure Synapse Analytics 的端到端数据处理解决方案将在本章后面的“使用 Azure Synapse Analytics 进行端到端分析”部分中描述。

### Azure HDInsight

Azure HDInsight 是 Azure 中的托管开源分析服务。使用 Azure HDInsight，您可以在 Azure 中部署用于 Apache Hadoop、Apache Spark、Apache Interactive Query/LLAP（Live Long and Process）、Apache Kafka、Apache Storm 和 Apache HBase 的分布式群集。能够快速搭建这些环境而无需采购和管理硬件，降低了开始构建现代数据仓库的组织的入门门槛。

Hadoop 和 Spark 等开源框架旨在通过使用扩展架构来处理大规模数据处理活动。虽然它们可以安装在单个服务器节点上用于测试目的，但大多数用例都利用多个服务器节点，这些节点聚集在一起以大规模执行处理活动。群集由一个头/驱动节点组成，该节点将作业分解为较小的任务，以及一个或多个工作节点，这些节点执行每个任务。

分布式框架还依赖于资源管理器（如 Apache Hadoop YARN（Yet Another Resource Negotiator））来管理群集资源和作业调度。资源管理器将计算资源（例如 CPU、内存、IO）分配给群集节点并监控资源使用情况。了解 YARN 和其他资源管理器的设计细节超出了 DP-900 考试和本书的范围，但如果您想了解更多信息，可以在以下链接中找到更多信息：`https://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html`。

Azure HDInsight 使管理 Hadoop 和 Spark 等分布式框架变得容易，并提供自定义群集部署的功能，例如添加新组件和语言。此外，由于 Azure HDInsight 是 PaaS 服务，您可以轻松地分配给群集的工作节点数量进行向上或向下扩展，以增加计算能力或降低成本。

了解不同的 Azure HDInsight 群集类型以及何时使用它们非常重要。此外，请记住，在部署 Azure HDInsight 群集后，您将无法更改群集类型。因此，了解群集将支持的场景至关重要。以下列表描述了 Azure HDInsight 支持的每种群集类型：

* Apache Hadoop 是一种用于分布式数据处理的开源技术。它使用 MapReduce 并行处理框架大规模处理数据，并使用 Hadoop 分布式文件系统（HDFS）作为分布式存储系统。MapReduce 作业将计算作业分解为较小的工作单元，以便在群集中的各个节点上并行运行。用户还可以利用 Apache Hive 与 Hadoop 一起在数据上投影架构，并使用 HiveQL 查询数据。有关 Apache Hive 的更多信息可以在 `https://docs.microsoft.com/en-us/azure/hdinsight/hadoop/hdinsight-use-hive` 找到。

Hadoop 的一个缺点是它仅支持批处理，迫使用户利用 Apache Storm 或 Apache Spark 等其他服务进行分布式流处理。Hadoop 还从磁盘读取和写入数据，可能导致比支持内存处理的 Apache Spark 更差的处理性能。

* Apache Spark 是一种开源的分布式处理框架，支持内存处理。由于其速度，Spark 已成为批处理和流分布式处理活动的标准框架，取代了 Hadoop。Apache Spark 还支持交互式查询功能，允许用户使用 Spark SQL 等流行开发语言轻松查询 ADLS 等分布式数据存储中的数据。更多 Spark 特定功能（例如开发语言、工作流和最佳实践）将在“Azure Databricks”部分中描述。

* Apache Kafka 是一种开源的分布式实时数据摄取平台，用于构建流处理数据管道。它提供消息代理功能，允许用户发布和订阅数据流。

* Apache HBase 是一种开源 NoSQL 数据库，构建在 Apache Hadoop 之上。它使用列式格式将行数据存储为列族，类似于 Azure Cosmos DB Cassandra API。开发人员可以使用 Hive 查询与 HBase 数据进行交互。

* Apache Storm 是一种开源的实时处理系统，用于非常快速地处理大数据流。与 Hadoop 和 Spark 类似，它使用分布式框架来并行化流处理作业。

