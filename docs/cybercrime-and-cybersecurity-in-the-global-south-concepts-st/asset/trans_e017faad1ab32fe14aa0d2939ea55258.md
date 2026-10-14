

本研究采用设计科学（DS）研究范式来开发我们的形式化网络犯罪分类本体（CCO）。DS 被描述为一种解决问题的范式，用于创建和评估旨在解决组织问题的创新 IT 制品（[Hevner et al., 2004](#ch12.xhtml#ref12_33)；[Simon, 1996](#ch12.xhtml#ref12_63)）。此外，DS 被认为是信息系统（IS）研究与实践之间的纽带（[Peffers et al., 2007](#ch12.xhtml#ref12_54)）。根据 [Gregor and Hevner (2013, p. 337)](#ch12.xhtml#ref12_28)，“在 IS 领域，DS 研究涉及构建广泛的社会技术制品，如决策支持系统、建模工具、治理策略、IS 评估方法和 IS 变革干预措施”。我们认为，这种方法特别适合解决我们的研究目标，因为它允许我们产出一个创新的 IS 制品来解决一个现实世界的问题，即网络犯罪分类。在本研究中，我们的 IS 制品便是我们基于知识的形式化 CCO，以 `Protégé OWL` 表达。

在构建我们的 CCO IS 制品时，我们遵循了 [Peffers et al. (2007)](#ch12.xhtml#ref12_54) 提出的 DSRM 中概述的步骤。根据 [Peffers et al. (2007)](#ch12.xhtml#ref12_54)，DSRM 强调设计和构建可应用的制品，这些制品有可能促进组织中 IS 的效用。我们选择 DSRM 有几个原因：（1）它适应构建实用的制品，因为其重点在于制品开发（[Peffers et al., 2018](#ch12.xhtml#ref12_53)）；（2）它不要求制品评估涉及嵌入在设计工作中的正式过程（[Peffers et al., 2018](#ch12.xhtml#ref12_53)）；（3）它建立在以往专注于 DS 研究指南的工作优势之上；以及（4）我们同意其他研究者的观点，即它提供了一个有用的综合通用模型（[Gregor & Hevner, 2013](#ch12.xhtml#ref12_28)）。下文将讨论 DSRM 方法论中的步骤及其在本研究中的应用。

### 问题识别与动机

此步骤涉及定义具体的研究问题并论证解决方案的价值。我们已在前文中定义了我们的问题，确立了其相关性和重要性，并论证了 CCO 制品的价值。

### 定义解决方案目标

解决方案的目标应从问题定义中推断得出。如前所述，我们的解决方案目标是通过设计来解决上述确定的当前研究空白：（1）供研究人员和网络犯罪调查人员使用的网络犯罪分类的显性综合概念化；（2）一个全面整体的、多视角的网络犯罪分类与分析模型，涉及一组简约的相关概念和直接关系；（3）一个能更好地对当前和未来网络犯罪攻击进行分类的灵活制品；（4）一个形式化的网络犯罪分类本体，可允许网络犯罪主体（人工或人类）共享知识；以及（5）一个可扩展的制品，能轻松容纳新概念和潜在的新关系。

### 设计与开发

创建制品，制品可以是构造、模型、方法、实例化，或技术、社会和/或信息资源的新属性。我们的网络犯罪分类本体概念模型以及我们基于知识的 CCO 制品（以 `Protégé OWL` 实现）将在后续章节中讨论。

### 演示

演示展示制品在一个实例中是否按预期工作（[Peffers et al., 2018](#ch12.xhtml#ref12_53)）。在后续章节中，我们通过使用 CCO 对发生在多个司法管辖区的两个真实网络犯罪案例进行分类来演示我们的 CCO。

### 评估

观察并衡量制品支持问题解决方案的程度。此活动涉及将解决方案目标与演示中使用制品所得的实际观察结果进行比较；我们的结果呈现在 [表 12.4](#ch12.xhtml#table12_4) 中。

### 沟通

向研究人员和其他相关受众（如实务专业人士）传达问题及其重要性、制品、其效用与新颖性、其设计的严谨性及其有效性。本章试图通过呈现研究问题及其重要性、制品的设计、效用和有效性来实现这一点。

## 12.5 概念模型与分类概念

### 12.5.1 我们的概念模型

借鉴先前的工作，我们在 [图 12.1](#ch12.xhtml#fig12_1) 中展示了我们提出的 CCO 概念模型。该模型确定了网络犯罪分类的主要特征及其相互关系。概念模型特征将在下文讨论。请注意，由于 CCO 设计为可扩展的，未来可根据需要添加额外的特征和关系。下文还有一个表格，展示了本章和先前工作中涵盖的分类概念。

![Figure 12.1 Our proposed CCO conceptual model](images/fig12_1_B.jpg)

[图 12.1 我们提出的 CCO 概念模型](#ch12.xhtml#R_fig12_1)

**Attack_Event（攻击事件）**。`Attack_Event` 是由 `Attacker` 实施的实际现实世界中的网络犯罪或恶意网络行为。`Attack_Event` 的示例包括：`EmailHacked_NudePhotosUploaded` 和 `LulzSecAssoicateIndicted`。其他相关元数据（如 `Attack_Event` 的开始和结束日期）将在已知的情况下被记录。这些元数据可帮助警务从业者识别随时间变化的网络趋势/模式。

**Vulnerability（漏洞）**。`Vulnerability` 是系统中被 `Attacker` 在网络 `Attack_Event` 中利用的缺陷或弱点。因此，`Vulnerability` 仅适用于针对 ICT（信息与通信技术）实施的网络 `Attack_Event`。[Howard (1997)](#ch12.xhtml#ref12_35) 建议了三种类型的漏洞：`ImplementationVulnerability`、`DesignVulnerability` 和 `ConfigurationVulnerability`。[Simmonds et al. (2004)](#ch12.xhtml#ref12_61) 建议了安全策略漏洞和技术漏洞。虽然技术漏洞通常是技术中的“弱点”，但安全策略漏洞是安全策略的弱点，如规划和控制不善。在本研究中，我们将漏洞分类为 `ImplementationVulnerability`、`DesignVulnerability`、`ConfigurationVulnerability` 和 `SecurityPolicyVulnerability`。

**Tool_and_Technique（工具与技术）** 可被视为 `Attacker` 用于执行网络 `Attack_Event` 的“手段”（即工具和/或技术）。本研究采用了 [Donalds and Osei-Bryson (2014)](#ch12.xhtml#ref12_16) 提出的 `Tool_and_Technique` 类别（`Tool`、`SocialEngineering`、`IllicitCollusion` 和 `AttackVector`）。

**Objective（目的）**。`Objective` 可被视为 `Attacker` 实施网络 `Attack_Event` 的主要目的、动机或最终目标。我们主要采用了 [Donalds & Osei-Bryson (2014)](#ch12.xhtml#ref12_16) 对攻击者目的的分类，并根据贸易媒体中网络犯罪案例的实证数据增加了新的类别。例如，我们加入了 `SelfPreservation` 和 `Moral`，以便对这些类型的 `Objective` 进行分类。

**Offence（罪行）**。`Offence` 可被描述为由 `Attacker` 实施的、依法可予惩处的非法网络行为或 `Attack_Event`。一个例子是“未经授权访问计算机程序或数据”（牙买加《网络犯罪法》，2015 年 – [Jamaica Houses of Parliament, 2015](#ch12.xhtml#ref12_38)）。

