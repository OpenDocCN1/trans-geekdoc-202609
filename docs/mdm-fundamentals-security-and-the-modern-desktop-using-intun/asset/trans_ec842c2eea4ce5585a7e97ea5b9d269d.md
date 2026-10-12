

![](images/cover.jpg)

版权所有 © 2019 John Wiley & Sons, Inc., Indianapolis, Indiana

在加拿大同步出版

ISBN: 978-1-119-56432-4

ISBN: 978-1-119-56434-8 (电子书)

ISBN: 978-1-119-56427-0 (电子书)

在美国制造

除 1976 年《美国版权法》第 107 条或第 108 条允许的情况外，未经出版商事先书面许可，或未通过版权许可中心 (Copyright Clearance Center, 222 Rosewood Drive, Danvers, MA 01923, (978) 750-8400, 传真 (978) 646-8600) 支付适当的每份复制费用获得授权，不得以任何形式或任何方式（电子、机械、影印、录制、扫描或其他方式）复制、存储于检索系统或传播本出版物的任何部分。要求出版商许可的请求应发送至 Permissions Department, John Wiley & Sons, Inc., 111 River Street, Hoboken, NJ 07030, (201) 748-6011, 传真 (201) 748-6008, 或在线访问 [http://www.wiley.com/go/permissions](http://www.wiley.com/go/permissions)。

责任限制/免责声明：出版商和作者不对本书内容的准确性或完整性做任何陈述或保证，并特此声明不承担任何明示或暗示的保证，包括但不限于对特定用途适销性的保证。销售或推广材料不得创建或延伸任何保证。本书包含的建议和策略可能不适用于所有情况。本书的销售基于这样的理解：出版商不从事提供法律、会计或其他专业服务的工作。如果需要专业协助，应寻求称职专业人士的服务。出版商和作者均不对由此产生的损害承担责任。本书引用的组织或网站作为引证和/或潜在的进一步信息来源，并不意味着作者或出版商认可该组织或网站可能提供的信息或建议。此外，读者应知悉，本书列出的互联网网站在本书撰写时和读者阅读时之间可能已发生变更或消失。

如需了解我们其他产品和服务的一般信息或获取技术支持，请联系我们的客户服务部：美国境内拨打 (877) 762-2974，美国境外拨打 (317) 572-3993，或传真 (317) 572-4002。

Wiley 以多种印刷和电子格式出版，并采用按需印刷方式。随标准印刷版附带的某些材料可能不包含在电子书或按需印刷版中。如果本书提及的媒体（如 CD 或 DVD）不在您购买的版本中，您可以在 [http://booksupport.wiley.com](http://booksupport.wiley.com) 下载这些材料。了解更多 Wiley 产品信息，请访问 [www.wiley.com](http://www.wiley.com)。

美国国会图书馆控制号：2019943877

商标：Wiley、Wiley 徽标和 Sybex 徽标是 John Wiley & Sons, Inc. 及/或其关联公司在美国和其他国家的商标或注册商标，未经书面许可不得使用。Windows 是 Microsoft Corporation 的注册商标。所有其他商标均为其各自所有者的财产。John Wiley & Sons, Inc. 与本书提及的任何产品或供应商均无关联。

# 献给我生命中所有坚强的女性。

# 致谢

首先，我要感谢来自 Microsoft 的 Cathy Moya，没有她，这本书就不可能完成。非常感谢你伸出援手，帮我找到合适的人来解答棘手的问题，并让我相信这本书是必要且可行的。说真的，没有你的帮助，这本书根本不会存在。

我接下来要特别感谢 Panu Saukko，企业移动性 MVP，他承担了技术编辑这项极不光鲜的工作，确保我没有“编造东西”，指出了我所有薄弱的环节，并贡献了他对该主题的深刻见解。你是一位坚强、睿智的男子汉，很荣幸能有你作为我的技术编辑。还要特别致敬 Yinghua (Sandy) Zeng，企业移动性 MVP，她帮助复核了各种项目，并在不止一个主题上帮我拨云见日。我真不敢相信你们两个脑子里装了多少信息和知识。

感谢 Stephen Rose 慷慨撰写序言并审阅 OneDrive 内容。

感谢来自 Microsoft 的全章审阅者和答疑解惑者：Michael Neihaus、Mahyar Ghadiali、Ken Revels、Christian Refvik、Craig Marl、Aisha Wang、Dilip Radhakrishnan、Riki June、Peter Kaufman、Chris Hopkins、Jan Ketil、Skanke、Joe Kim、Sreekar Mankala 以及 Microsoft 的其他朋友和审阅者。只是……哇。非常非常感谢你们从繁忙的工作中抽出时间帮助我，让这本书达到最好。

感谢 Sybex 的“梦之队”：Elizabeth Campbell、Judy Flynn、Christine O’Connor、Kenyon Brown 和 Pete Gaughan。正是你们让质量最终胜出。

感谢我的妻子和家人包容我错过的一些夜晚和周末。感谢我在 PolicyPak 和 `MDMandGPanswers.com` 的超级团队，每天都拿出最佳状态。我简直太喜欢和你们所有人一起工作了。

最后，如果你手捧此书（或在线阅读），我想感谢你尝试学习新事物、拓展新领域，并信任我。

感谢你购买本书，参加我的现场活动和访问 `MDMandGPanswers.com`，以及使用我的 PolicyPak 软件。

亲自见到你是我工作中最喜欢的部分，我期待听到这本书如何帮助了你。

# 作者简介

自成为世界上最早的 MCSE 之一以来，Jeremy Moskowitz 为国内一些最大的组织执行了 Active Directory、组策略和 MDM 的规划与实施。

他是一位获奖 15 年的 Microsoft MVP，最初在组策略和桌面管理领域，现在专注于企业移动性，重点关注 Intune。

Jeremy 是 `MDMandGPanswers.com` 和 PolicyPak Software 的创始人。《Computerworld》杂志将 `MDMandGPanswers.com` 评为对 IT 专业人员最有用的 20 个 Microsoft 网站之一。`EnterpriseMobilityExchange.com` 将 Jeremy (`@jeremymoskowitz`) 列入 IT 专业人士应在社交媒体上关注的“7 位终端管理领域的 Twitter 大咖”。

他的另一本 Sybex 出版的书是 *Group Policy Fundamentals, Security, and Troubleshooting, Third Edition*（第三版），随处可见于管理员的桌面上。

在 `www.MDMandGPanswers.com` 获取他的签名版书籍，并了解更多关于 Jeremy 的组策略和 MDM 大师班培训。在 `www.policypak.com` 了解如何保护您的桌面和应用程序、管理 Windows 10 的所有领域，并通过 MDM 服务部署所有组策略设置。

# 目录

1. [封面](fcover.xhtml)
2. [致谢](#f02.xhtml)
3. [作者简介](#f03.xhtml)
4. [序言](#f04.xhtml)
5. [导论](#f05.xhtml)
    1. [EMM 和 MDM 重新定义](#f05.xhtml#usec0002)
    2. [术语](#f05.xhtml#usec0003)
    3. [开始使用本书所需的准备](#f05.xhtml#usec0004)
    4. [本书不涵盖的内容](#f05.xhtml#usec0005)
    5. [如何知道买完书 80 秒后不会过时？](#f05.xhtml#usec0006)
    6. [关于组策略与 MDM 的最后说明](#f05.xhtml#usec0007)
    7. [关于我、本书、PolicyPak 及更多](#f05.xhtml#usec0008)
6. [第 1 章 企业移动性和 MDM 要点](#c01.xhtml)
    1. [准备使用本书](#c01.xhtml#usec0002)

