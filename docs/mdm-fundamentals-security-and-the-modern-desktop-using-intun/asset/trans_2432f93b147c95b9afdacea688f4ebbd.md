
如果你仔细查看[表 9.1](#c09.xhtml#table9-1)，会发现一条细则。即，Windows 的 30 个月生命周期仅提供给企业版和教育版，不提供给专业版。而且，该 30 个月的生命周期仅针对这些客户的 H2 版本提供。

换句话说：

*   企业版和教育版可选择 18 个月或 30 个月的周期。
*   企业版和教育版可选择 H1 或 H2 版本。如果选择 H2 版本，即表示选择加入 30 个月的周期。
*   如果客户使用的是 Windows 10 专业版，则必须每 18 个月升级一次才能保持在支持范围内。

![image](images/note.jpg) 此处可从时间与金钱的角度进行考量。你可以说：“对于使用 Windows 10 专业版的公司而言，每 18 个月升级一次的成本（人力成本）更高。”因此，鼓励组织购买企业版或教育版的一个理由是：虽然购买企业版需要花钱，但能节省持续的 Windows 10 升级人力成本（专业版 18 个月对比企业版 30 个月）。

如果想阅读关于此节奏变更的官方公告，可查看此处：

`https://www.microsoft.com/en-us/microsoft-365/blog/2018/09/06/helping-customers-shift-to-a-modern-desktop/`

如果想查看 Windows 10 发布以来微软推出的所有内容，可查看每个版本的“更改日志”：

`https://docs.microsoft.com/en-us/windows/whats-new/`

发布信息页面中的服务详情在此处：

`https://docs.microsoft.com/en-us/windows/windows-10/release-information`

我在一份幻灯片中看到一个有趣的演示图表，并在网上找到了一个副本，展示了每个版本都新增了*大量*功能。希望当你看到此处时该链接仍然有效，但请注意它始终会过时。无论如何，这是一个直观展示新增和改进功能的图表，你或许可以在此看到：`https://imgur.com/nhftbo9`。

但事实也是，在某个时间点，你必须进行升级。你不能像对待 Windows XP 那样拖延。这就是规则。除非你部署 Windows 10 LTSC。详见侧边栏。

另一个值得了解的实用链接是“Windows 生命周期事实表”，它解释了所有当前受支持的版本、其发布日期（即可用性日期）和终止服务日期，这些日期对于家庭版和专业版 SKU 与企业版和教育版 SKU 是不同的。

该实用链接（对服务器信息也很有用）位于：

`https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet`

### Windows 10 LTSC

Windows 诞生后，生命周期为 18 或 30 个月。

除非是 Windows 10 LTSC。LTSC 代表 `Long-Term Servicing Channel`（长期服务通道）。LTSC 与常规 Windows 10 大同小异，但又不完全相同。

首先，Windows 10 LTSC 旨在用于 MRI 机器、取款机、销售终端 (POS) 机器、安防摄像头机器及其他“专用设备”类型的计算场景。换句话说，你设置好 Windows 10，安装上你的单一用途软件，然后就不用再操心了。

长达 10 年。字面意义上的 10 年。

Windows 10 LTSC 的新版本大约每三年发布一次。

哇！如果这么好，为什么不是人人都用它？

有些人确实在用，但他们可能用得不对，也可能用得对。Windows 10 LTSC 不适合所有人的原因在于：持续更新的 Office 365 ProPlus 不支持在 Windows 10 LTSC 上运行，尽管 Office 2019 受支持。且 LTSC 不包含新版 Microsoft Edge 浏览器。

此外，还有一点真的会让人措手不及：LTSC 实际上与硬件的“硅级别”绑定。其含义是，如果你使用特定版本的 LTSC，该版本可能无法在尚未面世的新型现代 Intel 芯片上运行！这意味着如果你使用 LTSC 构建了“完美的黄金映像机器”，然后购买了一些新款台式机或笔记本电脑，Windows 可能根本无法工作！太疯狂了！

所以 LTSC 确实有其优势——再次强调，主要针对那些没有特定用户的单一用途机器。MRI 机器、取款机等是此用途最明显的机器类型。但也有一些更微妙的理由使用 LTSC。如需更多信息并查看 LTSC 是否为合适选择，可参考以下两个资源：

*   `博客：https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/LTSC-What-is-it-and-when-should-it-be-used/ba-p/293181`
*   视频：企业中 LTSC 的优缺点。在 YouTube 上搜索代码 THR3006 即可找到。

### 理解 Windows 修补节奏（质量更新）

这比功能更新节奏更容易理解。

每个受支持的 Windows 10 版本每月都会获得一次大型质量更新（即错误修复等）。这被称为“质量周二”，有时也称为“补丁周二”。

质量更新很简单：每月获得一次修复补丁（不包含新功能）。

如果你的 Windows 10 笔记本电脑离线放在抽屉里六个月怎么办？没问题。当它连接网络并检查更新时，Windows 10 只会下载最新的质量更新，该更新是累积的。这意味着你过去六个月错过的所有错误修复都会一并下载并应用。很棒。

在微软内部的“母舰”底层还有一些细节。具体来说，在常规月度质量周二更新发布两周后，会提供第二个质量更新作为预览版。Windows 不会自动安装这些预览版，但最终用户可以通过检查更新并同意安装来请求获取。

还有带外更新，你可以将其视为“紧急修复”，仅在需要时才会推送。当然，微软希望尽量减少此类更新，因为它们并非真正按计划进行。

此外，通常任何类型的质量更新完成后都会重启计算机（在活动时段之外；稍后详述）。没有人希望有不必要的重启。

如果想了解更多，请查看这两篇精彩的博客文章：

`https://blogs.windows.com/windowsexperience/2018/12/10/windows-monthly-security-and-quality-updates-overview`
`https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-10-update-servicing-cadence/ba-p/222376`

### 面向企业的 Windows 预览体验计划

作为对刚才讨论内容的一个补充，还有面向企业的 Windows 预览体验计划。面向企业的 Windows 预览体验计划旨在让你预览可能需要规划和推出的功能。

例如，在我最初撰写本章时，Windows 预览体验版刚刚发布了 Windows Sandbox（Windows 沙盒）功能，它就像一个迷你虚拟机，如果你进行小规模测试，用完即弃。随后，该功能随 Windows 10 1903 正式发布。

关键在于，你可以在功能被汇总并最终发布到半年频道之前，提前预览这些即将推出的建议功能。你可以据此做出明智的决策，决定是否推出，以及/或者如果认为其中有实用功能，为最终用户制定培训计划。

![image](images/tip.jpg) 要查看配置计算机使用预览体验版的组策略、MDM 和 SCCM 设置，请访问 `https://Aka.ms/manage-builds`。

### Office 服务

Windows 和 Office 如同表亲。它们相似，但各有风格。当然它们配合良好。因此，Office 365 ProPlus 拥有自己的部署节奏。以下是大致情况。

**月度频道** 前沿版本，包含所有最新功能。

