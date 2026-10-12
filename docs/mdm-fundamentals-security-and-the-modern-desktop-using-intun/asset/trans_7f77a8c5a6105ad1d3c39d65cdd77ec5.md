
由于 OneDrive for Business 随 Office 365 提供，具体取决于你在本书开篇是如何起步的，你可能拥有 Office 365，也可能没有。如果没有，且你只想学学门道，那得花点钱。

每位用户每月一杯星巴克拿铁的钱。

因此，每位用户每月 5.00 美元（按年支付）或每月 6.00 美元（无承诺），你就可以在现有计划中追加 Office 365 Business Essentials。同样，如果你已拥有 Office 365 E3 或 E5，则已支付费用并拥有无限存储空间。

如果你正在跟随本书学习，只是想体验 OneDrive 的运作方式，那就为两个用户购买以便跟随本章示例操作。以下是购买对象：

*   任意你喜欢的本地 AD 用户，如 `EastSalesUser1`。请记住，回在[第 2 章](#c02.xhtml)“设置 Azure AD 和 MDM”中，你使用了 `Azure AD Connect` 将本地 AD 账户同步到 Azure AD。

*   任意纯 Azure AD 用户，如 `Jack Tors`。请记住，Jack 是“完全诞生于云端”。他完全没有任何本地用户账户。而像他这样纯在 Azure AD 中创建的账户不会向后同步到本地 AD。Jack 彻头彻尾是云端用户！

如果你不确定哪些账户可能是合适的候选者，请查看[第 2 章](#c02.xhtml)中的 `图 2.49`。计划是：你将把 Office 365 Business Essentials 分配给一位来源为 Windows Server AD 的用户，把另一个许可证分配给一位来源为 Azure Active Directory 的用户。同样，请参阅 `图 2.49` 以回顾我的意思。

在此过程结束时，我们希望 `EastSalesUser1` 和 `Jack Tors` 都拥有 Azure 和 Office 365 Business Essentials 许可证。

为这两类账户各分配一个 Azure 账户和一个 Office 365 Business Essentials 许可证，将使我们能够探索以下场景：

*   对于 `EastSalesUser1`，你可以模拟拥有一台旧机器（Windows 7 或 Windows 10），并为他提供一台新（或较新）的 Windows 10 机器，让所有文件神奇地出现在你的本地用户群面前。

*   对于 `Jack Tors`，你可以模拟完全没有本地 AD 的环境。让 Jack 登录任何纯 MDM 注册的机器，并从任何地方获取文件。

*   第三个场景是 `EastSalesUser1` 完全脱离其本地 Active Directory，但仍能从任何地方获取其文件。

*   对于 `Jack Tors` 或 `EastSalesUser1`，关键的 Windows 10 操作系统设置和保存在 Windows 通用应用程序 (UWP) 中的数据将随他们漫游，每当他们登录到一台新电脑时。

提醒一下，起初 `EastSalesUser1` 必须登录到 `DJ++` 机器。同样，你在[第 2 章](#c02.xhtml)中设置了 `DJ++` 机器，当时你现有的本地域加入机器使用组策略将自身引导加入 Azure 并注册到 MDM。

再次提醒，Jack 只能登录已 MDM 注册但非 `DJ++` 的机器。请记住，像 `Jack Tors` 这样“纯云端”的用户无法使用 `DJ++` 机器，因为他们的账户仅存在于云端，没有本地账户可供登录。

正如我所说，Office 365 Business Essentials 相当便宜。为 `Jack Tors` 和 `EastSalesUser1` 购买后，没有可下载的 Office 软件（如 Word 或 Excel），这没关系。我们反正也不需要。

要为这些用户购买单个许可证，请访问 `portal.office.com`。然后在“账单”中选择“购买服务”。选择 Office 365 Business Essentials 并一次购买一个许可证。一个给 Jack，一个给 `EastSalesUser1`。请注意，在结账过程中有一个小复选框（未显示），名为“自动分配给所有无许可证的用户”。结账时请**不要**勾选它。

接下来，回到 `portal.office.com`，转到“用户”➢“活动用户”并选择 `Jack Tors`。然后选择“产品许可证”➢“编辑”（未显示）以添加 Office 365 许可证，如[图 7.3](#c07.xhtml#figure7-3)所示。

对 `EastSalesUser1` 重复该过程，但这一次还要确保你同时分配了 E5 许可证和 Office 365 Business Essentials 许可证。

现在，开始配置企业状态漫游和 OneDrive for Business。

![图 7.3 Jack 现已获得 Office 365 和 SharePoint（未显示）许可，这意味着他拥有 OneDrive 访问权限。确保本地（但已同步）用户如 `EastSalesUser1`（未显示）也获得 E5 和 Office 365 Business 许可证。](images/c07f003.jpg)

[**图 7.3**](#c07.xhtml#figureanchor7-3) Jack 现已获得 Office 365 和 SharePoint（未显示）许可，这意味着他拥有 OneDrive 访问权限。确保本地（但已同步）用户如 `EastSalesUser1`（未显示）也获得 E5 和 Office 365 Business 许可证。

## 企业状态漫游

它自 Windows 8.1 起就已存在。你可以在[图 7.4](#c07.xhtml#figure7-4)中看到。也就是说，任何拥有 Microsoft 账户的人都可以自动将设置存储“在云端”，并在他们登录的另一台设备上自动恢复。普通消费者用户只需转到“设置”➢“同步你的设置”，即可看到它，如[图 7.4](#c07.xhtml#figure7-4)所示。

但对于我们 IT 管理员来说，这项功能曾经一度不存在。但现在有了，它称为企业状态漫游，简称 ESR。ESR 与消费者服务非常相似，但正如你所料，它具备一些企业功能。基本上，该服务遵循智能业务规则，例如将数据保留在最近的 Azure 数据中心，对于德国等数据法规更严格的国家，则将数据完全保留在德国境内。此外还有日志记录功能，如果你需要排查同步过程，可以访问这些日志。

![图 7.4 Windows 消费者同步设置](images/c07f004.jpg)

[**图 7.4**](#c07.xhtml#figureanchor7-4) Windows 消费者同步设置

那么，启用 ESR 后，究竟有哪些内容会在计算机间漫游？列表如下：

*   UWP 应用程序数据（前提是应用程序支持；有些支持，有些不支持）

*   操作系统设置和个性化（如桌面、图标等）

*   辅助功能

*   语言设置

*   Edge 浏览器设置

*   凭据

然而，某些用户可能同时拥有消费者 Microsoft 账户和企业 Azure 账户，并在**同一台机器**上使用这两个账户。什么？普通用户使用你 IT 部门的电脑访问 Windows 消费者商店下载游戏或绘图应用？请看[图 7.5](#c07.xhtml#figure7-5)了解用户如何做到这一点的示例。

好吧，别慌。

正如你所料，首先，他们家里带有“宝贝，坚持住！”字样的猫咪壁纸不会神奇地漫游到你的商用电脑上。

而且，任何非来自“商业版 Windows 应用商店”的应用程序也不会漫游到 Azure 存储的数据中，进而下载到另一台电脑上。

ESR 仅面向企业。

![图 7.5 使用消费者 Microsoft Store 添加个人账户](images/c07f005.jpg)

[**图 7.5**](#c07.xhtml#figureanchor7-5) 使用消费者 Microsoft Store 添加个人账户

### 设置企业状态漫游

这将是本书中**毫无疑问最容易**设置的内容。

在 Azure 中，点击“设备”➢“企业状态漫游”，并在“用户可跨设备同步设置和应用数据”中选择“所有”。你可以在[图 7.6](#c07.xhtml#figure7-6)中看到此项。

![图 7.6 开启企业状态漫游](images/c07f006.jpg)

[**图 7.6**](#c07.xhtml#figureanchor7-6) 开启企业状态漫游

你也可以选择“选定”并指定哪些用户拥有此权限。但我建议直接保留“所有”设置即可。

点击“保存”，搞定。你已将其开启。

快速提示：Windows 10 电脑需要重启，每位用户需再次登录，魔法才会生效。此外，如果这不立即生效，请等待过夜后再试。
