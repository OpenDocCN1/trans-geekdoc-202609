
![image](images/note.jpg) 最好一开始就拦截所有能拦截的恶意软件。因此，请考虑结合 `SecureRun(TM)` 使用 `PolicyPak Least Privilege Manager`，它在这方面效果极好。

#### 在路上工作，以及获取分叉文件

以下是一个常见场景：

*   Sally 在路上，正在处理她的 OneDrive 文档。假设文件名为 `myFile.txt`。
*   Sally 随后离线。
*   Sally 在离线状态下继续编辑。进行了一堆更改并关闭了文件。
*   留在总部的 Fred 修改了 Sally 正在打开的同一文档 (`myFile.txt`)。Fred 进行并保存了他的更改，并将设置存储在 OneDrive 中。
*   Sally 重新上线……文件分叉了！

那么，什么是文件*分叉*？

当 Sally 的 OneDrive 同步客户端检测到 OneDrive 中的版本与她机器上的版本存在差异时，就会发生文件分叉。OneDrive 同步客户端不应覆盖云版本，也不应被 OneDrive 上的不同副本所覆盖。

在这种情况下，会发生以下情况：

*   Fred 的副本“获胜”。在此场景下，OneDrive 文件是“事实来源”。
*   Sally 的文件“失败”。Sally 的文件被重命名为 `myFile-COMPUTER1.txt`。
*   因为该文件是由 OneDrive 同步客户端新创建的，所以它会被上传到 OneDrive 服务。

结果？Sally 的 OneDrive 中会有 `myFile.txt`（实际上来自 Fred），而在 Sally 的电脑本地以及 OneDrive 中，都会看到一个新文件 `myFile-Computer1.txt`。

现在，如果你看到这种情况发生，那很可能就是上述原因。

请注意，Office 2016 及更高版本比较特殊，它具有合并更改或保留两个副本（分叉）的能力，如下所示。

![](images/c07uf006.jpg)

你可以通过策略设置**用户可以选择如何处理冲突中的 Office 文件**，来更改 Office 2016 及更高版本的此行为。

## 结束语

当你的电脑挂了，你带不走它。

但你可以把东西妥善地存放在云端：你的设置和你的文件。

这正是我们利用 `Enterprise State Roaming` 和 OneDrive 所做的事情。

在本章中，我们利用 OneDrive 完成了大量工作，但遗憾的是，还有许多内容我*无法*在 OneDrive 部分涵盖。我未涵盖的大部分内容都在 OneDrive 管理中心 (`admin.onedrive.com`) 中。在那里，你会发现更多可探索的内容，如设置审核、数据丢失防护 (DLP)、保留策略、警报等。

如果你想了解更多关于 OneDrive 的信息，此处列出了一些额外资源（其 URL 自我描述）：

*   `docs.com/OneDrive`
*   `https://docs.microsoft.com/en-us/onedrive/plan-onedrive-enterprise`
*   `aka.ms/ODAdminDocs` 供管理员指导参考。
*   `aka.ms/onedriveblog`
*   `aka.ms/OnPremSync`
*   `aka.ms/UninstallGroove`
*   `aka.ms/KFMFaq`
*   `aka.ms/FilesOnDemandMac`
*   `aka.ms/productivitylibrary`（面向最终用户）

以下是两个特别资源：

*   [OneDrive.uservoice.com](http://OneDrive.uservoice.com) 用于功能投票
*   OneDrive 博客，提供有趣且最新的资料。`https://techcommunity.microsoft.com/t5/Microsoft-OneDrive-Blog/bg-p/OneDriveBlog`。

如果你想观看 Ignite 2018 大会上最好的 OneDrive 视频，我建议在 YouTube 中输入以下会话代码：

*   THR2142: 关于管理 OneDrive for Business 你需要知道的事
*   BRK3099: Microsoft OneDrive 部署深度解析
*   THR4009: Microsoft OneDrive 同步基础与深度解析
*   BRK2131: 利用 OneDrive 推动采用与使用
*   BRK2126: 如何养成 OneDrive 习惯，让用户更快乐、更高效

现在，你（相当安全地）可以把那台机器扔进（虚拟的）湖里，并在下一章……通过 Autopilot 给用户配发一台全新的电脑了……

在你这么做之前，请在 Twitter 上 @jeremymoskowitz 并带上标签 #mdmbook，告诉我你在[第 7 章](#c07.xhtml)学到了什么！

# 第 8 章  

使用 Configuration Designer 和 Autopilot 进行推出与刷新

此时在本书中，你已经拥有了一个相当不错的“分层蛋糕”：

*   你已注册 MDM，从而获得远程管理机器的能力。
*   你的电脑能自动将自己放入动态组。
*   你拥有各种应用程序自动下载。
*   你有脚本在需要时运行。
*   你正在使用 MDM 分发 Windows 内置策略和某些应用程序的策略。
*   你的用户数据妥善地存储在 OneDrive 中。

一切进展顺利。

直到……Jack 在去机场的路上把电脑落在了出租车后座上。

糟糕。

现在怎么办？

依我之见，有四种场景：

**场景 1** Jack 落地后，让 Jack 自己跑去电子产品商店买台自己的机器。

**场景 2** Jack 落地后，可以去附近的公司分支机构，那里有人直接给他一台机器（方便的是，上面已经装好 Windows 10）。

**场景 3** 你可以直接向 Jack 发货一台新的、未配置的电脑（正好你办公室里有库存）。他第二天就能收到。

**场景 4：** 你可以与戴尔、联想等 OEM 合作伙伴合作，直接向 Jack 发货一台新机器。

在所有情况下，Jack 的新机器都必须配置为符合你们的企业标准。当然，我们希望尽可能自动化配置过程。

一路上还有几个场景值得 contemplation（考量）；例如，如果 Jack 离职，你想把 Jack 那台完好无损的电脑给别人用。如何快速清理 Jack 的专属数据并为 Tom 做好准备？还有一点要考虑：Jack 那台完好的机器突然挂了。确切地说是硬盘挂了。

针对上述所有场景，我们将在本章使用两种方法尽可能实现自动化：Windows Configuration Designer (WCD) 和 Autopilot。

这两种技术的目标表面上是相同的：与其擦除并重装一个已经预装完美操作系统的机器，不如利用 OEM 盒子里自带的系统。然后更快地接近你期望的配置目标。

这比擦除重装要快得多，还能避免准备“完美黄金映像”所需的所有赛前时间。

## Windows Configuration Designer

所以，让我们先假设场景 1。即，Jack 丢了笔记本，他只能去 Best Buy 或从 Amazon 买台新笔记本，或以其他方式弄台新机器。

这台机器很可能已经预装了 Windows 10，但可能不是正确的 Windows 10 *版本*。例如，是 Professional 版而非 Enterprise 版。

而且，我们绝对希望 Jack 能立即投入工作。让人把厂家预装的映像撕掉重装非常耗时，那是肯定的。是的，你可以争辩说撕掉重装能清除“预装垃圾软件”和不必要的项目，但你购买“签名版”电脑时就已经能做到这一点了。签名版电脑出厂时就不带陈旧的垃圾软件和垃圾文件。但通过我们即将一起做的事情，你也可以把机器上不需要的垃圾清理掉。

![image](images/tip.jpg) 你可以在此了解更多关于这些签名版机器的信息：

`https://www.microsoft.com/en-us/store/b/pcsignatureedition`

`https://www.laptopmag.com/articles/microsoft-signature-edition-windows-10-analysis`

但即便如此，也可以说工厂出厂时的电脑状态通常从性能角度来看是最好的：如果你不怎么动出厂预装的东西，你会获得最快的速度和最好的电池续航。

### 从 Windows Store 获取 WCD

我们如何接管一台已预装 Windows 10 的现有电脑并将其按我们的意愿进行转换？获取 Wicked！好吧，它真正叫 Windows Configuration Designer，简称 WCD，但我有时听到它被发音为 *wicked*。

WCD 有两种形式：

*   作为 Windows ADK (Assessment and Deployment Kit，评估和部署工具包) 的一部分

