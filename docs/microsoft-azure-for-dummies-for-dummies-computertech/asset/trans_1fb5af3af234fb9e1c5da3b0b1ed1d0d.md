

## 试用 Azure Monitor 中的其他指标控件

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

如果您读过[第 5 章](#c05.xhtml)，您可能对虚拟机 (VM) 是什么以及它们如何工作已经有了相当不错的了解。在我看来，Docker 容器代表了一种更敏捷的虚拟化程度。容器允许开发人员或管理员将应用程序及其所有依赖项打包成一个单一的模块化单元，从而实现快速部署。

> **请记住：** Docker 容器是一个虚拟化的应用程序，而不是完整的 VM。您可能会创建并运行不同数据库和数据库版本的 Docker 容器，以便针对这些数据库测试您的应用程序。这些容器仅包含（看我这双关语？）数据库引擎二进制文件及其依赖项——别无其他。

每个 VM 可能高达数百 GB，且需要更新、备份、监视和维护，而容器的大小范围可以从不到 100 MB 到几 GB 不等。

与 VM 一样，容器与其容器主机服务器共享硬件资源。与 VM 不同的是，容器从根本上是由纯文本 `Dockerfile` 定义的，其中包含构建容器的指令。

思路是将构成容器的所有资产放在一个目录中，并创建一个 `Dockerfile` 来编排容器的组成。然后将 `Dockerfile` 编译为二进制映像，该映像作为您的部署单元。最后，通过部署映像模板的实例，根据需要创建任意数量的容器。[图 6-1](#c06.xhtml#c06-fig-0001) 说明了 Docker 部署过程。

> **提示：** Docker 是一个庞大的主题，足以填满一本单独的书。如果您想了解更多关于创建容器映像的信息，请查看 Docker 文档：[`https://docs.docker.com`](https://docs.docker.com)。

![图 6-1：Docker 容器部署过程。](images/9781119612148-fg0601.png)

[图 6-1：](#c06.xhtml#rc06-fig-0001) Docker 容器部署过程。

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
    Docker Desktop 会作为一个图标出现在 Windows 通知区域（请参阅[图 6-2](#c06.xhtml#c06-fig-0002)）。
    右键单击 Docker 图标，您将在快捷菜单上看到各种选项（包括如果您在安装期间忘记启用该功能，则可以切换到 Windows 容器）。[图 6-2](#c06.xhtml#c06-fig-0002) 显示的是“切换到 Linux 容器”，如果您当前配置为 Windows 容器，Docker 会显示此选项。

> **请记住：** Docker 服务需要以提升的权限运行。如果您发现 Docker Desktop 没有将其图标放在通知区域中，请以管理员身份从桌面或“开始”菜单快捷方式运行该应用程序。

#### 运行 hello-world 容器

