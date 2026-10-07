

# 12
## Cloud Logging（云日志记录）

日志记录提供了环境的可视性，并有助于故障排除和事件响应。在本章中，我们将讨论什么是 Cloud Logging、它的工作原理、不同类型的日志及其应用，以及如何收集、存储、分析和导出日志。我们还将讨论日志产生者和消费者分别是谁，以及如何将日志导出到集中式日志解决方案或运行在本地或云端的安全信息和事件管理（SIEM）系统中。最后，我们将讨论如何安全地存储和保存日志，以满足合规性要求。

在本章中，我们将涵盖以下主题：

- Google Cloud Logging 概览
- 理解日志类别
- 日志管理
- 日志记录和审计最佳实践

## Google Cloud Logging 简介

Cloud Logging 是 Google Cloud 上的一项托管服务。它使你能够根据收集的日志进行收集、存储、搜索、分析、监控并设置告警。你可以使用 Cloud Logging 从 150 多个应用程序、Google Cloud 组件、第三方云服务提供商以及任何云平台的组合（混合环境）中收集日志数据。Cloud Logging 以前被称为 Stackdriver，是 Google Cloud 运营套件的一部分。它包含一个名为 Logs Explorer（日志查看器）的控制界面、日志查询以及一个用于程序化管理日志的 API。

![](img/f681dfc12450e3a4c257352b70dbceca_342_0.png)

如图 12.1 所示，Cloud Logging 是 Google Cloud 运营套件的四个组件之一。让我们深入探索这些组件。Cloud Logging 捕捉所有日志并提供搜索和过滤功能。Cloud Logging 从日志中派生指标，创建仪表板、离群值，并提供导出日志用于报告和分析的能力。我们将在本章的后后部分详细介绍这些内容。

应用性能管理（APM）将 Cloud Logging 和 Cloud Monitoring 的监控与故障排除能力与 Cloud Trace、Cloud Debugger 和 Cloud Profiler 结合，帮助降低延迟和成本，从而运行更高效的应用程序。这超出了 Google 专业安全工程师考试的范围。

此外，Google Cloud 运营套件通过对对 Google Cloud 和 Amazon Web Services 的支持，提供了多云能力，还可以监控本地资源并与合作伙伴解决方案集成。

## Google Cloud Logging 简介

默认情况下，运营套件监控所有系统指标，包括 Google Compute Engine (GCE) 和 Google Kubernetes Engine (GKE)。运营套件还监控和托管服务，如 Datastore 和 BigQuery。你可以利用运营套件的 Monitoring API 与用户交互并收集业务指标。你还可以在计算实例上部署监控代理，以收集支持服务的更低级和第三方指标（例如磁盘延迟/IO）。图 12.2 展示了运营套件的能力，以及云资源如何生成被不同操作功能消耗的信号和遥测数据。

![](img/f681dfc12450e3a4c257352b70dbceca_343_0.png)

图 12.2 – 运营套件层

现在我们将介绍一些基本的 Cloud Logging 原理以及一些重要术语。理解这些内容非常重要，因为它们将贯穿全文并在考试中进行评估：

- **日志条目（Log entry）：** 日志条目是计算机系统状态的记录或特定事件或交易的描述。每个日志条目根据生成日志的服务包含不同类型的数据。大多数日志条目包含以下属性：
    - 时间戳，指示事件发生的时间或被 Cloud Logging 接收的时间。
    - 产生日志条目的资源。
    - 负载（payload），也称为消息（message），以非结构化文本数据或 JSON 格式的结构化文本数据形式提供。
    - 所属日志的名称。某些日志带有关联元数据，例如每个关联日志条目的严重程度。

## Cloud Logging

- **日志（Logs）：** 在 Google Cloud 资源（如 Google Cloud 项目）中，日志是日志条目的命名集合。如果没有日志条目，就不会有日志。日志名称通过日志条目所属资源的完整路径识别，随后紧跟一个简单的日志 ID（例如 syslog），或包含日志写入者的结构化 ID（例如 compute.googleapis.com/activity）。
- **保留期（Retention period）：** 日志条目在 Cloud Logging 中存储特定的一段时间，被称为保留期。每种日志类型都有不同的保留期。你有能力创建自定义保留期，以比 Cloud Logging 提供的默认值更长的时间存储日志。

- **查询和过滤器（Queries and filters）：** 查询使用日志查询语言编写。查询返回匹配的日志条目。Logs Explorer 和 Logging API 都使用查询来选择和显示日志条目。

过滤器是日志查询语言中的查询，用于日志将匹配给定表达式的日志定向到存储目的地。过滤器还用于将匹配的日志重定向到 Cloud Monitoring。

- **日志路由器（Log Router）：** 为了到达 Cloud Logging API，所有收集的日志必须首先通过日志路由器。对于每个日志条目，日志路由器会检查预先存在的规则。我们将在本章稍后详细介绍路由器。

- **目的地（Sinks）：** 目的地由过滤器和一个存储目标组成。过滤器日志发送到目的地。

- **基于日志的指标（Log-based metrics）：** 你可以为日志定义指标并据此创建告警。

- **访问控制（Access control）：** 你控制谁访问日志。

每个日志类型都分为安全、用户或平台。我们稍详细查看这些类别。

## 日志类别（Log categories）

在本节中，我们大致将日志分为三类。我们将从安全角度查看安全、用户和平台日志。

![](img/f681dfc12450e3a4c257352b70dbceca_345_0.png)

图 12.3 – 日志类别

Cloud Logging 识别出三类：安全、用户和平台。我们将关注安全类别。

## 安全日志

Cloud Logging 提供两种形式的安全日志：审计日志（Cloud Audit Logs）和访问透明性（Access Transparency）。审计日志为每个项目、文件夹和组织生成以下类型的日志：

- **管理员活动日志（Admin Activity audit logs）：** 包含 API 调用和更改设置的操作。创建虚拟机或更改 IAM 权限都是管理员活动日志的示例。你无法配置、排除或禁用这些日志类型。出于安全考虑，它们始终会被记录。即使禁用了 Logging API，也会创建管理员活动日志。管理员活动的保留期为 400 天。
- **数据访问日志（Data Access audit logs）：** 显示谁在什么时候访问了什么数据以及执行了什么操作。数据访问日志保留 30 天。支持所有 Google Cloud 服务。数据访问日志默认禁用。
- **系统事件日志（System Event audit logs）：** 资源配置的事件记录在系统事件日志中。这些日志由系统自动生成，而不是由用户生成。系统事件日志无法配置且始终会被写入。
- **策略拒绝日志（Policy Denied audit logs）：** 当 Google Cloud 服务因安全策略拒绝用户或服务帐户访问时，会创建策略拒绝日志。VPC 服务控制决定策略并发送 Cloud Logging 策略拒绝日志。你的项目需要为策略拒绝日志存储付费。你无法禁用策略拒绝日志，但可以将其排除。

下一种安全日志是访问透明性。访问透明性提供了 Google 人员访问你的 Google Cloud 内容时的日志。访问透明性日志可以帮助你跟踪组织相对于法律和监管要求的合规状况。我们将在第3章“信任与合规”中详细介绍访问透明性。

