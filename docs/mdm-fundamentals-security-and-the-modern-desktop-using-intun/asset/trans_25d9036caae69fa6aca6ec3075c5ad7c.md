
*   您可以使用 PolicyPak 管理模板或 PolicyPak 首选项来配置该设置，并通过 MDM 进行交付（更多内容请参见[第 11 章](#c11.xhtml)，“MDM 附加工具：免费与付费”）。

但正如我所说，我打赌所有基于组策略的 OneDrive 设置最终都会进入 Intune 的管理模板功能中，希望等您读到这本书时已经实现了。

### 关于团队站点自动装载的最终想法

重点在于，OneDrive 团队站点自动装载在本地配合组策略运行完美，在非加域计算机上也运行完美。当您向 Windows 计算机提供库列表时，任何类型的计算机都可以将这些库作为驱动器映射的替代品使用。

干得漂亮，微软。

最后再补充一点：如果您迁移了内容，但仍然需要该内容伪装成一个驱动器号怎么办？正如我所说，某些应用程序坚持要求使用驱动器号。您可以查看以下工具（在您掌握了本章基础知识之后）：OneMapper。我在 `www.lieben.nu/liebensraum/onedrivemapper/` 发现了 OneMapper。我自己没试过，但其目标是帮助您在使用团队站点自动装载移动内容后，仍然保留驱动器号。

## OneDrive 同步客户端

OneDrive 存储（及后端服务）只是这桩“婚姻”的一方。

另一方是 OneDrive 同步客户端，它适用于 Windows、Mac、Android 和 iOS（还有适用于 Xbox 的 OneDrive，但那是消费者版 OneDrive，而非商业版 OneDrive）。我这里只深入讲解 Windows 版，但其他平台也可以安装。

在您的 Windows 机器上做个更改，然后立刻在 iPad 上看到该更改。非常棒。

各平台的下载链接可在 `https://onedrive.live.com/about/download/` 找到。

还有其他方式让 OneDrive 安装在 Windows 上：

*   **Windows 10 上：** OneDrive 随 Windows 10 预装。但它可能不是完全最新的。如果您等待一段时间，OneDrive 会根据自己的计划和发布环（稍后我们会讨论）自动更新。但我建议您现在就在少数测试机器上获取最新版本。
*   **即点即用版 Office 2016 及更高版本、专业增强版和/或通过 MDM 部署：** 这些方法中的任意一种都会安装最新的 OneDrive 客户端。
*   **Windows 7 上（如果您还有剩余的 Windows 7）：** 您必须部署 OneDrive 同步客户端。您可以使用我之前提到的链接处的可下载版本。
*   **SCCM 专用版本可用（如果您联系 Microsoft 代表）：** 此版本不会自动更新，必须每 60 天手动更新一次，否则将停止工作。仅建议那些必须完全亲自掌控所部署版本的客户使用。

然后，针对这两个平台，您都可以对其进行配置。现在让我们处理这两者。还要注意，还有旧版 `Groove.exe` 客户端。如果您使用 SharePoint 2016 或 2013，仍然需要它。现代 OneDrive 客户端仅支持本地部署的 SharePoint 2019。因此，您可能需要一个客户端，或者可能需要两个客户端，才能同时处理 OneDrive 和 SharePoint。

### OneDrive 客户端版本与发布环

正如您可能知道的，Windows、Office 和 OneDrive 都有“发布环”。也就是说，功能创建后会立即部署到预览体验环。然后随着功能成熟，它们会进入生产环。最后，功能会逐步推送到企业环（最保守的环境）。通常企业环比生产环滞后 60 天。

您始终可以在以下 URL 查看哪些版本位于哪个环（缩短为 `https://bit.ly/2glxd8Q`）：

`https://support.office.com/en-us/article/New-OneDrive-sync-client-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0`

您可能在该页面上看到的示例可见[图 7.24](#c07.xhtml#figure7-24)。

您可以看到下一个企业环可能的发布日期，这给您一些时间来下载、测试，并确保在 OneDrive 更新到最新版本之前，您的环境一切正常。

![图 7.24 显示发布环的 OneDrive 同步客户端页面](images/c07f024.jpg)

[**图 7.24**](#c07.xhtml#figureanchor7-24) 显示发布环的 OneDrive 同步客户端页面

默认情况下，任何 OneDrive 同步客户端都会尝试将自身更新到最新的生产环。OneDrive 同步客户端始终在检查可用更新。当 OneDrive 同步客户端运行时，它每 24 小时执行一次此操作。但它还有一个备选方案：有一个 Windows 10 计划任务也会更新 OneDrive 同步客户端（即使 OneDrive 已关闭且未启动）。您可以在此处阅读有关 OneDrive 同步客户端更新流程（关于发布环）的更多信息：`https://docs.microsoft.com/en-us/onedrive/sync-client-update-process`.

话虽如此，您可能想要使用最保守的企业环，而不是功能更多、经过更多消费者测试但不一定经过充分实战检验的生产环。

对于本地系统，您将使用我们之前部署好的 OneDrive ADMX 设置来实现这一点。在[图 7.25](#c07.xhtml#figure7-25) 中，您可以看到用户侧的 OneDrive 设置，位于“用户配置”➢“策略”➢“管理模板”➢“OneDrive”。您要找的策略设置是 `Delay updating Onedrive.exe until the second release wave`。

同一设置也可通过 Intune 中的管理模板进行配置，请回顾[图 7.23](#c07.xhtml#figure7-23)。在该屏幕截图中，它也称为 `Delay updating OneDrive.exe until the second release wave`，位于列表中的第四项。

它们的作用相同：同样非常适合您同时拥有使用组策略的本地客户端和使用 MDM 的全云客户端的情况。

![图 7.25 用户侧组策略 OneDrive 设置](images/c07f025.jpg)

[**图 7.25**](#c07.xhtml#figureanchor7-25) 用户侧组策略 OneDrive 设置

### 在 Windows 10 上安装 OneDrive 客户端

正如我所说，OneDrive 随 Windows 10 预装，但如果不更新，它总会稍微有点旧。请记住，OneDrive 客户端会自动更新，但当您安装即点即用版 Office 或通过 MDM 部署时，也会更新。

但我想花一点时间让您看看*如何*安装它，并谈谈一个我知道即将推出、且等您读到这本书时肯定已经发布的选项。

OneDrive for Windows 10 默认始终按用户安装；这有点不寻常。按用户安装意味着整个应用程序完全位于用户控制的空间内，具体为 `%appdata%\local\Microsoft\OneDrive`。这有优点也有缺点。优点是应用程序只需检测到有可用升级，下载它，执行升级，用户就能继续工作。不需要 IT 部门通过 Intune 或 SCCM 等执行某种升级。另一个优点是不需要管理员权限；软件以用户身份下载和安装，而不是以系统身份。

这种按用户模式的缺点是：当多人使用同一台机器，或机器为 RDS 或 VDI 时。问题在于现在您有了大量 OneDrive 实例，不同用户可能安装了不同版本，以及一堆其他问题……所有这些都使用同一台核心机器。

因此，OneDrive 团队宣布了即将推出的“按计算机”安装 OneDrive，专门针对这些情况。它刚在本书付印时发布，所以我无法提前测试。也就是说，关于它的文档可以在 `https://docs.microsoft.com/en-us/onedrive/per-machine-installation` 找到。
