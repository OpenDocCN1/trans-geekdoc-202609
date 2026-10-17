

就像专用 SQL 池一样，无服务器 SQL 池支持几种与 Microsoft SQL 产品套件常见的管理任务和工具。开发人员可以选择从 Synapse Studio 或通过常见客户端工具（如 Azure Data Studio 和 SQL Server Management Studio (SSMS)）针对无服务器 SQL 池终结点运行临时查询。此外，数据库管理员可以使用 SQL 身份验证和 Azure AD 来管理身份验证和授权。

虽然无服务器和专用 SQL 池都利用旨在管理大型数据集的分布式处理架构，但何时使用哪一个取决于用例要求和可接受的成本与性能阈值。无服务器 SQL 池使用按查询付费的成本模型，仅对每个查询处理的数据量向用户收费。这种成本模型为无服务器 SQL 池提供了一种廉价的替代方案，可用于通过临时查询快速分析数据。但是，由于存储不在无服务器 SQL 池本地且计算会自动缩放，查询的运行速度往往比针对专用 SQL 池执行的查询要慢（慢几秒或几分钟）。出于此原因，专用 SQL 池是需要优化且一致的性能要求的工作负载的更好选择。

## 使用无服务器 SQL 池进行探索性分析

Synapse Studio 使通过创建新的 SQL 脚本来开始使用无服务器 SQL 池分析数据变得容易。为此，请单击左侧工具栏上的 Develop 按钮，然后单击 + 图标。选择 `SQL script` 以打开新的 SQL 脚本窗口。在脚本窗口中，您可以编写使用无服务器 SQL 池或与工作区关联的专用 SQL 池之一的 SQL 脚本。脚本窗口右侧的属性窗格允许您重命名脚本并添加描述，以解释脚本的功能。您还可以通过单击脚本窗口顶部的 Publish All 将脚本保存在 Synapse Studio 或关联的 Git 存储库中。[Figure 5.47](#c05.xhtml#c05-fig-0047) 说明了 SQL 脚本窗口的布局。

![FIGURE 5.47 Synapse Studio SQL script window](images/c05f047.png)

[FIGURE 5.47](#c05.xhtml#R_c05-fig-0047) Synapse Studio SQL script window

SQL 脚本窗口顶部的功能区包括运行脚本、查看查询执行计划（仅限专用 SQL 池）、连接到 SQL 池以及设置数据库上下文的几个选项。要使用无服务器 SQL 池终结点执行查询，请确保在 Connect To 下拉菜单中选择了“Built-in”SQL 池（请参阅 [Figure 5.48](#c05.xhtml#c05-fig-0048)）。

![FIGURE 5.48 Choosing the Built-in SQL pool](images/c05f048.png)

[FIGURE 5.48](#c05.xhtml#R_c05-fig-0048) Choosing the Built-in SQL pool

在介绍如何在 Synapse Studio 中运行查询之前，让我们简要讨论一下无服务器 SQL 池查询的基本结构。执行探索性分析的无服务器 SQL 池查询严重依赖 `OPENROWSET` 函数来从外部存储设备读取数据。例如，以下查询使用 `OPENROWSET` 函数检索公开可用的纽约市黄色出租车数据集的前 100 条记录。

```
SELECT TOP 100 * FROM
OPENROWSET(
    BULK 'https://azureopendatastorage.blob.core.windows.net/
nyctlc/yellow/puYear=*/puMonth=*/*.parquet',
    FORMAT='PARQUET'
) AS [nyc]
```

`BULK` 参数指定数据的位置，而 `FORMAT` 指定正在读取的数据的文件格式。查询使用的 URL 位置还使用通配符（`*`）来读取所有年份和月份文件夹中的所有 Parquet 文件。

此查询还使用 Parquet 文件中的列元数据来推断结果集的列名和数据类型。如果存在标题行，查询还可以自动推断 CSV 文件的列名。但是，有时您希望显式定义架构以更好地控制数据。显式定义架构还允许您指定要从文件中读取哪些列。您可以通过在 `OPENROWSET` 命令末尾添加带有列名和数据类型的 `WITH` 子句来为数据定义架构。以下示例使用 `WITH` 子句从纽约市黄色出租车数据集中显式返回三列。

```
SELECT TOP 100 * FROM
OPENROWSET(
    BULK 'https://azureopendatastorage.blob.core.windows.net/
nyctlc/yellow/puYear=*/puMonth=*/*.parquet',
    FORMAT='PARQUET'
) WITH (
    tpepPickupDateTime DATETIME2,
    passengerCount INT,
    tripDistance FLOAT
) AS [nyc]
```

将整个存储 URL 传递给 `BULK` 参数是使用基本身份验证方法（例如用于 Azure AD 登录的 Azure AD 身份验证）或从公开可用的文件读取文件内容的快速简便方法。但是，此选项提供的身份验证选项有限，并且可能会变得繁琐，因为它迫使开发人员在查询存储帐户时将存储 URL 添加到 `BULK` 参数中。更可重复且更安全的选项是将位置作为外部数据源，并将访问凭据作为无服务器 SQL 池逻辑数据库中的外部作用域凭据进行持久化。

以下示例创建一个新的逻辑数据库和一个引用纽约市黄色出租车数据集位置的外部数据源。然后，您可以将外部数据源名称传递给 `OPENROWSET` 命令中的可选 `DATA_SOURCE` 参数。这样，您可以将传递给 `BULK` 参数的参数更改为仅需查询的文件夹路径。

```
CREATE DATABASE dp900_serverlessdb;

USE dp900_serverlessdb
GO;
CREATE EXTERNAL DATA SOURCE nyc_yellowcab
WITH
(
    location = 'https://azureopendatastorage.blob.core.windows.net/
nyctlc/yellow/'
);

SELECT TOP 100 * FROM
    OPENROWSET(
        BULK 'puYear=*/puMonth=*/*.parquet',
        DATA_SOURCE='nyc_yellowcab',
        FORMAT='PARQUET'
    ) WITH (
        tpepPickupDateTime DATETIME2,
        passengerCount INT,
        tripDistance FLOAT
    ) AS [nyc]
```

可以通过单击窗口顶部的 Run 按钮在 Synapse Studio SQL 脚本窗口中执行此脚本。[Figure 5.49](#c05.xhtml#c05-fig-0049) 显示了 SQL 脚本窗口和执行脚本的结果。

![FIGURE 5.49 Executing Serverless SQL Pool Queries in Synapse Studio](images/c05f049.png)

[FIGURE 5.49](#c05.xhtml#R_c05-fig-0049) Executing Serverless SQL Pool Queries in Synapse Studio

有关如何使用 `OPENROWSET` 通过无服务器 SQL 池查询外部数据的更多信息，请参阅 `https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/develop-openrowset`。

## 摘要

本章首先讨论了不同类型的数据工作流。事务系统（也称为在线事务处理 (OLTP) 系统）捕获业务交易，例如销售点系统中的销售。它们针对写密集型工作负载进行了优化，通常每天处理数百万笔交易。分析系统与事务系统不同，它们针对读密集型操作进行了优化。数据从多个源系统收集并整合到一个或几个数据存储中，用户可以使用这些数据存储进行报告、临时分析和数据科学项目。

分析系统可以批量处理数据，也可以作为连续的数据流进行处理。批处理涉及在预定的时间段或指定事件后处理大量数据。流处理在数据生成时实时摄取和转换数据。像 Lambda 架构这样的现代数据架构使在同一解决方案中同时使用批处理和流处理变得容易。

