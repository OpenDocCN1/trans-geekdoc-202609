

[图 13-9：](#c13.xhtml#rc13-fig-0009) 你的 Azure VPN 网关需要位于虚拟网络中的专用子网上。

#### 本地网络网关

在 Azure 中，本地网络网关是一种代表你本地网络的资源。本地网络网关包含两到三个重要的配置值：

*   本地 VPN 终结点的公共 IP 地址
*   本地网络的 IP 地址范围
*   （可选）BGP 设置，如自治系统编号和对等互连 IP 地址

仔细思考一下，这很合理，因为 Azure 不仅需要识别隧道另一端的 VPN 聚合器，还需要识别那些促进混合云流量路由的远程网络段。

![警告](images/warning.png)请小心你在 Azure 中使用的私有 IP 地址范围。你最不想做的就是排查/解决本地网络与 Azure VNet 之间的 IP 地址冲突。请始终使用不重叠的 IP 地址范围。

#### 连接

最后是连接。Azure 连接资源是将本地网络网关和 VPN 网关绑定在一起的粘合剂，并定义了混合云握手。

在连接定义中，你需要定义连接类型（S2S、VNet 到 VNet 或 ExpressRoute）以及本地网关和 VPN 网关将存储用于相互身份验证和数据加密的预共享密钥。

![提示](images/remember.png)我讨论的所有 Azure 混合云组件都是 Azure 产品系列的一部分，因此本书迄今为止涵盖的所有内容——包括 RBAC、策略、分类标记等——都同样适用于此处，就像适用于任何其他资源一样。不要害怕应用你的新知识。

### ExpressRoute

ExpressRoute 与 Azure S2S VPN 类似，因为它是本地网络与 Azure VNet 之间始终开启的专用连接。ExpressRoute 的独特之处在于它是一种真正的专用 Azure 连接，可绕过公共互联网。ExpressRoute 链路不需要隧道协议。

ExpressRoute 线路带宽选项范围从 50 Mbps 到 10 Gbps。这意味着你可以拥有与本地网络速度一样快的 Azure 连接。传入 ExpressRoute 的数据免费，但传出数据会收费，除非你购买了 ExpressRoute 无限数据计划。

ExpressRoute 有两种对等互连选项，你可以单独使用或组合使用：

*   **Azure 专用对等互连：** 从本地到 Azure VNet 的 ExpressRoute 链路
*   **Microsoft 对等互连：** 从本地到 Office 365 或 Dynamics 365 的 ExpressRoute 链路

[图 13-10](#c13.xhtml#c13-fig-0010) 描绘了典型的 ExpressRoute 实现。

![图 13-10：ExpressRoute 代表性拓扑。](images/9781119612148-fg1310.png)

[图 13-10：](#c13.xhtml#rc13-fig-0010) ExpressRoute 代表性拓扑。

你需要两个边缘路由器来构建 ExpressRoute 连接。你还需要与本地第三方 ExpressRoute 连接提供商合作，以帮助你对等互连到 Microsoft 云平台。

大多数客户通过询问其互联网服务提供商、咨询 Microsoft 合作伙伴或进行传统的在线搜索来寻找本地 ExpressRoute 服务提供商。

![技术细节](images/technicalstuff.png)Microsoft 要求你在 ExpressRoute 线路的你这一侧提供两个边缘路由器，主要有三个原因：

*   以便 Microsoft 提供其 ExpressRoute 服务级别协议 (SLA)
*   为了提供故障转移冗余
*   以便你将两个链路组合起来以最大化带宽

在撰写本文时，ExpressRoute 提供三种连接模型：

*   **云交换共置：** 你将边缘设备共置于 ExpressRoute 服务提供商的数据中心。
*   **点对点以太网连接：** 你通过使用点对点以太网（也称为城域以太网）连接，从你的园区建立 ExpressRoute 线路。
*   **任意到任意 (IPVPN) 连接：** 你将 Microsoft Cloud 作为一个节点添加到现有的多协议标签交换广域网云中。

## Azure Arc 简介

对于 Azure 专业人士来说，Microsoft Ignite 2019 大会发布的最重要的新产品公告是 Azure Arc。Arc 是一种在任何位置部署 Azure 服务并将基于 Azure 的管理扩展到混合、多云基础设施的解决方案。

### Arc 用例

![技术细节](images/technicalstuff.png)在信息技术中，*治理* 是指你的企业为确保符合组织和法律要求而制定的政策和程序。在 Azure 中，治理还用于限制成本、最大化安全性，以及了解哪些组拥有哪些基于 Azure 的资源。

Azure VPN 和 ExpressRoute 选项将你的本地网络扩展到 Azure，以便你能更直接地将基于 Azure 的 VM 和其他资源集成到本地 IT 治理策略中。

相比之下，Arc 将 Azure 资源管理器 (ARM) 的核心元素引入你的本地网络，以及你在其他云中维护的网络。[图 13-11](#c13.xhtml#c13-fig-0011) 显示了 Azure 拓扑的概览。

![图 13-11：Arc 拓扑概览。](images/9781119612148-fg1311.png)

[图 13-11：](#c13.xhtml#rc13-fig-0011) Arc 拓扑概览。

在 [图 13-11](#c13.xhtml#c13-fig-0011) 中，请注意流程是如何工作的。无需任何 VPN 或 ExpressRoute 要求，你就可以将标记、策略和日志分析等核心 Azure 功能不仅扩展到本地网络，还可以扩展到其他云，如 Amazon Web Services 和 Google Cloud Platform。

Arc 带来的第二个价值主张是在本地环境中直接部署 Azure 资源的概念。例如，你可以使用 ARM 模板将 VM、数据库和 Kubernetes 群集部署到自己的数据中心，然后使用 Azure 工具将这些资源与云原生资源一起进行管理。

### Arc 产品系列成员

在撰写本文时，Arc 产品系列包含三个成员，使你能够完成特定任务：

*   **用于服务器的 Azure Arc：** 使用原生 Azure 工具管理 Azure 之外的虚拟机和物理机。
*   **用于数据服务的 Azure Arc：** 在本地或其他云环境中运行 Azure 数据服务，如 Azure SQL 数据库和 Azure Database for PostgreSQL。
*   **用于 Kubernetes 的 Azure Arc：** 跨环境部署和管理 Kubernetes 应用程序。

![警告](images/warning.png)用于服务器的 Arc 处于公开预览版，而用于 Kubernetes 和数据平台的 Arc 处于私有预览版状态。通常你必须申请才能参加私有预览版，而公开预览版功能可供部分或所有 Azure 客户使用。请注意，Microsoft 通常不支持 Azure 预览版功能，也不为其提供 SLA。一般指导原则是，你应仅在测试/开发环境中运行 Azure 预览版功能。

在撰写本文时，用于服务器的 Arc 是唯一公开可用的功能，因此以下部分将重点介绍该产品。

### 准备环境

在我的本地实验室环境中，我有两个 VM：一个运行 Windows Server 2019，一个运行 Ubuntu Linux 16.04。为了保持 Arc 环境整洁，我创建了一个资源组来容纳这两台本地机器。在本节中，我将向你展示如何使用用于服务器的 Arc 将这些机器接入 Azure 订阅。

请按照以下步骤在 Azure 门户中创建一个新的资源组：

1.  **搜索**资源组，**并浏览到“资源组”边栏选项卡。**
    “资源组”边栏选项卡随即出现。
2.  **在“资源组”边栏选项卡上，单击“添加”。**
    “创建资源组”边栏选项卡随即出现。
3.  **在“创建资源组”边栏选项卡上，填写“基本信息”表单，然后单击“查看 + 创建”。**

