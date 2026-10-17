
![图 13-2：向 Azure Migrate 项目添加工具。](img/9781119612148-fg1302.png)

7. 在“选择迁移工具”边栏选项卡上，选择“Azure Migrate: 数据库迁移”。

8. 取消选择“跳过添加迁移工具”。

9. 返回“Azure Migrate - 数据库”边栏选项卡，单击链接以下载数据迁移助手 (DMA)。

   DMA 是一款免费的桌面应用，你将在管理工作站上下载并运行它。

图 13-3 显示了 DMA 界面。

![图 13-3：使用 DMA 评估本地 SQL Server 数据库的 Azure 就绪情况。](img/9781119612148-fg1303.png)

运行 DMA 时，你将针对以下四个目标之一对本地 SQL Server 数据库进行建模：

- Azure SQL 数据库
- Azure SQL 数据库托管实例
- Azure 虚拟机上的 SQL Server
- SQL Server

DMA 会根据你定义的 Azure 数据库选项检查数据库兼容性，并检查功能对等性，以确保你没有在本地使用 Azure 中不可用的功能。它还允许你将评估结果上传到 Azure Migrate 项目，这将进入下一阶段：迁移。

![技术内容](img/technicalstuff.png)Microsoft 设计 Azure Migrate 无需安全虚拟专用网络 (VPN) 连接即可工作。相反，你与 Azure 的连接使用 TLS/SSL 协议进行加密。因此，你可以确信在迁移过程之前、期间和之后的数据隐私。

### 使用 DMS 执行数据库迁移

在 Azure 中，你可以使用数据库迁移服务 (DMS) 将评估过的本地 SQL Server 数据库迁移到 Azure。DMS 支持其他多个数据库平台，包括：

*   MongoDB
*   MySQL
*   AWS RDS for MySQL
*   PostgreSQL
*   AWS RDS for PostgreSQL
*   Oracle

请按照以下步骤在 Azure 门户中开始使用 DMS：

1.  在你的 Azure Migrate - 数据库项目中，在“Get Started with DMS”标题下方，单击链接以创建 DMS 服务实例。

    将出现“创建迁移服务”边栏选项卡。

2.  完成“创建迁移服务部署”边栏选项卡。

    你需要将数据库迁移项目放置在你主区域的虚拟网络上。你还需要选择一个定价层。除了速度和容量之外，标准和高级定价层之间最大的区别在于只有高级层支持联机迁移。在我的咨询工作中，我发现大多数客户选择高级层，因为联机迁移是他们的业务需求。

3.  打开你的 Azure 数据库迁移服务实例，然后单击“新建迁移项目”。

4.  为项目指定一个有意义的名称，并完成“新建迁移项目”表单，如下所示：

    *   **源服务器类型：** 选择源服务器类型，例如 SQL Server。
    *   **目标服务器类型：** 选择你要迁移到的服务器类型，例如 SQL 数据库。
    *   **活动类型：** 如果你选择了高级定价层，你的选项包括脱机数据迁移、仅架构迁移、联机数据迁移和仅创建项目外壳。

迁移向导将接管后续工作，根据你的源数据库平台，包含多个阶段和选项。

一个重要提示：虽然数据库评估不需要 VPN，但你需要在本地数据库服务器和 Azure 之间建立现有的、安全的连接路径，才能使用 Azure 数据库迁移服务完成数据库迁移。这可以是点到站点 VPN、站点到站点 VPN 或 ExpressRoute 线路。

### 使用 DMA 执行数据库迁移

如果建立 VPN 不可行，你可以使用 DMA 工具执行数据库迁移，它使用标准安全 Web 协议且不需要 VPN。图 13-4 显示了该界面。

你可能会问：“Tim，既然 DMA 不仅可以评估我的本地数据库，还可以迁移它们，我为什么要使用 DMS？”

![图 13-4：DMA 工具既可以执行数据库迁移，也可以执行评估。](img/9781119612148-fg1304.png)

图 13-4： DMA 工具既可以执行数据库迁移，也可以执行评估。

这个问题的答案有两方面：

*   只有 DMS 支持非 SQL Server 数据库的迁移。
*   DMS 旨在大规模执行迁移。

总之，如果你只需要迁移少量 SQL Server 数据库，你可能不需要 DMS。但如果你跨供应商在大量潜在的巨型数据库上运行，DMS 非常合适。

## 服务器迁移选项

最后一类迁移是服务器迁移。迁移服务器最方便的方法是使用 Azure Site Recovery (ASR)，它支持物理服务器和虚拟服务器，并完全支持 VMware 和 Hyper-V 虚拟化环境。

但是，你也可以使用 `AzCopy` 将本地 VHD 迁移到 Azure 存储帐户；然后将上传的 VHD 转换为托管磁盘。

### VHD 上传

像 `AzCopy` 这样的工具的一个常见且仍然有效的用途是将通用 VHD 从本地迁移到 Azure，用于 Azure 虚拟机 (VM) 部署。为此，你首先上传通用的第 1 代 VHD。

![警告](img/warning.png)虽然 Azure 正在逐步推出对 Hyper-V 第 2 代 VHDX 文件的支持，但我建议你走稳妥路线，仅上传第 1 代 VHD。在将 VM 磁盘传输到 Azure 之前，你可能需要对其进行一些格式转换，特别是如果你使用 VMware 或其他非 Microsoft 虚拟化管理程序时。

当你将通用 VHD 放入存储帐户后，可以使用 Azure PowerShell 创建托管磁盘。请按以下步骤操作：

1.  创建一些变量，如下所示：

    ```
    $vmName = "vm-template"
    $rgName = "myResourceGroup"
    $location = "EastUS2"
    $imageName = "myImage"
    ```

2.  创建对 Azure 中通用 VHD 的引用，如下所示：

    ```
    $osVhdUri = https://mystorageaccount.blob.core.windows.net/vhdcontainer/vhdfilename.vhd
    ```

3.  运行一系列 AzImage cmdlet 以创建映像：

    ```
    $imageConfig = New-AzImageConfig -Location $location
    $imageConfig = Set-AzImageOsDisk -Image $imageConfig -OsType Windows -OsState Generalized -BlobUri $osVhdUri
    $image = New-AzImage -ImageName $imageName -ResourceGroupName $rgName -Image $imageConfig
    ```

当你的托管映像就位后，你可以基于该映像部署新 VM。在“创建虚拟机”边栏选项卡的“基本信息”选项卡上，单击“浏览所有公共和专用映像”，然后切换到“我的项目”选项卡，如图 13-5 的合成图像所示。第 5 章 涵盖了创建 Azure VM 的内容。

![图 13-5：基于你自己的自定义 VHD 映像部署 Azure VM。](img/9781119612148-fg1305.png)

图 13-5： 基于你自己的自定义 VHD 映像部署 Azure VM。

### Azure Migrate：服务器评估

另一种选择是将 Azure Migrate 用作本地服务器迁移的运营基地。请按照以下步骤开始操作：

1.  在 Azure 门户中，浏览到“Azure Migrate”边栏选项卡，选择“服务器”，然后单击“添加工具”。

2.  完成“迁移项目”选项卡。

    你需要填写元数据：订阅、资源组、迁移项目名称和地理位置。

3.  在“选择评估工具”选项卡上，选择“Azure Migrate: 服务器评估”。

    Microsoft 允许某些独立软件供应商合作伙伴将其工具包含在此列表中。图 13-6 显示了此界面。

4.  在“选择迁移工具”选项卡上，单击“Azure Migrate: 服务器迁移”。

![图 13-6：向 Azure Migrate 服务器迁移项目添加工具。](img/9781119612148-fg1306.png)

图 13-6： 向 Azure Migrate 服务器迁移项目添加工具。

然后，你可以启动发现和评估过程，该过程根据你在本地拥有 Hyper-V 还是 VMware 环境而采取不同的形式。

#### 发现和评估工作流

你下载一个 Migrate VM 设备，在本地网络中部署它，并让它完成工作。该设备能很好地枚举所有本地服务器，并报告它们如何转换为 Azure VM。

收集器设备还将其发现和评估数据发送到你的迁移项目，以便进行集中跟踪。交付成果是一系列 Microsoft Excel 电子表格和发送到你项目的迁移数据。

图 13-7 显示了一个示例服务器评估报告。除了提供 VM 大小建议外，服务器评估引擎还提供成本估算。在我担任 Azure 解决方案架构师的工作中，我从未遇到过不将最小化成本作为主要关注点的客户。

![FIGURE 13-7: Azure server assessment reports include graphs and table data.](img/9781119612148-fg1307.png)

图 13-7： Azure 服务器评估报告包含图表和表格数据。

![Tip](img/tip.png) 在其文档中，Microsoft 建议您尽可能长时间地运行评估，以收集本地服务器性能的所有峰值和低谷。运行评估两周到一个月或更长时间并不罕见。

### Azure Migrate：服务器迁移

在 Migrate 出现之前，通过复制迁移本地服务器的选项是使用恢复服务保管库和 ASR。您仍然使用 ASR，但将该技术合并到 Migrate 中的工作正在进行中。

以下是发生情况的高级概述：

1.  在 Azure 中为您的本地 VM 和物理服务器创建虚拟网络环境。
2.  将本地服务器的磁盘复制到 Azure，直到其数据同步。
3.  从本地环境执行故障转移到 Azure 虚拟网络。
4.  停止复制。
5.  退役您的本地服务器，因为您不再需要它们。
6.  继续在 Azure 中使用您的服务。

您不需要 VPN 或 ExpressRoute 连接即可执行此 Azure Migrate/ASR 复制。最终，VMware 环境的复制过程将无需代理（Hyper-V 已经是无代理的），但在撰写本文时，无代理 VMware 复制处于预览状态。

![Technical stuff](img/technicalstuff.png) 在 Migrate 术语中，`服务器迁移` 意味着“复制、故障转移，且不故障回复到本地环境。”

Migrate 服务器迁移的优点是复制意味着近乎零停机时间。缺点是初始复制的冲击可能很大，如果您有按流量计费的 Internet 连接，成本可能很高。

## 混合云选项

我将通过介绍将本地环境扩展到 Azure 的两种主要方式来结束本章：

*   站点到站点 (S2S) VPN
*   ExpressRoute 线路

部署混合云在成本、人力和时间方面都是密集型的，因此我无法在本书中深入介绍该过程的细节，但我希望能让您对这些技术有一个全局的了解。

### S2S VPN

VPN 是在不安全介质（Internet）上的安全连接。Azure S2S VPN 是始终在线的安全连接，它们通过使用 Internet 协议安全 (IPSec) 和 Internet 密钥交换 (IKE) 安全协议来隧道传输您的 Internet 流量。

在本地网络和 Azure 虚拟网络之间建立 VPN 隧道的价值主张是多方面的。VPN 允许您执行以下操作：

*   将 Azure VM 加入本地 Active Directory 域。
*   使用 System Center 或其他配置管理和监视平台管理 Azure VM。
*   使用 Azure 管理解决方案管理本地 VM。
*   确保本地环境与 Azure 之间的数据机密性。

*Extend*（扩展）是 Azure 混合云的一个恰当用词，因为混合云使您能够将本地网络提供给 Azure 订阅使用，反之亦然。

让我带您了解 S2S VPN 的各个部分和组件。图 13-8 显示了 Azure 混合云的高级视图：

*   本地网关
*   虚拟网络网关
*   本地网络网关
*   连接

#### 本地 VPN 网关

Azure 需要知道您本地 VPN 网关的公共 IP 地址以及所有本地虚拟局域网 (VLAN) 的网络地址。Azure 将此信息存储在一个称为本地网络网关的资源中；您负责使用 Azure 网关的公共 IP 地址和预共享密钥来配置本地 VPN 网关。

![FIGURE 13-8: Representative Azure S2S VPN topology.](img/9781119612148-fg1308.png)

图 13-8： 代表性 Azure S2S VPN 拓扑。

![Tip](img/tip.png) 我建议您阅读“关于 VPN 设备和站点到站点 VPN 网关连接的 IPsec/IKE 参数”（这文章标题真长，不是吗？）[`https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices`](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。该文章列出了 Microsoft 保证可与 Azure 配合使用的所有经过验证的 VPN 设备。您很可能会找到由设备制造商或 Microsoft 提供的详细配置指南链接。

Azure VPN 使用常规的 VPN 和路由协议，如 IPSec、IKE 和边界网关协议 (BGP)，因此即使您的硬件不在 Microsoft 的验证设备列表中，您也不应该在配置 VPN 隧道的本地方面遇到困难。

#### 虚拟网络网关

此 Azure 资源称为虚拟网络网关，而不是 VPN 网关，因为它是多功能的。使用此单一资源，您可以创建以下任意组合的连接：

*   **S2S VPN：** 您可以在本地网络或另一个云托管网络与您的 Azure VNet 之间配置此安全 IPSec 隧道。
*   **VNet 到 VNet VPN：** 您可以在两个 Azure 虚拟网络之间配置此安全 IPSec 隧道。严格来说，由于 VNet 对等互连，此网关不再是必需的。
*   **点到站点 VPN：** 您可以将特定客户端计算机配置为创建其自己的专用 VPN 隧道以进入您的虚拟网络。有关详细信息，请参阅本章后面的边栏“Azure P2S VPN”。
*   **ExpressRoute：** 您可以配置一个从本地环境到 Azure 的高速、始终在线的连接，该连接完全绕过 Internet。

也就是说，我将使用 *VPN 网关* 来表示配置了一个或多个 S2S VPN 连接的虚拟网络网关。是的，没错：单个 VPN 网关可以同时管理多个连接。

![Tip](img/tip.png) 当与 BGP 动态路由协议结合使用时，VPN 网关支持主动-主动故障转移方案以实现容错。有关更多信息，请阅读“BGP 和 Azure VPN 网关概述”[`https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-bgp-overview`](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-bgp-overview)。

VPN 网关有四种库存单位 (SKU) 可用；表 13-1 总结了它们的主要区别。

表 13-1 Azure VPN 网关 SKU 对比

| **网关类型** | **最大带宽** | **最大 S2S 隧道数** |
| --- | --- | --- |
| Basic | 100 Mbps | 10 |
| VpnGw1 | 650 Mbps | 30 |
| VpnGw2 | 1 Gbps | 30 |
| VpnGw3 | 1.25 Gbps | 30 |

另一个 VPN 网关配置选择是设备如何处理 IPSec 流量路由。基于路由的网关使用静态路由表，而基于策略的网关则利用 BGP 等动态路由协议。您的选择主要取决于本地 VPN 硬件的新旧程度。一般指导原则是，较旧的 VPN 硬件通常要求您为隧道的 Azure 端选择基于路由的网关。

最后，请知道您的 VPN 网关需要放置在中心虚拟网络的专用子网上。您可能已经注意到虚拟网络的“子网”边栏选项卡中的“网关子网”按钮（请参阅图 13-9）。您不必使用此按钮来创建网关子网，但该子网确实需要名为 `GatewaySubnet`（无空格）。

Microsoft 建议对网关子网使用尽可能小的 IP 地址空间，以便节约您的专用 IP 地址。`/29` 网络地址是常见的选择。

![FIGURE 13-9: Your Azure VPN gateway needs to be on its own subnet in your virtual network.](img/9781119612148-fg1309.png)

图 13-9： 你的 Azure VPN 网关需要位于虚拟网络中的专用子网上。

#### 本地网络网关

在 Azure 中，本地网络网关是一种代表你本地网络的资源。本地网络网关包含两到三个重要的配置值：

*   本地 VPN 终结点的公共 IP 地址
*   本地网络的 IP 地址范围
*   （可选）BGP 设置，如自治系统编号和对等互连 IP 地址
