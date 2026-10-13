
与 SQL 数据库一样，Cosmos DB 会自动备份您的数据，无需客户干预。Cosmos DB 每 4 小时进行一次数据库备份，并保留最新的两个备份。Cosmos DB 还会保留快照 30 天。

Azure 文档建议您使用 Azure 数据工厂，通过将数据复制到另一个 Cosmos DB 账户来手动备份 Cosmos DB 数据。

截至撰写本文时，您需要向 Microsoft 提交支持工单以请求任何类型的数据恢复。Cosmos DB 团队告诉我，Microsoft 已将用户发起的数据恢复列入新功能待办事项。谁知道呢；等您读到这一章时，也许该功能已经添加了！这就是 Azure。

共有四种 Azure 支持计划。所有即用即付订阅者均从基础支持计划开始，该计划免费；其他三个计划具有固定的月度费用。以下是这四个计划及其相关 SLA 的快速概览：

*   **基础：** 无响应时间 SLA
*   **开发人员：** 针对影响最小的支持问题，响应时间 SLA 少于 8 小时
*   **标准：** 针对关键业务影响的支持问题，响应时间 SLA 少于 1 小时
*   **专业直接：** 最短的响应时间，外加 Azure 架构和运营支持

假设您意外删除了 Cosmos DB 账户，并需要尽快恢复它。您必须提交支持工单。以下是步骤：

1.  **在 Azure 门户中，选择“帮助” ⇒ “帮助 + 支持”。**
    “帮助 + 支持”工具随即出现，如[图 10-7](#c10.xhtml#c10-fig-0007)所示。
2.  **选择“新建支持请求”，然后按提示操作。**
    在这种情况下，您需选择您的 Cosmos DB 实例，并选择“备份和恢复”问题类型。
3.  **定期查看“所有支持请求”边栏选项卡以获取更新。**
    Azure 支持可能会通过电子邮件和/或电话与您联系，具体取决于您提交支持请求时指定的偏好。

![图 10-7：在“帮助 + 支持”边栏选项卡上创建和跟踪 Azure 支持请求。](images/9781119612148-fg1007.png)

[图 10-7：](#c10.xhtml#rc10-fig-0007) 在“帮助 + 支持”边栏选项卡上创建和跟踪 Azure 支持请求。

# 第 11 章：使用 Azure Active Directory 管理标识和访问

## 本章内容

*   **区分 AD 产品**
*   **描述订阅与 AD 之间的关系**
*   **创建和管理 AD 用户和组**
*   **实施基于角色的访问控制**
*   **采纳 Azure 顾问建议**

每当您在 Azure 中执行工作时，您都在与 Azure Active Directory (Azure AD) 交互，后者是一种托管标识服务，与 Azure 架构师、管理员、开发人员、业务分析师、信息工作者甚至您的客户息息相关。

Azure AD 之所以在 Azure 中处于核心地位，是因为它构成了订阅的标识基础。任何需要访问您 Azure 订阅的人员或进程都必须在 Azure AD 中定义。

读完本章后，您将深入掌握 Azure AD 与 Azure 订阅之间的关系。您还将掌握使用最小权限安全性保护资源所需的技能。IT 安全的最小权限原则意味着您应仅授予用户完成其工作所需的权限，不多也不少。

## 理解 Active Directory

Azure AD 是一种多租户托管标识存储，供 Azure 以及其他 Microsoft 云服务使用，包括：

*   Office 365
*   Dynamics 365
*   Intune
*   Enterprise Mobility + Security

如今的任何计算机（无论运行 Windows、macOS 还是 Linux）都有一个本地标识存储，用于定义获授权使用该计算机的用户。自 1999 年以来，Microsoft 在其 Windows Server 产品中提供了 Active Directory 域服务 (AD DS)；AD DS 是本地网络的集中式标识存储。

*租户* 和 *多租户* 这两个术语容易让人困惑，所以我马上为您消除困惑。就 Azure AD 而言，*租户* 就是单个 Azure AD 实例。一个组织可以有一个或多个 Azure AD 实例——例如，一个供内部使用，另一个供客户使用。

Azure AD 之所以被称为多租户标识存储，是因为：

*   您可以拥有多个 Azure AD 租户。
*   每个租户可以托管来自多个来源的用户帐户，包括其他 Azure AD 租户。
*   一个或多个订阅可以信任 Azure AD（共享单个标识存储）。

另一个经常模糊不清的术语是 *云应用*。就 Azure AD 而言，云应用是指任何依赖 Azure AD 作为其用户标识存储的应用程序（Web、桌面或移动）。

### AD 与 AD DS 的对比

Azure AD 可能与本地网络中的 Active Directory 域服务 (AD DS) 共享部分名称，但这些目录服务截然不同。[表 11-1](#c11.xhtml#c11-tbl-0001) 提供了高层对比。

[表 11-1](#c11.xhtml#rc11-tbl-0001) Azure AD 与 AD DS 对比

| | **AD DS** | **Azure AD** |
| --- | --- | --- |
| 访问协议 | 轻型目录访问协议 | Microsoft Graph REST API |
| 林/树域结构 | 是 | 否 |
| 组策略管理 | 是 | 否 |
| 组织单位 | 是 | 否 |
| 动态组 | 否 | 是 |
| 多重身份验证 | 否 | 是 |

尽管 AD DS 和 Azure AD 差异很大，但可以将它们结合成混合标识解决方案。您可以部署 Azure AD Connect（Microsoft 免费的标识同步引擎），将本地 AD 帐户同步或联合到 AD，从而为云应用提供单一登录。

> **提示：** 有关使用 Azure AD Connect 将本地 Active Directory 扩展到 Azure AD 的详细信息，请参阅 [`https://docs.microsoft.com/en-us/azure/active-directory/hybrid/whatis-azure-ad-connect`](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/whatis-azure-ad-connect)。

### 订阅与 AD 租户之间的关系

您还需要清楚地了解 Azure AD 租户与 Azure 订阅的关系。要创建 Azure 帐户，您需要使用 Microsoft 帐户标识。这样做时，您的试用订阅将链接到一个默认 AD 租户，通常标记为“默认目录”。

Azure AD 租户可以独立于订阅存在，但在 Azure AD 租户链接到至少一个订阅之前，Azure 不会允许您部署任何资源。[图 11-1](#c11.xhtml#c11-fig-0001) 说明了这一点。

[图 11-1](#c11.xhtml#c11-fig-0001) 描绘了 Azure 订阅与单个 Azure AD 租户之间存在的信任关系。

![图 11-1：Azure AD 与 Azure 订阅之间的关系。](images/9781119612148-fg1101.png)

[图 11-1：](#c11.xhtml#rc11-fig-0001) Azure AD 与 Azure 订阅之间的关系。

#### 多租户 Azure AD

虽然 Azure AD 可以作为多个订阅的标识存储，但单个 Azure 订阅一次只能信任单个 Azure AD 租户。要理解这些概念，请执行以下步骤：

1.  **以管理用户身份登录 Azure 门户。**
2.  **选择“创建资源”。**
3.  **在 Azure 市场边栏选项卡上，搜索并选择 Azure Active Directory，并考虑拥有多个 Azure AD 租户的含义。**
    您可以部署任意数量的 Azure AD 租户（取决于您的用例），但在将 Azure 订阅绑定到它们之前，您无法对它们进行任何实质性操作。Azure AD 租户是资源，与 Azure 资源管理器 (ARM) 中的任何其他资源非常相似。
4.  **使用全局搜索框浏览到“订阅”边栏选项卡，并在订阅列表中选择您的订阅。**

