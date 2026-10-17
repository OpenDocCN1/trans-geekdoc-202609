
# Exam Ref AZ-500 Microsoft Azure 安全技术，第二版

### `ScoutAutomatedPrintCode`

## 致谢

- **总编辑**：Brett Bartow
- **执行编辑**：Loretta Yates
- **赞助编辑**：Charvi Arora
- **开发编辑**：Rick Kughen
- **制作编辑**：Sandra Schroeder
- **高级项目编辑**：Tracey Croom
- **校对编辑**：Rick Kughen
- **索引员**：Tim Wright
- **校对员**：Donna Mulder
- **技术编辑**：Mike Martin
- **编辑助理**：Cindy Teeters
- **封面设计**：Twist Creative, Seattle
- **排字员**：codeMantra
- **图形设计**：codeMantra

#### 配置委托访问

## 配置 Microsoft Defender for SQL

## 致谢

作者感谢 Loretta Yates 和整个 Microsoft Press/Pearson 团队的支持。我们还感谢 Mike Martin（Microsoft MVP）对本书的审阅，以及 Rick Kughen 的编辑。Yuri 还要感谢我的妻子和女儿们无尽的支持；感谢上帝赋予我力量并指引我的道路；朋友兼合著者 Orin Thomas 在该项目中提供的极佳合作；我的经理 Rebecca Hall 总是鼓励我超越自我。最后，感谢我的父母辛勤工作让我接受了教育，这是我每天用以不断前进的基石。

## 关于作者

YURI DIOGENES, MSC Yuri 拥有网络安全情报与取证科学硕士学位（UTICA College），是 Microsoft Defender for Cloud 团队的首席 PM 经理，他管理着一个由经理组成的团队，负责改进产品并帮助客户部署。Yuri 自 2006 年以来一直在微软工作，担任过多个职位，包括担任 CSS Forefront Edge 团队五年的高级支持工程师。2011 年至 2017 年期间，他是微软内容开发团队的成员，协助创建了自 2016 年发布以来的 Azure Security Center 体验。Yuri 已出版 26 本书，大部分关于信息安全和微软技术。Yuri 还拥有 MBA 学位以及许多 IT/安全认证，如 CISSP, CND, CEH, CSA, CHFI, CompTIA Security+, CySA+, Cloud Essentials Certified, Mobility+, Network+, CASP, CyberSec Responder, MCSE 和 MCTS。你可以在 Twitter 上通过 `@yuridiogenes` 关注 Yuri。

ORIN THOMAS 是微软的首席云运营倡议者，为 Microsoft Press 编写了三十多本书，涵盖了 Windows Server、Windows Client、Azure、Microsoft 365、Office 365、System Center、Exchange Server、安全和 SQL Server 等主题。他在 Pluralsight 上编写了 Azure 架构课程，并针对多种 IT 专业的主题编写了多门微软官方课程和 EdX 课程，目前正在查尔斯斯图特大学攻读云计算安全与合性的信息技术博士学位。你可以在 Twitter 上通过 `@orinthomas` 关注他。

## 引言

AZ-500 考试涉及高级主题，要求候选人对 Azure 安全技术具有卓越的实践知识。考试的部分内容即使是经验丰富的 Azure 安全管理员，如果不经常处理 Azure 的所有方面，也会遇到这些主题。要在考试中取得成功，候选人需要理解如何管理 Azure 身份和访问。他们还需要理解如何实施 Azure 平台保护、管理 Azure 安全运营以及保护 Azure 数据和应用程序。他们还需要跟进 Azure 安全技术的最新进展，包括扩展的功能和界面的变化。

此考试的候选人应在实施安全控制和威胁防护、管理身份和访问，以及在云和混合环境中的保护数据、应用程序和网络方面具有专家知识。

Azure 安全工程师的职责包括维护安全态势、使用各种安全工具识别并修复漏洞、实施威胁防护以及响应安全事件升级。Azure 安全工程师通常是致力于云管理、安全或端到端基础设施混合环境的大型团队的一员。

此考试的候选人应熟悉脚本和自动化，并对网络和虚拟化有深入理解。候选人还应熟悉云功能、Azure 产品和服务以及其他微软产品和服务。为了通过考试，候选人需要深入的理论理解和相关技术的意义的实践经验。

本书的第二版涵盖了从 2022 年开始的 AZ-500 考试目标。随着 Azure 安全功能的演进，AZ-500 考试目标也会随之变化。因此，您应该仔细检查自本书编写以来是否发生了任何变化，并据此进行学习。

本书涵盖了考试中出现的每一个主要主题领域，但并没有涵盖所有的考试题。只有微软考试团队有权访问试题，而且微软会定期向考试中添加新题，因此涵盖特定的考题是不可能的。您应该将本书视为您相关实战经验以及其他学习材料的补充。如果您在书中遇到某个您认为自己完全熟悉的主题，请使用文中提供的“更多信息？（More Info?）”链接来查找更多信息，并花时间研究和学习该主题。在`docs.microsoft.com`、MS Learn 以及博客和论坛上可以获得优质信息。

本书根据为考试发布的“所测技能”（Skills measured）列表进行组织。在 Microsoft Learn 网站上，每场考试都可以找到“所测技能”列表，地址为：`microsoft.com/learn`。书中的每一章对应列表中的一个主要主题领域，每个主题领域中的技术任务决定了章节的结构。例如，如果一项考试涵盖六个主要主题领域，本书将包含六章。

## 准备考试

微软认证考试是建立简历并让世界了解您专业水平绝佳方式。认证考试验证了您的工作经验和产品知识。虽然实战经验无法替代，但通过学习和实操练习进行准备可以帮助您应对考试。本书的设计目的并非教授您新技能。

我们建议您通过结合现有的学习材料和课程来完善您的备考计划。例如，您可以使用《考试参考》（Exam Ref）和另一本学习指南进行“在家备考”，并参加微软官方课程（Microsoft Official Curriculum course）以获得课堂体验。请选择您认为最适合自己的组合方式。您可以在 `microsoft.com/learn` 了解更多关于可用课堂培训的信息，并找到免费的在线课程和直播活动。`aka.ms/practicetests` 提供许多考试的微软官方练习题（Microsoft Official Practice Tests）。

请注意，本考试参考是基于关于考试的公开信息以及作者的经验。为了确保考试的完整性，作者无法访问正式考试。

微软认证通过证明您对当前微软产品和技术的广泛技能和经验的掌握，使您脱颖而出。考试及相应的认证旨在验证您在使用微软产品和技术设计、开发、实施和支持本地及云端解决方案时对关键胜任能力的掌握情况。认证为个人、雇主和组织带来了各种利益。

经常回来查看最新动态！

在书中，您将发现作者建议您访问以获取更多信息的网页地址。其中某些地址（也称为 URL）手动输入到浏览器中可能非常费力，因此我们将它们汇成一个列表，供纸质版的读者在阅读时查阅。

URL 按章节和标题组织。每当您在书中遇到 URL 时，请在列表中找到超链接以直接访问该网页。

我们尽了所有努力确保本书及其配套内容的准确性。您可以在以下位置访问本书的更新内容（形式为提交的错误列表及其相关修正）：

如果您发现了未列出的错误，请在同一页面向我们提交。

如需额外的书籍支持和信息，请访问

请注意，微软软件和硬件的产品支持不通过上述地址提供。如需微软软件或硬件的帮助，请访问 `support.microsoft.com`。

让我们保持交流！我们可以在 Twitter 上关注：`twitter.com/MicrosoftPress`。

## 第一章

## 管理身份和访问

在保护工作负载时，一个重要的步骤是确定您允许哪些流量以及阻止哪些流量。在过去，您可能使用网络位置和流量类型做出此判断。例如，您可能会允许来自特定 IP 地址并通过特定端口的流量，如果流量不满足这些特定条件，则拒绝。随着时间的推移，聪明的攻击者学会了伪造 IP 地址信息，使其能够绕过这些传统屏障。今天，您会听到安全从业人员说一句格言：“身份是新的控制平面”。这意味着当网络位置或流量属性不是判断主机或流量是否可靠的良好指标时，用于与您尝试保护的资源进行交互的身份可能是更好的指南。如果这些身份通过多因素身份验证等技术进行了加固，这一点尤为真实。在本章中，您将学习管理云端身份、保护云端资源和应用程序的访问，以及管理对云端管理工具的访问控制。

## 本章技能

- 技能 1.1：管理 Azure Active Directory 身份
- 技能 1.2：使用 Azure AD 管理安全访问
- 技能 1.3：管理应用访问
- 技能 1.4：管理访问控制

### 技能 1.1：管理 Azure Active Directory 身份

本目标涉及 Azure Active Directory 内部的身份。在 Azure Active Directory 中，身份表示为用户、服务主体、托管身份或组。Azure Active Directory 允许使用多种身份验证方法保护这些身份，包括一次性密码和多因素身份验证。

#### 为 Azure 资源创建并管理托管身份

当需要控制应用程序对 Azure 资源的访问权限时，我们会配置服务主体安全性。当您注册 Azure Active Directory 应用程序时，将在 Azure Active Directory 租户中创建以下对象：

**应用程序对象**：应用程序对象存储在 Azure AD 实例中并定义应用程序。应用程序对象属性的架构由 Microsoft Graph 应用实体资源类型定义。应用程序对象是跨 Azure AD 租户的全局表示。应用程序对象作为模板，当 Azure AD 创建相应的服务主体对象时，决定通用和默认属性。应用程序对象与软件应用程序之间存在一对一的关系，并与相应的服务主体对象存在一对多的关系。

**服务主体对象（Service principal object）**：Azure AD 中的用户主体（user principal）是代表用户的对象。服务主体是代表应用程序的 Azure AD 对象。`ServicePrincipal` 对象允许你为组织内的 Azure AD 租户中，为应用程序以及该应用程序的用户指定访问策略和权限。对于每个使用该应用程序的租户都需要一个服务主体。单租户应用程序将只有一个服务主体，而多租户应用程序将为每个来自该租户且已同意使用该应用程序的租户拥有一个服务主体。Microsoft Graph 服务主体实体定义了用于 `ServicePrincipal` 对象属性的架构。服务主体是应用程序在特定 Azure AD 租户中的表示。

在 Azure AD 中注册应用程序允许你利用 Microsoft 标识身份验证平台（Microsoft identity platform）的安全性登录和授权功能供该应用程序使用。在 Azure AD 中注册应用程序需要你提供相关信息，包括访问该应用程序的 URL、身份验证发生后转发回复的 URL 以及标识你的应用程序的 URI。你将在本章的后半部分学习更多关于在 Azure AD 中注册应用程序的知识。

服务主体与本地 Active Directory 服务帐户类似，因为它们都允许应用程序拥有身份和安全上下文。Azure AD 中的服务主体可以包含以下内容：

- 通过 `application ID` 属性对应用程序对象的引用
- 本地用户和组应用程序角色分配属性
- 本地用户和管理员应用程序权限
- 本地策略数据，包括关于条件访问策略的信息
- 关于备用本地应用程序设置的数据，包括：
  - 声明转换规则（Claims transformation rules）
  - 属性映射（用户配置）
  - 目录特定的应用角色（当应用程序支持自定义角色时）
  - 目录特定的名称或标志

### 创建服务主体

正如你已经学到的，当你向 Azure AD 实例注册应用程序时，Azure AD 会创建一个服务主体。这是大多数 Azure AD 服务主体的创建方式。你可以从 Azure PowerShell 会话通过 `New-AzADServicePrincipal` 命令创建服务主体。运行 Azure PowerShell 的简单方法是通过 Cloud Shell 会话。例如，要从 Azure PowerShell 会话创建一个名为 `ExampleServicePrincipal` 的新服务主体，请运行以下命令。

```
$servicePrincipal = New-AzADServicePrincipal -DisplayName "ExampleServiceprincipal"
```

服务主体可以使用两种不同的身份验证：基于密码的身份验证和基于证书的身份验证。如果你在创建服务主体时未指定登录验证类型，将使用基于密码的身份验证，并为服务主体账户分配随机密码。

要查看与 Azure AD 实例关联的服务主体列表，请从 Azure PowerShell 会话运行以下命令：

```
Get-AzAdServicePrincipal | format-table
```

### 通过角色为服务主体分配权限

为了在订阅内提供访问权限，你需要为应用程序关联的服务主体分配一组权限。实现此目标最直接的方法是为应用程序分配特定角色。例如，如果你想让应用程序对特定资源组内的资源具有读取权限，你可以为与应用程序关联的服务主体分配 `Reader` 角色。

要向已注册到 Azure AD 实例的应用程序分配角色，请执行以下步骤：

1. 在 Azure 门户中，选择与应用程序关联的订阅，然后从**订阅（Subscriptions）**页面选择**访问控制 (IAM)**节点，如图 1-1 所示。

   ![FIGURE 1-1 Access control (IAM) for a subscription](img/01fig01.jpg)

   **图 1-1** 订阅的访问控制 (IAM)

2. 在**访问控制 (IAM)** 页面上，选择**添加分配**，选择要分配给应用程序的角色，并在**分配给**下拉菜单中选择**Azure AD 用户、组或服务主体**，如图 1-2 所示，然后在**选择**文本框中指定应用程序的名称。

   ![FIGURE 1-2 Assign a role to an application](img/01fig02.jpg)

   **图 1-2** 为应用程序分配角色

3. 点击**保存**将角色分配给服务主体。

正如可以通过订阅级别的访问控制节点通过角色分配权限一样，你也可以使用资源组或资源级别的访问控制 (IAM) 节点为服务主体分配角色。在为服务主体分配权限时，应以最严格的方式分配权限。这意味着你应该只在适当的作用范围内分配角色，并仅分配应用程序所需的角色。如果应用程序仅对资源组需要 `Reader` 权限，请勿在订阅级别为服务主体分配 `Contributor` 角色。

你可以使用 `New-AzRoleAssignment` PowerShell 命令为服务主体分配角色。例如，要创建一个新的服务主体并在订阅级别为其分配读取权限，请执行以下 PowerShell 命令：

```
$servicePrincipal = New-AzADServicePrincipal -DisplayName "ExampleServiceprincipal"
New-AzRoleAssignment -RoleDefinitionName "Reader" -ApplicationId $servicePrincipal.ApplicationId
```

在命令行环境中处理服务主体需要使用应用程序 ID 而不是显示名称。这就是为什么在上一个示例的第二个命令中指定了 `ApplicationId`，以便将角色分配给第一个命令创建的服务主体。

你可以通过以下步骤确定在订阅、资源组或资源级别为服务主体分配了哪些角色：

1. 在 Azure 门户中，选择与应用程序关联的订阅、资源组或资源，然后选择**访问控制 (IAM)**节点。
2. 选择**角色分配（Role Assignments）**部分。此页面列出了分配到此作用范围的所有角色。在**类型**列中，服务主体显示为 **App** 类型，如图 1-3 所示。

   ![FIGURE 1-3 Checking Role assignments for service principals](img/01fig03.jpg)

   **图 1-3** 查看服务主体的角色分配

#### 管理 Azure AD 组

组允许你将用户分组，然后为他们分配权限以及对工作负载或服务的访问权限。与其直接为用户分配工作负载或服务的访问权限，你可以将这些权利分配给组，然后通过将用户账户添加到相应的组来间接分配给用户。使用组允许你通过向组添加或删除用户来分配访问权限和权利。虽然可以按用户分配访问权限和权利，但在管理上非常繁琐，并且难以确定哪些用户拥有特定权限。如果仅将权限委托给组，确定权限将变得容易得多。如果你仅向组分配权利，或者需要确定权限，只需检查组的成员关系即可。
