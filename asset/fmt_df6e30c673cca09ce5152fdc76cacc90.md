
因此，我们成功地使用 Azure 区块链联盟将以太币从一个账户转移到了另一个账户。我们现在可以为我们的区块链开发智能合约。我将在后续章节中介绍智能合约和其他相关主题。

# 结论

在本章中，我们学习了如何在 Azure 上设置以太坊区块链，并使用 MetaMask 通过向另一个账户转移一些以太币来测试我们的区块链。下一节将重点介绍智能合约以及如何设置编写智能合约的开发环境。

![](img/Figure_2.2.39.jpg)

**图 2.2.39**

# 问题

1. 什么是 Azure？
2. 什么是以太坊工作量证明联盟？
3. Azure 上的资源组是什么？
4. 什么是 MetaMask？
5. MetaMask 使用什么节点？
6. 用简单的方式解释工作量证明。

# 第三部分：智能合约开发

在上一节中，我们学习了如何使用联盟领导者在 Microsoft Azure 上设置以太坊区块链。现在是进行一些开发工作的时候了。在继续介绍智能合约及其开发之前，作为先决条件，必须设置开发环境。本节将专门介绍如何为智能合约开发设置开发环境。在下一节中，我们将了解什么是智能合约以及如何开发它们。

![](img/Figure_3.0.1.jpg)

**图片来源：** [`pixabay.com`](https://pixabay.com)

**图 3.0.1**

# 工具与开发环境

在进行实际开发之前，我们将使用一系列工具来设置开发环境。我将在 Microsoft Azure 上使用全新的 Windows 安装。在开始之前，您可以按照上一节中的步骤在 Azure 上设置虚拟机。我们将在新机器上安装 Chrome 浏览器，随后安装 `MetaMask`（Chrome 插件），它将帮助我们进行身份验证。Microsoft 提供免费的 `Visual Studio Code`，我们可以将其作为智能合约开发的 IDE。我们将安装 `NuGet 包管理器 (NPM)` 和 `Chocolatey`（也是一个包管理器），以获取开发所需的其他工具和包。我们将结合 `Git`、`NPM` 和 Windows 构建工具来构建/编译代码。我们将使用一个名为 `Test RPC` 的内存测试服务器来测试应用程序，最后使用 `Truffle`。当我们开始开发时，将更深入地探讨 `Truffle`。

# 设置智能合约开发环境

![](img/Figure_3.1.1.jpg)

**图 3.1.1**

## Azure

Azure 是 Microsoft 的云平台，在云计算领域提供大量资源。其中一项资源是 `虚拟机 (VM)`，即只需点击几下，几秒钟内即可创建一个功能齐全、配置和操作系统均由您选择的机器。您可以使用安全凭据从任何地方远程访问该机器，并进行任何您想要的操作，例如托管网站、开发应用程序、为软件创建生产或测试环境等。让我们逐步了解如何实现这一点。

## 结构

在本章中，我们将讨论以下主题：

*   Azure 上的虚拟机设置
*   为智能合约开发准备环境

## 目标

学习完本单元后，您应该能够：

*   为编程智能合约设置开发环境。

## Azure 账户设置

如果尚未完成，请按照上一节中的步骤设置 Azure 账户。

## Azure 上的虚拟机设置

1.  进入仪表板后，单击仪表板上的 `Virtual machines`（虚拟机）链接，右侧面板将打开，显示您所有的虚拟机。由于我们要创建新的，且没有现有的，因此面板将为空。单击 `Create virtual machine`（创建虚拟机）：

    ![](img/Figure_3.1.2.jpg)

    **图 3.1.2**

2.  单击 `Create virtual machine` 后，您将看到 Azure 提供的用于创建机器的所有操作系统和解决方案模板。您可以根据需求选择 Windows 或 Linux 操作系统，但请注意涉及的成本：

    ![](img/Figure_3.1.3.jpg)

    **图 3.1.3**

3.  由于本节旨在学习如何创建虚拟机，我将选择配置最低的 `Windows Client`（Windows 客户端）机器，您可以根据需求和需要进行选择。因此，选择 `Windows Client`，如下截图所示：

    ![](img/Figure_3.1.4.jpg)

    **图 3.1.4**

4.  您将看到许可协议和法律条款窗口。请仔细阅读并按下 `Create`（创建）按钮：

    ![](img/Figure_3.1.5.jpg)

    **图 3.1.5**

5.  单击 `Create` 后，系统将要求您填写一些基本要求，如下截图所示。按您的选择命名；例如，我将其命名为 `AKHILPC`，将 `VM disk type`（虚拟机磁盘类型）保留为 `SSD`，或根据需要选择。提供您远程连接机器时所需的用户名和密码。请妥善保管用户名和密码。选择订阅，如果您有付费订阅，请选择该订阅，否则选择您获得的试用订阅。您必须提供 `Resource group`（资源组）。您可以创建一个新的或使用现有的。资源组为您的所有 Azure 资源提供逻辑分离。由于我已有一个现有的资源组，因此我将使用它。选择 `Location`（位置），勾选确认复选框，然后单击 `OK`：

    ![](img/Figure_3.1.6.jpg)

    **图 3.1.6**

6.  单击 `OK` 后，您将看到第二部分，用于选择机器大小，其中列出了内存、硬盘大小、SKU 和区域。每种配置都有相关成本，因此请根据您的需求和预算进行选择。出于培训/教程目的，我选择了成本最低的第一个，如下截图所示：

    ![](img/Figure_3.1.7.jpg)

    **图 3.1.7**

7.  在第三步中，您需要选择与可用性、存储和网络相关的特定设置。根据您的判断选择/提供设置：

    ![](img/Figure_3.1.8.jpg)

    **图 3.1.8**

8.  单击 `OK` 后，将显示一个摘要页面，列出您选择的所有配置、每小时成本和操作系统。通过勾选确认复选框确认一切正常（如下截图所示），然后单击 `Create`（创建）按钮。

    ![](img/Figure_3.1.9.jpg)

    **图 3.1.9**

9.  单击 `Create` 后，创建虚拟机可能需要一段时间。它将显示 `Submitting deployment for`…… 等待部署完成。对我来说，花费了 `5~9` 分钟：

    ![](img/Figure_3.1.10.jpg)

    **图 3.1.10**

10. 部署完成后，您将看到已部署虚拟机的部分，您可以选择 `Start`（启动）、`Stop`（停止）、`Restart`（重启）、`Move`（移动）或 `Delete`（删除）您创建的虚拟机。单击 `Connect`（连接）将在右侧面板显示两个选项，即 `RDP` 和 SSH。我们将选择通过 `RDP` 连接，因此下载右侧面板显示的 RDP 文件。单击 `Download RDP File`（下载 RDP 文件）按钮获取文件。或者，您可以直接在本地计算机上通过 `mstsc` 命令打开 RDP 连接。您可以在 RDP 部分看到 IP 地址，如下截图所示：

     ![](img/Figure_3.1.11.jpg)

     **图 3.1.11**

11. 下载的 RDP 文件将位于您本地的下载位置。单击它以配置 RDP 连接。

     ![](img/Figure_3.1.12.jpg)

     **图 3.1.12**

12. IP 地址会自动填入，只需填写用户名和密码即可连接。

     ![](img/Figure_3.1.13.jpg)

     **图 3.1.13**

13. 连接成功后，您将看到欢迎消息，同时 Windows 正在加载并进行首次使用配置。请稍等片刻。

     ![](img/Figure_3.1.14.jpg)

     **图 3.1.14**

14. Windows 加载完成后，您将看到如下所示的桌面。现在您可以随心所欲地使用这台机器：

     ![](img/Figure_3.1.15.jpg)

     **图 3.1.15**

     `请注意，您使用机器的时间将按小时收费。`

15. 如果您一段时间不想使用该机器，或希望每天在指定时间停止机器，可以通过单击 Azure 仪表板上的 `Virtual machines` 选项手动操作。您将看到您的虚拟机。选择您的虚拟机并单击 `Stop`（停止）。您可以随时启动。这样可以节省大量成本。

     ![](img/Figure_3.1.16.jpg)

     **图 3.1.16**

16. 此外，通过点击您选择的 VM，您可以监控其每小时/每日的使用统计信息，如下截图所示：

     ![](img/Figure_3.1.17.jpg)

     **图 3.1.17**

看看仅通过几次简单的点击就在 Azure 上设置 VM 是多么容易。现在您不必依赖任何物理机器来完成您的工作。

# 工具和包的分步安装

正如我在前面章节所述，让我们开始其他工具和包的分步安装：

1.  **安装 Chrome 浏览器** - 第一步是安装 Chrome 浏览器。如果您已经安装了 Chrome 浏览器，请打开浏览器并参考步骤 3，否则请下载 Chrome 浏览器：

    ![](img/Figure_3.1.18.jpg)

    **图 3.1.18**

2.  阅读 `Google` 条款和服务，并将其安装在刚创建的新机器上。

    ![](img/Figure_3.1.19.jpg)

    **图 3.1.19**

3.  现在我们必须安装 `MetaMask`，这是一个 Chrome 插件，将帮助我们进行身份验证和测试。`MetaMask` 是一个工具，可帮助您在浏览器中快速与以太坊网络交互。它使用 `infura.io`。请注意 `MetaMask` 不支持挖矿和合约部署。

     从 GitHub 以下 URL 下载 `MetaMask`：[`github.com/MetaMask`](https://github.com/MetaMask)。如下截图所示，选择 `Pinned repositories` 中显示的 `metamask`-extension 链接并点击它：

    ![](img/Figure_3.1.20.jpg)

    **图 3.1.20**

4.  我选择了 `4.7.4` 版本；当您尝试下载时，可能会看到最新的稳定版本。通过点击链接 `metamask-chrome-4.7.4.zip` 下载 Chrome 插件，如下截图所示：

    ![](img/Figure_3.1.21.jpg)

    **图 3.1.21**

5.  将下载的 zip 文件解压到 Windows 上的任意位置：

    ![](img/Figure_3.1.22.jpg)

    **图 3.1.22**

6.  现在在 Chrome 中输入以下 URL 打开 Chrome 扩展设置：`chrome://extensions`。开启 `Developer mode`，如下截图所示，然后点击 `LOAD UNPACKED` 以加载解压后的下载扩展：

    ![](img/Figure_3.1.23.jpg)

    **图 3.1.23**

7.  现在导航到 `MetaMask` Chrome 扩展解压的文件夹并选择该根文件夹，如下截图所示：

    ![](img/Figure_3.1.24.jpg)

    **图 3.1.24**

8.  点击 `OK` 后，扩展将加载到 Chrome 中，您将看到 `MetaMask` 主页，确认该扩展现在是 Chrome 浏览器的一部分。您将在 Chrome 右上角看到一个狐狸图标作为扩展。现在您可以返回之前打开的 Chrome 扩展页面，并禁用我们在加载解压扩展时启用的 `Developer mode`：

    ![](img/Figure_3.1.25.jpg)

    **图 3.1.25**

9.  现在下载 `Visual Studio Code`，这是一个帮助我们进行开发的 IDE。`VS Code` 广受欢迎，是微软提供的轻量级免费 IDE。导航至 URL：[`code.visualstudio.com/`](https://code.visualstudio.com/)。下载最新稳定版本，如下截图所示：

    ![](img/Figure_3.1.26.jpg)

    **图 3.1.26**

10. 下载可执行文件后，点击它进行安装。阅读许可协议并接受，按照安装向导的说明将 `VS Code` 安装到您的机器上：

     ![](img/Figure_3.1.27.jpg)

     **图 3.1.27**

11. 现在轮到下载 `NPM`。导航至 URL - [`nodejs.org/en`](https://nodejs.org/en) 并下载窗口上显示的最新发布稳定版本。我正在下载 `8.11.2 LTS` 版本的 `NPM`，如下截图所示：

     ![](img/Figure_3.1.28.jpg)

     **图 3.1.28**

12. 下载安装程序后点击它并按照步骤操作。

     ![](img/Figure_3.1.29.jpg)

     **图 3.1.29**

13. 保持所有设置为默认值，点击 `Next` 按钮直到安装成功完成：

     ![](img/Figure_3.1.30.jpg)

     **图 3.1.30**

14. 安装完成后点击 `Finish` 按钮：

     ![](img/Figure_3.1.31.jpg)

     **图 3.1.31**

15. 现在，正如本节前面所述，我们还需要一个包管理器。让我们也安装它，即 `Chocolatey`。它可以使用 `PowerShell` 命令安装，我们可以在 URL [`chocolatey.org/`](https://chocolatey.org/) 上获取命令/脚本。访问网站并点击 `Install Chocolatey Now` 按钮，如下截图所示：

     ![](img/Figure_3.1.32.jpg)

     **图 3.1.32**

16. 在跳转的页面上，向下滚动到看到子标题 `Install with PowerShell.exe` 的部分。复制脚本，如下截图红框所示。脚本内容为：

     ```
     Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
     ```

     ![](img/Figure_3.1.33.jpg)

     **图 3.1.33**

17. 现在从 Windows 开始菜单打开 PowerShell 窗口，如下所示，点击 `Run as administrator` 启动 PowerShell 命令提示符：

     ![](img/Figure_3.1.34.jpg)

     **图 3.1.34**

18. 命令提示符将如下截图所示：

     ![](img/Figure_3.1.35.jpg)

     **图 3.1.35**

19. 现在将复制的脚本粘贴到命令提示符中并按 `Enter`。

     ![](img/Figure_3.1.36.jpg)

     **图 3.1.36**

20. 一旦 `Chocolatey` 命令和 `NuGet` 包就位，我们将使用 `Chocolatey` 的 install 命令安装 GitHub 客户端；这将安装开发过程中使用的其他有用工具。

     因此，在命令提示符中输入命令：`choco install git -params "/GitAndUnixToolsOnPath"`，如下截图所示，然后按 `Enter`。

     ![](img/Figure_3.1.37.jpg)

     **图 3.1.37**

21. 命令提示符上的安装程序将询问是否运行脚本以允许全局配置。您可以输入 `Y` 表示是，然后按 `Enter` 以允许。

     ![](img/Figure_3.1.38.jpg)

     **图 3.1.38**

22. 现在关闭并重新打开 PowerShell 窗口，以确保所有内容均已正确安装。

     ![](img/Figure_3.1.39.jpg)

     **图 3.1.39**

23. 现在让我们执行以下命令：

     *   关闭 Git 中的所有安全调用验证功能：`git config --system http.sslverify false`

         ![](img/Figure_3.1.40.jpg)

         **图 3.1.40**

     *   通过 `NPM` 安装 node 插件构建工具：`npm install -g node-gyp`

         ![](img/Figure_3.1.41.jpg)

         **图 3.1.41**

     *   安装 Windows 构建工具：`npm install --global --production windows-build-tools`

         ![](img/Figure_3.1.42.jpg)

         **图 3.1.42**

     *   安装 Windows 构建工具将花费一些时间，请耐心等待，在此期间如果您愿意可以吃点东西 😊。
