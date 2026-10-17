
# MDM 基础、安全与现代桌面：Intune、Autopilot 与 Azure 管理、部署及保护 Windows 10 指南

![](img/cover.jpg)

## 献给我生命中所有坚强的女性。

## 致谢

首先，我要感谢来自 Microsoft 的 Cathy Moya，没有她，这本书就不可能完成。非常感谢你伸出援手，帮我找到合适的人来解答棘手的问题，并让我相信这本书是必要且可行的。说真的，没有你的帮助，这本书根本不会存在。

我接下来要特别感谢 Panu Saukko，企业移动性 MVP，他承担了技术编辑这项极不光鲜的工作，确保我没有“编造东西”，指出了我所有薄弱的环节，并贡献了他对该主题的深刻见解。你是一位坚强、睿智的男子汉，很荣幸能有你作为我的技术编辑。还要特别致敬 Yinghua (Sandy) Zeng，企业移动性 MVP，她帮助复核了各种项目，并在不止一个主题上帮我拨云见日。我真不敢相信你们两个脑子里装了多少信息和知识。

感谢 Stephen Rose 慷慨撰写序言并审阅 OneDrive 内容。

感谢来自 Microsoft 的全章审阅者和答疑解惑者：Michael Neihaus、Mahyar Ghadiali、Ken Revels、Christian Refvik、Craig Marl、Aisha Wang、Dilip Radhakrishnan、Riki June、Peter Kaufman、Chris Hopkins、Jan Ketil、Skanke、Joe Kim、Sreekar Mankala 以及 Microsoft 的其他朋友和审阅者。只是……哇。非常非常感谢你们从繁忙的工作中抽出时间帮助我，让这本书达到最好。

感谢 Sybex 的“梦之队”：Elizabeth Campbell、Judy Flynn、Christine O’Connor、Kenyon Brown 和 Pete Gaughan。正是你们让质量最终胜出。

感谢我的妻子和家人包容我错过的一些夜晚和周末。感谢我在 PolicyPak 和 `MDMandGPanswers.com` 的超级团队，每天都拿出最佳状态。我简直太喜欢和你们所有人一起工作了。

最后，如果你手捧此书（或在线阅读），我想感谢你尝试学习新事物、拓展新领域，并信任我。

感谢你购买本书，参加我的现场活动和访问 `MDMandGPanswers.com`，以及使用我的 PolicyPak 软件。

亲自见到你是我工作中最喜欢的部分，我期待听到这本书如何帮助了你。

## 作者简介

自成为世界上最早的 MCSE 之一以来，Jeremy Moskowitz 为国内一些最大的组织执行了 Active Directory、组策略和 MDM 的规划与实施。

他是一位获奖 15 年的 Microsoft MVP，最初在组策略和桌面管理领域，现在专注于企业移动性，重点关注 Intune。

Jeremy 是 `MDMandGPanswers.com` 和 PolicyPak Software 的创始人。《Computerworld》杂志将 `MDMandGPanswers.com` 评为对 IT 专业人员最有用的 20 个 Microsoft 网站之一。`EnterpriseMobilityExchange.com` 将 Jeremy (`@jeremymoskowitz`) 列入 IT 专业人士应在社交媒体上关注的“7 位终端管理领域的 Twitter 大咖”。

他的另一本 Sybex 出版的书是 *Group Policy Fundamentals, Security, and Troubleshooting, Third Edition*（第三版），随处可见于管理员的桌面上。

在 `www.MDMandGPanswers.com` 获取他的签名版书籍，并了解更多关于 Jeremy 的组策略和 MDM 大师班培训。在 `www.policypak.com` 了解如何保护您的桌面和应用程序、管理 Windows 10 的所有领域，并通过 MDM 服务部署所有组策略设置。

**注意**：原始列表中缺失页码 14、74、116、134、232，此处按原文保留缺失状态。
