

密钥配置错误或未正确复制。只需重新复制主密钥或切换到辅助密钥即可解决此问题。

应用程序在尝试执行写入操作时使用的是只读密钥。如果应用程序应获授权以创建或删除数据，请将密钥切换为读写密钥。

应用程序尝试在容器创建完成之前访问该容器。这种情况通常发生在容器被删除，然后使用相同名称重新创建时。

#### 禁止异常

当来自应用程序的数据平面请求的 IP 地址未被 Azure Cosmos DB 防火墙加入白名单，或无法与 Azure Cosmos DB 关联的 VNet 通信时，会发生禁止异常。这些异常由 403 状态代码表示。

此错误的解决方案取决于应用程序请求是否来自可以与 Azure Cosmos DB 通信的 IP 地址。它们还取决于帐户使用的网络隔离类型。如果应用程序请求来自预期路径，请使用以下建议：

*   如果 Azure Cosmos DB 帐户使用防火墙，请检查以确保请求的 IP 地址已在 Azure Cosmos 防火墙中加入白名单，或来自启用了 Azure Cosmos DB 服务终结点的子网。

*   如果 Azure Cosmos DB 帐户使用私有终结点，请确保请求的 IP 地址可以与私有终结点关联的 VNet 通信。

如果应用程序请求不是来自预期路径，则问题可能与应用程序端配置有关。请根据帐户使用的网络隔离类型，使用以下指南来排查问题：

*   如果应用程序请求预期应使用服务终结点，但改为使用公共 Internet，请检查应用程序 IP 地址所在的子网是否已启用 Azure Cosmos DB 服务终结点。

*   如果应用程序请求预期应通过私有终结点，但改为来自公共 Internet，请检查应用程序使用的 DNS 是否可以将帐户终结点解析为与私有终结点关联的私有 IP 地址。

### 管理工具

Azure 提供了两个 Azure Cosmos DB 管理工具，开发人员可以使用它们在将查询添加到应用程序之前编写和测试查询。Data Explorer 和 Azure Cosmos DB Explorer 为开发人员和管理员提供了创建新资源和管理现有资源的能力，以及优化吞吐量的成本性能比。以下部分将详细介绍每个工具。

#### Data Explorer

Data Explorer 是 Azure 门户中可用的开发环境，用于查询和管理 Azure Cosmos DB。它可以用于创建和删除数据库、容器、存储过程、用户定义函数和触发器等资源。开发人员可以使用查询窗口（类似于 SSMS 和 Azure Data Studio 中的窗口）来编写读取、写入或删除数据的 SQL 语句。

管理员也可以利用 Data Explorer 来管理 Azure Cosmos DB。诸如缩放吞吐量、修改索引策略和设置生存时间（TTL）周期等任务可以使用 Data Explorer 来处理。

#### Azure Cosmos DB Explorer

Azure Cosmos DB Explorer 是 Data Explorer 工具的全屏扩展。它提供相同的功能，例如创建新帐户对象、编写查询和缩放吞吐量。但是，与 Data Explorer 不同，Azure Cosmos DB Explorer 可以在 Azure 门户之外使用。连接到 Azure Cosmos DB 帐户的用户只需要使用与帐户一起生成的读写密钥或只读密钥之一。这使管理员能够限制谁可以修改数据，同时仍为开发人员提供易于使用的开发环境。

使用以下步骤从 Azure 门户打开 Azure Cosmos DB Explorer：

1.  转到先前创建的 Azure Cosmos DB 帐户，然后单击 Data Explorer。

2.  单击 Data Explorer 边栏选项卡最右侧的“打开全屏”图标。[图 3.15](#c03.xhtml#c03-fig-0015) 显示了可以找到此图标的位置。

    ![FIGURE 3.15 Azure Cosmos DB Explorer Open Full Screen icon](images/c03f015.png)

    [FIGURE 3.15](#c03.xhtml#R_c03-fig-0015) Azure Cosmos DB Explorer Open Full Screen icon

3.  单击此图标后，您将看到两个 URL 选项：`Read and Write` 和 `Read Only`。您可以复制其中一个链接，或单击“打开”按钮在单独的浏览器选项卡中打开 Azure Cosmos DB Explorer。[图 3.16](#c03.xhtml#c03-fig-0016) 说明了此弹出页面的外观。

    ![FIGURE 3.16 Azure Cosmos DB Explorer pop-up screen](images/c03f016.png)

    [FIGURE 3.16](#c03.xhtml#R_c03-fig-0016) Azure Cosmos DB Explorer pop-up screen

4.  打开 Azure Cosmos DB Explorer 后，您将看到与 Data Explorer 相同的界面。

## 摘要

本章介绍了 NoSQL 数据库，包括键值、文档、列式和图数据库。虽然它们专注于不同的场景，但确实共享一些共同特征。这些特征包括 ACID 原则的模糊实现、灵活的架构设计以及水平扩展的能力。

Azure Cosmos DB 是一个完全托管、高可用的 PaaS NoSQL 数据库，为每种类型的 NoSQL 数据存储提供多个数据库 API，包括 Azure Cosmos DB 表 API、Azure Cosmos DB Core (SQL) API、Azure Cosmos DB API for MongoDB、Azure Cosmos DB Cassandra API 和 Azure Cosmos DB Gremlin API。这些 API 中每个都至少提供 99.99% 的 SLA，并可以轻松复制到世界各地的不同区域。Azure Cosmos DB 允许用户从五个不同的一致性模型中进行选择，以平衡一致性、可用性和性能之间的权衡。

在 Azure Cosmos DB 中，计算以读取和写入数据所需的吞吐量来衡量。吞吐量表示为每秒请求单位（`RU/s`）。`RU/s` 可以在数据库和容器级别设置，方法是预配专用的 `RU/s` 数量，或设置数据库或容器可以缩放到的最大 `RU/s` 数量。还有一个无服务器选项，允许 Azure Cosmos DB 根据工作负载使用所需的任意数量的 `RU/s`。

就像 Azure 中的关系数据库一样，Azure Cosmos DB 可以在 Azure 门户中手动部署，也可以使用脚本或基础设施即代码模板进行自动化部署。存储在 Cosmos DB 中的数据也在多个层级上受到保护，原生加密静态数据和传输中的数据，并提供灵活的网络隔离和访问管理选项。

本章最后介绍了可用于管理和查询 Azure Cosmos DB 的两个主要管理工具：Data Explorer 和 Azure Cosmos DB Explorer。Data Explorer 可以在 Azure 门户中访问。Azure Cosmos DB Explorer 是一个独立的 Web 应用程序，提供与 Data Explorer 相同的选项和界面，通常由无权访问 Azure 门户的开发人员使用。

## 考试要点

*   描述 NoSQL 数据库的特征。由于近年来数据量在更快的速度下产生，NoSQL 数据库变得越来越流行。敏捷开发标准的出现和存储成本的降低也使软件开发人员能够更有能力使用提供更多动态存储选项的数据库平台。

    不同 NoSQL 数据库类别之间的共同特征包括架构灵活性、对 ACID 原则的模糊解释以及水平扩展的能力。

