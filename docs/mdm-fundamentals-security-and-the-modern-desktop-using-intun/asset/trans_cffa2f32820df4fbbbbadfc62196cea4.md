

### Windows 更新策略与部署环境

*   **5% 的公司人员**（开发人员和 IT 测试人员）应立即获取：
    *   Windows 10 H1 或 H2 版本发布后立即获取（发布后前 30 天内）
    *   `Office 365 ProPlus` 月度构建版
    *   `OneDrive` 生产环境预览版构建版

*   **15% 的公司人员**（可能也会遇到问题，但不应因此责怪你）应获取：
    *   `OneDrive` 生产环境预览版构建版
    *   Windows 半年频道构建版。即该群体同时获取三月（H1）和九月（H2）版本。
    *   `Office 365 ProPlus` 半年定向频道构建版

*   **80% 的公司人员**应获取：
    *   `OneDrive` 企业环境预览版构建版
    *   仅限九月的 Windows 半年频道构建版（H2）
    *   `Office 365 ProPlus` 半年频道构建版

我意识到数学加起来是 101%，但希望你能理解我的意图。你将以一种易于管理的方式将升级风险分散到整个公司。而且，你将提前学到一些重要的东西。

以下是两个例子。

例如，假设现在是一月，公司 5% 的人员正在使用月度 `Office 365 ProPlus` 构建版。然后，糟糕！你古怪的 Outlook 插件停止工作了！别慌。至少现在你知道了，并且在三月 `Office 365 ProPlus` 半年定向频道版本被接下来 15% 的公司人员使用前，你有几个月的时间来处理它。

再举个例子。假设现在是四月，公司那 15% 的群体（如上所述）在三月使用了 Windows 半年频道构建版。现在，奇怪的是，某些品牌 X 的笔记本电脑显示文字倒立。在你的测试中，你发现如果回滚到之前的 Windows 版本，问题就会消失。（同样，这是一个完全虚构的例子。）好的！你有到今年九月，或者可能是明年九月的时间来解决这个问题。记住，九月版本对企业和教育客户拥有 30 个月的生命周期。

我刚才展示的图景和数学计算有一个轻微的缺点。如果你的环境中同时存在三月和九月版本的 Windows，可能会意味着一些额外成本。例如，如果你的防病毒软件供应商无法跟上节奏，那将会成为我建议你每次 Windows 升级都让那 15% 群体升级的一个潜在问题。

你也可以争辩说 `Windows Insider` 构建版根本不适合任何人用于生产环境。我认为有时确实如此，但并非总是如此。这就是为什么我建议将其保留在开发人员进行测试的机器上，以及 IT 团队模拟未来生产环境的机器上。

关键是要能够预测未来，而未来总是比你意识到的来得更快。

关于如何配置“谁应该获取哪个版本的 OneDrive”，我已经在 OneDrive 章节（[第 7 章](#c07.xhtml)：“企业状态漫游和 OneDrive for Business”）中介绍其组策略和 ADMX 设置时讲过，所以这里不再重复。详见 [第 7 章](#c07.xhtml) 中的“OneDrive 客户端版本和预览版”部分。但既然我还没讲 Windows 或 Office 升级设置，现在我们就来讲讲。

#### Windows Update for Business

同样，在崭新的世界里，不再有 `WSUS` 服务器。取而代之的是，你只是在控制延迟——即这些机器**最终**将安装更新和升级的“时间”。

我有时喜欢这样向人们解释：想想你的智能手机。智能手机有更新。但它不让你挑选要安装哪个小更新或微更新。你必须接受智能手机上的整个更新包。而且你**最终**会接受它。你可以稍后再说“稍后提醒我”或“今晚睡觉时更新我的手机”。如果由于某种原因更新没有按预期开始，你最终仍将不得不接受该更新。哦是的，**你将在智能手机上接受该更新**。所有内容。

这正是 Windows 10 为你准备的理念。目标不是控制你在 Windows 10 上消费哪个小更新或微更新。你拥有的唯一旋钮和拨盘，只是用于调整你**最终**将消费这些更新的“时间”。

用于管理 Windows 10“何时”消费更新的这些设置称为 `Windows Update for Business`，简称 `WUfB`。（发音为 *WOOF-bee*，这不是开玩笑。这真的是你大声读出该缩写的方式。）

因此，`WUfB` 设置同时存在于组策略和 MDM 领域。其要点相同，且两套设置都配置终结点上注册表中完全相同的位置。最终，使用组策略或 `SCCM` 传统管理的机器和由 MDM 管理的机器，都是从同一个地方下载更新：`Windows Update Service`。

请参见 [图 9.1](#c09.xhtml#figure9-1) 了解我的意思。

![图 9.1 传统设备和现代设备如何使用同一个 Windows Update Service。](images/c09f001.jpg)

[**图 9.1**](#c09.xhtml#figureanchor9-1) 传统设备和现代设备如何使用同一个 Windows Update Service。

简而言之，你需要告诉计算机它们属于哪个预览版，每个预览版包含一些属性。基本属性如下：

*   **服务频道**：
    *   半年频道：即三月（H1）或九月（H2）
    *   `Windows Insider - Fast`
    *   `Windows Insider - Slow`
    *   `Release Windows Insider`
*   推迟获取质量更新的天数（稍后详述）
*   推迟获取功能更新的天数（稍后详述）
*   活动时间：即 Windows 在更新后不应重启的时间段
*   功能更新卸载期：在机器上保留旧版 Windows 并可用于回滚的天数

还有其他一些旋钮和设置，但以上是最重要的。

在组策略中，你需要转到 `计算机配置` ➢ `策略` ➢ `管理模板` ➢ `Windows 组件` ➢ `Windows Update` ➢ `Windows Update for Business`。所有设置都在里面。有关组策略 `WUfB` 设置的“演练”，请参阅：

`https://docs.microsoft.com/en-us/windows/deployment/update/waas-wufb-group-policy#configure-windows-update-for-business-in-windows-10-version-1607`

在 MDM 领域，你需要使用一个特殊的配置文件。在 `Intune` ➢ `软件更新` ➢ `Windows 10 更新预览版` 中找到它。然后创建一个配置文件，如 [图 9.2](#c09.xhtml#figure9-2) 所示。

![图 9.2 在 Intune 中设置 WUfB 策略](images/c09f002.jpg)

[**图 9.2**](#c09.xhtml#figureanchor9-2) 在 Intune 中设置 WUfB 策略

完成后保存（未显示）。然后选择“分配”并分配给一组计算机，例如你之前创建的名称中包含“Computer”的计算机组，如 [图 9.3](#c09.xhtml#figure9-3) 所示。

![图 9.3 将 Windows 10 更新预览版分配给一组计算机](images/c09f003.jpg)

[**图 9.3**](#c09.xhtml#figureanchor9-3) 将 Windows 10 更新预览版分配给一组计算机

这些是基础知识，但你可能有一些我未涵盖的特殊场景或需求。有关保持 Windows 10 最新的所有事项的起点是 `https://docs.microsoft.com/en-us/windows/deployment/update/`。

有关 Windows 10 更新的更多信息，以下是我的首选推荐：

*   Windows 即服务快速指南：
    `https://docs.microsoft.com/en-us/windows/deployment/update/waas-quick-start`
*   “使用 Microsoft Intune 和 Windows Update for Business 保持 Windows 10 设备最新”是我发现的一篇小佳作。此材料对组策略和 MDM 都很棒。可在以下位置找到：
    `https://www.microsoft.com/en-us/itshowcase/keeping-windows-10-devices-up-to-date-with-microsoft-intune-and-windows-update-for-business`
*   `WUfB` 和 `Intune` 的简单文档可在此处找到：

