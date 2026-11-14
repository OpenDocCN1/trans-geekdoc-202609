

除了众多优势之外，Kubernetes 还带来了一些必须解决的安全挑战。因此，了解容器化环境中的各种安全风险至关重要。

启用 Microsoft Defender for Containers 时，Azure Kubernetes Service 集群和 Azure Arc 启用的 Kubernetes 集群（预览版）将受到默认保护。启用 Microsoft Defender for Containers 时，安全建议会显示在 Defender for Cloud 仪表板上，如图 7.7 所示。

## 图 7.7 Microsoft Defender for Containers

![](img/5ab9852bf401dd309bf0f81797a91445_363_0.png)

Defender for Cloud 为 Azure Kubernetes Service 集群提供运行时防护并收集节点信号，无需安装代理软件。Defender 配置文件会部署到每个节点上，提供运行时防护并收集节点信号。Azure Policy 的 Kubernetes 插件包含用于准入控制策略的集群和工作负载配置。图 7.8 描绘了 Azure Kubernetes Service 集群。

- Defender 配置文件包含一个 DaemonSet，这是一组专注于收集清单和安全事件的容器。
- 开源策略代理 (OPA) 的 Gatekeeper 是准入控制器 Webhook，它在集群上实现大规模执行和大规模防护。

## 图 7.8 Azure Kubernetes Service 集群

![](img/5ab9852bf401dd309bf0f81797a91445_364_0.png)

Pod 安全标准和密钥是 Kubernetes 的安全组件。另一方面，Azure 的安全组件包括 Active Directory、Microsoft Defender for Containers、Azure Policy、Azure Key Vault、网络安全组和编排的集群升级。

以下安全组件与 AKS 结合，可提供以下功能：

- 提供身份验证和授权机制。
- 可以使用 AKS 的 Azure Policy 保护您的应用程序。
- 借助 Microsoft Defender for Containers，您可以从开发到部署获得端到端的洞察。
- 定期更新 AKS 集群的操作系统安全性和 Kubernetes 版本。
- 安全地访问敏感凭据和 Pod 流量。

## 摘要

了解组织与 Microsoft 之间安全职责的分类至关重要。

通过将安全职责转移给云提供商，可以提高安全覆盖率，从而使组织能够将注意力集中在其他业务优先事项上，并重新分配其安全资源。

本章介绍了 Azure PaaS 工作负载安全基线的简要描述以及 Microsoft Defender for Cloud 支持哪些 Azure PaaS 工作负载。您还学习了如何为 IaaS VM 指定安全基线，以及无论操作系统如何都可以实施的一般准则。我们讨论了如何在 SaaS 环境中使用 Microsoft 安全分数跟踪安全态势随时间的改善，以及 IoT 工作负载的安全要求。

此外，您还了解了 Azure App Service 如何使用 Microsoft Defender for App Service 提供态势管理和威胁检测。讨论了数据和存储工作负载的要求。此外，还讨论了容器编排和安全要求。

## 考试要点

### 能够识别 SaaS、PaaS 和 IaaS 服务的安全基线。

安全基线是标准化文档，描述 Azure 产品功能以及通过改进工具、跟踪和安全功能增强安全性的最佳配置。

对于 IaaS、SaaS 和 PaaS，在为云工作负载设计安全策略时，您需要考虑不同的云服务会有额外的安全要求。

物理基础设施位于堆栈底部，Microsoft 在此层缓解常见风险和职责。由于 Microsoft 持续监控 Microsoft 云，攻击者试图攻击它几乎没有意义。除非攻击者拥有大量资金和资源，否则不太可能针对 Microsoft 云。

### 识别 IoT 工作负载的安全要求。

OT 网络用于通过物联网 (IoT) 连接数十亿台联网设备。由于缺乏对安全性的重视，传统系统无法保护 IoT 和 OT 网络。每一次新的创新浪潮都会使 IoT 设备和 OT 网络面临越来越多的攻击面。

深度防御策略对于保护物联网 (IoT) 基础设施至关重要。此外，将 SIEM 解决方案与安全 IoT 解决方案集成以进行威胁检测也至关重要。

### 能够识别数据工作负载的安全要求，包括 SQL Server、Azure SQL、Azure Synapse 和 Azure Cosmos DB。

必须保护本地数据和云数据，防止意外和恶意访问。意外访问是指用户获得了不应访问的数据。恶意内部人员或外部攻击者故意试图访问数据，可能导致意外的数据泄露、数据破坏以及违反数据安全和隐私法规。恶意内部人员可能滥用数据，或受到外部攻击者的影响，后者可以删除、篡改、外泄并加密您的敏感数据。

Microsoft Defender for SQL 可以管理数据库的安全态势，因此您可以将其用于数据工作负载。SQL 数据库、SQL 托管实例和 Azure Synapse Analytics 均与 Microsoft Defender for Cloud 兼容。该产品可以识别数据库漏洞并加以缓解，还可以检测可能表明数据库基线安全威胁的异常活动。

### 能够识别 Web 工作负载的安全要求，包括 Azure App Service。

Azure App Service 是一种基于 HTTP 的服务，用于部署 Web 应用程序、REST API 和移动后端。在考虑 Azure App Service 时，您需要考虑 Web 工作负载的安全要求。基于 Windows 和 Linux 的环境都与应用程序兼容。

为提高 Web 工作负载的整体安全态势，如同任何其他云工作负载一样，需要持续的安全评估。借助云的规模，Microsoft Defender for App Service 可以识别针对 Web 应用程序的攻击。攻击者会探测 Web 应用程序的弱点并加以利用。Azure 应用程序的请求会经过多个网关，在被路由到特定环境之前，这些网关会对请求进行检查和记录。

### 能够识别存储工作负载的安全要求，包括 Azure Storage。

每秒输入/输出 (IOP) 操作适用于需要快速且一致响应时间的工作负载。Azure 存储帐户包含您在 Azure 存储帐户中使用的所有数据对象，包括 Blob、文件共享、队列、表和磁盘。

为提高 Web 工作负载的整体安全态势，如同任何其他云工作负载一样，需要持续的安全评估。

### 能够识别容器的安全要求。

容器是在主机系统上运行应用程序的轻量级、隔离的沙箱。容器构建在主机操作系统的内核（操作系统的底层管道）之上，仅包含应用程序以及一些轻量级 API 和服务。尽管容器与主机共享内核，但它无法完全访问内核，相反，容器获得的是系统的隔离（有时是虚拟化）视图。

您可以查看 Defender for Cloud 的建议页面，如果它在您的云中发现错误配置，可以通过将其与应用于订阅的计划进行比较来修复问题。Defender for Cloud 在发现错误配置时会生成安全建议。

### 能够识别容器编排的安全要求。

容器编排系统 Kubernetes 已成为许多组织计算堆栈的重要组成部分。可以使用三种服务在 Azure 上轻松部署和管理 Kubernetes 集群。Kubernetes 是一种流行的解决方案，拥有强大的开发者社区。Azure Kubernetes Service (AKS)、Azure Container Service Engine (ACS-Engine) 和 Azure Container Instance 均可用。

当 Defender for Cloud 保护托管在 Azure Kubernetes Service 中的集群时，它会收集无代理且无摩擦的审计日志数据。

