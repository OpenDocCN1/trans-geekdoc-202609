
### Azure 门户界面元素

*   **全局订阅筛选器 (D)**：显示 Azure 订阅的子集，使 Azure 门户视图列表更易于浏览。![图 2-5：Azure 门户是你的管理运营基地。](images/9781119612148-fg0205.png)

    [图 2-5：](#c02.xhtml#rc02-fig-0005) Azure 门户是你的管理运营基地。

*   **通知 (E)**：查看当前和过去部署的进度。

*   **你的帐户 (F)**：注销、切换目录和编辑帐户配置文件。

*   **收藏夹 (G)**：加载你最常用的 Azure 服务。

*   **资源窗格 (H)**：使用搜索框查找需要配置的设置。

*   **配置边栏选项卡 (I)**：*边栏选项卡* 是指你在其中进行 Azure 工作的详细屏幕。水平滚动条可帮助你左右移动。

![记住](images/remember.png)你的 Azure 门户自定义仅影响你的用户帐户。你的同事将拥有她自己的收藏夹列表、订阅筛选器、自定义仪表板等。

![提示](images/tip.png)响应式 Web 应用程序会动态重新排列自身以适应不同的 Web 浏览器和屏幕尺寸。然而，在智能手机上访问完整门户通常并不有趣。Microsoft 为 iOS 和 Android 移动设备提供了 Azure 门户的移动版本。你可以在该移动应用中执行大多数管理任务，包括访问 Cloud Shell。

### Azure PowerShell

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

![提示](images/tip.png)每当你想使用 PowerShell 管理 Azure 时，都需要使用上述步骤。但是，你可以通过使用一种称为服务主体的特殊 Azure Active Directory 帐户来实现 Azure PowerShell 登录自动化。有关详细信息，请参阅 Azure 文档文章“使用 Azure PowerShell 创建 Azure 服务主体”，网址为 [`https://docs.microsoft.com/en-us/powershell/azure/create-azure-service-principal-azureps?view=azps-3.2.0`](https://docs.microsoft.com/en-us/powershell/azure/create-azure-service-principal-azureps?view=azps-3.2.0)。

### Azure CLI / Azure Cloud Shell

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

![技术细节](images/technicalstuff.png)Cloud Shell 之所以如此快速，是因为 Microsoft 在其全球内容分发网络中预置了 Docker 容器。Azure 使用你的客户端 IP 地址和地理位置将你连接到最近的 Cloud Shell 容器，从而提供最快的连接。
