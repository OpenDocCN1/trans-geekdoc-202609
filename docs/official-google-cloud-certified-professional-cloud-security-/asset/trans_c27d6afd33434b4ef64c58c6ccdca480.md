

# 理解 Google Cloud Identity

在本章中，我们将介绍 Google Cloud Identity，它是 Google 提供的身份即服务 (IDaaS) 和企业移动设备管理 (EMM) 产品。我们将涵盖目录管理、如何创建和管理用户账户及群组，以及如何同步 Google Cloud Directory Sync (GCDS) 等目录服务等方面。我们还将涵盖其他功能和服务，包括单点登录 (SSO) 以及设备和应用管理。

此外，我们将介绍如何使用 Google Cloud Identity 来强制执行两步验证 (2SV)、密码管理、会话管理以及报告和管理员日志活动。Cloud Identity 内部的话题非常广泛，涵盖了一些与 Google Workspace（以前称为 G Suite）相关的方面，我们在本章中将讨论限制在与 Google 专业级云安全安全工程师考试相关的主题上。

在本章中，我们将涵盖以下主题：

- Cloud Identity 概述
- 账户安全，例如配置用户、双重身份验证、会话管理和 SAML
- 如何配置 Google Cloud Directory Sync

# Cloud Identity 概述

Google Cloud Identity 与我们在这书中将介绍的其他一些云安全产品不同。它的不同之处在于它涵盖了两个不同的平台：Google Workspace 和 Google Cloud。Google Workspace 不在涵盖范围内，因为它不属于 Google 专业级云安全工程师工程师的范围；我们将涵盖的功能和方面将仅与 Google Cloud 使用 Cloud Identity 相关。

首先，让我们了解 Cloud Identity 的几个方面。Cloud Identity 通过单独控制台 (admin.google.com) 访问。Cloud Identity 也是您在配置 Google Cloud 环境时交互的第一个产品，因为超级管理员账户存在于 Cloud Identity 中。本章稍后将会有关于超级管理员账户的内容。Cloud Identity 仅提供身份验证服务而不提供授权。授权方面由 Google Cloud 身份和访问管理 (IAM) 涵盖，它通过 Google Cloud 控制台 (console.google.com) 访问。

在进入 Cloud Identity 的配置和设置之前，让我们来看一些关键功能以更好地理解 Cloud Identity。Cloud Identity 是驱动 Google Workspace 的相同 IDaaS，它提供免费版和高级版。高级版对用户数量没有限制，尽管在免费版中，您可以要求 Google 将用户数量从默认的 50 个限制限制增加。其他区别还包括高级版对 Secure LDAP 的支持、访问 Google 安全中心、移动设备管理、将审核日志自动导出到 BigQuery 以及会话长度管理（您可以控制身份验证令牌的时长）。最后，免费版不带服务水平协议 (SLA)。

现在我们知道了免费版和高级版 Cloud Identity 之间的差异，让我们快速查看本章将涵盖的 Cloud Identity的一些功能。

# 单窗视图 (Single pane of glass)

![](img/f681dfc12450e3a4c257352b70dbceca_88_0.png)

图 5.1 - Google Cloud Identity 功能

前面的图捕捉了 Google Cloud Identity 的关键功能。让我们看看与 Google Cloud 更相关的功能。在生命周期管理方面，您可以创建或将用户账户导入到云目录。如果您在本地环境中使用 Active Directory，则可以使用 GCDS 工具配置 Active Directory 并将用户、群组和成员关系导入 Google Cloud Identity。

您可以在用户加入组织、更改角色或离开时，控制配置和取消配置（部署）的过程。账户安全让您能够强制使用 2SV、应用密码策略，并开启/关闭对 Google Cloud 控制台的访问。您还可以使用 Google 身份验证或通过外部身份提供者 (IdP，如 Okta 或 Ping Identity）使用 SSO。我们将在本章稍后的部分详细介绍 SSO。

在下一节中，我们将介绍如何开始使用 Cloud Identity，涵盖域名验证的内容。

# 域名设置

在开始之前，请记住 Cloud Identity 通过 admin.google.com 访问，为了确保您拥有 Google Cloud 的 Identity 域名设置。出于治理和合规性要求，将 Google Cloud 账户与 Workspace 账户分开是一个好主意。

配置新域名包括以下步骤：

1. 注册 Cloud Identity。提供个人信息，如姓名、电子邮件地址、业务、地区。
2. 下一步是身份验证，以确保您拥有超级管理员账户。如果您知道您的域名，可以使用 Google 生成的验证码添加 TXT 记录来验证域名：httpspackt.link/Qiq。

正如之前提到的，这些步骤是为了完整性让您成为 Cloud Identity 域所有者。接下来我们将介绍超级管理员角色，在进入如何创建和管理用户群组之前。

# 超级管理员最佳实践

Cloud Identity 拥有超级管理员角色，这与 Google IAM 组织管理员不同，但超级管理员默认是组织管理员，并对两个平台拥有权限。超级管理员通过 admin.google.com 管理，并拥有管理用户、群组和安全设置的访问权限。它还用于授权 Cloud IAM 组织管理员角色。对于所有目的，超级管理员不应使用 console.google.com 来配置 Google Cloud 资源。

鉴于超级管理员的重要性，应该遵循一些最佳实践。这些最佳实践包括：

- 始终为超级管理员账户启用 2SV/多因素身份验证。
- 在安全位置保留备份密钥。
- 禁用设备信任并限制 Web 会话长度。
- 防止对个人的过度依赖，建议限制超级管理员账户的使用并最多保留 4 个。这种预防措施降低了单点故障相关的风险，并确保在紧急情况下有足够的超级管理员。
- 设置恢复电话和电子邮件选项，并确保恢复安全且受 2SV 保护。

> 注意
> 如果由于没有设置恢复电子邮件/电话而丢失对超级管理员账户的访问权限，则需要域名 DNS 访问来验证所有权。

- 创建专用超级管理员账户并锁定。这是一个在紧急情况下使用的断路（break-glass）账户。
- 分配 Cloud Identity 角色以委托管理用户、群组等。
- 将 Google Cloud 资源的设置和管理委托给其他管理员，并为他们分配功能性 IAM 角色，以确保职责分离。
- Cloud Identity 超级管理员将始终跳过任何 SSO；他们将直接与 Google Identity 验证。

Cloud Identity 的主题非常广泛，某些领域与 Google Cloud Workspace 的功能重叠。在本节中，我们只涵盖了从 Google 专业级云安全工程师考试视角相关的内容。如果您想进一步学习，可以参考 Cloud Identity 的文档。接下来，我们将介绍 Cloud Identity 的一些与安全相关的功能。

