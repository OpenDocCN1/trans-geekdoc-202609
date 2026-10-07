

# 6 Google Cloud 身份与访问管理 (IAM)

在本章中，我们将探索 Google Cloud 身份与访问管理 (IAM)，这是考试中必须理解的一项服务。通过 IAM，你可以对云服务进行授权，并为用户和应用程序分配适当的权限。深入理解 IAM 对于确保你的云端实现遵循最小权限原则（将访问限制在必要范围内）至关重要。

在本章中，我们将涵盖以下主题：

- IAM 概述
- IAM 角色与权限
- 服务账号
- IAM 策略绑定
- IAM 条件
- 云存储 (Cloud Storage)、IAM 与 访问控制列表 (ACLs)
- 日志记录与 IAM API

## IAM 概述

在上一节中，我们讨论了 Google Cloud 身份及其在 Google Cloud 和 Google Workspace 的身份验证、用户管理和设备管理中的作用。现在，让我们探索 IAM，它侧重于 Google Cloud 中的授权。授权是云计算的核心原则之一，用于解决各种需求并确保对资源的安全访问。它解决的一些问题包括：

- 我如何向人员和工作负载授予访问权限？
- 我如何提供限时访问权限？
- 我如何创建具有最小权限的服务账号？
- 我如何在一个特定项目中启用服务而在其他项目中禁用？
- 我如何为用户提供恰当的访问权限？
- 我如何在多云环境中进行操作？
- 我如何发现过度授权的访问权限？
- 我如何排查访问问题？

![](img/f681dfc12450e3a4c257352b70dbceca_116_0.png)

在图 6.1 中，你可以看到 IAM 是如何根据“谁（身份）对何种资源拥有什么访问权限（角色）”的原理工作的。主体实体通常是用户、组或服务账号。然而，正如后文解释的那样，还有其他主体。角色是一组细粒度的权限。权限是你在特定资源（例如，BigQuery）上可以执行的预定义操作。给定资源的权限是固定的，无法自行创建。我们将在本章稍后部分讨论服务账号。此时，需要记住的是，服务账号代表 Google Cloud 中的服务或应用程序身份。这是 Google Cloud 处理工作负载权限时最重要的区别点之一。

## IAM 概述

在 Cloud IAM 中，支持以下主体：

- Google 账号（Gmail 账号是 Google 账号的一种形式）：使用个人 Google 云的用户拥有 Google 账号。这可能是一个开发者、管理员或任何使用该服务的人。可以通过任何关联到 Google 账号的电子邮件地址来识别身份。这可以是 gmail.com 或任何域名。
- 服务账号 (Service account)：服务账号是应用程序或虚拟机实例的身份，而不是人员。服务账号既是主体也是资源。我们稍后会详细介绍。
- Google 组 (Google group)：Google 组是 Google 账号和服务账号的组合。每个 Google 组都有一个唯一的电子邮件地址。Google 组为个人组应用 IAM 策略提供了一种方便的方法。你不需要为每个人单独管理访问控制，而是同时为一个实体添加或修改访问控制。此外，你可以轻松地从 Google 组中添加或删除成员，无需因移除用户修改 IAM 策略。
- Google Workspace 账号：Google Workspace 账号是关联到你特定 Google Workspace 的 Google 账号。它拥有业务邮箱。除了你可能学过的其他应用外，Google Workspace 还包含 Docs、Slides 和 Sheets 等 Google 应用。
- Cloud Identity 域 (Cloud Identity domain)：Cloud Identity 域类似于 Google Workspace 账号，但不包含任何 Google 应用。如果你的组织不使用 Google Workspace，你通常会获得免费版的 Cloud Identity。请注意，某些功能只有 Cloud Identity 高级版才能提供。请参考 Google 支持文档对比免费版和高级版的区别。
- 所有经过身份验证的用户 (All authenticated users)：allAuthenticatedUsers 是所有服务账号以及互联网上所有使用 Google 账号登录人员的唯一标识符，即任何使用 Google 账号登录的人。这可以是 gmail.com 或任何其他域名。对于所有使用 Google 账号登录的互联网上的所有人员以及所有服务账号，allAuthenticatedUsers 是一个唯一标识符。
- 所有用户 (All users)：所有用户。在图 6.1 中，你可以看到 IAM 是如何根据“谁（身份）对何种资源拥有什么访问权限（角色）”的原理工作的。主体实体通常是用户、组或服务账号。然而，正如后文解释的那样，还有其他主体。

- 恰恰允许的访问权限。

## IAM 角色与权限

在 IAM 中，角色是权限的集合。有三种类型：

- 基础角色（Basic roles）
- 定义角色（Predefined roles）
- 自定义角色（Custom roles）

### 基础角色

在 IAM 中存在三种基础角色。这些是遗留角色：

- 查看者 (Viewer)：对资源的只读权限，不影响状态。
- 编辑者 (Editor)：具有查看权限，以及修改资源状态的操作权限。
- 所有者 (Owner)：具有编辑者权限，以及管理项目及其内部所有资源的权限。

### 定义角色

IAM 提供了特定服务的定义角色，便于分配。这些角色由 Google 维护。也就是说，权限的更改（添加或弃用）由 Google 负责，因此通常建议为服务创建自定义角色。

在资源层级结构的任何级别，你都可以为用户授予多种角色。例如，同一用户可以在项目上拥有计算网络管理员和日志查看角色，同时在特定的 BigQuery 数据集中拥有 BigQuery 编辑者角色。

现在你已经了解什么是定义角色，让我们看看如何为你的工作负载选择定义角色。我们将 BigQuery 角色为例。

### 选择定义角色

IAM 中有很多定义角色。通常，这些角色是为特定的云服务身定制的。以 BigQuery 为例，以下是 Google 为 BigQuery 提供的定义角色：

- BigQuery 管理员 (Admin)
- BigQuery 连接管理员 (Connection Admin)
- BigQuery 连接用户 (Connection User)
- BigQuery 数据编辑者 (Data Editor)
- BigQuery 数据所有者 (Data Owner)
- BigQuery 数据查看者 (Data Viewer)
- BigQuery 过滤数据查看者 (Filtered Data Viewer)
- BigQuery 作用户 (Job User)
- BigQuery 元数据查看者 (Metadata Viewer)
- BigQuery 读取会话用户 (Read Session User)
- BigQuery 资源管理员 (Resource Admin)
- BigQuery 资源编辑者 (Resource Editor)
- BigQuery 资源用户 (Resource User)

如何决定使用哪个定义角色？考虑以下步骤：

1. 识别必要的权限。
2. 找到包含权限的角色。
3. 选择与权限匹配的最合适角色。这可以是一个或多个角色，以授予最小权限。
4. 决定在资源层级的哪个层级授予角色。
5. 将角色授予主体，并在必要时使用条件。

了解在哪个层级（资源/文件夹/组织）向主体授予角色也很重要。我们经常强调这一点，因为了解其中的区别很重要，因为它会影响用户能够执行的操作。

让我们以 BigQuery User 角色为例。查看该角色包含的权限：

- bigquery.bireservations.get
- bigquery.capacityComments.get

