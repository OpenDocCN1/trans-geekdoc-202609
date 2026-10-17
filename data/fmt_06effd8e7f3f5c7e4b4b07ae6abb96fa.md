
是时候熟悉最常用的 Azure 管理工具了。本书中描述的所有分步过程都假设你在 Windows 10 工作站上工作，但你可以在 macOS 或 Linux 系统上完成本书中的几乎每一项任务。

## Azure 门户

Azure 门户 ([`https://portal.azure.com`](https://portal.azure.com)) 是一个响应式 Web 应用程序，构成了 Azure 中基本的图形管理平台。图 2-5 显示了 Azure 门户。

### Azure 门户界面元素

*   **页面标题栏 (A)：** 顶部导航栏有时称为 `全局导航`，因为这些控件在 Azure 门户的任何位置均可用。打开“收藏夹”菜单。
*   **全局搜索 (B)：** 搜索任何 Azure 资源。搜索结果包含文档链接。
*   **Cloud Shell (C)：** 打开 Azure Cloud Shell 以执行命令行 Azure 工作。
*   **全局订阅筛选器 (D)**：显示 Azure 订阅的子集，使 Azure 门户视图列表更易于浏览。
*   **通知 (E)**：查看当前和过去部署的进度。
*   **你的帐户 (F)**：注销、切换目录和编辑帐户配置文件。
*   **收藏夹 (G)**：加载你最常用的 Azure 服务。
*   **资源窗格 (H)**：使用搜索框查找需要配置的设置。
*   **配置边栏选项卡 (I)**：*边栏选项卡* 是指你在其中进行 Azure 工作的详细屏幕。水平滚动条可帮助你左右移动。

![图 2-5：Azure 门户是你的管理运营基地。](img/9781119612148-fg0205.png)

![记住](img/remember.png)你的 Azure 门户自定义仅影响你的用户帐户。你的同事将拥有她自己的收藏夹列表、订阅筛选器、自定义仪表板等。

![提示](img/tip.png)响应式 Web 应用程序会动态重新排列自身以适应不同的 Web 浏览器和屏幕尺寸。然而，在智能手机上访问完整门户通常并不有趣。Microsoft 为 iOS 和 Android 移动设备提供了 Azure 门户的移动版本。你可以在该移动应用中执行大多数管理任务，包括访问 Cloud Shell。

## Azure PowerShell

Azure 门户很好用，但如果你被要求部署 10 个、100 个或 1,000 个 VM 怎么办？你肯定不想在 Azure 门户中通过点击来执行重复性操作。

对于管理自动化，你需要使用 Azure PowerShell。PowerShell 是一种自动化语言，可用于在 Windows Server、macOS、Linux、Azure、AWS 等环境中执行任何重复性任务。

如果你还没有开始提升 PowerShell 技能，今天就是开始的日子；你需要至少具备中级 PowerShell 技能，才能在 Azure 中充分发挥生产力。

请遵循以下步骤，在 Windows 10 工作站上安装 Az 模块：

1.  **打开提升权限的 PowerShell 控制台。**

    在 Windows 10 中，打开“开始”菜单，输入 PowerShell，右键单击图标，然后从快捷菜单中选择“以管理员身份运行”。

2.  **从 PowerShell 库安装 Az 模块。**

    Microsoft 运营一个经过策划的 PowerShell 模块存储库，名为（非常贴切地）PowerShell 库。运行以下命令以下载并安装 Azure PowerShell：

    ```
    Install-Module -Name -Az -Verbose -Force
    ```

    从技术上讲，`-Verbose` 和 `-Force` 开关参数是可选的，但我建议使用 `-Verbose` 以便阅读详细的命令输出，并使用 `-Force` 以便在计算机上已安装模块时进行升级。

3.  **更新本地帮助。**

    PowerShell 默认不附带本地帮助，因为文档变化非常快。请使用以下命令，确保你拥有最新的 PowerShell 命令帮助：

    ```
    Update-Help -Force -ErrorAction SilentlyContinue
    ```

    `-ErrorAction SilentlyContinue` 部分会抑制帮助文件下载过程中可能发生的任何错误或故障。出于多种原因，运行 `Update-Help` 时偶尔会遇到错误（例如，PowerShell 团队的某人可能忘记为某个命令创建帮助文章）。

4.  **登录到 Azure 订阅。**

    运行以下命令以生成“登录到你的帐户”对话框。通过身份验证后，你将返回到 PowerShell 控制台，已登录并准备就绪。

    ```
    Connect-AzAccount
    ```

5.  **要关闭 PowerShell 连接，请关闭控制台窗口。**

![提示](img/tip.png)每当你想使用 PowerShell 管理 Azure 时，都需要使用上述步骤。但是，你可以通过使用一种称为服务主体的特殊 Azure Active Directory 帐户来实现 Azure PowerShell 登录自动化。有关详细信息，请参阅 Azure 文档文章“使用 Azure PowerShell 创建 Azure 服务主体”，网址为 [`https://docs.microsoft.com/en-us/powershell/azure/create-azure-service-principal-azureps?view=azps-3.2.0`](https://docs.microsoft.com/en-us/powershell/azure/create-azure-service-principal-azureps?view=azps-3.2.0)。

## Azure CLI / Azure Cloud Shell

Azure 命令行接口 (CLI) 是……嗯，一个用于 Azure 的跨平台命令行接口。我发现一些 Azure 管理员和开发人员更喜欢 Azure CLI 而不是 Azure PowerShell，因为 CLI 的学习曲线更平缓，并且速度极快，尤其是在交互模式下。

在本书中，你将在 Azure Cloud Shell 中使用 Azure CLI。Cloud Shell 是一个基于浏览器的命令行环境，可让你访问 PowerShell、Azure CLI 以及许多其他管理和开发工具。

请遵循以下步骤，开始熟悉 Azure Cloud Shell 和 Azure CLI：

1.  **在 Azure 门户的全局导航栏上，单击 Cloud Shell。**

    “你没有装载存储”对话框随即打开。

2.  **选择你的 Azure 订阅，然后单击“创建存储”。**

    首次启动 Cloud Shell 时，需要指定一个存储帐户。你可以使用该存储帐户存储所有 Cloud Shell 资源（模块、脚本等）。

    如果想要使用现有存储帐户，或想要完全控制存储帐户的名称和区域，请单击“显示高级设置”。

    你需要指定是要从 Bash 还是 PowerShell 开始。我建议选择 PowerShell。

3.  **在 Cloud Shell 工具栏上，确保 PowerShell 是当前环境。**

    你可以通过检查 Azure Cloud Shell 工具栏上的第一个元素来做到这一点。请注意，只需从此菜单中进行选择，即可在 Bash 和 PowerShell 环境之间切换。

    你可以从 PowerShell 会话或 bash shell 会话启动 Cloud Shell 会话。这些步骤是在 PowerShell 环境中进行的。

4.  **运行 `Get-CloudDrive` 以查看云驱动器信息。**

    该命令会告诉你关于 Cloud Shell 文件所在位置的所有信息。你的云驱动器指向指定 Azure 存储帐户中的文件共享。

5.  **输入 `az interactive` 以启动交互式 Azure CLI 会话。**

6.  **针对发送遥测信息给 Microsoft 的请求回答是或否。**

    首次启动 Azure CLI 交互式环境时请耐心等待。通常需要一分钟或更长时间才能完全初始化。

7.  **输入以下命令以查看可用的存储帐户：**

    ```
    az storage account list -o table
    ```

    在输入时，请注意 Azure CLI 中以下我认为非常有用的行为：

    *   Azure CLI 提供自动完成下拉菜单，帮助你完成命令。请善用这些菜单。按 Tab 键接受突出显示的选项，或使用箭头键选择替代项。
    *   在屏幕中间，Azure CLI 在你输入时提供内联文档。
    *   Azure CLI 默认提供 JSON 输出，但在这种情况下，请指定表格格式。然后运行 `az configure` 以指定表格或其他更适合你习惯的默认输出格式。

8.  **要退出 Cloud Shell，请关闭窗格。**

![技术细节](img/technicalstuff.png)Cloud Shell 之所以如此快速，是因为 Microsoft 在其全球内容分发网络中预置了 Docker 容器。Azure 使用你的客户端 IP 地址和地理位置将你连接到最近的 Cloud Shell 容器，从而提供最快的连接。

![提示](img/tip.png)虽然我在本书中使用 Cloud Shell 内的 Azure CLI，但你也可以在 Windows、macOS 或 Linux 工作站上安装 Azure CLI。请访问 Azure 下载页面 [`https://azure.microsoft.com/en-us/downloads`](https://azure.microsoft.com/en-us/downloads) 以下载安装程序。

## Azure SDK

正如本章前面所述，REST API 是一种基于 HTTP 的接口，允许两个软件系统进行通信，而 Azure 门户、PowerShell 和 Azure CLI 是*抽象*（隐藏底层细节）底层 ARM REST API 的方式。

对于软件开发人员，软件开发工具包 (SDK) 代表了另一层 API 抽象层。截至撰写本文时，Azure SDK 实际上可用于以下编程语言和框架：

*   Android
*   Go
*   iOS
*   Java
*   .NET
*   Node.js
*   PHP
*   Python
*   Ruby
*   Swift
*   Windows
*   Xamarin

Azure SDK 提供了与 Azure 服务交互所需的项目模板和代码库。在本书中，我使用 Visual Studio 2019 来使用 Azure SDK。如图 2-6 所示，你只需启用 Azure 开发工作负载；Visual Studio 会处理其余的设置工作。

![提示](img/tip.png)如果你是 Visual Studio 新手，可能需要获取有关修改已安装工作负载的更详细说明。请参阅 Microsoft 文档文章“修改 Visual Studio”，网址为 [`https://docs.microsoft.com/en-us/visualstudio/install/modify-visual-studio?view=vs-2019`](https://docs.microsoft.com/en-us/visualstudio/install/modify-visual-studio?view=vs-2019)。

顺便说一句，如果你在想：“嘿，我不是开发人员；我不想为 Visual Studio 付费！”请稍等一下。Microsoft 免费提供 Visual Studio 2019 Community Edition，供测试和开发使用。Windows 和 macOS 版本均可用。

![图 2-6：在 Visual Studio 2019 中启用 Azure 开发工作负载。](img/9781119612148-fg0206.png)

## ARM REST API

如果你愿意，可以深入到 ARM REST API 的“最底层”。图 2-7 显示了 Azure 资源浏览器 ([`https://resources.azure.com`](https://resources.azure.com/))，这是一个基于浏览器的 ARM REST API 界面。

注释如下：

*   **A：** 选择要附加的 Azure AD 目录。
*   **B：** 将环境设置为“只读”（默认）或“读/写”。在读/写模式下工作时要小心，因为你是在直接操作 Azure 资源。
*   **C：** 虽然资源浏览器使用知名地址，但访问需要身份验证，界面中显示的内容反映了你的用户帐户的 Azure AD 和 Azure 资源权限。
*   **D：** 使用 ARM REST API 资源提供程序命名空间浏览订阅并深入查看资源。
*   **E：** 使用 HTTPS 动词 `GET`、`PUT`、`POST` 和 `DELETE` 执行 ARM REST API 操作。
*   **F：** 以原生 JSON 格式查看资源定义。如果将资源浏览器置于读/写模式，你可以直接进行更改。

![图 2-7：Azure 资源浏览器让你访问 ARM API。](img/9781119612148-fg0207.png)

![警告](img/warning.png)正如包括开源社区人士在内的许多人常说的那样，“能力越大，责任越大。”

你可能想知道何时以及为何需要在基本 REST API 层面与 Azure 交互。然而，这种交互比你想象的更常见。也许你正在排查资源行为故障，却无法在 Azure 门户或其他抽象层中找到所需的控件。又或许你正在编写自己的 API，需要知道如何为自己的用途构建 ARM REST API 调用。

# 第 2 部分：将计算资源部署到 Microsoft Azure

**本部分内容……**

*   像专家一样管理 Azure 存储
*   在 Microsoft Azure 中规划和实施虚拟网络
*   部署和配置 Windows Server 和 Linux 虚拟机 (VM)
*   区分 Docker 容器与 VM，并学习如何在 Azure 公有云中驾驭它们

# 第 3 章：在 Azure 中管理存储

**本章内容**

*   **区分存储数据类型**
*   **创建和使用存储帐户**
*   **决定 VM 磁盘的存储位置**
*   **为数据备份奠定基础**

存储是 Microsoft Azure 云中一个几乎通用的服务示例。无论你运行何种工作负载——VM、应用服务、Functions、机器学习或其他——你都可能需要持久的对象存储。

读完本章后，你将牢固掌握 Azure 存储帐户：它是什么、如何工作、如何部署，以及如何存储和检索不同的数据类型。

## 了解 Azure 存储数据类型

Azure 存储帐户代表一个多用途容器资源，为三种主要数据类型提供高可用、持久的存储：非结构化、半结构化和结构化。

### 非结构化数据

*非结构化数据*是没有模式强制约束的数据。你可以将*二进制大对象* (blob) 视为文件、虚拟硬盘、文档文件和媒体文件。所有这些对象都是文件存储对象，可以具有任何特定格式和内容。

![技术细节](img/technicalstuff.png)虽然 *blob* 一词包含 *large* 之意，但 blob 对象可以是任意大小的文件，无论是 1 KB 的文本文件还是 120 GB 的虚拟硬盘文件。

### 半结构化数据

*半结构化数据*没有关系数据的列行排列，但也不像纯二进制非结构化数据那样自由。Azure 存储帐户中的表服务以键/值数据对的形式呈现半结构化数据。

NoSQL 数据库是半结构化数据的一个例子。正如我在第 9 章中所述，Cosmos DB 是 Azure 的主要 NoSQL 数据库产品。

### 结构化数据

如果你使用过任何关系数据库系统，你就懂*结构化数据*——即分解为一个或多个表中的数据，其中每一列都受特定数据类型约束。

到目前为止，我已解释 Azure 存储帐户存储非结构化和半结构化数据。但结构化数据怎么办？

事实上，Azure 存储帐户没有结构化数据存储选项。相反，你需要使用 Microsoft 的关系数据平台即服务 (PaaS) 产品之一，或在虚拟机 (VM) 内运行数据库。

Azure 生态系统中的结构化数据库示例包括 Azure SQL 数据库和 Azure Database for MySQL 服务器。

此时，你已了解 Azure 存储帐户提供用于非结构化数据的 Blob 服务和用于半结构化数据的表服务。但你应该知道还有两种额外的存储帐户服务：

*   **队列：** 支持应用程序组件之间的异步消息传递。该服务速度快、可扩展，且开销低。
*   **文件：** 创建兼容服务器消息块 (SMB) 和网络文件系统 (NFS) 的文件共享，并从 Azure 内部或外部访问它们。

## 使用存储帐户

现在考虑如何规划 Azure 存储。Azure 通用存储帐户包含多个配置选项，因此为了节省成本和安全，你需要做出正确的决策。

### 创建存储帐户

在创建第一个存储帐户之前，你应该了解一些关键事实。首先，你需要确定需要哪种类型的存储帐户。你的选择如下：

### 存储账户类型

*   **General-purpose v2（通用 v2）：** 除非您有令人信服的理由选择其他类型，否则应在大多数情况下选择此类型，因为它是功能最全面的选项。它包含所有四种存储账户服务：Blob、表、队列和文件。
*   **General-purpose v1（通用 v1）：** 此选项主要用于支持经典 Azure 部署，其功能比 v2 少。
