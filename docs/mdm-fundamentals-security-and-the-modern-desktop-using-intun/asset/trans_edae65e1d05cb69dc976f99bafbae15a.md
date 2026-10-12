

# 第 4 章  

## 共同管理与共同策略管理

Intune 刚推出时，官方立场很明确：一台机器不应同时由 Active Directory（配合组策略）、SCCM 和 Intune 来管理。那将是一场灾难，因为你根本无法知道某个设置究竟源自何处。

那是“故事 1.0 版”。我想先解释这个故事，然后再讲“故事 2.0 版”，后者发生在 2017 年 9 月左右，我会说明它有何不同以及是如何演变的。

这个“故事 1.0 版”被称为混合 MDM。

这个“故事 2.0 版”被称为共同管理，它涉及你的 MDM 服务与 SCCM 和组策略协同工作。

确实，将组策略与 MDM 结合使用有一些有趣的优势和陷阱。首先，你可以使用组策略来“引导”现有机器加入你的 MDM 服务。但是，一旦机器同时接收组策略和 MDM 设置，谁生效呢？

这有很多内容需要解释和探讨，这也是本章的全部主题。

## SCCM 与 Intune 的共同管理

同样，回到 Intune 发布之时，阻止设备同时在 SCCM 和 Intune（或任何 MDM 服务）中注册，在当时是一个完全明智的决定。

你不会希望设置从多个来源下发，而这些来源之间却无法真正通信。更别提，那些已经将 SCCM 作为其“首选大型管理系统”并投入大量精力的管理员，也不想为了做事而跑两个控制台。因此微软创建了 Intune 连接器。

Intune 连接器使管理员能够继续使用其本地 SCCM 控制台，并执行与直接登录 Microsoft Intune 并在另一个控制台中操作完全相同的任务。微软称这种设计为混合设计，如[图 4.1](#c04.xhtml#figure4-1)所示。

![Figure 4.1 The old Microsoft Intune and SCCM hybrid design with the Intune Connector](images/c04f001.jpg)

**图 4.1** 旧版 Microsoft Intune 和 SCCM 带有 Intune 连接器的混合设计

但在 2017 年 Microsoft Ignite 大会上，微软宣布了思路的转变。他们不再主动阻止机器独立地从本地 Active Directory（即组策略）、SCCM 和/或 MDM 服务（如 Microsoft Intune）获取指令，而是展示了一张类似[图 4.2](#c04.xhtml#figure4-2)的图片，这是一个称为*共同管理*概念的极简版本。共同管理的术语最初专用于 Microsoft Intune，但正如你稍后将看到的，其他 MDM 服务也纷纷加入，采用了相同的术语。

![Figure 4.2 Simplified version of on-prem and cloud co-management](images/c04f002.jpg)

**图 4.2** 本地与云共同管理的简化版本

![image](images/tip.jpg) 确实，微软已在以下博客文章中解释他们正在停止混合模式：

`https://blogs.technet.microsoft.com/intunesupport/2018/08/14/move-from-hybrid-mobile-device-management-to-intune-on-azure/`

共同管理彻底颠覆了最初的规则。不再主动阻止设备同时在 SCCM 和 Intune 中注册（以及 Active Directory 配合组策略），现在他们彻底允许并鼓励这样做。

启用共同管理的想法和基本原理，源于微软意识到组织根本不会从其根深蒂固的本地解决方案（主要是 SCCM）“一跃而下”直接跳到 Intune（或任何 MDM）。其思路是：共同管理是一种方式，首先将“所有线路”从 Windows 10 连接到你的本地系统，同时也连接到你的 MDM 系统。然后，随着时间的推移，决定由什么技术（SCCM 或 Intune）来处理哪些*工作负载*（微软的称呼）。

如果你拥有现有的本地 SCCM 基础设施，启用共同管理需要经历不少步骤。但 SCCM 中的关键屏幕可见于[图 4.3](#c04.xhtml#figure4-3)，SCCM 管理员可在其中决定“哪个工具管理哪些策略”。

![Figure 4.3 Microsoft SCCM co-management screen to decide which technology will handle what workload](images/c04f003.jpg)

**图 4.3** Microsoft SCCM 共同管理屏幕，用于决定由哪种技术处理哪种工作负载

[图 4.3](#c04.xhtml#figure4-3)所示的工作负载屏幕，使 SCCM 管理员（在预先配置好共同管理的前提下）只需拖动一个或多个滑块，即可决定一种或多种工作负载策略类型现在将由 Configuration Manager (SCCM) 或 Intune 处理。

终结点随后将从 MDM 通道和传统的 SCCM 客户端同时获取指令。两全其美，直到你决定切断 SCCM 的连接。这就是其核心理念。也就是说，微软最新的立场是 SCCM 共同管理可能会维持相对较长一段时间。所以你甚至可能根本不会切断 SCCM 的连接。

而且，正如你在[图 4.3](#c04.xhtml#figure4-3)中所见，Intune 实际上有两个位置：试点 Intune 和 Intune。思路是你可以先有一个试点组，确保一切按预期运行。然后，彻底拨动开关，砰！你已为该工作负载切断了与本地 SCCM 的连接，现在仅使用 Intune 来处理该工作负载。在未来的某个时刻，你已移动所有滑块，所有工作负载均由 Intune 处理，嘿，看那样！你也许可以彻底告别 SCCM（或不再过多依赖它）。

我认为值得一提的是，真实的共同管理图景比我在[图 4.2](#c04.xhtml#figure4-2)中展示的用于引入主题的简化图表包含更多活动部件。换句话说，通过展开其所有部件，可以更好地用图形描述共同管理，如[图 4.4](#c04.xhtml#figure4-4)所示。

![Figure 4.4 Co-management with all of its moving parts](images/c04f004.jpg)

**图 4.4** 包含所有活动部件的共同管理

因此，充实 Microsoft 共同管理的所有细节超出了本书范围和我要涵盖的内容。但你可能确实拥有本地 SCCM，并希望启用 SCCM 和 Intune 共同管理，需要弄清 Microsoft 在谈论什么，并能理解他们的目标以及为什么希望你踏上 SCCM 和 Intune 共同管理之路。

在本书中，我*不*假设你拥有 SCCM。我是说，也许你有，那对你来说很棒。但我认为要求你搭建一个 SCCM 环境仅为尝试共同管理，未免负担过重。但如果你已有 SCCM 且对共同管理感兴趣，一个很棒的（虽然漫长且艰巨）六部分演练可从此处开始：`www.scconfigmgr.com/2017/11/23/how-to-setup-co-management-part-1/`。

