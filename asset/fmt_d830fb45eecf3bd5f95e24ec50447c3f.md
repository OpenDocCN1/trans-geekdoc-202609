
# 网络恐怖主义指南：理解网络威胁环境与事件响应规划

![image](img/cover.jpg)

## 反恐网络安全

了解网络威胁环境和事件响应规划的指南

除非符合《版权、设计和版权法 1988》规定的研究或私人研究、批评或评论的公平使用范围，否则本出版物只能在获得出版商事先书面授权的情况下，或在版权许可证条款允许的情况下，以任何形式或任何方式复制、存储或传输。关于超出上述条款的复制请求，请联系以下出版商地址：

`[www.itgovernancepublishing.co.uk](http://www.itgovernancepublishing.co.uk)`

作者依据《版权、设计和版权法 1988》主张在此作品中被标识为作者的权利。

封面图片最初来源于 Shutterstock®。

*致谢 Milena。*

*感谢一切。*

理查德·宾利曾领导并参与多个关键安全项目，包括伦敦 2012 奥运会、索契 2014 奥运会，以及担任 London First 安全与弹性分部的执行董事。他是 `[CSARN.org](http://CSARN.org)` 的联合创始人兼董事。

截至目前，他的出版作品包括：

- `[The Security Consultant’s Handbook](https://www.itgp.com/handbook)`（ITGP：2015）；
- `[Terrorism: Just the Facts](https://www.heinemann.com/tf)`（Heinemann：2003）；以及
- `[Arms Trade: Just the Facts](https://www.heinemann.com/atf)`（Heinemann：2003）。

他曾于 2012–15 年担任伯克夏新大学安全与弹性高级讲师，并担任 BNU 商学院院长。他是 CSARN 全球网络安全学院的首席执行官兼 principal，也是网络安全和未来技术问题的常客评论员，最近曾为 `[London Evening Standard](https://www.les.co.uk)` 和 `[Sunday Express](https://www.sundayexpress.co.uk)` 作出贡献。

如果你和我一样，在购买非虚构书籍之前（或之后）会先思考两个问题：*是谁写的？为什么写的？* 毕竟，完成一本内容丰富的书需要大量时间进行研究、撰写和组织。

可能的第一步解释是：我已在两十多年的职业生涯中，从事与恐怖主义研究直接相关的工作，或在职位上显著涉及将恐怖威胁视为组织和人员风险的角色。职业经历多样，包括 `IT` 经理、政府代言人、内阁活动协调员、护卫人员（`CPO`）以及英国武装部队成员。超过十年，我还担任高等教育讲师和安全风险管理培训师，为各类机构、军队及知名企业客户提供培训。每个角色都让我有机会向众多出色的安全管理思想家和组织领袖学习。希望通过写这本指南，能够对那些默默无闻、默默奉献以保障我们安全的同仁作出一点实质性的回馈。

一些命运的奇特安排也促使我写下此书，并专注于我所撰写的具体内容。我差点错过了 2005 年 7 月 7 日阿尔卡伊达在伦敦公共交通系统的恐怖袭击。那天早晨，我正步入威斯廷顿工作（计划因为是我三十岁生日而只上半天），恰好迟到了利物浦街车站。我差点错过了阿尔德盖附近的 Circle Line 地铁爆炸，迟了四到五分钟。多年后，作为普利茅斯市议会议长，我部分负责该市在一名愤怒的“`incel`”（involuntary celibate，非自愿独身者）论坛用户实施连环杀戮后制定的危机恢复计划。这些以及其他人生经历有时会迫使我们以存在主义的方式思考，并更加努力做好“意外之事”的准备。此外，还要把身边的人团结起来行动！我认为，我并不特别独特，只是被恐怖分子的行动者稍微影响了一点。而且，我从未遭受过身体伤害，这与许多不幸他人形成鲜明对比。尽管如此，预防恐怖主义，或帮助他人应对恐怖主义，一直是我工作的重要主题之一。此书，我想，是出于提高意识、在风险管理和事件响应方面提供指导的愿望所产生的产物。

我最初产生撰写“网络恐怖主义”手稿的想法，是因为尽管缺乏科学依据，但我仍然强烈感觉到许多当代恐怖案件高度依赖于互联网驱动的计算机系统。自千禧年以来，社交媒体和交互式 `Web 2.0` 平台的推出已无处不在，不仅限于美国和更富裕的经济体。一些国家迅速采取措施规范公共使用，并将内容传输的直接责任置于互联网服务提供商（`ISP`）的肩上。其他国家则没有这样做——这正是互联网诞生五十多年后，许多国家和公司所面临的未经监管的遗产。

当社交媒体兴起，为未经审核的终端用户提供 `24/7` 的可用性和功能时，一个“神仙”从瓶中逃了出来，为那些考虑进行主动政治极端主义的人提供了便利。无论多么遥远、政治无足轻重或思想扭曲，暴力非国家行为体现在此都能轻松与其原本有限的作战范围之外的受众进行互动。来自边缘地区、倾向于宣扬暴力歧视和教条主义的人物——通常在其本国司法管辖区内被民间社会排斥——如今得以接触到令人着迷的、可靠的国际宣传和双向受众互动工具。

更为有利的是（对于恐怖分子而言），图片内容可以针对、并直接“手递手”地送达数字沉迷的大众。实施最残忍暴行的恐怖分子发现，他们可以绕过主流新闻机构，自行设定观看议程。与此同时，主流媒体编辑被迫覆盖恐怖袭击者的血腥内部视角。如果某些新闻机构试图摒弃“血腥即新闻”的口号，不提供低端点击诱饵，他们就面临消失的风险，并可能惹怒其股东。

对于极端演说者和恐怖招募者，精心措辞的操纵、诽谤与谴责开始在我们的智能手机和平板屏幕上频繁出现。这些由 themselves（自制）的激进新闻稿，包装了报导与评论，配以抓眼球的口号，它们的出现速度、权威性和精致度与主流新闻主播和纪录片制作的节目相当。先进的技术确实带来了“信息民主化”。但与此同时，也孕育了相当大的无序局面。似乎，paradoxically（悖论地），尽管全球在 `9/11` 恐怖袭击后更加协同推进国际反恐合作，信息通信技术（`ICT`）带来的显著人类安全挑战却在美、欧及其他地区几乎未得到充分关注。

本书将展示，自 2000 年代初以来，网络恐怖主义已获得显著——甚至可以说是未受遏制的——关注。网络恐怖主义的概念在理解当代恐怖现象的诸多必要细节方面变得至关重要。如今，由于先进通信和机器人技术的广泛获取，恐怖活动变得更加分散、随机、不可预测，甚至可以说是无法完全追责的。（一些恐怖组织和政治极端组织似乎已经失去了对其名义下所进行行动的完全集中控制。）最近的正式调查、庭审和司法报告已提供了支持这一数字化导致的暴力极端主义分散化的证据。检察官在法庭上提交的电子取证显示，数字媒体平台往往成为个体“激活”并沿情绪谱向实施物理恐怖袭击前进的*最主要原因*。

自 19 世纪初以来，众多恐怖主义学者、权威新闻机构和政府机构将恐怖主义定义为非国家行为体实施的预谋政治暴力。（尽管该术语最初来源于 1793/4 年法国后革命政府的血腥行为——即“恐怖统治”或 *Règne de la Terreur*。）在讨论“网络恐怖主义”时，情况略显混乱。当我着手撰写此书时，我不理解为何许多新闻报道中的“网络恐怖主义”并未严格遵循这一简洁的*非国家*定义标准。尤其是在我看来，大量网络恐怖行为确实是由非国家行为体实施的，且许多组织的世界观明显是*反政府*的。

事实上，我在此书写作过程中最大的困难之一是决定哪些案例和方面应省略，以及原因。为了读者的利益，我希望兼顾两个目标：保持简洁并提供概览。此书本可以轻松扩展为三到四倍的规模。所呈现的案例和案例研究仅是当前局势的片段。因此，本书主要是一个概览与指南，融合案例研究与实用指引。我希望它能激发进一步、更为详尽的研究。（如果你愿意接受这个挑战，请联系我！）

因此，本书并不 *per se*（本身）涵盖国家赞助的网络恐怖主义。即，网络攻击或协助物理攻击的行为，无论是由政府直接授权和实施，还是通过“可信的可辩驳”代理。虽然有少数例外案例和参考文献，其责任链条模糊，或攻击方式被证明是恐怖组织所关注的，但大多数威胁情报分析师应该能理解，政府指令或默许的网络攻击——旨在恐吓或杀害人类目标——通常属于*网络战争*或*战争*的定义范畴。我将把这片丰沃且广阔的研究领域留给其他作者去开发。

在新冠疫情之后，随着混合办公模式的推动，伊斯兰国在战场上的物理衰落，以及 2021 年国会山骚乱，仍然没有专门针对企业的网络恐怖主义指南轻易可得。信息安全经理和首席信息安全官（`CISO`）仍然热切期待同行评审的行业标准的出版，这些标准能够阐明应对先进技术带来的安全风险的最佳方法。例如，人工智能（`AI`）安全风险管理标准直到 2025 年才会发布。本书作为应对迫切的先进技术网络恐怖主义问题的一部分，因此描述并挖掘人工智能、聊天机器人、无人机和加密货币领域中的工具和产品。我们解释这些强大能力是如何被恐怖势力利用的。我们探讨虽然风险管理框架可能相当传统，但可以如何应用于当代先进的数字信息通信技术（`ICT`）世界中。

### 个人备注

这是我第四本出版的书。它远远是我完成的最艰难的一本。部分原因是目标主题极其宽广，且 `cybersphere`（网络领域）内的利用可能性以令人难以轻易应对的速度和复杂性进行特征化！写书的负担是身体和精神上的。这是一个漫长、持久、情感消耗的过程。你花费大量时间独自工作以保持专注并抓住手头的问题。这种超专注的心理模式很快会感觉像是在施加惩罚性的禁欲。就像自愿将你的心灵关入一年或更长时间的 `solitary confinement`（独居）中。除了你的日常工作（我的工作是教学）之外，你很难阅读除相关书籍和文章之外。（文中大量引用的书籍和文章总计约 360 种。）新的精彩书籍和电影匆匆而过，未被注意到。职业上的挫败感也潜伏在表面之下。新闻报道似乎每天都有，与‘你的主题’相关。但如果你试图发表评论或深入研究，你最终会变得分散注意力……延长了未能完成手稿的折磨！然后出现审阅和修订的各个阶段。但我们（我说‘我们’，因为不只是我）最终到达了那里。

因此，我很想记录非常重要的‘谢谢’。首先，向我的出版商 `ITGP` 和 Publications Manager（出版经理）`Nicola Day`，感谢她在写作过程中展现的孔孟之 `patience`（耐心）。我想感谢 `GRC International Group PLC` 的 Copy Editor `Kirsty Ridge`，她帮助我对本书的材料进行了校对。我完全低估了研究和内容所需的规模和范围。我也想感谢本书的两位审稿人。首先是 `Simon King`，前巴克什尔新大学（`Buckinghamshire New University`）安全与韧性高级讲师；在我们大学教书 `days`（教书日子）时是好同事。我很高兴地说，如今我们更多讨论板球，而不是安全困境。他的细致反馈极大地提升了第一稿。我们的第二位审稿人 `Ze’ev Portner` 是一名法学讲师。`Ze’ev` 拥有丰富的学术前身背景，曾在议会大厦担任首席助理。他还曾在英国各地的多个安全行业岗位工作。他的法律生涯始于以色列和伦敦的律所。`Ze’ev` 对本书对非技术读者的相关性的积极态度极大地帮助我们塑造了结构并精确调整最终成品。

同时，我也要感谢 `Marshall Kent`，前伦敦大都会警署的反恐协调员。`Marshall` 亲自提供了访谈，我最近的对话也非常有启发性和价值，推动了网络恐怖主义考量向官员和决策者推进。同样向以下人士致谢：`Helen Prendergast`，她在 2022/23 年耐心而有力地支持我在这个 *other world*（其他世界）中的努力。`David Evans`（创始人兼主席）和 `Andy Williams`（副主席）在 Global Terrorism Information Network（`TINYg`）任职；在我看来，这是目前最佳的公私部门反恐讨论合作伙伴。已故的 `Graeme McGowan`，前 `GCHQ` 和内政部成员，因他鼓舞人心且持续的支持、能量和积极态度而受到感谢。（`GMG` 在本书出版前不久不幸逝世。）最后，衷心感谢我的妻子 `Milena`，她始终支持并相信我。

到 2021 年为止——在二十年安全领域的经验之后——我认为我所有的会议演讲、课程编写、教学以及酒吧警告，都毫无意义……除非我能成功概括眼前的问题：网络恐怖主义。然后，清晰地解释防止其毁灭性影响的重要性。对我个人而言，是时候‘付诸行动或保持沉默’。将安全行业的思考、研究成果和媒体评论整合在一起。正如 `Arnold Schwarzenegger` 著名的话所说：“You can have results or excuses.”（你可以有结果，或者找借口。）我在此尝试提供一个基础的概述和快照，关于网络恐怖主义。超出此范围的内容——例如让读者更新安全计划，或向他人推荐这本 `ITGP` 书——显然是积极的结果！

`Richard Bingley`。

`London, 2024.`

Security practitioners are increasingly confronted with a chilling phrase: *cyber terrorism*. For many, such as me, it conveys a sense of fear and hopelessness at the same time. What is this thing called ‘cyber terrorism’? Moreover, what can we begin to do about it? Until it hits us, the impact feels a million miles away. Another person’s nightmare. Another organisation’s problem. Another country’s war.

For the purposes of precisely understanding cyber terrorism throughout this book, we have borrowed and applied the National Cyber Security Centre’s core two principles used to define and characterise a cyber crime:

**1. Cyber-dependent crimes** – crimes that can be committed only through the use of information and communications technology (`ICT`) devices, where the devices are both the tool for committing the crime, and the target of the crime.

**2. Cyber-enabled crimes** – traditional crimes that can be increased in scale or reach by the use of computers, computer networks or other forms of `ICT`. (`CPS`: 2019)

We will demonstrate how terrorists intentionally use computer systems to attack and harm human beings and property. They also use computer systems to diversify, complicate and increase terrorist attack impacts, including body counts and escalated public panic. Or to provide **disinformation** and **misinformation** to target audiences, including the emergency services and/or investigators, to sabotage aid, medical assistance and evidence. Nefarious `ICT` users, programmers and programs (including much `AI`-powered software) have all been instrumental in recruiting, inspiring, training, executing and amplifying acts of terrorism, which has resulted in the loss of life and/or lifechanging physical injuries that could never have occurred without `cybersphere` support and facilitation, whether by inanimate technology or others on the network using it. All of the above can be encapsulated by the phrase ‘cyber terrorism’.

### The issue at hand

互联网已成为绝大多数企业和个人日常生活的组成部分。根据数字、文化、媒体与体育部的数据，即使在新冠疫情导致的远程办公浪潮之前，九成成年人已经（有时甚至可以说）在线生活。我们以多种方式使用互联网来丰富和改变我们的生活。例如，数十亿人利用互联网免费学习兴趣爱好、正式教育，或提升职业前景。但这里有一个负面面：*“在错误的手中，互联网可以被用来传播恐怖主义和其他非法或有害内容”* (`DCMS`: 2019)。

这条政府警告在以下背景下显得尤为令人不安：互联网的接入正变得不再是自愿的。网络接入已被视为一种**存在主义的人权**，是公民身份和社会归属的前提。在某些司法管辖区，以及在某些公共安全事件情境（如疫情管理和军事宵禁）中，使用在线公共服务是联系公共部门支持并获取关键国家基础设施的**强制**手段。（许多公司和公共机构已完全取消客户电话线路和其他非正式支持渠道。）因此，喜欢与否，我们似乎都必须在线。
