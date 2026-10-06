

# 第 7 章 Windows Server 2012 中的 Active Directory

有关提高域和森林功能等级的详细步骤，请参阅“**提高域和森林功能级别**”一节。

# Windows Azure Active Directory 简介

我们之前讨论过 Active Directory 是本地的。这意味着你公司内的 Active Directory 受到外部世界的保护。让我们回想一下你为什么要使用 Active Directory。你需要此服务来集中存储和管理你的所有用户和计算机，以控制你的 Windows 基础设施。

在 Active Directory 开发几年后，IT 面临一个大问题。没有 Active Directory，每个应用程序都需要在数据库或服务器本身存储其访问凭据。Windows NT 有一种管理用户和计算机的简单方法，但这种方案无法满足企业的需求。开发 Active Directory是为了集中管理基础设施。同样的问题出现在 Windows Azure 中。现在，应用程序格局出现了一些用户名和密码，应用程序可以验证并授权用户使用此应用程序。但现在 Windows Azure Active Directory 加入了。在本节中，我们将本地 Active Directory 称为“Active Directory”，将云托管 Active Directory 称为“Windows Azure Directory”（WAAD、Azure AD 或 Azure Directory）。

Windows Azure Directory 是一项为你的云应用程序提供身份和访问控制的服务。许多在线应用程序使用 Windows Azure AD；其他的是使用 Dynamics Online 和 Windows Directory。WAAD 是一项多户服务，可以处理数百万公司、超过1亿亿用户以及同一平台上的数千个租户。它针对可用性和一致的可扩展性进行了优化。这意味着你不再需要本地 Active Directory？是的。Windows Azure AD 可以独立使用，但最常见的场景是将其视为云端的 Active Directory 架构（见图 7.69）。

将你的本地 Active Directory 扩展到云端允许你在本地管理用户并将其同步到 WAAD，我们将稍后讨论 DirSync。由于这种机制，你将能够为你的云托管应用程序创建单点登录（SSO）体验。如果你仅使用 DirSync 将无法获得 SSO 体验。对于 SSO，你还需要在本地 Active Directory 中部署 Active Directory 联合（AD FS）。更多详情，请参阅“**Active Directory 登录**”一节。

# 使用 Windows Azure Active Directory

如何为 Azure Active Directory 中的 AD 租户获取账户？最简单的方法是注册 Office 365 账户，你将立即拥有 Windows Azure Active Directory。这是因为 Office 365 使用 Windows Azure Active Directory。另一种获取 WAAD 的方法是在 Windows Azure (http://www.windowsazure.com/) 上线注册。无论选择哪种方法，你都可以从两个门户管理你的账户。

注册 Windows Azure 后，你就可以开始管理目录了，如图 7.70 所示。

# Windows Azure Active Directory 简介

图 7.69
Windows Azure Directory 集成

![](img/41a8320e6906a373262023b836cea7_404_0.png)

图 7.70
WAAD 门户

![](img/41a8320e6906a373262023b836cea7_404_1.png)

Windows Azure 管理门户、Windows Azure AD 门户、Office 365 账户门户、Windows Intune 账户门户以及 Windows Azure PowerShell 所有的都读自和写入与你组织租户关联的单个 Windows Azure AD 共享实例所示。

# 图 7.71
管理 Windows Azure Active Directory

![](img/41a8320e6906a373262023b836cea7_405_0.png)

# 如何与 Windows Azure Active Directory 交互

如果你已经熟悉 Active Directory，可能已经使用轻量级访问协议（LDAP）来查询目录对象。LDAP 是一种用于访问和维护目录信息的应用程序协议。然而，你不能使用 LDAP 访问 WAAD，因为 LDAP 并不是为多户场景设计的。其中一个问题是协议必须独立于跨不同技术的多个平台。因此，微软构建了一个用于访问 WAAD 的 REST 接口。表述状态转换（REST）是一种使用 HTTP 通过 GET、POST、PATCH 和 DELETE 方法执行创建、读取、更新和删除（CRUD）操作的架构。微软将此 REST 接口称为 Windows Azure Active Directory Graph。

使用这种接口有几个优势：

- **平台无关**——任何设备都能够使用 HTTP 并调用 HTTP 方法。
- **语言无关**——任何编程语言都可以使用 REST 架构与其他编程语言进行通信；例如，C# 可以与 Java 通信。
- **基于标准**——因为它运行在 HTTP 上并基于 HTTP 标准，因此 Windows AD Graph 可以在任何平台上使用。
- **易于管理**——防火墙可以轻松配置允许 HTTP 流量。

# 测试 WINDOW AZURE ACTIVE DIRECTORY GRAPH

为了了解 Graph API 如何工作，你可以尝试一下。微软在 Windows Azure 中提供了一个名为 Graph Explorer 的测试应用程序，它可以让你对你的租户运行查询。访问 http://graphexplorer.cloudapp.net/ 并用你的微软账户登录；然后使用右上角的“使用演示公司”。这会将你发送到位于 https://graph.windows.net/ 的测试租户（GraphDir1）。

为了让你的租户拥有数据，该工具同步密码哈希值。例如，该工具同步的是用户的密码哈希值，而不是明文密码（这会产生安全问题）。你可以通过以下 URL 查看：https://graph.windows.net/GraphDir1.microsoft.com。

在 Windows Azure 中，你还可以看到如何 同步你的本地 Active Directory。对于 Windows Azure Directory 还有其他协议。REST/HTTP 只是这些协议中的之一。你还需要在 Windows Azure Directory 中了解更多信息。本章不会深入探讨这些技术。表 7.3 提供了这些协议的概述。

表 7-3：Windows Azure 协议
| 协议 | 目的 |
|---|---|
| REST/HTTP | 创建、读取、更新和删除对象 |
| OAuth 2.0 | 服务间访问 |
| SAML 2.0 | Web 应用单点登录 |
| WS-Federation 1.3 | Web 单点登录 |

# 同步 Windows Azure Active Directory

在此之后，你已经了解 WAAD 是什么，以及你为什么要与本地 Active Directory 集成。图 7.69 如前所示提供了集成概念的高级视图。

主要目标是让你的本地 Active Directory 作为数据源，Azure 目录接收用户、组和联系对象。“数据源”意味着你管理本地 Active Directory，你所做的任何更改都会覆盖 Azure AD 中的设置。更新 Windows Azure AD 的机制是一个名为 DirSync 的工具。该工具允许你在本地同步用户到 WAAD 并保持更新。一旦安装了 DirSync，它会在后台运行，每几小时同步一次 WAAD。最新版本的 DirSync 还能将用户的密码同步到云端。不是同步明文密码，而是工具同步密码的哈希值。想象一下这给公司带来的好处。

你的用户可以使用与公司本地网络相同的凭据访问云应用程序。

# DirSync 工具

DirSync 设置相对容易。它是一个 64 位工具，需要 SQL Server 2008 R2 破解或完整版 SQL Server。一旦安装完成，它基本上是“设置后即可忽略”，意味着你不需要再次触碰它。

