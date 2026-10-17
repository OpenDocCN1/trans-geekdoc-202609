
目前，我不希望你盲目冲动地部署 OneDrive 客户端。

但我确实需要你准备一台安装了最新版 OneDrive 客户端的机器，以便提取一些关键文件。

OneDrive 客户端的大部分管理都是通过组策略完成的。

为此，你需要获取最新的 OneDrive ADMX 文件并将其放入组策略存储中：中央存储或本地存储（推荐使用中央存储）。

最新的 OneDrive ADMX 文件总是随 OneDrive 客户端一起安装（贴心设计）。所以，正如我所说，在一台独立的机器上，访问 `https://onedrive.live.com/about/download/` 找到 Windows 10 版本的下载（或重新安装）链接。再说一遍，即使你认为已安装，也请重新下载并重装，以确保你使用的是最新版 OneDrive 客户端。

完成后，在 Windows 10 机器上，你会在 `%localappdata%\Microsoft\OneDrive\BuildNumber\adm` 找到这些文件（是的，出于某些原因文件夹名为 `adm` 而非 `ADMX`）。

然后复制 `OneDrive.admx` 和 `OneDrive.adml` 并将它们放入你的组策略存储（中央存储或本地存储）中。

如果你*不知道*我在说什么，那么我有一本详尽的组策略书籍可以帮助你，网址是 `www.MDMandGPanswers.com/book`。立即获取你的签名版！（再给朋友买一本！）

但如果你只想快速了解，这里有我制作的两个视频：

*   如何创建组策略中央存储：`www.youtube.com/watch?v=Q4DBdQo4XZs`
*   如何更新中央存储（获取新 ADMX 文件时）：`www.youtube.com/watch?v=Op7hAvc5a0M`

所以如果你已有中央存储，只需按第二个视频中的演示操作即可。视频结束时，你的文件应已位于中央存储中，如图 7.2 所示。

![图 7.2 将 OneDrive.admx 和 OneDrive.adml（未显示）放入中央存储](img/c07f002.jpg)

**图 7.2** 将 `OneDrive.admx` 和 `OneDrive.adml`（未显示）放入中央存储

我假设你已按要求将 OneDrive ADMX 和 ADML 文件放入了中央存储。

### 获取 OneDrive 许可（随 Office 365）

由于 OneDrive for Business 随 Office 365 提供，具体取决于你在本书开篇是如何起步的，你可能拥有 Office 365，也可能没有。如果没有，且你只想学学门道，那得花点钱。

每位用户每月一杯星巴克拿铁的钱。

因此，每位用户每月 5.00 美元（按年支付）或每月 6.00 美元（无承诺），你就可以在现有计划中追加 Office 365 Business Essentials。同样，如果你已拥有 Office 365 E3 或 E5，则已支付费用并拥有无限存储空间。

如果你正在跟随本书学习，只是想体验 OneDrive 的运作方式，那就为两个用户购买以便跟随本章示例操作。以下是购买对象：

*   任意你喜欢的本地 AD 用户，如 `EastSalesUser1`。请记住，回在第 2 章“设置 Azure AD 和 MDM”中，你使用了 `Azure AD Connect` 将本地 AD 账户同步到 Azure AD。
*   任意纯 Azure AD 用户，如 `Jack Tors`。请记住，Jack 是“完全诞生于云端”。他完全没有任何本地用户账户。而像他这样纯在 Azure AD 中创建的账户不会向后同步到本地 AD。Jack 彻头彻尾是云端用户！

如果你不确定哪些账户可能是合适的候选者，请查看第 2 章中的 `图 2.49`。计划是：你将把 Office 365 Business Essentials 分配给一位来源为 Windows Server AD 的用户，把另一个许可证分配给一位来源为 Azure Active Directory 的用户。同样，请参阅 `图 2.49` 以回顾我的意思。

在此过程结束时，我们希望 `EastSalesUser1` 和 `Jack Tors` 都拥有 Azure 和 Office 365 Business Essentials 许可证。

为这两类账户各分配一个 Azure 账户和一个 Office 365 Business Essentials 许可证，将使我们能够探索以下场景：

*   对于 `EastSalesUser1`，你可以模拟拥有一台旧机器（Windows 7 或 Windows 10），并为他提供一台新（或较新）的 Windows 10 机器，让所有文件神奇地出现在你的本地用户群面前。
*   对于 `Jack Tors`，你可以模拟完全没有本地 AD 的环境。让 Jack 登录任何纯 MDM 注册的机器，并从任何地方获取文件。
*   第三个场景是 `EastSalesUser1` 完全脱离其本地 Active Directory，但仍能从任何地方获取其文件。
*   对于 `Jack Tors` 或 `EastSalesUser1`，关键的 Windows 10 操作系统设置和保存在 Windows 通用应用程序 (UWP) 中的数据将随他们漫游，每当他们登录到一台新电脑时。

提醒一下，起初 `EastSalesUser1` 必须登录到 `DJ++` 机器。同样，你在第 2 章中设置了 `DJ++` 机器，当时你现有的本地域加入机器使用组策略将自身引导加入 Azure 并注册到 MDM。

再次提醒，Jack 只能登录已 MDM 注册但非 `DJ++` 的机器。请记住，像 `Jack Tors` 这样“纯云端”的用户无法使用 `DJ++` 机器，因为他们的账户仅存在于云端，没有本地账户可供登录。

正如我所说，Office 365 Business Essentials 相当便宜。为 `Jack Tors` 和 `EastSalesUser1` 购买后，没有可下载的 Office 软件（如 Word 或 Excel），这没关系。我们反正也不需要。

要为这些用户购买单个许可证，请访问 `portal.office.com`。然后在“账单”中选择“购买服务”。选择 Office 365 Business Essentials 并一次购买一个许可证。一个给 Jack，一个给 `EastSalesUser1`。请注意，在结账过程中有一个小复选框（未显示），名为“自动分配给所有无许可证的用户”。结账时请**不要**勾选它。

接下来，回到 `portal.office.com`，转到“用户”➢“活动用户”并选择 `Jack Tors`。然后选择“产品许可证”➢“编辑”（未显示）以添加 Office 365 许可证，如图 7.3 所示。

对 `EastSalesUser1` 重复该过程，但这一次还要确保你同时分配了 E5 许可证和 Office 365 Business Essentials 许可证。

现在，开始配置企业状态漫游和 OneDrive for Business。

![图 7.3 Jack 现已获得 Office 365 和 SharePoint（未显示）许可，这意味着他拥有 OneDrive 访问权限。确保本地（但已同步）用户如 `EastSalesUser1`（未显示）也获得 E5 和 Office 365 Business 许可证。](img/c07f003.jpg)

**图 7.3** Jack 现已获得 Office 365 和 SharePoint（未显示）许可，这意味着他拥有 OneDrive 访问权限。确保本地（但已同步）用户如 `EastSalesUser1`（未显示）也获得 E5 和 Office 365 Business 许可证。

## 企业状态漫游

它自 Windows 8.1 起就已存在。你可以在图 7.4 中看到。也就是说，任何拥有 Microsoft 账户的人都可以自动将设置存储“在云端”，并在他们登录的另一台设备上自动恢复。普通消费者用户只需转到“设置”➢“同步你的设置”，即可看到它，如图 7.4 所示。

但对于我们 IT 管理员来说，这项功能曾经一度不存在。但现在有了，它称为企业状态漫游，简称 ESR。ESR 与消费者服务非常相似，但正如你所料，它具备一些企业功能。基本上，该服务遵循智能业务规则，例如将数据保留在最近的 Azure 数据中心，对于德国等数据法规更严格的国家，则将数据完全保留在德国境内。此外还有日志记录功能，如果你需要排查同步过程，可以访问这些日志。

![图 7.4 Windows 消费者同步设置](img/c07f004.jpg)

**图 7.4** Windows 消费者同步设置

那么，启用 ESR 后，究竟有哪些内容会在计算机间漫游？列表如下：

*   UWP 应用程序数据（前提是应用程序支持；有些支持，有些不支持）
*   操作系统设置和个性化（如桌面、图标等）
*   辅助功能
*   语言设置
*   Edge 浏览器设置
*   凭据

然而，某些用户可能同时拥有消费者 Microsoft 账户和企业 Azure 账户，并在**同一台机器**上使用这两个账户。什么？普通用户使用你 IT 部门的电脑访问 Windows 消费者商店下载游戏或绘图应用？请看图 7.5 了解用户如何做到这一点的示例。

好吧，别慌。

正如你所料，首先，他们家里带有“宝贝，坚持住！”字样的猫咪壁纸不会神奇地漫游到你的商用电脑上。

而且，任何非来自“商业版 Windows 应用商店”的应用程序也不会漫游到 Azure 存储的数据中，进而下载到另一台电脑上。

ESR 仅面向企业。

![图 7.5 使用消费者 Microsoft Store 添加个人账户](img/c07f005.jpg)

**图 7.5** 使用消费者 Microsoft Store 添加个人账户

### 设置企业状态漫游

这将是本书中**毫无疑问最容易**设置的内容。

在 Azure 中，点击“设备”➢“企业状态漫游”，并在“用户可跨设备同步设置和应用数据”中选择“所有”。你可以在图 7.6 中看到此项。

![图 7.6 开启企业状态漫游](img/c07f006.jpg)

**图 7.6** 开启企业状态漫游

你也可以选择“选定”并指定哪些用户拥有此权限。但我建议直接保留“所有”设置即可。

点击“保存”，搞定。你已将其开启。

快速提示：Windows 10 电脑需要重启，每位用户需再次登录，魔法才会生效。此外，如果这不立即生效，请等待过夜后再试。

首先尝试做什么？我建议以 `EastSalesUser1` 身份登录到你的 DJ++ 机器，并将桌面背景更改为另一张内置图片，如 图 7.7 所示。

![图 7.7 更改背景图片](img/c07f007.jpg)

**图 7.7** 更改背景图片

保持登录状态，并随意登录到另一台 Windows 10 机器。

然后，以 `EastSalesUser1` 身份登录到另一台 DJ++ 或仅加入 AAD 的机器。甚至如果你*已经以* `EastSalesUser1` 身份登录了……等一下……再等一下……宾果！

桌面背景一样！

下一站：Edge 收藏夹。在第一台机器上，使用 Edge 访问 [MDMandGPanswers.com](http://MDMandGPanswers.com) 并将其添加为收藏夹。很好。现在关闭 Edge。现在在第二台机器上，打开 Edge 并直接转到“收藏夹”选项卡。等一下……再等一下……（这对我来说比桌面背景同步花的时间更长）……然后再次宾果！当 Edge 正在运行时，你可以看到收藏夹设置同步过来了。太神奇了！

在两台仅加入 Azure 的机器上，使用 Jack Tors 重复相同的体验。因为企业状态漫游默认影响所有 Azure AD 用户，所以这直接就能工作。

但请记住，如果你尝试对 UWP 应用程序执行此操作，它可能会也可能不会神奇地漫游设置。这取决于 UWP 开发人员决定是否要以这种方式存储和漫游设置数据。

关于企业状态漫游的 Microsoft 文档在此（以及故障排除指南）：

`https://docs.microsoft.com/en-us/azure/active-directory/devices/enterprise-state-roaming-enable`

如果你遇到麻烦，ESR 也有一个不错的故障排除指南，其中还解释了如何开启日志记录，地址如下：

`https://docs.microsoft.com/en-us/azure/active-directory/devices/enterprise-state-roaming-troubleshooting`

最后，关于企业状态漫游和另一种漫游技术 Microsoft UE-V（在侧边栏“其他 Microsoft 漫游技术：Windows UE-V、漫游配置文件和 fsLogix [最近被 Microsoft 收购]”中解释）的一个不错的视频（虽然有点旧），可以在 `www.youtube.com/watch?v=OG58JBMliH8` 找到，或搜索“Understand settings roaming solutions in Windows”。

### 其他 Microsoft 漫游技术：Microsoft UE-V、漫游配置文件和 fsLogix（最近被 Microsoft 收购）

那么下一个显而易见的问题是，如果企业状态漫游旨在漫游桌面和 WUP 应用程序，我该如何漫游 Win32 应用的设置？

在撰写本文时，有两个官方答案，还有一个即将推出。

官方答案是使用 Microsoft UE-V，即用户体验虚拟化。这是一个可供企业付费客户使用的产品，允许将 Win32 应用程序的状态存储在共享或主文件夹中，并在用户漫游到另一台机器时根据需要将这些设置下载回来。

UE-V 设置起来不是超级难，但要让它完全按预期完美工作有点繁琐。它曾经是一个单独的附加产品。现在，客户端组件内置于 Windows Enterprise 和 Education 版中，并通过组策略进行管理。文档在此：

`https://docs.microsoft.com/en-us/windows/configuration/ue-v/uev-for-windows`

UE-V 已有一段时间未更新，因此其进展似乎已停滞，正如这篇帖子所证明的那样，其前景似乎不妙：

`https://www.reddit.com/r/sysadmin/comments/8qu07u/ms_may_kill_uev/`

另一个“岌岌可危”的 Microsoft 技术是漫游配置文件，我在拙作《组策略：基础、安全与托管桌面》的第 9 章中详细介绍了它。也许你已经在使用漫游配置文件，且效果相当不错。但多年来一直有传言说它们最终可能会被淘汰。

如果漫游配置文件和 UE-V 都在潜在的砍掉名单上，那什么能取代它们呢？

嗯，在 2018 年 12 月，Microsoft 宣布收购 fsLogix，这是一家试图彻底解决漫游配置文件问题的公司。fsLogix 的关键作用是将整个配置文件存储为可重新附加的 VHD（虚拟磁盘）文件。这与过去人们尝试解决此问题的方式完全不同。当有人在机器间漫游时，只要 VHD 可用（或已缓存），然后……宾果。即时漫游桌面。

在撰写本文时，Microsoft 已宣布支持 RDSH（即终端服务）场景、VDI 场景以及其 Windows 虚拟桌面 (WVD) 服务。

如果客户拥有任何 RDSH 许可证、VDA 或 WVD 权利，也可以使用 fsLogix。目前不清楚的是，如果客户没有 RDSH 许可证，他们是否仍可以将 fsLogix 技术用于其本地系统……比如普通、枯燥的桌面？仍在静待事态发展。

fsLogix 技术修复了 VDI 固有的一些关键问题，可能是漫游配置文件的继任者，也许也是 UE-V 的继任者。事实上，他们已经表示肯定会使用 fsLogix 来替代 RDSH 的用户配置文件磁盘 (UPD)（后者将在未来某个时间点停止使用）。

在 fsLogix 被收购时，我写了一篇博客文章，总结了我当时对收购的看法：

`https://www.policypak.com/pp-blog/microsofts-acquisition-of-fslogix-is-good-for-cloud-vdi-and-policypak-customers`

请注意，当你阅读此文时，该文章可能已过时，具体取决于 Microsoft 保留或砍掉了 fsLogix 产品线中的哪些内容。

## OneDrive for Business

让我们把一件事弄得完全清楚：OneDrive for Business 不是 OneDrive。是的，这也可能有点令人困惑。所以让我们理清一下：

*   **OneDrive 个人版**：消费者文件共享系统。这是供个人管理个人文件使用的，就像你表弟 Jimmy 刚从 Best Buy 买了一台电脑，文件挂在 Microsoft 的公有云里。
*   **OneDrive for Business (ODB)**：这是用于员工存储业务文件的，由 IT 部门中的你进行管理。它不仅处理文件，还处理 SharePoint 库。这随 Office 365 订阅提供，或在你使用 SharePoint 时提供。

我们将**只**、**只**、我是指**只**处理 OneDrive for Business，通常缩写为 ODB。

但伙计，每次都要打这么多字和说这么多话。

所以，别怪我，但在本章中，我就叫它 OneDrive 了。实际上，这也是 Microsoft 的叫法，除非他们在指出特定的商业或消费者功能。

不管怎样，让我们继续学习 OneDrive。（看懂我的双关了吗？）

如果你还在犹豫，或者可能不确定 OneDrive，我可以推荐一个单一资源，它很好地为企业中的 OneDrive 奠定了基础。如果你多出一两分钟（好吧，文档页面说是 40 分钟，但我觉得你可以快得多），在继续之前快速阅读一下。我们将会涉及其中的一些，但不是所有概念。

`https://docs.microsoft.com/en-us/onedrive/plan-onedrive-enterprise`

话虽如此，如果你不读也完全没关系。我不会依赖你已经读过它；它只是对我们的谈话有点有用的预先铺垫。
