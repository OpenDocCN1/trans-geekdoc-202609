

单击“设置属性”页面底部的“确定”后，将创建数据集，并将其添加为复制活动中的接收器数据集。与 Azure SQL 数据库数据集类似，“接收器”选项卡中有几个与所选数据集类型相关的其他设置。“接收器”选项卡（以及“源”选项卡）还允许你使用“打开”按钮（位于“接收器数据集”设置旁边）打开数据集。此按钮将打开一个新页面，允许你进行特定于数据集类型的多项更改。由于接收器数据集是存储在 ADLS 中的 CSV 数据，可编辑的设置列表包括数据的压缩方式、数据的列和行分隔符、数据的编码方式，以及是否应将第一行视为标题。你还可以使用此页面为数据集定义文件名。[图 5.32](#c05.xhtml#c05-fig-0032) 说明了包含所有可用数据集设置的此页面。

在正确配置数据集设置后，通过单击页面顶部的“管道”选项卡返回到管道。单击“映射”选项卡，将源数据集列映射到接收器列。此选项卡还允许你设置数据类型设置，例如日期/时间格式，以及是否截断长于列定义允许范围的数据。[图 5.33](#c05.xhtml#c05-fig-0033) 是“映射”选项卡的示例。

![FIGURE 5.32 Using the Azure Data Factory Studio to edit a CSV dataset](images/c05f032.png)

[FIGURE 5.32](#c05.xhtml#R_c05-fig-0032) 使用 Azure 数据工厂工作室编辑 CSV 数据集

![FIGURE 5.33 Copy Data Activity: Mapping tab](images/c05f033.png)

[FIGURE 5.33](#c05.xhtml#R_c05-fig-0033) 复制数据活动：映射选项卡

映射源和接收器列后，导航到“设置”选项卡。此选项卡允许你设置要分配给管道的 DIU 数量，或者是否希望管道自动应用最佳数量的 DIU。你还可以设置复制活动将使用的并行度，如果源数据集的数据量需要扩展解决方案。

复制活动中的最后一个选项卡是“用户属性”选项卡。这允许你标记和监视特定 ADF 资源，例如数据集。

单击页面顶部的“全部发布”按钮以保存管道和数据集。要运行管道或计划管道在以后运行，请单击画布顶部的“添加触发器”按钮，并选择“立即触发”以开始管道运行，或选择“新建/编辑”以创建计划或基于事件的触发器。[图 5.34](#c05.xhtml#c05-fig-0034) 说明了“全部发布”和“添加触发器”按钮的位置。发布管道后，单击“触发器”按钮，立即运行管道或创建计划以在以后运行。

![FIGURE 5.34 Using the Publish all button to save the pipeline and datasets.](images/c05f034.png)

[FIGURE 5.34](#c05.xhtml#R_c05-fig-0034) 使用“全部发布”按钮保存管道和数据集。

## 实时 Azure 数据处理服务

虽然前面描述的一组服务可用于各种数据处理任务，但请注意，还有其他用于利基数据处理用例的 Azure 数据服务。例如，Azure 流分析和 Azure 数据资源管理器几乎专用于流处理工作流。这些服务不在 DP-900 考试范围内，仅在以下部分中简要介绍。

### Azure 流分析

Azure 流分析是一种 PaaS 流处理引擎，可用于处理来自多个源的大量流式数据。用户可以通过 Azure 门户、Azure CLI、Azure PowerShell 或基础设施即代码模板（如 ARM）创建 Azure 流分析作业。作业由三个核心组件组成：一个或多个输入、一个查询和一个或多个输出。

输入可以包括实时消息引入服务（如 Azure 事件中心和 Azure IoT 中心）以及持久数据存储（如 Azure Blob 存储和 Azure SQL 数据库）。这使开发人员能够将流式数据与历史数据或用于查找操作的参考数据相结合。

开发人员可以使用流分析查询语言来筛选、排序、聚合或联接来自不同源的数据。这种语言是标准 T-SQL 的子集，具有用于在特定时间窗口上应用计算的附加功能。该语言还可以使用 JavaScript 和 C# 用户定义函数进行扩展。

作业将处理后的信息传递到一个或多个输出。Azure 流分析允许你根据处理的数据结果自定义发生的情况。以下是一些常见输出：

*   服务，例如 Azure 事件中心、Azure 服务总线或 Azure Functions，用于触发警报或自定义工作流

*   Power BI 仪表板，用于实时仪表板

*   持久数据存储，例如 Azure Blob 存储、ADLS、Azure SQL 数据库或 Azure Synapse Analytics 专用 SQL 池，用于长期存储或批处理

如果要了解有关 Azure 流分析的更多信息，请访问 `https://docs.microsoft.com/en-us/azure/stream-analytics/stream-analytics-introduction`。

### Azure 数据资源管理器

Azure 数据资源管理器是一种近实时处理引擎，用于分析跨时间窗口的结构化、半结构化和非结构化数据。它使用 Kusto 查询语言 (KQL) 分析数据，并能够引入和分析 PB 级数据。Azure 数据资源管理器的典型用例包括交互式分析日志以及对 IoT 传感器的指标数据进行时间序列分析。

如果要了解有关 Azure 数据资源管理器的更多信息，请访问 `https://docs.microsoft.com/en-us/azure/data-explorer/data-explorer-overview`。

## 使用 Azure Synapse Analytics 进行端到端分析

Azure Synapse Analytics 是一种企业分析系统，可在单个环境中集成多个服务，用于服务分析工作负载。通过 Azure Synapse 工作区，用户可以利用以下服务构建现代数据仓库解决方案：

*   `Synapse Studio` 是一个统一环境，用户可以在其中管理 Azure Synapse Analytics 生态系统的所有组件。可以使用 `Synapse Studio` 执行以下任务：

    *   构建可自动在预定时间或特定事件后运行的 ETL 和 ELT 工作流。

    *   配置和部署专用 SQL、Apache Spark 和数据资源管理器池。

    *   开发 SQL、Spark 或 KQL 代码，以使用 SQL、Spark 或数据资源管理器池分析数据。

    *   监视 SQL、Spark 或数据资源管理器池之间的资源利用率、查询性能和用户访问情况。

    *   与 CI/CD 和数据目录服务（例如 Azure DevOps 和 Azure Purview）集成。

*   `专用 SQL 池` 是分析数据存储，使用扩展的大规模并行处理 (MPP) 架构有效管理多个 PB 级数据。存储和计算是解耦的，允许用户轻松扩展计算能力，而无需移动数据。Azure Synapse 工作区可以有一个或多个专用 SQL 池。

*   `无服务器 SQL 池` 是一种无服务器查询服务，允许分析师使用 T-SQL 交互式查询 Azure 存储文件。它没有本地存储或引入功能。每个 Azure Synapse 工作区都带有一个无法删除的无服务器 SQL 池终结点。Azure Synapse 工作区仅支持单个无服务器 SQL 池（名为“内置”）。

