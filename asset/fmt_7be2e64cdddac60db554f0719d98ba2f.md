
![警告](img/warning.png) 请务必将任何额外的 NSG 放置在与你的 NSG 相同的 Azure 区域中。否则，你的 VM 和 VNet 都无法使用它们。

如果你一直在按顺序阅读本书（我衷心希望如此），你已经知道如何创建 NSG。

### 添加一条入站规则以允许入站远程桌面协议流量

你将在第 4 章中学习如何创建网络安全组。

### 浏览到 VM 的“网络”边栏选项卡，然后选择其 vNIC

你需要将新的 NSG 与 VM 的 vNIC 关联，以防止基于 Internet 的访问。

### 从“网络接口”设置菜单中选择“网络安全组”，单击“编辑”，选择新的 NSG，然后单击“确定”

现在我们说到点子上了！通过这一简单步骤，你已大幅减少了这台新 VM 的攻击面。

### 在“网络接口”设置中，选择“IP 配置”设置，然后单击 `ipconfig1`

vNIC 始终有一个名为（毫无想象力地）`ipconfig1` 的单一 IP 配置。你需在 IP 配置中指定专用和公用 IP 地址。

图 5-10 将引导你完成在 Azure 中查找 IP 地址存储位置的点击路径：

1. 在网络接口的设置列表中，单击“IP 配置”。
2. 单击 `ipconfig1`（默认 IP 配置）。
3. 根据需要调整公用和专用 IP 地址。

![图 5-10：Azure 门户中的 Azure VM TCP/IP 设置。](img/9781119612148-fg0510.png)

图 5-10： Azure 门户中的 Azure VM TCP/IP 设置。

![提示](img/tip.png)以下是关于 Azure VM IP 地址的一些考虑要点：

*   请记住，为 VM 分配公共 IP 地址可能不是必需的，甚至可能不是个好主意。存在许多其他用于基于 Internet 访问 VM 的选项，例如 Azure 防火墙、手动配置的跳板机、负载均衡器或虚拟专用网络。
*   您的私有 IP 地址来自其所在虚拟网络上的子网。您可以在此处分配静态私有 IP 地址，而不依赖 Azure 动态地址分配。

### 重新访问 VM 的“网络”边栏选项卡并验证您的更改

您至少应该能看到 NSG 入站端口规则。不错！

## 启动、停止和调整 VM 大小

![记住](img/remember.png)在教您如何启动和停止 VM 之前，我想提醒您，Microsoft 会为 VM 运行的每一分钟或处于已分配状态下已停止的每一分钟向您收费。我之前提到的一条规则在此也适用：尽可能从 VM 外部执行与 Azure 相关的 VM 管理。

如果您使用 Azure 门户、PowerShell 或 Azure 命令行界面关闭 VM，则根据您添加的参数，您将关闭并释放 VM，从而停止计费。

只需知道，释放 VM 会释放已分配给它的任何动态资源，例如公共/私有 IP 地址和临时存储。

### 启动和停止 VM

您可能已经注意到 Azure 门户中 VM“概述”边栏选项卡上的“启动”、“重启”和“停止”按钮。您可以使用这些按钮来控制 VM 的分配状态（从而控制计费），但我将教您如何使用 PowerShell 来停止和启动 VM。图 5-11 显示了该界面。

![图 5-11：使用工具栏在 Azure 门户中启动、停止或重启 VM。](img/9781119612148-fg0511.png)

图 5-11： 使用工具栏在 Azure 门户中启动、停止或重启 VM。

当您使用 Cloud Shell 时，Azure 会自动将您的用户帐户向 Azure Active Directory 进行身份验证。相比之下，您需要在本地计算机上使用 Azure PowerShell 之前手动进行身份验证。

请遵循以下步骤，在 Windows 10 工作站上使用 PowerShell 来停止并启动给定的 VM：

#### 打开管理员 PowerShell 控制台，并登录到 Azure

为此，请运行 `Connect-AzAccount`，并向 Azure 进行身份验证。

![提示](img/tip.png)如果您有多个订阅，且 Azure 将您的会话与错误的订阅关联，请使用以下命令进行切换：

```
Set-AzContext -SubscriptionName 'MySubscription'
```

#### 列出资源组中的 VM

您可能不记得 VM 的名称，但如果您记得资源组名称，请尝试以下命令：

```
Get-AzVM -ResourceGroupName 'Wiley'
```

![提示](img/tip.png)在 PowerShell 中，您可以使用单引号或双引号将字符串（字符）数据括起来。PowerShell 的设计初衷是不针对此类事情过于挑剔。

#### 使用此命令停止目标 VM

```
Stop-AzVM -Name 'vm-win-test' -ResourceGroupName 'Wiley' -Force
```

请务必包含 `-Force` 开关参数，以确保您既停止又释放 VM。

#### 启动 VM

哇——变化真快！但这一步是一个很好的学习机会。请看这个技巧：

```
Get-AzVM -Name 'vm-win-test' -ResourceGroupName 'Wiley' | Start-AzVM
```

管道符 (`|`) 将第一部分（获取对目标 VM 的引用）的结果传递给第二部分。此技术称为*管线*。

### 调整 VM 大小

正如我之前提到的，动态调整 VM 大小的能力与维护本地硬件相比，是一个巨大的范式转变。

![警告](img/warning.png)Azure 中的 VM 调整大小有一个缺点：它们会重启您的 VM。请务必仅在预定义的维护时段内执行此操作。

要调整 VM 大小，请遵循以下步骤：

#### 在 VM 设置中，选择“大小”

“大小”边栏选项卡包含一个表，列出了您所在区域中所有可用的 VM 大小。并非所有 VM 大小在每个区域都可用。

#### 编辑筛选器以筛选可用的 VM 大小

您可以使用以下属性的任意组合来筛选 VM 大小：

*   **大小：** 选项为小型、中型和大型。
*   **代系：** 选项为当前、上一代和旧版。
*   **系列：** 选项为通用、GPU、高性能计算、计算优化、内存优化和存储优化。
*   **高级磁盘：** 选项为支持和不支持。
*   **vCPU：** 选项范围为 1 到 64 个 vCPU 核心。
*   **RAM：** 选项范围为 2 到 432 GB。

#### 选择所需的 VM 大小，然后单击“调整大小”

您的 VM 将使用新的虚拟硬件资源重启。这难道不比在本地数据中心申请、订购和安装硬件容易得多吗？

## 扩展 VM 功能

在本章接近尾声之际，我想向您展示如何为 Azure 中的 Windows Server 和 Linux VM 配置基本的诊断日志记录。

### 启用诊断日志记录

Microsoft 为 Linux 和 Windows Server VM 提供了三种粒度日益细化的监视选项：

*   **主机级指标：** 由 Azure 平台提取的基本 CPU、磁盘和网络利用率数据，无需代理软件
*   **来宾级监视：** 更详细的监视；需要 Azure 诊断代理
*   **Azure Monitor Log Analytics：** 功能最强大的监视；需要 Log Analytics 代理和关联的 Azure Monitor Log Analytics 工作区

在本章中，我将使用来宾级监视。要访问它，请打开“诊断设置”边栏选项卡，然后选择“启用来宾级监视”。

来宾级监视从您的 Windows Server VM 中收集以下数据：

*   **选定的性能监视器计数器：** CPU、内存、磁盘和网络。
*   **事件日志消息：** 应用程序、安全和系统。
*   **CPU 内核崩溃转储数据：** 此数据可帮助 Microsoft 支持代表诊断 VM 的问题。

来宾级监视包含来自您的 Linux VM 的以下指标和日志：

*   CPU、内存、网络、文件系统和磁盘指标
*   用于身份验证、任务计划、CPU 和其他设施的 Syslog 日志数据

![技术细节](img/technicalstuff.png)在 Azure 监视命名法中，*指标* 是存储供后续分析的测量值时间序列。

#### 在 Azure Monitor 中查看诊断数据

假设您需要为已创建的 Linux 和 Windows Server VM 绘制 CPU 利用率数据，以便为您的经理生成基线数据。

请遵循以下步骤在 Azure Monitor 中创建监视图表：

#### 在 Azure 门户中打开“监视器”，并导航到“指标”边栏选项卡

我在图 5-12 中向您展示了 Azure Monitor。

#### 在“图表标题”字段中，为新图表指定一个描述性名称

在此练习中，我将其命名为“Windows Server 与 Linux CPU 对比”。

#### 配置初始指标行以绘制某个 VM 的 CPU 数据

以下是我为 Windows Server VM 指定的属性：

*   **资源：** vm-win-test
*   **指标命名空间：** 虚拟机主机
*   **指标：** CPU 百分比
*   **聚合：** 平均值

![图 5-12：Azure Monitor 是基础设施和应用程序监视的中心点。](img/9781119612148-fg0512.png)

图 5-12： Azure Monitor 是基础设施和应用程序监视的中心点。

#### 单击“添加指标”，并配置指标行以绘制另一个 VM 的 CPU 数据

能够绘制来自多个 Azure 资源的指标对您的监视工作大有裨益。

#### 试用 Azure Monitor 中的其他指标控件

请查看这些控件：

*   **新建图表：** 您可以创建一个图表，显示诸如 Azure 存储帐户读取事务之类的内容。
*   **折线图：** 尝试更改绘图类型，观察视图如何改变数据的可见性。
*   **新建警报规则：** 您可以根据定义的指标阈值生成警报、通知和修正操作（例如，当 Linux VM 超过预定义的 CPU 利用率阈值时触发警报）。
*   **固定到仪表板：** 您可以将 Azure 仪表板用作商业智能仪表板。

# 第 6 章：在 Azure 中部署 Docker 容器

## 本章内容

*   理解 Docker 和容器
*   回顾 Azure 对 Docker 容器的支持
*   实施 Azure 容器实例和 Azure 容器注册表
*   探索 Azure Kubernetes 服务
*   在 Azure 应用服务 Web 应用程序中部署 Docker 容器

Docker 容器正在席卷全球！

好吧，也许我需要弱化一下这种夸张说法。许多企业正在意识到在开发和生产环境中使用 Docker 容器的经济效益。简而言之，Docker 容器使开发人员构建软件产品变得更快、更容易。

Microsoft 以多种方式在其云中支持 Docker 容器。读完本章时您可能还不是 Docker 专家，但我完全有信心您将掌握容器的用法以及在 Azure 中使用 Docker 的可能性。

## 理解 Docker

如果您读过第 5 章，您可能对虚拟机 (VM) 是什么以及它们如何工作已经有了相当不错的了解。在我看来，Docker 容器代表了一种更敏捷的虚拟化程度。容器允许开发人员或管理员将应用程序及其所有依赖项打包成一个单一的模块化单元，从而实现快速部署。

> **请记住：** Docker 容器是一个虚拟化的应用程序，而不是完整的 VM。您可能会创建并运行不同数据库和数据库版本的 Docker 容器，以便针对这些数据库测试您的应用程序。这些容器仅包含（看我这双关语？）数据库引擎二进制文件及其依赖项——别无其他。

每个 VM 可能高达数百 GB，且需要更新、备份、监视和维护，而容器的大小范围可以从不到 100 MB 到几 GB 不等。

与 VM 一样，容器与其容器主机服务器共享硬件资源。与 VM 不同的是，容器从根本上是由纯文本 `Dockerfile` 定义的，其中包含构建容器的指令。

思路是将构成容器的所有资产放在一个目录中，并创建一个 `Dockerfile` 来编排容器的组成。然后将 `Dockerfile` 编译为二进制映像，该映像作为您的部署单元。最后，通过部署映像模板的实例，根据需要创建任意数量的容器。图 6-1 说明了 Docker 部署过程。

> **提示：** Docker 是一个庞大的主题，足以填满一本单独的书。如果您想了解更多关于创建容器映像的信息，请查看 Docker 文档：[`https://docs.docker.com`](https://docs.docker.com)。

![图 6-1：Docker 容器部署过程。](img/9781119612148-fg0601.png)

图 6-1： Docker 容器部署过程。

> **技术资料：** 应用程序虚拟化在 Linux 中早于 Docker 就已存在。Docker 只是一家将这些预先存在的技术进行标准化和扩展的公司。Microsoft 和 Docker 建立合作伙伴关系，主要是为了将 Docker 容器引入 Windows Server，本章几乎完全专注于 Windows Server 容器。

### 使用 Docker 容器

开发人员喜爱 Docker 容器，因为容器很敏捷。正如我之前提到的，`Dockerfile` 是纯文本文档，这意味着开发团队可以将它们存储在源代码控制系统中，并随时间跟踪其变更。

假设 Jane Developer 需要针对三个 MySQL 数据库版本测试她公司的业务线应用程序。启动三个独立的 VM 通常是一个缓慢且劳动密集型的过程。当她需要启动并使用每个基于 VM 的 MySQL 安装的多个实例时，这种痛苦会变得更大。如果 VM 的来宾操作系统需要更新，或者 MySQL 需要更新，该过程会更慢。

相比之下，Jane 可以使用 Docker 命令行界面或托管容器平台启动任意数量的运行不同软件版本的 MySQL 容器。测试完成后，她可以用一条命令处理掉这些容器。如果 MySQL 需要更新，她或队友只需编辑 `Dockerfile` 并重新编译映像即可。

可移植性是容器的另一大优势。Microsoft Azure 是一个 Hyper-V 生态系统。如果您需要将 VM 迁移到（比如说）Google Cloud Platform，而那里使用的是另一个管理程序，该怎么办？

我花费了太多时间重新配置虚拟机，以使它们适应不同云提供商的生态系统。有了 Docker，您就拥有了一个通用格式，可在任何支持 Docker 的云中工作。

只要有 Docker 守护进程（服务器服务）组件可用，您就几乎可以在任何地方运行容器，且无需任何修改。

### 在工作站上设置 Docker

Docker 运行时环境相对轻量且便携。在本节中，我将向您展示如何在 Windows 10 工作站上安装 Docker Desktop。

> **请记住：** 就本书而言，我假设您使用的是基于 Windows 10 的计算机。不过，Docker Desktop 及其相关工具也适用于 macOS 和 Linux。Docker 在标准化用户界面方面做得很好，因此如果您使用的是 macOS 或 Linux，应该会发现以下步骤对您同样适用。

#### 安装 Docker Desktop

请遵循以下步骤在 Windows 10 系统上设置 Docker：

1.  **在 Docker Hub 注册免费用户帐户。**

    Docker Hub ([`https://hub.docker.com`](https://hub.docker.com)) 是 Docker 容器的主要公共存储库。

2.  **从** [`https://www.docker.com/products/docker-desktop`](https://www.docker.com/products/docker-desktop) **下载并安装 Docker Desktop。**

    该网站鼓励您完成一个交互式教程；请随意尝试。

3.  **安装过程中接受默认设置。**

    此规则的例外情况发生在安装程序询问您是否要使用 Windows 容器而不是 Linux 容器时。请选择 Windows 容器。在 macOS 或 Linux 计算机上，您不会看到此选项。

4.  **重启计算机。**

    安装程序要求您注销并重启，以安装 Hyper-V 和容器 Windows 10 功能。

5.  **验证 Docker 服务正在运行。**

    Docker Desktop 会作为一个图标出现在 Windows 通知区域（请参阅图 6-2）。

    右键单击 Docker 图标，您将在快捷菜单上看到各种选项（包括如果您在安装期间忘记启用该功能，则可以切换到 Windows 容器）。图 6-2 显示的是“切换到 Linux 容器”，如果您当前配置为 Windows 容器，Docker 会显示此选项。

> **请记住：** Docker 服务需要以提升的权限运行。如果您发现 Docker Desktop 没有将其图标放在通知区域中，请以管理员身份从桌面或“开始”菜单快捷方式运行该应用程序。

#### 运行 hello-world 容器

### Docker 的 hello-world 参考镜像

Docker 的 hello-world 参考镜像能让你从客户端的角度体会如何使用 Docker。请遵循以下步骤：

![图 6-2：Docker Desktop 可从 Windows 通知区域轻松访问。](img/9781119612148-fg0602.png)

**图 6-2：** Docker Desktop 可从 Windows 通知区域轻松访问。
