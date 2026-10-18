

*   `Data source crawler`: 此功能会自动检查数据湖中的数据文件，以推断其底层结构，从而实现数据的高效组织和分类。

*   `Data catalog creation and maintenance`: AWS Lake Formation 便于创建和持续管理数据目录，提供元数据的中央存储库，从而实现数据湖中数据的轻松发现和探索。

*   `Data transformation processing`: 借助内置的数据转换功能，该服务允许处理和转换存储在数据湖中的数据，使数据科学家和分析师能够使用经过优化的数据集。

*   `Data security and access control`: AWS Lake Formation 通过提供全面的访问控制机制并实现细粒度权限管理，确保强大的数据安全性，确保数据仅由授权的个人和团队访问。

Lake Formation 与 AWS Glue 集成，AWS Glue 是一款无服务器的 `Extract, Transform, Load` (`ETL`) 和数据目录服务，用于提供数据目录管理和数据 ETL 处理功能。我们将在后续章节中分别介绍 ETL 和数据目录组件。

Lake Formation 提供集中式数据访问管理功能，用于管理数据库、表或不同注册 S3 位置的数据访问权限。对于数据库和表，权限可以细粒度地分配给单个表和列以及数据库功能，例如创建表和插入记录。

## 数据摄取

数据摄取是数据源与数据存储之间的桥梁。它在从多种来源获取数据方面发挥着至关重要的作用，包括结构化、半结构化和非结构化格式，例如数据库、知识图谱、社交媒体、文件存储和物联网设备。其主要职责是将这些数据持久地存储在各种存储解决方案中，例如对象数据存储（如 Amazon S3）、数据仓库或其他数据存储。有效的数据摄取模式应同时包含实时流式传输和批量摄取机制，以适应不同类型的数据源并确保及时高效的数据获取。

各种数据摄取技术和工具适用于不同的摄取模式。对于流式数据摄取，流行的选择包括 Apache Kafka、Apache Spark Streaming 和 Amazon Kinesis/Kinesis Firehose。这些工具支持实时数据摄取和处理。另一方面，对于面向批量的数据摄取，通常使用 `Secure File Transfer Protocol` (`SFTP`) 和 AWS Glue 等工具。特别是 AWS Glue，它支持多种数据源和目标，包括 Amazon RDS、MongoDB、Kafka、Amazon DocumentDB、S3 以及任何支持 JDBC 连接的数据库。这种灵活性允许从各种来源无缝摄取数据到所需的数据存储或处理系统。

在决定使用哪些工具进行数据摄取时，根据实际需求评估工具和技术非常重要。以下是决定数据摄取工具时的一些注意事项：

*   `Data format, size, and scalability`: 考虑各种数据格式、数据大小和可扩展性需求。机器学习项目可能使用来自不同来源和不同格式（例如，`CSV`、`Parquet`、JSON/XML、文档或图像/音频/视频文件）的数据。确定基础设施在必要时能否高效处理大量数据，并在数据量低的时期缩减规模以降低成本。

*   `Ingestion patterns`: 考虑需要支持的不同数据摄取模式。该工具或多种工具的组合应支持批量摄取模式（在特定时间间隔传输大量数据）和实时流式传输（实时处理传感器数据或网站点击流等数据）。

*   `Data preprocessing capability`: 评估摄取的数据在存储到目标数据存储库之前是否需要预处理。寻找提供内置处理功能或与外部处理工具无缝集成的工具。

*   `Security`: 确保所选工具为身份验证和授权提供强大的安全机制，以保护敏感数据。

*   `Reliability`: 验证工具是否提供故障恢复机制，以防止在摄取过程中丢失关键数据。如果缺乏恢复功能，请确保有从源重新运行摄取作业的选项。

*   `Support for different data sources and targets`: 所选摄取工具应与多种数据源兼容，包括数据库、文件和流式来源。此外，它们应提供 API 以便轻松摄取数据。

*   `Manageability`: 另一个需要考虑的重要因素是可管理性。该工具是否需要自行管理，还是完全托管的解决方案？在做出决定之前，请考虑成本与运营复杂性之间的权衡。

AWS 提供多种用于将数据摄取到其平台数据湖中的服务。这些服务包括 Kinesis Data Streams、Kinesis Firehose、AWS Managed Streaming for Kafka 和 AWS Glue Streaming，用于满足流式数据需求。对于批量摄取，可选 AWS Glue、SFTP 和 AWS `Data Migration Service` (`DMS`) 等选项。在即将到来的章节中，我们将深入探讨使用 Kinesis Firehose 和 AWS Glue 来管理数据湖的数据摄取流程。我们还将讨论 AWS Lambda（一款无服务器计算服务），作为一种简单轻量的数据摄取替代方案。

### Kinesis Firehose

Kinesis Firehose 是一款简化将流式数据加载到数据湖过程的服务。它是一个完全托管的解决方案，这意味着您无需担心管理底层基础设施。相反，您可以与该服务的 API 交互，以处理数据的摄取、处理和交付。

Kinesis Firehose 为各种可扩展的数据摄取需求提供全面支持，包括：

*   与网站、物联网设备和视频摄像头等多种数据源无缝集成。这是通过使用摄取代理或摄取 API 实现的。

*   将数据交付到多个目标（包括 Amazon S3、Amazon Redshift（AWS 数据仓库服务）、Amazon OpenSearch（托管搜索引擎）和 Splunk（日志聚合和分析产品））的灵活性。

*   与 AWS Lambda 和 Kinesis Data Analytics 无缝集成，提供高级数据处理功能。借助 AWS Lambda，您可以利用无服务器计算来执行用 Python、Java、Node.js、Go、C# 和 Ruby 等语言编写的自定义函数。有关 Lambda 功能的更全面信息，请参阅官方 AWS 文档。

下图说明了 Kinesis Firehose 的数据流：

![](OEBPS/Images/B20836_04_05.png)

图 4.5：Kinesis Firehose 数据流

Kinesis 通过建立传送流来运行，传送流是 Firehose 架构中负责从数据生产者接收流式数据的基础组件。这些传送流可以配置为各种交付目标，例如 S3 和 Redshift。为了适应生产者生成的数据量，您可以通过指定分片数量来调整数据流的吞吐量。每个分片有能力摄取每秒 1 MB 的数据，并可以支持每秒 2 MB 的数据读取速率。此外，Kinesis Firehose 提供 API，用于在需要时增加分片数量并合并分片。

### AWS Glue

