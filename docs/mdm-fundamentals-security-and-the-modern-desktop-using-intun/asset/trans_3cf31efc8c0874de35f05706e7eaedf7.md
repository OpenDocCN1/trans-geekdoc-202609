
![image](images/tip.jpg) 如果你想了解有趣的硬盘灾难案例，请查看此链接：

`https://www.itnews.com.au/news/kroll-ontrack-dishes-out-top-ten-data-disasters-161908`

想一想：如果你的应用程序状态和用户文件都在云端，当你更换设备时，那些体验（状态和文件）就会自动恢复。

而且，如果你仍在使用 Windows 7（你自己清楚），你可以利用这里学到的相同方法，将用户本地机器上现有的文档迁移到 OneDrive。然后，当命运之日来临，擦除 Windows 7 并在他们的机器上安装 Windows 10 时（手动安装，或者正如你将在下一章学到的，可能通过 Autopilot），用户的文件已经预先暂存好，可在其全新的 Windows 10 环境中立即使用。

OneDrive 本身拥有一些非常引人注目的功能和优势。我最喜欢的有：

*   **OneDrive 按需文件**：用户无需在设备上存储 100% 的项目，而是可以在本地拥有完全可搜索的占位符文件，这些文件不占用磁盘空间。文件一旦被打开，就会同步到本地设备，从而确保始终拥有同步的本地版和云端版。如果你愿意，甚至可以选择让某个文件始终在本地设备上可用，以应对没有网络连接的情况。这对于 Surface Go 等存储空间仅 64GB 的移动及准移动设备来说非常棒。本章稍后我将演示此功能。

*   **文件还原**：恶意软件令人头疼。当用户点击受感染的文件时，它会开始级联加密硬盘上的所有文件、每个驱动器号，以及它能触及的“所有东西”。OneDrive 的文件还原功能允许用户（或管理员）点击发起“时间点还原”，将文件从灾难发生前的时间点“起死回生”。本章稍后我将演示此功能。

*   **文件预览器**：如果文件在 OneDrive 中，市场部的 Jane 如何知道文件长什么样？例如，如果 Jane 看到 `.XD` 文件类型，她能知道里面是什么吗？借助 OneDrive，内置了预览器。这样 Jane 只需点击 `.XD` 文件……bingo……它就是 Adobe XD 文件的线框预览（来自 Adobe XD，一个她从未听说过的真实程序，`https://helpx.adobe.com/xd/help/faq.html`）。但至少她无需预装 Adobe XD 就能大致了解文件内容。不错。OneDrive 目前支持超过 400 种不同的文件预览器，未来还会增加更多。

*   **告别驱动器映射**：OneDrive 构建于 SharePoint 之上（稍后我会详细解释）。因此，Microsoft 提供了一个工具，让你能够吸纳现有的文件共享并将其转存到 SharePoint 文档库中。目标？不再需要驱动器号，只需使用 OneDrive 访问文件（以前这些文件通过驱动器号访问）。

*   OneDrive 还拥有令人难以置信、震撼人心的人工智能功能。用户可以进行通用搜索，例如搜索单词 `school`，任何包含单词 `school` 的图片（只要清晰到足以识别）以及任何包含单词 `school` 的视频都会被找出来。简直太震撼了。

当然，我们首先得把数据迁移过去，这正是本章的重点。在下一章，我们将讨论获取新设备，届时云端的所有文件和状态将再次出现，仿佛什么都没发生过。

拜托：在时机成熟前，不要急着跳到前面去下载、安装或管理 OneDrive 客户端。我想先为你摆好筵席，再请你入座享用。

![image](images/tip.jpg) 如果你想全面了解 OneDrive 的功能，请前往 YouTube 搜索代码为 BRK2133 的 Ignite 2018 演讲视频。

当然，会有人说道：“我已经在用 Google Drive、Dropbox、Box……或其他网盘了。”我建议你至少调研一下 OneDrive，看看它提供的功能是否适合你的场景。事实上，你可能免费获得无限存储空间。许多版本的 Office 365（E3/E5 SKU）都附带无限 OneDrive 存储空间，绝对值得一试。话虽如此，如果你铁了心永不使用 OneDrive，可以使用位于 `计算机配置` ➢ `管理模板` ➢ `Windows 组件` ➢ `OneDrive` ➢ **防止将 OneDrive 用于文件存储** 的组策略，这将禁止使用 OneDrive。

## 本章赛前准备

本章节奏会很快。但为了跟上节奏，我们需要做一些赛前准备。

在真正开始前，我需要你现在完成以下三件事：

*   获取你的 Azure 租户 ID。
*   在组策略中正确暂存 OneDrive ADMX 文件。
*   为两个用户分配 EM+S E3 或 E5 许可证（如果尚未分配）。
*   为两个用户分配 Office 365 许可证（从而获得 OneDrive 权利）。

现在让我们逐一完成这些任务。

### 获取你的 Azure 租户 ID

通常不需要 Azure 租户 ID，但配置 OneDrive 时需要用到它。

回到 Azure 门户，点击“Azure Active Directory”。然后在“管理”下点击“属性”。你可以在[图 7.1](#c07.xhtml#figure7-1) 中看到包含租户 ID 的“目录 ID”框。在阅读本章时请保留此信息以备查阅。

![图 7.1 获取 Azure 租户/目录 ID](images/c07f001.jpg)

[**图 7.1**](#c07.xhtml#figureanchor7-1) 获取 Azure 租户/目录 ID

### 在组策略中暂存 OneDrive ADMX 文件

稍后我们会介绍，OneDrive 可以通过多种方式部署。

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

所以如果你已有中央存储，只需按第二个视频中的演示操作即可。视频结束时，你的文件应已位于中央存储中，如[图 7.2](#c07.xhtml#figure7-2) 所示。

![图 7.2 将 OneDrive.admx 和 OneDrive.adml（未显示）放入中央存储](images/c07f002.jpg)

[**图 7.2**](#c07.xhtml#figureanchor7-2) 将 `OneDrive.admx` 和 `OneDrive.adml`（未显示）放入中央存储

我假设你已按要求将 OneDrive ADMX 和 ADML 文件放入了中央存储。

### 获取 OneDrive 许可（随 Office 365）
