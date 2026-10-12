

# Google BigQuery 架构

Google BigQuery 架构建立在 **Dremel** 之上，Dremel 是 Google 设计的一种分布式系统，用于查询海量数据库。在 Dremel 中，查询的执行被分解为 **槽位**，即使众多用户并发搜索数据库，也能保证公平性。在底层，Dremel 使用 **Jupiter**（Google 的内部数据中心网络）来访问分布式文件系统（昵称为 **Colossus**）上的数据存储。Jupiter 也是 Google Cloud Storage 的骨干网络。数据复制、数据恢复和数据分发管理均由 Colossus 处理。BigQuery 对其数据采用 **列式存储结构**，从而实现了高压缩比和高扫描吞吐量。另一方面，您也可以将 BigQuery 与存储在其他 Google Cloud 服务中的数据配合使用，例如 **Bigtable**、**Cloud Storage**、**Cloud SQL** 和 **Google Drive**。

得益于专为处理海量数据而设计的架构，当 BigQuery 获取数 PB 信息进行评估时，性能达到峰值。BigQuery 最适合人们需要对只读数据集进行交互式临时查询的用例。在大多数情况下，针对关系数据库的复杂分析查询需要运行数秒。这正是使用 BigQuery 的理想场景，这也是为什么它常被用在大数据 ETL 流水线的末端、处理过的数据之上。由于自带缓存，BigQuery 在数据不发生频繁变更的情况下表现非常出色。

由于它是一项完全托管的服务，无需安装、设置或维护任何底层基础设施即可正常运行。客户仅为其存储的数据量和对数据库运行的查询次数付费。

# 使用 BigQuery

## 步骤 1：打开 BigQuery

按照 [图 1.43](#ch01.xhtml#fig1-43) 中描述的步骤打开 BigQuery：

![](images/Figure_1.43.png)

**图 1.43：BigQuery**

1.  用户可在搜索框中输入 `BigQuery`。
2.  或者，他们可以在 **Analytics** 下导航至 `BigQuery | SQL workspace`。

## 步骤 2：BigQuery 登录页面

BigQuery 的登录页面如 [图 1.44](#ch01.xhtml#fig1-44) 所示：

![](images/Figure_1.44.png)

**图 1.44：BigQuery 登录页面**

1.  点击 **SQL workspace** 以创建和运行查询、处理表以及查看作业历史。
2.  **BigQuery Data Transfers Service** 可将数据按计划、受控地自动传输到 BigQuery 中。
3.  **Scheduled queries** 选项用于定期运行查询。查询需采用标准 SQL 编写。
4.  **Analytics Hub** 有助于跨组织高效、安全地传输数据资产。
5.  **SQL translation** 帮助用户将 SQL 方言转换为 BigQuery 标准 SQL 查询。
6.  BigQuery 的 **Performance monitoring** 信息和日志数据可在 **Monitoring** 部分下获取。
7.  **Capacity management** 基于历史利用率信息协助进行容量规划。
8.  **BI Engine** 是一项内存分析服务。
9.  **ADD DATA** 提供从各种来源导入数据的选项，包括公共和私有数据集。
10. **Editor window** 用于编写查询以获取数据。
11. 列出已创建的 **Projects**（显示 Project ID 而非项目名称）。点击三个点并选择 **Create data set**。

## 步骤 3：BigQuery 数据集创建

我们使用的是 Kaggle 上列在公共领域许可下的数据集。您可以将数据以 csv 格式下载到本地机器。

[https://www.kaggle.com/datasets/jimschacko/airlines-dataset-to-predict-a-delay](https://www.kaggle.com/datasets/jimschacko/airlines-dataset-to-predict-a-delay)

按照 [图 1.45](#ch01.xhtml#fig1-45) 中描述的步骤在 BigQuery 中创建数据集：

![](images/Figure_1.45.png)

**图 1.45：BigQuery 数据集创建**

1.  选择项目。数据集将在所选项目下创建。
2.  **Data set ID**：数据集的名称。
3.  **Data location**：选择位置。
4.  **Enable table expiry**：如果选中此选项，则创建的任何表将在用户在框中指定的天数后被删除。
5.  **Advanced options**：用于加密，以在 Google 托管或客户托管加密之间进行选择。
6.  点击 **CREATE DATA SET**。

## 步骤 4：表创建

按照 [图 1.46](#ch01.xhtml#fig1-46) 中描述的步骤在数据集下创建表：

![](images/Figure_1.46.png)

**图 1.46：数据集中的表创建**

1.  创建的数据集将列在所选项目下。
2.  选择 **Create table** 以导入数据。

## 步骤 5：表的数据选择

按照 [图 1.47](#ch01.xhtml#fig1-47) 中描述的步骤将数据上传到 BigQuery：

![](images/Figure_1.47.png)

**图 1.47：将数据上传到 BigQuery 表**

1.  可通过从本地机器、**Google Cloud Storage**、**Google Drive**、**Google Bigtable**、**Amazon S3 bucket**、**Azure blob storage** 上传数据来创建表。
    本示例中，数据已下载到本地机器，选择从本地机器上传的选项。选中上传选项后，BigQuery 提供选择文件及文件格式（csv）的选项。
2.  **Project**：创建数据集所在的项目。
3.  **Dataset Name**：需在其下创建表的数据集。
4.  输入需创建的表的名称。
5.  **Table type**：Native type 是唯一选项；原生表是由原生 BigQuery 存储支持的表。
6.  **Edit schema**：用户可启用此选项以手动输入数据的架构。（选中数据后，自动检测选项将被启用）。
7.  **Partition**：分区将表划分为更小的段。将创建分区列，可对分区列使用过滤条件以减少扫描数据所需的时间。
8.  **Clustering** 根据架构中指定列的内容组织数据。
9.  **Encryption** 选项在 **Advanced options** 下提供。
10. 点击 **create Table**。

## 步骤 6：在 BigQuery 表上运行查询

按照 [图 1.48](#ch01.xhtml#fig1-48) 中描述的步骤在上传的数据上运行 SQL 查询：

![](images/Figure_1.48.png)

**图 1.48：用于获取数据的 SQL 查询**

1.  创建的表名将显示在所选数据集下。
2.  在 **SQL editor** 中，用户可编写查询并点击 **Run** 执行。示例使用的查询如下：

```
Select * from `vertex-ai-gcp.flight_delay_prediction.delay_table`
Where AirpottFrom = "ATL"
LIMIT 10
```

`vertex-ai-gcp` 是项目名称，`flight_delay_prediction` 是数据集名称，`delay_table` 是表名称。

3.  查询结果显示在 **Query results** 部分。**JOB INFORMATION** 提供关于作业 ID、耗时、位置等信息。
4.  查询结果以表结构显示在 **RESULTS** 部分。
5.  查询结果以 JSON 结构显示。
6.  **Execution details** 包含处理的数据量、执行消耗的槽位时间等信息。
7.  **SAVE RESULTS** 提供将结果保存为 CSV、JSON 或 BigQuery 表的选项。
8.  **EXPLORE DATA** 提供使用数据工作室（可视化工具）探索数据的选项。
9.  **SAVE** 选项提供保存查询以供后续使用的选项。
10. **Schedule** 提供安排查询的选项。
11. **MORE** 提供格式化查询、SQL 翻译等选项。

## 步骤 7：数据集删除

按照 [图 1.49](#ch01.xhtml#fig1-49) 中描述的步骤删除数据集：

![](images/Figure_1.49.png)

**图 1.49：BigQuery 数据集删除**

1.  点击三个点并选择 **Delete**。弹出窗口将要求确认。

# 身份和访问管理

