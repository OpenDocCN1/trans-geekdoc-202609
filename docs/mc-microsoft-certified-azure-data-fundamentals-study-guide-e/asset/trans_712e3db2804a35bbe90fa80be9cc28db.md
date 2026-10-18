

Azure 提供多种服务，数据工程师在构建现代数据仓库解决方案时可以使用这些服务。Azure HDInsight 是一种 PaaS 资源，可用于构建数据处理管道，支持多种流行的开源框架，例如 Apache Hadoop、Apache Spark、Apache Kafka、Apache HBase、Apache Interactive Query 和 Apache Storm。Azure Databricks 是另一种 PaaS 资源，为构建数据处理管道的数据工程师提供统一平台，基于 Databricks Spark。Databricks Spark 是 Apache Spark 的高度优化版本，因此是大多数 Spark 应用程序最理想的服务。

Azure HDInsight、Azure Databricks 以及多种其他数据移动和数据转换活动可以通过 Azure 数据工厂 (ADF) 进行编排。ADF 使数据工程师能够使用 Azure 数据工厂 Studio（一种拖放式、低代码/无代码开发环境）构建数据工程管道。开发人员可以编写数据移动和数据转换活动以并行运行，或将它们链接在一起以顺序运行。由于 ADF 是一种 PaaS 产品，计算基础设施以集成运行时的形式对用户进行了抽象。但是，用户可以选择在虚拟机上安装自托管集成运行时，以使用自己的计算基础设施。这允许用户利用位于本地和专用网络中的数据源。

希望使用单一平台实现端到端分析的组织可以使用 Azure Synapse Analytics。使用 Azure Synapse Analytics，用户可以使用 Synapse Studio 管理数据处理生命周期的所有方面。开发人员可以编写低代码/无代码数据集成管道来移动和转换数据，利用无服务器 SQL 池在不移动数据的情况下使用 T-SQL 探索操作数据和对象数据存储，使用 Apache Spark 池构建可扩展的数据工程解决方案，并将报告就绪数据存储在关系表中，这些表针对使用专用 SQL 池服务分析查询进行了优化。

## 考试要点

### 描述事务性工作负载和分析性工作负载之间的区别。

事务性系统用于捕获支持企业日常运营的业务事务，而分析性系统将事务性数据和其他数据源转换为用于决策的信息。请记住，事务性数据高度规范化以支持写入操作，而分析性数据反规范化以支持读取操作。根据用例，分析性工作负载可以将数据存储在关系数据仓库（例如 Azure Synapse Analytics 专用 SQL 池）中，或作为文件存储在企业数据湖（例如 ADLS）中。

### 描述批处理和流处理。

数据工程师可以使用一种或两种技术的组合来构建数据处理管道：批处理和流处理。对于 DP-900 考试，请记住，批处理工作流在预定义的时间段内或在特定事件发生后处理批量数据。流处理工作流实时摄取和转换连续的数据流。了解两种处理类型各组件所列出的技术。还要记住，现代基于云的架构使得在同一解决方案中实现批处理和流处理工作流变得容易。

### 描述数据仓库功能。

请记住，数据仓库存储针对分析查询进行了优化的数据，通常用作对业务部门决策至关重要的数据的 `单一事实来源`。数据模型遵循星型架构设计模式，其中业务实体及其相关描述符存储在维度表中，与业务实体相关的可衡量事件存储在事实表中。

### 描述 Azure HDInsight。

Azure HDInsight 是 Azure 中的一种托管开源分析服务，可用于为 Apache Hadoop、Apache Spark、Apache Interactive Query/LLAP、Apache Storm、Apache Kafka 和 Apache HBase 部署分布式群集。请记住，与 Azure Databricks 和 Azure Synapse Analytics Apache Spark 池不同，Azure HDInsight 群集无法暂停。您需要销毁群集并使用自动化脚本构建新群集来管理 Azure HDInsight 成本。出于此及其他管理原因，建议您使用其他 Azure 服务（例如 Azure Databricks、Azure Synapse Analytics 和 Azure 事件中心 Kafka 终结点）进行分布式分析。

### 描述 Azure Databricks。

Azure Databricks 是一个统一的分析平台，支持针对批处理和流处理优化的 Spark 群集。该平台是一种 PaaS 资源，提供原生笔记本环境，开发人员可以使用 SQL、Python、Java 或 R 构建 Spark 工作流。请记住，Databricks 群集使用 Azure VM 作为计算节点，处理以 Databricks 单元 (DBU) 计量。Databricks 群集可以配置为单个用户的专用计算、预定的处理作业（单节点或标准），或用于多个用户进行交互式分析的并发工作负载（高并发）。请记住，您可以通过创建装载点或使用服务主体通过直接路径连接来与 Azure 存储帐户建立连接。ADLS 帐户也可以直接使用 Azure AD 凭据直通访问。

### 描述 Azure 数据工厂。

Azure 数据工厂 (ADF) 是一种托管云服务，可用于构建复杂的 ETL、ELT 和数据集成项目。ADF 实例为数据工程师提供了一个平台，用于编写无代码的数据移动和数据转换活动，并通过管道顺序或并行运行它们。ADF 管道可以手动执行，也可以通过计划或基于事件的触发器自动执行。用户可以定义到 90 多个数据源和计算资源的连接作为链接服务。为数据源创建的链接服务可用于表示数据存储中的特定数据结构，例如关系数据库表或一组文件。请记住，集成运行时是为管道活动提供动力的计算基础设施。集成运行时有三种类型：一种用于可通过公共终结点访问的 Azure 资源，一种用于本地资源或仅通过专用网络可访问的 Azure 资源的自托管集成运行时，以及一种 SSIS 特定的集成运行时，允许用户在 ADF 管道中运行旧版 SSIS 包。

### 描述 Azure Synapse Analytics。

Azure Synapse Analytics 是一种企业分析系统，将服务于分析工作负载的多种服务统一在单一环境中。在 Synapse Studio 中，数据工程师可以使用 Synapse 管道自动化数据移动和处理活动，使用专用 SQL 池作为分析数据存储来管理需要快速为报告和分析应用程序提供服务的数据，使用无服务器 SQL 池交互式查询 Azure 存储中的数据，使用 Apache Spark 池使用 Spark 执行数据工程活动，以及使用 Data Explorer 池近乎实时地分析遥测数据。分析人员还可以将 Power BI 工作区链接到 Azure Synapse Analytics 工作区，以便在管理数据和编写查询的同一环境中构建报告。

## 复习问题

### 1. 以下陈述中斜体部分是正确的，还是需要用下面出现的其他片段之一替换它？

服务于事务性工作负载的关系数据库通常使用 `星型架构` 作为其数据模型策略。这种建模模式最适合写入密集型操作。

1. `1NF`
2. `3NF`
3. `2NF`
4. 无需更改

