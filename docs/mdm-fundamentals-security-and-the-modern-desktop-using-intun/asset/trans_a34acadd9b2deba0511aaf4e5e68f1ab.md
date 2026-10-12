
如果您想要提供精选列表中不存在的某个内置 ADMX 首选设置，您的 MDM 服务*似乎*允许您这样做。但实际上不行。您无法将操作系统 ADMX 文件导入 MDM 服务，并交付任意在组策略中自然生效的组策略设置（伤心脸）。请记住，只有那些精选设置才是真正被允许的。

允许的是支持第三方 ADMX 设置的应用程序的第三方 ADMX 设置。我们也将探讨这一点。

![image](images/tip.jpg) 把那个伤心脸扔到外太空去。如果您确实有某个钟爱的 ADMX 设置（实际上，任何组策略设置都可以），并希望使用 MDM 服务进行交付，那么（再次无耻推销）PolicyPak MDM 来拯救您了。请访问 `www.policypak.com/products/policypak-mdm-edition.html` 查看 PolicyPak MDM 版本，并观看视频，了解如何部署真正的组策略、组策略首选项和组策略安全设置——这些都是微软不允许您部署的。演示操作方法的视频就在那个页面上。

因此，通过 Intune 推送这些精选 ADMX 设置主要有两种方式（其他 MDM 可能有所不同）：Administrative Templates 节点和 Custom URIs。

现在让我们一起探索这两种方式。

### 通过 Intune 使用 Administrative Templates 节点

在 Microsoft Ignite 2018 大会上，微软宣布了在 Intune 中通过简单的点击操作即可访问某些 Admin Template 设置的技术预览版。在预览版中，Administrative Templates 节点位于配置文件类型内，如[图 3.15](#c03.xhtml#figure3-15)所示。

![Figure 3.15 The preview of Administrative Templates node in Intune](images/c03f015.jpg)

[**图 3.15**](#c03.xhtml#figureanchor3-15) Intune 中 Administrative Templates 节点的预览版

创建 Administrative Templates 配置文件后，可能的设置会显示在其自己的边栏选项卡中，如[图 3.16](#c03.xhtml#figure3-16)所示。精选的 ADMX 设置以扁平但可搜索的列表形式呈现。在[图 3.17](#c03.xhtml#figure3-17)中，我搜索关键字 *desktop*，相关的设置随即出现。

![Figure 3.16 The list of curated ADMX settings in a flat list in Intune](images/c03f016.jpg)

[**图 3.16**](#c03.xhtml#figureanchor3-16) Intune 中以扁平列表形式呈现的精选 ADMX 设置

![Figure 3.17 Searching for relevant ADMX settings](images/c03f017.jpg)

[**图 3.17**](#c03.xhtml#figureanchor3-17) 搜索相关的 ADMX 设置

您可能会注意到，该列表并非层级结构，这与我们在组策略领域习惯看到的不同。我不知道微软是会保持现状，还是会通过引入层级结构使其更像组策略。就我而言，我倾向于以层级方式查看分组在一起的相关设置。您可以按 Path 排序，这在一定程度上能实现该效果，但这不是我的首选。无论如何，我猜测这可能会发生变化，因为该功能处于预览阶段，在本书付印前可能会有所更改。

单击任意策略设置会打开另一个边栏选项卡，这对组策略用户来说应该很熟悉。您可以看到“三态”选择：Not configured（默认）、Enabled 或 Disabled。

![](images/c03uf002.jpg)

随后，您可以将该配置文件分配给一组用户或计算机。在我的测试中，这些设置在针对 User 或 Machine 侧进行定位时似乎都能生效，但我并未测试所有设置。

我将以一个小小的坦白/疑问结束本节：如果有 386 个特殊的精选设置，为什么它们不*全*在这里？我粗略统计，预览版中仅列出了 231 个项目，其中一些还是针对 Office 的，按理说不应计入在内。

我知道这项工作正在进行中，请持续关注其进展。我预计此部分会首先针对 Office、IE 和 OneDrive 设置得到改进，然后扩展到其他精选的 ADMX 支持设置。

### 无 GUI 的 PolicyCSP 项目的 Custom URIs

因此，如果您的 MDM 服务没有提供一种巧妙的点击式方法来查找和配置 ADMX 支持的策略设置，那么是时候弄脏手来处理这些“第三类”设置了。

我认为我们即将共同演示的过程相当繁琐，但值得了解如何操作（即使在未来某个时刻，所有可用的 CSP 设置都浮出水面并启用了 GUI）。这就像知道如何转动钥匙启动汽车，或者知道如何使用搭电线给汽车搭电启动。

让我们来搭电启动吧。

同样，我即将展示的过程仅在您的 MDM 没有提供执行相同功能的 GUI 方法时才需要。我们要用作示例的是 `PolicyCSP/InternetExplorer/DisableAdobeFlash`，如[图 3.18](#c03.xhtml#figure3-18)所示。

![Figure 3.18 An example ADMX-backed setting](images/c03f018.jpg)

[**图 3.18**](#c03.xhtml#figureanchor3-18) ADMX 支持设置的示例

我在 Windows Intune 中摸索了约 20 分钟，找不到通过 GUI 点击启用它的方法。这并不意味着 Windows Intune 团队明天不会醒来并说：“嘿，让我们为‘禁用 Adobe Flash’设置启用 GUI 并提供给大家！”只是他们目前还没有……而已。

所以，在我们完全踏上这条路之前，先验证一下 Flash 在我们的 Windows 10 IE 中是否快乐、正常工作且已启用……然后再由我们“扼杀”它。（看来本书里我们做了很多“扼杀”工作。别告诉我妈。）

在 Windows 10 上启动 IE，然后访问 `http://get.adobe.com/flashplayer/about/`。您是否看到了如[图 3.19](#c03.xhtml#figure3-19)所示的充满活力的 Adobe 弹跳框？

![Figure 3.19 Adobe Flash enabled by default within IE](images/c03f019.jpg)

[**图 3.19**](#c03.xhtml#figureanchor3-19) IE 中默认启用的 Adobe Flash

很好，现在让我们使用自定义的 ADMX 支持 MDM 策略来“扼杀” Adobe Flash。

现在，如果我要使用组策略来完成这项工作（我知道我不会），该设置在 User 和 Computer 两侧均可找到。我在[图 3.20](#c03.xhtml#figure3-20)中展示了 User 侧的示例，打开组策略编辑器，在 User Configuration ➢ Admin Templates ➢ Windows Components ➢ Internet Explorer ➢ Add-on Management ➢ **Turn off Adobe Flash in Internet Explorer and prevent applications from using Internet Explorer technology to instantiate Flash objects** 下找到它。（是的，难以置信，那真的是该策略的全名。）

![Figure 3.20 The Group Policy setting we're going set, but using MDM](images/c03f020.jpg)

[**图 3.20**](#c03.xhtml#figureanchor3-20) 我们将要设置的组策略设置，但使用 MDM 实现

如果您查看[图 3.18](#c03.xhtml#figure3-18)，会看到文档阐述了该设置在组策略 ADMX 内部的位置。

文档中 ADMX Info 块的内容如下：

*   GP English name: Turn off Adobe Flash in Internet Explorer and prevent applications from using Internet Explorer technology to instantiate Flash objects
*   GP name: `DisableFlashInIE`
*   GP path: Windows Components/Internet Explorer/Security Features/Add-on Management
*   GP ADMX file name: `inetres.admx`

正如组策略设置可以是用户侧或计算机侧一样，MDM 设置也可以。在 MDM 术语中表达这一点的格式和方式如下：

*   `./User/Vendor/MSFT/Policy/Config/*AreaName*/*PolicyName*`
*   `./Device/Vendor/MSFT/Policy/Config/*AreaName*/*PolicyName*`

请注意 `/User` 和 `/Device` 前的前导点 (`.`)。

现在，当我们查看[图 3.20](#c03.xhtml#figure3-20)时，这是一个仅包含 Enabled 和 Disabled 的简单策略，没有什么花哨的地方，这也是我们要首先处理的目标。因此，我们的任务是向该策略设置交付“Enabled”，但使用的是 MDM 而非组策略。

我们现在需要将已知的所有信息片段和所需使用的片段收集起来，将它们全部组合在一起。
