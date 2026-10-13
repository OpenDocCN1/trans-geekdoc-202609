

### 4. 在地图上方，点击横幅文本 `You can now automatically manage replication, connectivity, and failover of this database by adding it to a failover group` 横幅。

![Tip](images/tip.png) Azure 门户一直在变化，所以如果你看不到此横幅，请导航到你的虚拟服务器，选择“故障转移组”设置，然后单击“添加组”。

### 5. 按如下方式完成“故障转移组”配置边栏选项卡：

*   **读/写故障转移策略：** 选择“自动”。
*   **读/写宽限期(小时)：** 此设置是 Azure 在数据丢失可能发生时，自动故障转移到辅助数据库之前等待的时间量。此处的决定在于设置一个足够短的宽限期以维护你的服务级别协议，但又不能长到导致不必要的服务拒绝。

### 6. 单击“创建”将部署提交给 Azure 资源管理器。

![Technical stuff](images/technicalstuff.png) 虽然这些步骤将 Azure 配置为自动故障转移数据库，但你负责更改应用程序源代码中的连接字符串以指向辅助实例。Azure 可能很聪明，但没聪明到那种程度。要获取数据库的连接字符串，请在 Azure 门户中打开数据库的设置并浏览到“连接字符串”边栏选项卡。

[图 9-6](#c09.xhtml#c09-fig-0006) 显示了一个已完成的异地复制配置。

#### 配置

“配置”边栏选项卡是你可以更改服务层级的地方。如果你使用 DTU，可以在“基本”、“标准”和“高级”级别之间切换。你也可以在 DTU 和 vCore 购买模型之间切换。

![FIGURE 9-6: Georeplicated Azure SQL database with automatic failover configured in less than 5 minutes.](images/9781119612148-fg0906.png)

[图 9-6：](#c09.xhtml#rc09-fig-0006) 在 5 分钟内配置了自动故障转移的异地复制 Azure SQL 数据库。

### 检查虚拟服务器

此过程可帮助你了解新 SQL 数据库与其父虚拟服务器之间的关系。请遵循以下步骤：

1.  **导航到 SQL 数据库的“概述”页面。**
2.  **在“要点”窗格上，单击“服务器名称”超链接。**

    ![Tip](images/tip.png) 虚拟服务器名称位于 `database.windows.net` 公共 DNS 区域中。

3.  **在“设置”列表中进行以下选择：**
    *   **SQL 数据库：** 你应该能看到你的数据库，以及其状态和当前定价层。
    *   **管理备份：** Azure 默认会备份你的数据库。你可以选择你的数据库并单击“配置保留”以调整 Azure 备份数据库的频率，以及它保留每日（时间点还原）、每周、每月和每年备份的时长。
    *   **DTU 配额：** 此设置显示你的数据库在当前（每月）Azure 计费周期中消耗了多少资源。

### 连接到数据库

要连接到 SQL 数据库，你需要下载并安装 SQL Server Management Studio ([`https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017`](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017))，这是免费的 SQL Server/Azure SQL 数据库管理界面。安装该产品后，请遵循以下步骤：

1.  **在数据库的“概述”边栏选项卡上，复制虚拟服务器的域名服务 (DNS) 名称。**
2.  **启动 SQL Server Management Studio 并使用管理用户帐户进行身份验证。**

    你需要填写以下信息：

    *   **服务器名称：** 格式为 `<server-name>.database.windows.net` 的虚拟服务器名称
    *   **身份验证：** SQL Server 身份验证

        ![Tip](images/tip.png) 如果你已配置 Azure Active Directory 身份验证，则可以使用它。你将在 [第 11 章](#c11.xhtml) 中了解 Azure AD。

    *   **登录名/密码：** 你为虚拟服务器定义的管理凭据

3.  **展开“数据库”容器，并选择 Adventure-Works 数据库。**
4.  **选择“文件”⇒“来自当前连接的新查询”。**

    将出现一个新的空白 SQL 查询窗口。

5.  **在查询窗口中，键入以下 Transact-Structured Query Language (T-SQL) 查询：**

    ```
    SELECT TOP (10) [CustomerID] ,[Title] ,[FirstName] ,[LastName] ,[CompanyName] FROM [SalesLT].[Customer]
    ```

6.  **选择该查询，然后单击 SQL 编辑器工具栏上的“执行”。**

    或者，你可以右键单击选定的查询，然后从快捷菜单中选择“执行”。

    [图 9-7](#c09.xhtml#c09-fig-0007) 显示了查询的结果。

![FIGURE 9-7: Querying an Azure SQL Database.](images/9781119612148-fg0907.png)

[图 9-7：](#c09.xhtml#rc09-fig-0007) 查询 Azure SQL 数据库。

## 实现 Azure Cosmos DB

关系数据库的核心在于*模式*，即结构。我常说，要成为一名关系数据库管理员，你应该是一名微观管理者，因为每一行数据都需要受到严格约束以适应表、关系和数据库模式。

尽管关系数据库提供了出色的数据一致性，但由于所有模式开销，它们往往在可扩展性方面表现不佳。非关系数据库应运而生。

与其称非关系数据库为*无模式*，不如说 NoSQL 数据库具有灵活的模式更为准确。乍一看，你可能会认为灵活的模式会使查询几乎不可能。但 NoSQL 数据库可以通过跨多个群集节点对数据集进行分区，并将原始计算能力应用于查询执行来克服这一障碍。

![Technical stuff](images/technicalstuff.png) *NoSQL* 通常被理解为 *not only SQL*（不仅仅是 SQL）。

### 了解 Cosmos DB

Cosmos DB（最初称为 Document DB）是 Azure 的多模型、异地复制、非关系数据存储。你可以结合使用 Cosmos DB，或将其用于替代关系数据库系统。

以下部分将带你了解 Cosmos DB 的功能。

#### 多模型

最初 Document DB 是一个 JavaScript Object Notation (JSON) 文档模型 NoSQL 数据库。然而，Microsoft 希望拥抱更广泛的客户群，因此推出了 Cosmos DB，它支持五种数据模型/应用程序编程接口 (API)：

*   **核心 (SQL)：** 此 API 是原始 Document DB 的继任者。数据存储由 JSON 文档组成，核心 API 提供了一个类 SQL 查询语言，关系数据库管理员和开发人员应该会立即感到得心应手。
*   **用于 MongoDB API 的 Azure Cosmos DB：** 此 API 支持 MongoDB 线路协议。MongoDB 也是一个 JSON 文档存储，它允许你像查询 MongoDB 实例一样查询 Cosmos DB。
*   **Cassandra：** 此 API 与 Cassandra 宽列存储数据库兼容，并支持 Cassandra 查询语言。
*   **Azure 表：** 此 API 指向 Azure 存储帐户的表服务。它是一个键/值数据存储，你可以使用 ARM 的表述性状态传输 (REST) API 进行访问。
*   **Gremlin (图)：** 此 API 支持基于图的数据视图和 Apache Gremlin 查询语言。

你是否看到了一个主题？其理念是，几乎任何需要 NoSQL 数据存储的开发人员都应该能够使用 Cosmos DB，而无需牺牲原始源代码或客户端工具。

#### 一站式全球分发

只需几次鼠标点击，你就可以指示 Azure 将 Cosmos DB 数据库复制到任意数量的 Azure 区域，以将数据置于靠近用户的位置。

![Technical stuff](images/technicalstuff.png) Cosmos DB 使用多主复制方案，为读取和写入操作提供 99.999% 可用性服务级别协议。

#### 多种一致性级别

