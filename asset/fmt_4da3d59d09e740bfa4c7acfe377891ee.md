
**Vulnerability（漏洞）**。`Vulnerability` 是系统中被 `Attacker` 在网络 `Attack_Event` 中利用的缺陷或弱点。因此，`Vulnerability` 仅适用于针对 ICT（信息与通信技术）实施的网络 `Attack_Event`。Howard (1997) 建议了三种类型的漏洞：`ImplementationVulnerability`、`DesignVulnerability` 和 `ConfigurationVulnerability`。Simmonds et al. (2004) 建议了安全策略漏洞和技术漏洞。虽然技术漏洞通常是技术中的“弱点”，但安全策略漏洞是安全策略的弱点，如规划和控制不善。在本研究中，我们将漏洞分类为 `ImplementationVulnerability`、`DesignVulnerability`、`ConfigurationVulnerability` 和 `SecurityPolicyVulnerability`。

**Tool_and_Technique（工具与技术）** 可被视为 `Attacker` 用于执行网络 `Attack_Event` 的“手段”（即工具和/或技术）。本研究采用了 Donalds and Osei-Bryson (2014) 提出的 `Tool_and_Technique` 类别（`Tool`、`SocialEngineering`、`IllicitCollusion` 和 `AttackVector`）。

**Objective（目的）**。`Objective` 可被视为 `Attacker` 实施网络 `Attack_Event` 的主要目的、动机或最终目标。我们主要采用了 Donalds & Osei-Bryson (2014) 对攻击者目的的分类，并根据贸易媒体中网络犯罪案例的实证数据增加了新的类别。例如，我们加入了 `SelfPreservation` 和 `Moral`，以便对这些类型的 `Objective` 进行分类。

**Offence（罪行）**。`Offence` 可被描述为由 `Attacker` 实施的、依法可予惩处的非法网络行为或 `Attack_Event`。一个例子是“未经授权访问计算机程序或数据”（牙买加《网络犯罪法》，2015 年 – Jamaica Houses of Parliament, 2015）。

### 位置

**位置** 涉及五个概念：`Attacker`（攻击者）、`Attack_Event`（攻击事件）、`Victim`（受害者）、`Complainant`（报告者）和 `Target`（目标）。**位置** 是指个人/团体 `Attacker`、经历 `Attack_Event` 的 `Victim` 和/或 `Target`、报告 `Attack_Event` 的 `Complainant` 所在的国家（通常）和/或具体地址，以及 `Attack_Event` 发起的地点。然而我们要指出，虽然可能识别出涉及网络 `Attack_Event` 的计算机的 **位置**，但该 **位置** 不一定对应攻击者的 **位置**，因为攻击发生在网络空间，或者 `Attack_Event` 可能从多个来源发起。

### 报告者

**报告者** 是报告网络 `Attack_Event` 从而使当局知晓非法活动的人。**报告者** 可以是 `Individual`（个人）或 `Group`（团体）类型。此外，**报告者** 可能是 `Victim`（受害者），也可能不是。例如，某个人发现其家用电脑卷入了网络犯罪；此人可能既是 `Victim` 也是 **报告者**。然而，如果在一个组织中，员工因邮件服务器被黑而无法访问/检索邮件，相关员工可能会联系信息技术（IT）部门报告此事，因此该员工是 **报告者**，而非 `Victim`。虽然该员工会受到网络犯罪的影响，但 `Victim` 应是该组织。

### 受害者

**受害者** 是指以某种方式受网络 `Attack_Event` 影响的实体。由于 **受害者** 可以是 `IndividualVictim`（个人受害者）、`GroupVictim`（团体受害者）、`OrganizationVictim`（组织受害者）、`GovernmentVictim`（政府受害者）类型，我们提出 `VictimType`（受害者类型）以捕获网络 `Attack_Event` 中涉及的 **受害者** 类型。**受害者** 可能是特定网络 `Attack_Event` 的具体 **目标**，也可能不是。当 **受害者** 被专门针对时，**受害者** 和 **目标** 就是同一实体。另一方面，如果例如 `Attacker` 大规模分发病毒，**受害者** 不一定是特定 **目标**，而是基于机会（特定系统中的 `Vulnerability` 漏洞）成为 **受害者**。

### 目标

**目标** 是网络 `Attack_Event` 专门针对的实体。Hansman and Hunt (2005) 将硬件、软件和网络确定为 **目标** 的类型。Simmons et al. (2009) 将 **目标** 确定为操作系统、网络、本地[计算机]、用户和应用程序。van Herdeen et al. (2012) 提出个人计算机、网络基础设施设备、服务器和工业设备作为 **目标** 的类型。Barn and Barn (2016) 提出 `TargetIndividual`、`TargetTechnology`、`State` 和 `Organization` 作为 **目标** 类型。我们提出 `TargetType`（目标类型），用于标识网络 `Attack_Event` 中涉及的 **目标** 类型，包括：`TargetInfrastructure`（基础设施目标）、`TargetPersonalDevice`（个人设备目标）、`TargetNetworkDevice`（网络设备目标）、`TargetOrganization`（组织目标）、`TargetIndividual`（个人目标）、`TargetGovernment`（政府目标）、`TargetGroup`（团体目标）、`TargetSoftware`（软件目标）和 `TargetSite`（站点目标）。值得注意的是，一个 `Attack_Event` 可能涉及一个或多个目标，这些目标可以是上述 `TargetType` 中的任意一种或组合。

### 影响

**影响** 可定义为网络 `Attack_Event` 对 **受害者** 造成的直接效果。先前的研究将 **影响** 分类为运营影响和信息影响（Applegate & Stavrou, 2013；Simmons et al., 2009），以及经济、心理和地缘政治影响（Barn & Barn, 2016）。由于经济影响与运营影响有重叠，在本研究中，我们提出 `Operational`（运营）、`Informational`（信息）、`Psychological`（心理）和 `Geopolitical`（地缘政治）作为 **影响** 的类型。

### 攻击者

**攻击者** 可定义为为实现 `Objective`（目的）而尝试或实施网络 `Attack_Event` 的实体。我们采纳并扩展了 Donalds and Osei-Bryson (2014) 提出的 **攻击者** `Classification`（分类）值。

**攻击者** 可以是一个团体。Choo (2008) 提出了三类利用 ICT 进步来侵犯法律和监管控制的犯罪团体：(1) 传统有组织犯罪团体，其主要动机是获利或增加财富；(2) 纯在线运作的有组织网络犯罪团体；(3) 由意识形态和政治动机驱动的个人组成的有组织团体。van Herdeen et al. (2012) 提出有组织犯罪团体、抗议团体和网络军队。Barn and Barn (2016) 提出 `StateAgent`（国家代理人）和 `OrganizationAgent`（组织代理人）作为团体攻击者的类型（在该研究中称为代理人）。我们提出四种 `GroupAttacker`（团体攻击者）类型：`OrganizedCriminalGroup`（有组织犯罪团体）——包括为获取经济或其他物质利益而实施网络 `Attack_Event` 的传统和纯在线有组织犯罪团体；`StateGroup`（国家团体）——指为情报收集、窃取知识产权和/或身份、经济利益或政治动机而实施网络 `Attack_Event` 的民族国家或其代理人；`SexualGratificationGroup`（性满足团体）——指为性快感而实施网络 `Attack_Event` 的团体；`IdeoliticalGroup`（意识形态/政治团体）——指出于意识形态、政治、伦理或道德原因而实施网络 `Attack_Event` 的团体。

**攻击者** 可以是 **侵略者**。根据 van Herdeen et al. (2012)，**侵略者** 描述的是与 **攻击者** 的关联关系，而非 **攻击者** 的类型，指可能被雇佣或授权实施网络 `Attack_Event` 的实体。在本研究中，**侵略者** 可以是 `StateAggressor`（国家侵略者）、`CommercialAggressor`（商业侵略者）、`IndividualAggressor`（个人侵略者）、`SelfInstigator`（自发者）或 `UnknownAggressor`（未知侵略者）。值得注意的是，当 **攻击者** 和 **侵略者** 为同一实体时，适用 `SelfInstigator`。

## 12.5.2 网络犯罪分类模型的结构性比较

在本小节中，我们在先前研究的背景下探讨我们的网络犯罪分类模型的创新性。我们首先考察各模型所涵盖概念的异同。在表 12.1 中，我们使用勾选标记展示了给定研究所涉及的概念；每个主要概念以粗体显示，其子类型紧随其后并以斜体字体显示。应当注意，尽管在某些情况下先前研究可能对我们模型中的等效概念使用了不同名称，但我们认为该概念也包含在该先前研究的模型中。未涉及的概念保持未勾选/空白状态。

### 表 12.1 本研究及先前作品涵盖的网络犯罪分类概念

| **概念** | **本研究** | **Hansman and Hunt (2005)** | **Kjaerland (2005)** | **Simmons et al. (2009)** | **van Herdeen et al. (2012)** | **Applegate and Stavrou (2013)** | **Donalds and Osei-Bryson (2014)** | **Barn and Barn (2016)** |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Attack_Event** | ✓ | | | ✓ | | ✓ | | ✓ |
| **Vulnerability** | ✓ | ✓ | | | ✓ | ✓ | | |
| *:Categorization* | ✓ | | | | | | | |
| **Tool_and_Technique** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| *:Categorization* | ✓ | | | | | | ✓ | |

## 12.6 存在论表示、分类、比较与评估

### 12.6.1 基于 Protégé OWL 的网络犯罪分类存在论表示

在本节中，我们将概念模型（图 12.1）转化为我们的 CCO，并使用 Protégé OWL（[`protege.stanford.edu/`](http://protege.stanford.edu)）实现。概念模型可直接转化为 OWL 类，如图 12.2 所示。用于将类实例链接在一起的对象属性也一并展示。我们的 CCO 工件是对用于对网络犯罪进行分类的特征及其相互关系的显式形式化规范。

![图 12.2 我们的存在论工件的类层级与对象属性层级](img/fig12_2_B.jpg)

图 12.2 我们的存在论工件的类层级与对象属性层级

### 12.6.2 对两起真实网络攻击事件进行分类与存储

在以下小节中，我们通过使用基于 Protégé OWL 的 CCO 来存储和分类两起真实网络犯罪：`EmailHacked_NudePhotosUploaded` 和 `LulzSecAssoicateIndicted`，以展示我们工件的实用性。本节还将比较先前确定的分类方案与本研究提出的分类方案对这些网络犯罪的分类方式。

#### 12.6.2.1 攻击事件 1 —— EmailHacked_NudePhotosUploaded —— 的详情及其在 Protégé OWL 中的分类

`Attack_Event` 1 `EmailHacked_NudePhotosUploaded` 的摘要见图 12.3。使用我们的 Protégé OWL CCO，我们从两个视角展示该 `Attack_Event`：一个以 `Attack_Event` 为中心实例的视图（图 12.4），另一个从所谓 `Attacker` 的视角出发（图 12.5）。每个视图展示了 `Attack_Event` 的不同特征，并阐释了 `Attack_Event` 与 CCO 中其他特征之间的关系。此外，图 12.5 还展示了一些推断出的关系（右下角以黄色高亮显示）。

![图 12.3 攻击事件 1 摘要：EmailHacked_NudePhotosUploaded](img/fig12_3_B.jpg)

图 12.3 攻击事件 1 摘要：EmailHacked_NudePhotosUploaded

![图 12.4 EmailHacked_NudePhotosUploaded 的“Attack_Event”视角](img/fig12_4_B.jpg)

图 12.4 EmailHacked_NudePhotosUploaded 的“Attack_Event”视角

![图 12.5 EmailHacked_NudePhotosUploaded 的“Attacker”视角](img/fig12_5_B.jpg)

图 12.5 EmailHacked_NudePhotosUploaded 的“Attacker”视角

#### 12.6.2.2 攻击事件 1 —— EmailHacked_NudePhotosUploaded —— 的分类方案比较

利用 `EmailHacked_NudePhotosUploaded` 的详细信息，我们展示了我们的 CCO 与上文讨论的先前提出的分类方案在对 `Attack_Event` 进行分类方面的对比。针对计算机/网络攻击提出的分类方案被省略，因为它们无法对个人实施的 `Attack_Events` 进行分类。表 12.2 展示了对 `EmailHacked_NudePhotosUploaded` 进行分类的结果。

### 表 12.2 使用先前提出的分类方案及我们提出的 CCO 对 EmailHacked_NudePhotosUploaded 进行分类

#### KJAERLAND

| **名称** | **来源部门** | **作案手法** | **影响** | **目标部门** |
| :--- | :--- | :--- | :--- | :--- |
| `EmailHacked_NudePhotosUploaded` | | | 社会工程学 | 破坏 泄露 | |

#### SIMMONS ET AL

| **名称** | **攻击向量** | **操作影响** | **防御** | **信息影响** | **目标** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `EmailHacked_NudePhotosUploaded` | 社会工程学 | | | 破坏泄露 | 邮件服务器 |

#### APPLEGATE & STAVROU

| **名称** | **向量** | **信息影响** | **操作影响** | **系统影响** | **防御** | **行为体** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `EmailHacked_NudePhotosUploaded` | 社会工程学 | 拒绝 泄露 | | | | Ronald Oates Denyque Bianca Bartley |

#### DONALDS & OSEI-BRYSON

| **名称** | **受害者** | **攻击者** | **攻击者：类别** | **目的** | **工具与战术** | **影响** | **结果** | **关系** | **目标** | **罪行** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `EmailHacked_NudePhotos Uploaded` | Denyque Bianca Bartley | Ronald Oates | Black Hat Hacker_Professional_Elite | Financial Gain | Social Engineering | Loss of access | Negative Publicity Shame Reputational Damage | External | Denyque Bianca Bartley | Unauthorized Obstruction Unauthorized Access Unlawfully making available data for the commission of an offence |

#### BARN & BARN

| |
| :--- |
