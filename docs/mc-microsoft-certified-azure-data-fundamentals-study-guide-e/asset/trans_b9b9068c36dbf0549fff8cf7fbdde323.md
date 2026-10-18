

4. Azure 使用自动备份为 Azure SQL 托管实例管理备份。在第一个 Azure SQL 托管实例上使用不同的名称，对两天前的数据库备份执行时间点还原。然后，使用 Azure 数据同步将还原的数据库从第一个 Azure SQL 托管实例复制到第二个。

16. 适用于 Azure SQL 数据库的常规用途服务层使用哪种购买模型？

1. `vCore-based`
2. `DTU-based`
3. `DWU-based`
4. `DBU-based`

17. 以下语句中斜体部分是正确的，还是需要替换为下面出现的其他片段之一？“*Azure Database for MySQL* 提供三种部署模型，包括使用横向扩展架构支持大型 OLTP 工作负载的超大规模部署模型。”

1. `Azure Database for MariaDB`
2. `Azure Database for PostgreSQL`
3. `Azure Database for HBase`
4. 无需更改

18. 从本地计算机或 VM 运行 Azure PowerShell 脚本时，必须在脚本开头运行以下哪个 Azure PowerShell 命令以与 Azure 环境建立连接？

1. `Connect-AzSession`
2. `Connect-AzAccount`
3. `Connect-AzureRmAccount`
4. `Connect-AzureRmSession`

19. 你正在设计一个 Azure Synapse Analytics 专用 SQL 池数据仓库，它将用作电子商务公司的单一事实来源。有几个大型事实表，每个表都包含用于标识每行的列。这些列具有许多不同的值。以下哪种表分布设计最适合这些事实表？

1. 轮询
2. 复制表
3. 哈希
4. 广播

20. Azure 用于管理 Azure SQL 数据库部署的资源提供程序和资源类型组合是以下哪个？

1. `Microsoft.Sql/managedInstances`
2. `Microsoft.Sql/databases`
3. `Microsoft.Sql/servers`
4. `Microsoft.Sql/servers/databases`

21. 可以使用哪个 Azure PowerShell 命令创建新的 Azure SQL 数据库？

1. `New-AzSqlDatabase`
2. `Create-AzSqlDatabase`
3. `New-AzRmSqlDatabase`
4. `Create-AzRmSqlDatabase`

22. 以下哪个 RBAC 角色允许用户创建和管理数据库，但不授予访问权限？选择授予用户最少权限的选项。

1. Azure Active Directory 管理员
2. SQL DB 参与者
3. SQL 安全管理器
4. 参与者

23. 你正在设计一个应用程序，该应用程序将向 Web 应用程序提供高度敏感的信息。数据必须加密，以便只有应用程序可以解密数据，防止数据库管理员查看原始值。以下哪个选项是加密存储此敏感信息的列的最佳选择？

1. 动态数据掩码
2. 使用 `DENY` 语句拒绝访问列
3. Always Encrypted
4. 透明数据加密

24. 哪个数据库管理工具最适合执行管理任务，例如管理用户权限、优化查询和构建 HADR 解决方案？

1. Azure Data Studio
2. Azure PowerShell
3. Azure 门户
4. SQL Server Management Studio

25. 你是一家大型电子商务公司的数据库管理员。一名开发人员在连接到你管理的某个 Azure SQL 数据库时遇到问题，并向你寻求帮助。SSMS 中的错误消息指示登录失败，并指出用户无法打开“master”数据库。你得知该开发人员正在使用包含的数据库用户登录到数据库。你应该告诉开发人员采取什么步骤来修复此问题？

1. 将 SSMS 登录屏幕上的数据库上下文从 *default* 更改为用户有权访问的数据库。
2. 使用 SQL 管理员凭据登录到逻辑服务器以访问数据库。
3. 使用 AAD 帐户登录到数据库。
4. 为 SQL 实例启用 TCP/IP。

26. `CREATE TABLE` 语句属于哪类 SQL 语句？

1. DML
2. DDL
3. DCL
4. TCL

27. Azure Defender for SQL 的哪个组件会向用户发出恶意活动（例如 SQL 注入和数据外泄）的警报？

1. SQL 审核
2. 漏洞评估
3. SQL Server 扩展事件
4. 高级威胁防护

28. 可以使用哪个 T-SQL 语句将 Azure Active Directory 用户或组添加为 Azure SQL 数据库的用户？

1. `CREATE EXTERNAL PROVIDER AAD; CREATE USER \[<AAD\_User>\] FROM AAD;`
2. `CREATE USER \[<AAD\_User>\] FROM EXTERNAL PROVIDER;`
3. `CREATE USER \[<AAD\_User>\] FROM EXTERNAL SERVICE;`
4. `CREATE USER \[<AAD\_User>\]`

29. 在 T-SQL SELECT 语句的逻辑处理顺序中，以下哪个步骤排在第一位？

1. `FROM`
2. `GROUP BY`
3. `ORDER BY`
4. `SELECT`

30. 以下哪个是用于定义可变大小字符串数据的 Unicode 数据类型？

1. `VARCHAR()`
2. `NVARCHAR()`
3. `CHAR()`
4. `NCHAR()`

31. 以下语句中斜体部分是正确的，还是需要替换为下面出现的其他片段之一？“A(n) *Full Join* 是一种用于检索同时满足连接条件的两个表数据的连接类型。”

1. Full inner join
2. Inner join
3. Outer join
4. 无需更改

# 第 3 章

## Azure 中的非关系型数据库

非关系型数据库，通常也称为 NoSQL 数据库，允许用户存储和查询非关系型数据，而无需将其调整以适应预定义的架构。NoSQL 数据库通常用于需要快速摄入和读取数据的场景，例如游戏、电子商务、IoT 和移动应用程序。NoSQL 数据库的主要类别包括键值、文档、列式和图形。本章将讨论不同类别的 NoSQL 数据库、如何使用 Azure Cosmos DB 实现它们，以及 Azure 中 NoSQL 数据库的基本管理任务。

### 非关系型数据库功能

在过去几年中，数据驱动型应用程序的兴起迫使组织重新思考如何存储数据。大量形状和大小各异的数据需要在近乎实时的情况下被捕获，这使得组织几乎不可能对所有数据存储需求都使用传统的关系型模型。此外，云计算的出现使组织能够轻松且廉价地在不同地理区域横向扩展其数据存储解决方案。这使组织能够以其自然格式存储数据，而无需先应用复杂的数据规范化规则。出于这些原因，NoSQL 数据库已成为需要动态数据存储解决方案的软件开发人员的热门选择。

NoSQL 数据库不强制数据适应严格的架构，而是使用针对所存储数据的要求进行优化的存储模型。无需过多关注数据库管理，使软件开发人员能够以更敏捷的方法构建应用程序，从而更快地适应不断变化的需求。

虽然有几种类别的 NoSQL 数据库，但它们共享以下特征：

* ACID 原则的实现模糊不清。这对于处理大量数据且速度非常快的事务性工作负载是有益的。
* 由于数据之间没有关系，因此可以轻松地在多个分区和存储设备上横向扩展，允许数据存储在任何位置。

