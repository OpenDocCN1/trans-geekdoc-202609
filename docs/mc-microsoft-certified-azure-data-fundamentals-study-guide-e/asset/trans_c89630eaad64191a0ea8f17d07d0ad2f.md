

* `Service-level agreement (SLA)`—所有三个选项均提供高标准、符合行业标准的 SLA。PaaS 选项保证 99.99% 的 SLA，而 IaaS 为基础设施保证 99.95% 的 SLA，这意味着组织需要实施额外机制来确保数据库可用性。有关 Azure SQL SLA 的更多信息，请参阅以下文档：`https://docs.microsoft.com/en-us/azure/azure-sql/azure-sql-iaas-vs-paas-what-is-overview#service-level-agreement-sla`。

* `Migration timeline`—如果组织是将应用迁移到 Azure，而不是从零开始构建具有云原生设计的应用程序，则必须考虑此因素。组织可能会根据时间线的长短选择其中一个选项。例如，数据库可以在相对较短的时间内迁移到虚拟机，因为虚拟机可以托管与本地 SQL Server 实例相同版本的 SQL Server。Azure SQL MI 也提供与本地 SQL Server 几乎相同的功能平等性，但可能需要应用一些更改，尤其是当要迁移的数据库托管在较旧版本的 SQL Server 上时。

* `Administration`—Azure SQL 数据库和 Azure SQL MI 通过管理典型的数据库管理活动（如数据库备份、补丁、版本升级、HA 和威胁防护）来最大限度地减少开销。然而，这也限制了可以执行的自定义管理活动的范围。

* `Feature parity`—因为 Azure SQL 数据库将操作系统和数据库服务器组件与用户隔离，因此某些 SQL Server 功能在 Azure SQL 数据库中不受支持。这些功能包括跨数据库联接、CLR 集成和 SQL Server Agent。Azure SQL MI 与 SQL Server 几乎 100% 功能兼容，但仍保留一些差异，例如依赖于 Windows 相关对象的功能。Azure VM 上的 SQL Server 提供 100% 的功能平等性，因为它与托管在本地虚拟机上的 SQL Server 实例相同。然而，由于可能存在 SQL Server 版本差异，从旧版本的 SQL Server 迁移到 Azure VM 上的较新版本的 SQL Server 或其中一个 PaaS 选项时，可能会出现功能差异。可以使用数据迁移助手 (DMA) 发现已弃用的功能和与 PaaS 选项不兼容的功能。DMA 将在本章后面部分详细介绍。

各种 Azure SQL 产品具有不同级别的抽象和管理。[图 2.4](#c02.xhtml#c02-fig-0004) 说明了每个选项中抽象与管理工作量之间的关系。

![图 2.4 Azure SQL 抽象与管理工作量对比](images/c02f004.png)

[图 2.4](#c02.xhtml#R_c02-fig-0004) Azure SQL 抽象与管理工作量对比

如图所示，Azure VM 上的 SQL Server 需要最多的管理工作量，因为它对 SQL Server 实例和底层操作系统提供完全控制。这非常适合需要高度自定义操作系统和/或数据库映像，或需要对 SQL Server 引擎进行非常精细控制的场景。Azure SQL MI 从用户角度移除了操作系统层，但与 Azure SQL 数据库相比，它更像本地 SQL Server 实例，因为它提供了封装在 VNet 中的完全隔离环境，并包含系统数据库。将数据库托管在 Azure SQL MI 上的用户仍然可以从使用 PaaS 数据库中受益，因为补丁、SQL Server 版本升级、备份、HA、DR、数据加密、审核和威胁防护均由 Microsoft 在幕后处理。Azure SQL 数据库将操作系统层和数据库引擎与用户完全隔离。使用云原生最佳实践开发的绿地解决方案通常将 Azure SQL 数据库用作其后端关系数据库。

归根结底，选择合适的 Azure SQL 选项取决于解决方案需求以及对操作系统和数据库引擎所需的控制程度。以下各部分将详细探讨每个选项。

### Azure 虚拟机上的 SQL Server

组织希望将其应用程序迁移到云端有多种原因。最常见的原因可能是将其拥有或租赁的硬件和网络设备的维护工作卸载给云提供商。数据中心租约到期或硬件老化迫使许多公司重新思考其 IT 基础设施的管理方式。虽然许多组织会努力将其应用程序现代化为云原生，但其中大多数仍然使用依赖于 Azure SQL PaaS 产品中不可用的 SQL Server 功能的旧版应用程序。也可能存在需要对数据库引擎及其所在的操作系统进行精细控制的特定情况。出于这些原因，组织可能决定将其现有的 SQL Server 足迹迁移到 Azure SQL 的 IaaS 产品：Azure VM 上的 SQL Server。

就数据库引擎而言，Azure VM 上的 SQL Server 与托管在本地环境物理服务器上的 SQL Server 实例没有区别。这使开发人员和数据库管理员能够快速适应在 Azure 上使用 SQL Server。部署 Azure VM 上 SQL Server 的工程师可以选择三种方法之一：

* 从 Azure 市场选择可用的 SQL Server VM 映像之一。这些映像允许您轻松在所选操作系统上部署特定版本的 SQL Server。

* 在 VM 上安装您自己的 SQL Server 许可证。在 Azure 中拥有现有 VM 的用户可以选择使用现有许可证安装 SQL Server，以节省部署新 VM 的需求。

* 使用 Azure Migrate 将本地环境中的现有 VM 迁移到 Azure（迁移并转换）。Azure Migrate 是可用于评估和迁移本地基础设施到 Azure 的工具。托管 SQL Server 的 VM 可以使用 Azure Migrate 迁移到 Azure，而无需通过 Azure 市场部署新 VM。有关使用 Azure Migrate 将 VM 迁移到 Azure的更多信息，请参阅 `https://docs.microsoft.com/en-us/azure/migrate/migrate-services-overview#azure-migrate-server-migration-tool`。

利用 Azure 市场中可用的现成映像大大减少了在 Azure 中预配 SQL Server VM 所需的时间。SQL Server VM 有两种许可类型：即用即付和自带许可证 (BYOL)。即用即付通过按实例按分钟使用计费来简化许可成本。[表 2.1](#c02.xhtml#c02-tbl-0001) 概述了 Azure 中可用的即用即付 SQL Server 映像。

[表 2.1](#c02.xhtml#R_c02-tbl-0001) 可用的即用即付 SQL Server 映像

| 版本 | 操作系统 | 版本 |
| --- | --- | --- |
| SQL Server 2019 | Windows Server 2019 | Enterprise, Standard, Web, Developer |
| SQL Server 2019 | Ubuntu 18.04 | Enterprise, Standard, Web, Developer |
| SQL Server 2019 | Red Hat Enterprise Linux (RHEL) 8 | Enterprise, Standard, Web, Developer |
| SQL Server 2019 | SUSE Linux Enterprise Server (SLES) v12 SP5 | Enterprise, Standard, Web, Developer |
| SQL Server 2017 | Windows Server 2016 | Enterprise, Standard, Web, Express, Developer |
| SQL Server 2017 | Red Hat Enterprise Linux (RHEL) 7.4 | Enterprise, Standard, Web, Express, Developer |
| SQL Server 2017 | SUSE Linux Enterprise Server (SLES) v12 SP2 | Enterprise, Standard, Web, Express, Developer |
| SQL Server 2017 | Ubuntu 16.04 LTS | Enterprise, Standard, Web, Express, Developer |
| SQL Server 2016 SP2 | Windows Server 2016 | Enterprise, Standard, Web, Express, Developer |
| SQL Server 2014 SP2 | Windows Server 2012 R2 | Enterprise, Standard, Web, Express |

