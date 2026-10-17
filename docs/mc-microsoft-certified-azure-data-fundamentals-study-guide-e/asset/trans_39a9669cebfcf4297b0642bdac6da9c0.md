

Apache Interactive Query 是一个开源的、内存中缓存服务，用于交互式和更快速的 Hive 查询。此集群类型可供开发人员或数据科学家使用，以便轻松针对存储在 Azure Blob Storage 或 ADLS 中的大型数据集运行 Hive 查询。

与 Azure 中的任何服务一样，您可以通过 Azure 门户、Azure PowerShell 或 Azure CLI 脚本，或通过 ARM 或 Bicep 等基础设施即代码模板来配置和部署 Azure HDInsight 群集。在 Azure 中创建 Azure HDInsight 群集会部署所选的群集类型、用于管理群集资源的 Apache Hadoop YARN 资源管理器，以及 Ambari、Avro、Hive、Sqoop、Tez、Pig 和 Zookeeper 等多种流行的开源工具。这大大缩短了构建分布式解决方案所需的时间。

大多数现代数据仓库场景利用 Apache Spark 而非 Apache Hadoop、Apache Storm 和 Apache Interactive Query 来处理大型数据集，原因在于其速度、执行批处理和流处理活动的能力、数据源连接器的数量以及整体易用性。事实上，ADF 映射数据流使用 Apache Spark 群集执行 ETL 活动。Apache Spark 还使数据科学家和数据分析师能够交互式地并发操作数据。

部署 Azure HDInsight 群集时，必须考虑以下几个管理方面：

*   预配后，Azure HDInsight 群集无法暂停。这意味着，如果您希望在群集未使用时节省成本，则需要删除群集。组织通常使用 Azure Automation 等自动化框架，在运行完成后使用 Azure PowerShell 或 Azure CLI 删除群集。然后，他们可以使用自动化脚本或基础设施即代码模板重新部署群集。

*   群集缺少暂停功能，为元数据管理带来了两难困境。Azure HDInsight 群集使用 Azure SQL Database 作为中央架构存储库，也称为元存储。默认元存储与群集的生命周期绑定，这意味着删除群集时，元存储以及所有关于 Hive 表架构的信息也会被删除。可以通过使用自己的 Azure SQL Database 作为自定义元存储来避免此问题。自定义元存储不与群集的生命周期绑定，允许您创建和删除群集而不会丢失任何元数据。它们还可用于管理多个群集的 Hive 表架构。有关自定义元存储的更多信息，请参阅 `https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-use-external-metadata-stores#custom-metastore`。

*   群集默认不支持 Azure AD 身份验证、RBAC 和多用户功能。可以通过在部署工作流中将企业安全性包 (ESP) 添加到群集来集成这些服务。有关 ESP 的更多信息，请参阅 `https://docs.microsoft.com/en-us/azure/hdinsight/enterprise-security-package`。

本章后面将讨论可用于构建 Apache Spark 群集的另外两项 Azure 服务。Azure Databricks 和 Azure Synapse Apache Spark 池是两个基于 Apache Spark 的分析平台，可克服 Azure HDInsight 带来的管理开销。这两项服务都允许您轻松暂停（在 Azure Databricks 中称为“终止”）Spark 群集，并无需自定义外部元存储即可维护架构元数据。它们还与 Azure AD 原生集成，使用户能够利用其现有的身份验证/授权机制。由于易于使用以及提供数据工程师统一开发体验的其他组件，Azure Databricks 和 Azure Synapse Analytics 是 Apache Spark 工作负载的首选。有关使用 Azure Databricks 而非 Azure Synapse Analytics Apache Spark 池以及反之亦然的原因，将在以下部分中描述。

Azure HDInsight 群集通常用于无法使用 Azure Databricks 和 Azure Synapse Analytics 或需要 Apache Kafka 的场景。无法使用 Azure Databricks 和 Azure Synapse Analytics 的最常见场景示例是：解决方案要求其 Azure 资源来自不支持这两项服务的区域。Azure 事件中心还提供与 Apache Kafka 兼容的终结点，大多数 Apache Kafka 应用程序可以将其作为管理 Azure HDInsight 中 Apache Kafka 群集的替代方案。配置 Azure 事件中心 Kafka 终结点超出了 DP-900 考试的范围，但如果您想了解更多信息，可以参阅 `https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview`。

## Azure Databricks

Apache Spark 于 2009 年由加州大学伯克利分校的研究人员开发。他们的目标是构建一个解决方案，以克服 Apache Hadoop MapReduce 框架在大数据处理活动中的低效性。虽然基于 MapReduce 框架来在多个计算服务器之间分发处理活动，但 Apache Spark 通过在内存中执行多个操作来增强该框架。Spark 还通过允许用户即时交互式查询数据并创建流处理工作流来扩展 MapReduce。

Spark 架构与 Hadoop 使用的分布式模式非常相似。从高层次来看，Spark 应用程序可以分解为以下四个组件：

*   `Spark driver` 负责将数据处理操作划分为由 Spark 执行器执行的较小任务。Spark 驱动程序还负责从群集管理器为 Spark 执行器请求计算资源。具有多个节点的群集在驱动程序节点上托管 Spark 驱动程序。

*   `Spark session` 是 Spark 功能的入口点。建立 Spark 会话允许用户使用弹性分布式数据集 (RDD) API 和 Spark DataFrame API。这些代表了开发人员可用于构建 Spark 数据结构的低级和高级 Spark API。

*   `cluster manager` 负责管理群集的资源分配。Spark 支持四种类型的群集管理器：内置群集管理器、Apache Hadoop YARN、Apache Mesos 和 Kubernetes。

*   `Spark executor` 从 Spark 驱动程序获取任务并执行该任务。群集中的每个工作节点都分配有自己的 Spark 执行器。Spark 执行器通过将任务分配给节点上的 `slot` 来进一步并行化工作。工作节点插槽的数量由分配给节点的核心数决定。

[Figure 5.4](#c05.xhtml#c05-fig-0004) 说明了 Spark 应用程序的组件如何适应三节点（一个驱动程序和两个工作节点）Spark 群集的架构。

![FIGURE 5.4 Apache Spark distributed architecture](images/c05f004.png)

[FIGURE 5.4](#c05.xhtml#R_c05-fig-0004) Apache Spark distributed architecture

Spark Core API 使开发人员能够使用多种流行的开发语言构建 Spark 应用程序，包括 Java、Scala、Python、R 和 SQL。这些语言具有特定于 Spark 的 API，例如用于 Python 的 PySpark 和用于 R 的 SparkR，旨在跨 Spark 执行器并行化代码操作。Spark 的创建者还开发了多个基于 Spark 的库，旨在用于各种大数据场景，包括用于分布式机器学习应用程序的 MLlib、用于图处理的 GraphX、用于流处理的 Spark Structured Streaming，以及用于结构化和分析数据的 Spark SQL + DataFrames。

