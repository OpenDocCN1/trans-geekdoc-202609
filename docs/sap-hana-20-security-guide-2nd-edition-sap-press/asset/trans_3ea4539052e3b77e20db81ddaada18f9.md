

组织必须确保托管在 SAP HANA 系统中的数据的完整性。记录财务交易时，这些记录应受到保护，防止未经授权的更改。数据完整性通过仅允许授权人员更改数据，并通过审计、加密和强密码身份验证策略来保护。

组织还必须确保 SAP HANA 系统的可用性。安全性是维护系统可用性的重要组成部分。授权用户和未经授权的用户都可能导致数据库可用性降低。安全模型可以管理受信任用户之间的访问，即那些在数据库中被明确授予权限的用户。但是，组织必须确保用户访问仅限于其职责范围。你还必须确保用户已针对其访问级别接受良好培训。未经授权的用户是指组织外部且未在 SAP HANA 系统中被明确授予权限的用户。这些用户通常通过不正当或未经授权的手段获取访问权限，并意图窃取数据或干扰数据库的运行。安全模型既可以管理授权访问，也可以防止未经授权的访问。

在从客户处收集敏感数据时，组织必须保护这些数据。未能保护客户数据的组织往往声誉受损。如果客户无法信任你的组织来处理其敏感数据，他们可能会选择与你的竞争对手开展业务。如果敏感客户数据未得到保护，你的组织也可能面临巨额罚款。

因此，你的组织应出于多种原因优先考虑、强调并审查其 SAP HANA 安全模型。在本书中，我们将教你如何实施安全模型、识别风险权限，并在可能的情况下遵循最佳实践。

### 摘要

我们现在准备好开始探索 SAP HANA 安全模型的旅程，首先是 SAP HANA cockpit 的概述，这是管理许多 SAP HANA 安全工件的重要工具。

# 1 使用 SAP HANA Cockpit 管理安全性

在本章中，我们将向你介绍 SAP HANA cockpit 以及管理安全设置和安全模型所需的许多工作流程。

自诞生以来，大部分 SAP HANA 安全模型一直使用 SAP HANA Studio 开发和维护，这是安装在 SAP HANA 开发人员或管理员工作站上的客户端工具。但是，在 2016 年 11 月，SAP 宣布并发布了 SAP HANA 2.0，其中包括一种名为 SAP HANA cockpit 的新管理工具。

SAP HANA cockpit 提供监控、配置、性能优化、安全性、平台生命周期管理和其他管理功能。与 SAP HANA Studio 不同，SAP HANA cockpit 不提供应用程序或内容开发工具。这些工具已迁移到 SAP Web IDE for SAP HANA，这是 SAP HANA 2.0 产品组合中的另一种独立的基于 Web 的开发工具。

SAP HANA cockpit 是一个独立的、基于 Web 的 HTML5 应用程序服务器，而不是基于桌面的客户端工具。它在 SAP HANA 扩展应用服务，高级模型（SAP HANA XSA）中运行，并且还需要 SAP HANA 2.0 express edition 数据库或 SAP HANA 2.0 租户数据库才能运行。SAP HANA cockpit 的架构旨在集中化和简化整个 IT 环境中 SAP HANA 的管理和运维。鉴于其在 SAP HANA 安全领域的重要性，本章的目标是向你介绍可以在 SAP HANA cockpit 中管理的各种安全工作流程和安全选项。但是，本章不旨在作为使用 SAP HANA cockpit 的全面指南。

###### 其他基于 Web 的管理工具

从 SAP HANA 2.0 SPS 04 开始，安全模型的某些方面仍可以使用 SAP HANA 基于 Web 的开发工作台进行管理。该工具托管在旧版 SAP HANA 扩展应用服务，经典模型（SAP HANA XS）引擎（XS 引擎）中。

在整本书中，对 SAP HANA cockpit 的引用将非常突出，因此你需要对其及其安全相关界面有基本了解。在本章中，我们将提供 SAP HANA cockpit 的概述，介绍其架构、基本导航步骤和特定的安全管理界面。我们还将介绍 SAP HANA 数据库资源管理器和 SQL 控制台，其中执行安全相关的 SQL 命令，并将概述你将用于管理安全相关项目的关键用户界面，包括用于用户和角色管理的图形界面。我们还将讨论用于管理数据加密、身份验证和数据库安全性的其他界面。

## 1.1 SAP HANA Cockpit 是什么？

在本节中，我们将提供 SAP HANA cockpit 架构的概述，向你展示如何首次访问它，回顾 SAP HANA cockpit 管理器，并引导你完成在 SAP HANA cockpit 中注册 SAP HANA 数据库所需的步骤。

### 1.1.1 SAP HANA Cockpit 架构

从架构上讲，SAP HANA cockpit 是一个 SAP HANA XSA 多目标应用程序（MTA），需要 SAP HANA 数据库才能运行。SAP 提供多种部署选项，如 [图 1.1](#01_001.html#f1.1) 所示。

如 [图 1.1](#01_001.html#f1.1) 所示，你可以使用 SAP HANA express edition 在受支持的独立服务器上部署 SAP HANA cockpit。SAP HANA cockpit 也可以与现有的 SAP HANA 实例一起安装，或通过使用共享同一实例的独立租户数据库安装在现有实例中。在所有情况下，软件必须部署到受支持的 Linux 操作系统（OS）。请务必根据你选择的部署选项正确调整硬件大小。

独立安装和作为独立实例安装都需要使用 SAP HANA express edition。幸运的是，SAP HANA cockpit 的安装介质包含每个所需组件，并为你部署整个架构。安装介质还可以将 SAP HANA cockpit 部署到现有的 SAP HANA 数据库、SAP HANA XSA 应用程序和专用租户（如果你选择该选项）。

[![SAP HANA Cockpit 的部署选项](bilderklein/klein01_001.png)](img-f1.1.html)

**图 1.1** SAP HANA Cockpit 的部署选项

###### 关于安装和升级 SAP HANA Cockpit 的更多信息

有关安装、SAP HANA cockpit 架构和升级选项的更多信息，请参阅 SAP HANA 安装和更新指南，可在 [`http://s-prs.co/v498200`](http://s-prs.co/v498200) 获取。

### 1.1.2 开始使用 SAP HANA Cockpit

在开始在 SAP HANA 中管理安全性之前，你必须先学习如何访问 SAP HANA cockpit、创建 SAP HANA cockpit 用户并注册 SAP HANA 系统。在某些情况下，你还需要创建资源组，以限制用户在访问 SAP HANA cockpit 时查看注册的资源或 SAP HANA 数据库连接。在本节中，我们将引导你完成确定 SAP HANA cockpit URL、访问 SAP HANA cockpit 管理器、创建 SAP HANA cockpit 用户、创建资源组以及最后注册 SAP HANA 数据库的高级流程。请注意，本章不旨在作为 SAP HANA cockpit 的全面指南。相反，本章的目标是讨论使用 SAP HANA cockpit 管理 SAP HANA 安全模型部分所需的高级功能。

#### SAP HANA Cockpit 的重要 URL

