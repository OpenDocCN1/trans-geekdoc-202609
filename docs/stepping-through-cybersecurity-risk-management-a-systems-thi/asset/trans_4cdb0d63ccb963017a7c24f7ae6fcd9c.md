

FrameCyber 将评估、控制、事件、问题、指标和人员连接在一起，使企业能够管理网络安全风险。[图 1.11](#c01.xhtml#c1-fig-0011) 是框架元素连接方式的简化示意图。`Issues` 是表示固有风险的情况。`Assessments` 有助于问题识别。`Events` 是风险的证据。`Controls` 用于将风险降低到可接受的剩余水平。`Metrics` 有助于监督并支持关于网络安全风险的管理决策。与网络安全相关的 `Risks` 通过 FrameCyber 变得可见，这种理解支持做出明智的决策。

![Figure 1.11 Cybersecurity Risk Framework in a Nutshell](images/c01f011.jpg)

[**Figure 1.11**](#c01.xhtml#R_c1-fig-0011) Cybersecurity Risk Framework in a Nutshell

## 参考文献

1. Bernstein, P. (1996). `Against the Gods, The Remarkable Story of Risk`. Wiley.

2. Boardman, J. and Sauser, B. (2008). `Systems Thinking: Coping with 21st Century Problems`. Taylor and Francis.

3. COSO (2017). `Enterprise Risk Management: Integrating with Strategy and Performance`. Committee of Sponsoring Organizations of the Treadway Commission.

4. INCOSE (2023). “Most General ‘System’ Definition,” International Council On Systems Engineering, 2023, [https://www.incose.org/about‐systems‐engineering/system‐and‐se‐definitions](https://www.incose.org/about-systems-engineering/system-and-se-definitions) (访问日期：2024 年 2 月 14 日)。

5. ISO/IEC 27001 (2022). `Information Security, Cybersecurity and Privacy Protection – Information Security Management Systems — Requirements`. International Organization for Standardization/International Electrotechnical Commission. [www.iso.org](http://www.iso.org).

6. NIST‐CSF (2024). Framework for Improving Critical Infrastructure Cybersecurity, version 2.0. National Institute of Standards and Technology. [https://csrc.nist.gov/publications](https://csrc.nist.gov/publications) (访问日期：2024 年 1 月 15 日)。

7. Smith, L., “Shift‐Left Testing,” Dr. Dobb’s Journal. 26 (9): 56, 62, September 2001, [https://www.drdobbs.com/shift‐left‐testing/184404768](https://www.drdobbs.com/shift-left-testing/184404768) (访问日期：2024 年 1 月 14 日)。

8. Spafford, G., Metcalf, L. and Dykstra, J. (2022). `Cybersecurity Myths and Misconceptions, Avoiding the Hazards and Pitfalls that Derail Us`. Addison‐Wesley.

# 2 威胁

美国国家标准与技术研究院将威胁定义为：

> 任何可能通过信息系统未经授权访问、销毁、泄露或修改信息，以及/或拒绝服务，对组织运营（包括使命、职能、形象或声誉）、组织资产、个人、其他组织或国家产生不利影响的任何情况或事件（NIST [2012](#c02.xhtml#c2-bib-0022））。

[图 2.1](#c02.xhtml#c2-fig-0001) 中的系统图将此定义缩小到网络威胁。主要观点是，威胁鼓舞利用漏洞的对手，这些漏洞暴露了使对手目标得以实现的资产。这就是网络威胁的基本理念。威胁本身是对手相信将使目标得以实现的情况或事件。

## 2.1 威胁行为者

关于网络安全威胁最需要知道的是，实施威胁的行为者可能是危险的对手。其次需要知道的是，无论目标是否选择主动参与，对手与其目标之间都存在交互作用。一个推论是：`如果目标没有主动对抗对手，那么对手就具有优势`。在《孙子兵法》中，孙武通过以下话语对此情况进行了阐明：

`知彼知己`

   `百战不殆。`

`知己不知彼`

   `一胜一负。`

`不知彼不知己`

   `每战必败。`

![Figure 2.1 Threats](images/c02f001.jpg)

[**Figure 2.1**](#c01.xhtml#R_c2-fig-0001) Threats

似乎常识表明，网络威胁防范不能仅靠了解自己。孙武可能假设，一旦了解对手的漏洞，威胁目标当然会加强自身以抵御已知对手，因此不会畏惧战斗。他的观点是，你不仅需要了解自己的能力，还需要了解对手的能力，才能确信你的能力能使你免于失败。

在 FrameCyber^® 系统定义中，添加到主要观点的第一个上下文是它 `记录威胁企业的行为者`。遵循孙武的建议，网络安全对手的研究始于针对企业的不良行为者列表。一个著名的此类 `威胁目录` 示例是 ATT&CK 平台（MITRE 2015–[2023](#c02.xhtml#c2-bib-0014)）。MITRE 是一家不是缩写的公司（MITRE 中的 MIT 并不代表麻省理工学院）。MITRE 的 ATT&CK 框架根据与共同来源相关的活动簇将网络安全威胁行为者分类为组别。网络安全威胁分析师跟踪这些威胁行为者组别，并将他们的观察结果贡献给该平台。当然，由于网络威胁的短暂性，不同组织的威胁行为者定义可能与其他组织指定的定义部分重叠或部分矛盾。一些组别由于不同组织以不同名称跟踪同一组别而积累了多个别名。尽管如此，共享此类信息（即此 `威胁情报`）的目的是充分了解已知正在积极针对您的企业或市场或技术相似的企业的行为者。了解对手的第一步是了解哪些行为者正在针对您和您所在行业的其他人。

![Figure 2.2 Adversaries](images/c02f002.jpg)

[**Figure 2.2**](#c02.xhtml#R_c2-fig-0002) Adversaries

正如我们需要了解自己的网络安全框架来了解对手一样，我们还必须了解威胁行为者针对我们所运行的系统。深入研究 [图 2.1](#c02.xhtml#c2-fig-0001) 和 [2.2](#c02.xhtml#c2-fig-0002) 中的威胁系统定义，详细阐述了对手运作的上下文。对手类别包括（但不限于）罪犯、黑客活动家、国家、施虐者和恐怖分子。对手目标也各不相同。罪犯通常追求金钱。黑客活动家想要影响力。恐怖分子通常想要破坏。国家通常寻求信息/数据，但越来越多的国家也在寻求破坏、金钱和影响力。施虐者通常与复仇相关，但复仇可能采取破坏或金钱等其他更具体的目标形式。这些不同对手的共同点是，他们关注拥有可用于实现其目标的资产的目标。企业、政府和个人都有需要维护的信息、运营、人员、基础设施和声誉。威胁通过盗窃和/或滥用这些资产，对这些组织及其社区中可能的其他组织产生负面影响。

