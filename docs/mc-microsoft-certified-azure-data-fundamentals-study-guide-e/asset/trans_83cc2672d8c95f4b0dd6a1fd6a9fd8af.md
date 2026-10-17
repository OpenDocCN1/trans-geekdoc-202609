

Azure 中关系数据库的访问管理围绕 `least-privilege`（最小权限）概念展开。这始于 Azure 基础设施层面的基于角色的访问控制（`RBACs`），允许组织仅限制那些需要此类访问权限的用户来管理在 Azure 中处理的数据库操作，例如更改维护窗口和缩放计算资源。下一步是将数据库访问权限限制为仅需要访问权限的用户，也称为数据库身份验证。最后，能够对数据库进行身份验证的用户需要被授予数据库中数据和对象的不同权限级别，这些权限应设置为用户所需的最小权限量。这称为用户的授权级别。以下各部分将探讨这些不同的访问管理级别。

## 基于角色的访问控制 (RBAC)

通过 Azure 处理的关系数据库的管理操作（例如网络隔离、缩放计算资源和更改维护窗口）通过 `RBAC` 进行控制。`RBAC` 是构建在 `ARM` 之上的授权系统，为 Azure Active Directory 中的用户和对象提供 Azure 资源的精细访问管理。需要注意的是，`RBAC` 与数据库级别的安全性是解耦的，因此这些角色不影响数据库访问。

较高级别的 `RBAC` 角色（例如 `Owner` 和 `Contributor`）可用于管理 SQL 资源，但会授予可能不必要的额外权限。有专门针对 Azure SQL 的内置 `RBAC` 角色，可以授予 Azure Active Directory 帐户，从而无需为管理 Azure SQL 资源使用较高级别的角色。PaaS 关系数据库包括以下内置角色：

*   `SQL DB Contributor`—允许用户管理 Azure SQL 数据库，但不允许访问它们。此外，此角色不允许用户管理安全相关策略或其关联的逻辑服务器。

*   `SQL Managed Instance Contributor`—允许用户管理 Azure SQL 托管实例和所需的网络配置，但不允许访问它们。

*   `SQL Security Manager`—允许用户管理 Azure SQL 数据库和管理数据库的逻辑服务器的安全相关策略，但不允许访问它们。

*   `SQL Server Contributor`—允许用户管理 Azure SQL 数据库及其关联的逻辑服务器，但不允许访问它们。此外，此角色不允许用户管理安全相关策略。

这些角色不适用于 Azure VM 上的 SQL Server，因为数据库引擎在 VM 中进行管理。但是，有特定于 VM 的 `RBAC` 角色可用于管理 VM 配置。有关这些及其他内置 `RBAC` 角色的更多信息，请参阅 `https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles`。

## 身份验证

身份验证是验证尝试访问数据库的用户身份的过程。所有版本的 Azure SQL 都支持两种身份验证方法：SQL 身份验证和 Active Directory (`AD`)。

`SQL 身份验证`涉及在 master 数据库中存储 SQL Server 特定的登录名和密码信息，或者在数据库包含用户的用户数据库中存储这些信息。事实上，在创建 Azure VM 上的 SQL Server、Azure SQL MI、Azure SQL 数据库或 Azure Synapse Analytics 专用 SQL 池时定义的管理员帐户就是一个 SQL 登录示例。管理员还可以创建其他 SQL 登录，供其他用户或自动化服务（例如 SQL Server Agent 或 Azure Data Factory）用于与数据库交互。

`Active Directory 身份验证`涉及将存储在 Windows AD 或 Azure AD (`AAD`) 中的用户或组添加为 SQL 中的登录名或包含用户。这是首选的身份验证方法，因为它比 SQL 身份验证更安全且更易于管理。如果包含 Azure VM 上的 SQL Server 的 VNet 加入了具有 AD 的域，则 Azure VM 上的 SQL Server 可以使用 Windows AD 登录进行身份验证。截至本书撰写时，Azure VM 上的 SQL Server 不能使用 AAD 用户和组进行身份验证。另一方面，Azure SQL 数据库和 Azure SQL MI 可以使用 AAD 对象。以下步骤概述了如何将 AAD 用户或组添加为 Azure SQL 数据库逻辑服务器的管理员。

1. 登录到 `portal.azure.com`，并在页面顶部的搜索栏中搜索 `SQL servers`。单击 `SQL servers` 进入 Azure 门户中的 SQL servers 页面。此页面是 Azure SQL 数据库逻辑服务器的主页。

2. 单击创建 Azure SQL 数据库时创建的逻辑服务器。

3. 在左侧面板的“设置”下单击 `Azure Active Directory`。单击 `Set admin` 将 AAD 用户或组添加为服务器上的管理员。[Figure 2.17](#c02.xhtml#c02-fig-0017) 说明了单击 `Set admin` 之前此页面的显示情况。

4. 添加帐户后，单击 `Save` 将帐户保存为管理员。

![FIGURE 2.17 Adding an AAD Administrator](images/c02f017.png)

[FIGURE 2.17](#c02.xhtml#R_c02-fig-0017) Adding an AAD Administrator

非管理员 AAD 用户和组也可以使用 `T-SQL` 添加。要将其他 AAD 用户和组添加为数据库用户，请使用具有在数据库中创建用户权限的登录名，通过 SQL Server Management Studio（本章后面将介绍管理工具）等管理工具连接到逻辑服务器。这可以包括 SQL 身份验证服务器管理员或 AAD 服务器管理员。登录后，可以使用以下命令将包含用户添加到数据库。

```
CREATE USER [<AAD_User>] FROM EXTERNAL PROVIDER;
```

有三种方法可用于使用 AAD 登录名连接到数据库。正确的选择取决于组织如何配置 AAD。这些方法如下：

*   `Azure Active Directory—Integrated`：如果用户使用 AAD 帐户登录到正在从中连接到数据库的 Windows 计算机，则可以使用此方法。

*   `Azure Active Directory—Password`：此方法强制用户输入 AAD 登录名和密码以连接到数据库。

*   `Azure Active Directory—Universal with MFA`：这是一种交互式方法，使用多因素身份验证 (`MFA`) 为数据库提供额外的访问安全性。

## 授权

授权是指用户在数据库中拥有的权限级别。这些权限包括是否可以在不同表中读取或写入数据、执行存储过程以及添加或删除其他用户。权限通常由数据库角色管理，这些角色包含一组预定义的权限。数据库角色包括 SQL Server 和 Azure SQL 中包含的固定数据库角色，以及由数据库管理员创建的用户定义数据库角色。

用户权限还可以通过对象级别的权限进行管理，例如授予或撤销在特定表或视图中选择、更新或删除数据的能力。对象级别的权限还可以限制用户可以访问哪些列。使用 `T-SQL` 拒绝访问表中特定列的示例如下所示：

```
DENY SELECT ON <table_name>(<column_1, column_2>) TO User
```

还有一种特殊的数据库授权类型，用于限制对不同表中特定行的访问。`Row-level security (RLS)` 允许数据库管理员根据运行查询的用户的特征控制对表中行的访问。这是通过用户定义的表值函数实现的，这些函数基于某些安全谓词阻止对行的访问。`RLS` 支持两种类型的安全谓词，以防止用户访问特定行：

*   Filter predicates that silently filter the rows available to read operations

