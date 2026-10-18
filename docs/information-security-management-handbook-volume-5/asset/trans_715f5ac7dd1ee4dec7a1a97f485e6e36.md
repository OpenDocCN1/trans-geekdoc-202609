

Centrify DirectAudit 帮助符合法规要求，进行深入故障排除，并保护 UNIX 和 Linux 系统免受内部威胁。DirectAudit 的详细日志增强了合规性报告，并通过显示哪些用户访问了哪些系统、执行了哪些命令以及对关键文件和数据做了哪些更改，帮助发现可疑活动。使用 DirectAudit，还可以通过重播和报告可能导致系统故障的用户活动，进行即时的深入故障排除。并且，其对当前用户会话的实时监控可帮助发现可疑活动。

DirectAudit Agent 以加密、压缩的格式持续将用户会话活动传输到 DirectAudit Collector 服务。Collector 服务随后将数据存储在中央 SQL Server 存储库中，提供企业级性能和可扩展性。为了提高可靠性，DirectAudit Agent 在没有网络连接时仍会继续记录会话数据，并在网络可用时将其转发到 DirectAudit Collector 服务。当 DirectAudit Agent 的部署规模达到数百或数千台时，Centrify 还支持多个 DirectAudit Collector 服务之间的负载均衡。

在 DirectAudit 控制台中，右键单击可以重播任何受审计系统上的任何用户会话，以查看执行了哪些命令、对关键文件和数据做了哪些更改，以及出现了哪些系统输出。暂停、倒带或快进类似于使用录像机。此播放功能提供了一种监控活动、排查可能导致系统故障的更改或记录系统配置任务的工具。

DirectAudit 控制台的开箱即用视图可提供对活动会话和历史会话的可见性，或者自定义构建的视图可显示特定用户、机器、时间段或其他条件的会话。它们还可以执行全文搜索，例如，查找所有会话中所有密码命令的实例。DirectAudit 采用非专有 SQL 数据格式，使通过第三方工具进行报告和查询成为可能。

DirectAudit 控制台提供了对每个受审计 UNIX 和 Linux 系统上每个用户会话的集中式、实时视图。对于每个会话，可以查看谁已登录，并可以立即深入查看他们当前正在做什么。控制台有助于发现可疑活动，并帮助排查系统问题。

# IBM Tivoli Compliance Insight Manager

Consul Insight Suite 集成了日志管理、基于规则和策略的监控以及报告。它对特权用户活动进行标准化、分析和报告。

Tivoli Compliance Insight Manager 提供了一个易于使用的安全合规性仪表板，用于汇总数十亿个日志文件。通过此仪表板，您可以快速了解安全合规性状况，将用户活动和安全事件与可接受使用框架进行比较，并监控特权用户和相关安全事件（[图 4.1](#9781466508507_epub_c04_r1.htm#fig_4.1)）。

IBM Tivoli Consul Manager 亮点：

![](OEBPS/images/box.jpg) 通过自动化日志管理收集、存储、调查和检索日志

![](OEBPS/images/box.jpg) 对数据库、应用程序、服务器和大型机执行特权用户监控和审计（PUMA）

![](OEBPS/images/box.jpg) 通过企业合规性仪表板和灵活的报告分发帮助自动化审计报告

![](OEBPS/images/box.jpg) 通过高级策略和报告定义引擎创建自定义合规性模块

![](OEBPS/images/box.jpg) 通过将捕获的本地审计日志数据转换为易于理解的语言来支持审计需求

![](OEBPS/images/box.jpg) 通过高级工具包轻松添加新的日志收集器和解析器

![](OEBPS/images/box.jpg) 通过与众多 IBM Tivoli 身份和访问管理产品以及高级数据库集成，利用完整的审计和合规性基础架构

![](OEBPS/images/fig_4.1.jpg)

![](OEBPS/images/line-2.jpg)

**图 4.1 Tivoli Compliance Insight Manager 捕获有关人员和技术的安全信息，用于审计和合规性报告**

# 特权用户控制解决方案

# e-DMZ 全特权访问管理（TPAM）套件

TPAM 套件是一个模块化解决方案，由基于两个设备（密码自动存储库和 eGuardPost）的以下单独授权模块组成（[图 4.2](#9781466508507_epub_c04_r1.htm#fig_4.2) 和 [图 4.3](#9781466508507_epub_c04_r1.htm#fig_4.3)）。

![](OEBPS/images/box.jpg) 特权密码管理（PPM）

![](OEBPS/images/box.jpg) 应用程序密码管理

![](OEBPS/images/box.jpg) 特权会话管理

![](OEBPS/images/box.jpg) 特权命令管理

![](OEBPS/images/fig_4.2.jpg)

![](OEBPS/images/line-2.jpg)

**图 4.2 TPAM 套件**

![](OEBPS/images/fig_4.3.jpg)

![](OEBPS/images/line-2.jpg)

**图 4.3 全特权访问管理**

# 特权密码管理模块

提供跨异构系统和应用程序部署的特权密码的安全存储、发布控制和变更控制。e-DMZ 的密码自动存储库（PAR）提供企业级功能、特性和可扩展性。

# 应用程序密码管理模块

通过 PAR 支持的强大 CLI/API，可以将硬编码密码替换为简单的调用脚本或程序调用 PAR，以满足应用程序到应用程序（A2A）、应用程序到数据库（A2DB）和应用程序到系统（A2S）的需求。

# 特权会话管理模块

eGuardPost 提供完整的会话管理和控制，包括细粒度资源访问控制、活动会话监控以及以高效格式进行完整会话录制以供将来重播。支持的广泛会话代理类型包括：SSH、RDP、http/https、ICA、telnet、x5250 和 VNC。

# 特权命令管理模块

通过 eGuardPost 提供，支持将特权访问控制扩展到特权命令级别。它能够控制、记录和监控会话，并可以将用户的连接限制为特定命令，适用于 Unix/Linux 和 Windows 系统。

# Cyber-Ark 特权身份管理（PIM）套件

Cyber-Ark 的特权身份管理（PIM）套件是一种企业级、全生命周期解决方案，用于保护、管理、自动更改和监控与特权账户相关的所有活动。这包括 UNIX/Linux 上的 Root 账户、Windows 中的 Administrator、Cisco Enable、Oracle 系统 sys、MSSQL SA、SAP 应用服务器，以及许多其他账户，例如紧急或“Firecall” ID。

PIM 套件包括以下产品：

![](OEBPS/images/box.jpg) 企业密码保险库

![](OEBPS/images/box.jpg) 应用程序身份管理器

![](OEBPS/images/box.jpg) 特权会话管理器

企业密码保险库（EPV）使组织能够保护、管理、自动化、存储、保障并记录与特权、共享和提升账户相关的所有活动。EPV 支持超过 50 种操作系统、数据库、防火墙、网络设备、业务套件和关键系统。

应用程序身份管理器（AIM）提供一套全面的软件和服务，用于安全地管理嵌入式、特权应用程序和脚本账户，并消除使用硬编码凭据。AIM v5.5 包含安全且强大的身份验证方法。

