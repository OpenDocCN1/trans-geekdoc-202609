
# 数据、区块链、物联网与网络防护高级网络安全技术

> 本书深情献给我的父亲 Shri Shyam Kishor Chaubey，他是我们的灯塔；以及我的母亲、已故的 Mrs. Subhraji Chaubey，她激励我有目的、有意义地生活，始终专注于回馈社会。他们的爱、勇气、奉献一直是我奋斗的力量源泉。
>
> **Nirbhay S. Chaubey**
>
> 甘帕特大学，印度古吉拉特邦
>
> 本书献给我的父母，Neelam Chaubey 和 Nirbhay Chaubey，你们都是我的榜样，教导我践行真理与诚实，激励我成为一个有价值观的好人。我的妹妹 Medha Chaubey 和弟弟 Om Chaubey，感谢你们持续不断的支持。感谢我的外祖父 Shri Hiramani Shukla 和外祖母 Smt. Shubhadra Shukla，以及家人、老师和朋友们，你们总是鼓励我所做的一切。
>
> **Neha N. Chaubey**
>
> 伦敦帝国理工学院，英国

## 编辑顾问委员会

Kalpdrum Passi，加拿大劳伦森大学  
Om Prakash Vyas，印度阿拉哈巴德 IIIT  
Savita R. Gandhi，印度 GLS 大学  
Jyoti Pareek，印度古吉拉特邦古吉拉特大学  
Noor Zaman Jhanjhi，马来西亚泰莱大学  
Gua Xiangfa，新加坡国立大学  
Rajkumar Buyya，澳大利亚墨尔本大学  
Sabu M. Thampi，印度喀拉拉数字科学、创新与技术大学  
Maniklal Das，印度 DA-IICT  
Jigisha Patel，加拿大谢里丹学院  
Payal Mahida，澳大利亚维多利亚理工学院  
Mohit Tahiliani，印度卡纳塔克邦国家理工学院  
H.S. Mazumdar，印度 Dharmsinh Desai 大学  
Debabrata Singh，印度 Siksha O Anusandhan 大学  
Deepak Garg，印度 SR 大学  
Sandeep Kautish，印度昌迪加尔大学  
Sarang C. Dhongdi，印度 BITS Pilani  
Amrita Chaturvedi，印度 IIT(BHU)  
Lal Bihari Barik，沙特阿拉伯阿卜杜勒阿齐兹国王大学  
Satyen Parikh，印度甘帕特大学  
Kiran Amin，印度甘帕特大学  
Priyanka Sharma，印度古吉拉特邦国家国防大学  
Digvijaysinh Rathod，印度国家法医科学大学  
Apurv Shah，印度瓦多拉拉 M.S. 大学  
Deepak H Sharma，印度孟买大学  
Parameshachari B. D.，印度 Visvesvaraya 技术大学  
Rakhee，牙买加西印度大学  
Seema Mahajan，印度 Indus 大学  
Anand Kumar，印度 Visvesvaraya 技术大学  
Madhuri Bhavsar，印度 Nirma 大学  
Sanjay Garg，印度 Jaypee 工程技术大学  
Jagdish Rathod，印度 BVM 工程学院，古吉拉特技术大学  
Maulika Patel，印度 CVM 大学  
Balaji Rajendran，印度 CDAC  
Mayuri Mehta，印度 Sarvjanik 大学  
Aditya Sinha，印度 CDAC  
Harshal Arolkar，印度 GLS 大学  
Binod Kumar，印度 JSPM 大学  
Vrushank Shah，印度艾哈迈达巴德 Indus 大学  
Manish Patel，印度 Sakalchand 大学  
Vishal Jain，印度 Sharda 大学  
D.B. Choksi，印度 Sardar Patel 大学  
Jignesh Doshi，印度 L. J. 大学  
Padmapriya Praveenkumar，印度 SASTRA 大学  
Parvej Faruki，印度古吉拉特技术大学

## 前言

我非常荣幸能为这部重要的新书——《面向数据、区块链、物联网与网络防护的高级网络安全技术》撰写前言。本书由 Nirbhay Kumar Chaubey 教授（博士）和 Neha Chaubey 女士编辑。这部包含 16 章的综合性著作探讨了传统与量子密码学方法的交汇点，提供了关于网络安全最紧迫关切与网络防御机遇的专家视角，展示了保护复杂系统、区块链、物联网和网络基础设施的尖端技术。向编辑和作者们致以祝贺，感谢你们取得的这一卓越成就，它必将启迪寻求高级网络安全知识的研究人员、从业者和学生。本书是一项合作成果，汇聚了杰出作者、编辑、审稿人和顾问委员会成员的专业知识，他们以在计算机科学、网络安全、网络与通信工程领域的学术卓越而闻名。最终成果是一部权威的研究手册。

我强烈推荐本书作为学者、研究人员和大学生，以及寻求掌握高级网络安全技术复杂性的商务专业人士和行业专家不可或缺的资源。

**Akshai Aggarwal**  
古吉拉特技术大学 (GTU)，印度

## 序言

由物联网、区块链和网络物理系统驱动的数字化革命，已经改变了全球互动与商业模式。然而，这种日益增强的连通性也加剧了网络安全漏洞，亟需创新且具韧性的安全措施，以应对日益猖獗的网络威胁，包括数据泄露、`APT` 攻击（高级持续性威胁）和新兴的基于量子的攻击。

曾经作为安全通信支柱的经典密码学的局限性，正变得日益明显。随着量子计算的进步并超越当今系统的计算能力，传统加密方法面临过时的风险。计算机算力的不断增强和量子计算即将取得的突破所带来的漏洞，使得保护数字基础设施的方法必须发生范式转变。量子密码学的出现，为加强网络安全提供了一条令人振奋且充满希望的途径。其固有的、理论上不可破解的加密能力，使其成为依赖安全数据传输和保护的行业的游戏规则改变者。

## 致谢

编辑们想向所有参与该项目的人员表达谢意，特别是作者们。没有他们的贡献和支持，本书就不会问世。我们向每一位作者为其宝贵的投入表示衷心的感谢。我们还想感谢审稿人和编委会成员的重大贡献，他们的见解有助于提高章节的质量、连贯性和呈现效果。此外，我们非常感激那些承担了额外审稿人职责的作者们。

我们要向 GLS 大学计算机科学院院长 Savita Gandhi 博士（印度艾哈迈达巴德）表达最诚挚的感谢，感谢她在撰写本书过程中给予的鼓励和支持。她持续的协助和卓越的指导是我们塑造这部作品的最大动力。我们也深深感激 Gujarat Technological University（GTU）前校长 Akshai Aggarwal 博士（印度艾哈迈达巴德）在本书项目执行过程中提供的宝贵见解和指导。此外，我们要感谢家人们的支持和耐心，他们在整个书籍项目过程中发挥了关键作用。

编辑们要向出版商 IGI Global 表达最衷心的感谢，他们在整个出版过程中持续给予我们支持和指导。

# 第 1 章：网络安全本体的综合综述

Vatsal Hasmukhbhai Shah  
BVM Engineering College, India

Rahil Maniar  
![Orcid Imagehttps://orcid.org/0009-0000-7321-9415](https://orcid.org/0009-0000-7321-9415)  
BVM Engineering College, India

## 摘要

随着语义网架构的演进和生成式 AI 的进步，网络安全领域对通用接受的本体的需求显著增加。本文综述了五个著名的本体框架：`STIX`、`STUCCO`、`UCO`、`CTIM`和`WAVED`。它评估了它们的优势和局限性，提供了比较分析。该研究为开发最优本体提供了建议，旨在增强网络安全系统的互操作性、安全性和自动化，从而解决当前的差距，促进更统一的网络安全格局。

### 1.1 简介

网络安全领域长期以来一直在为开发统一本体而争论不休。已经提出了几种本体作为该问题的通用解决方案，但迄今为止，尚无任何一种达成集体共识，被公认为通用的、权威的本体。通用本体的接受将使网络安全从业者受益，并将显著降低未来系统对各种恶意威胁的脆弱性。

为了说明，下面列出了一些著名的网络安全本体：

*   `STIX` (Structured Threat Information Expression)
*   `CybOX` (Cyber Observable eXpression)
*   `MAEC` (Malware Attribute Enumeration and Characterization)
*   `CAPEC` (Common Attack Pattern Enumeration and Classification)
*   `CWE` (Common Weakness Enumeration)
*   `ATT&CK` (Adversarial Tactics, Techniques, and Common Knowledge)
*   `OpenIOC` (Open Indicators of Compromise)
*   `VERIS` (Vocabulary for Event Recording and Incident Sharing)
*   `MISP` (Malware Information Sharing Platform & Threat Sharing)
*   `CIM` (Common Information Model)
*   `MITRE CAR` (Cyber Analytics Repository)
*   `MAR` (Malware Analysis Repository)

从所有这些来源收集信息，并在过滤、消除冗余、预处理和修正后将它们与现有系统集成，将阻碍打算有效利用它们的组织。此外，在可预见的未来，自动化系统的效率和使用预计将显著提高，并且随着生成式 AI 的当前趋势，完全自动化的基于 AI 的系统可能会进一步推动该领域的发展。在本文中，我们考察了提出其本体的五种独特方法，并提供了关于它们大致效用以及它们在当前场景中表现如何的各种见解。本文的结构如下。第 2 节将简要描述我们采用的方法论，而第 3 节包含每个小节中相关本体的考察。每个小节包含两个进一步的小节，分别代表它们的优点和缺点。第 4 节包含结论和未来工作展望。本文着重于为开发通用本体方法所做的工作及其详尽总结，以帮助在该领域工作的研究人员。结论和未来工作部分提供了关于此的进一步见解。

### 1.2 方法论

对发表原始本体的每篇论文进行了彻底分析。提供了每个本体框架的简要描述，以及直接来自源头的本体架构图，以增强可读性。检查了源论文和现有综述论文以提取优点和缺点，主要是分别助益和阻碍本体的因素。一个简洁的汇总表包含在审查最后一个本体的章节中，列出了每个本体的优点和缺点。

### 1.3 本体考察

#### 1.3.1 漏洞管理本体 (OVM)

我们要研究的第一个本体是漏洞管理本体（OVM），由 Wang & Guo (2009) 发布。

它包含 NVD（国家漏洞数据库）中的所有现有漏洞（Booth et al., 2013）。诸如漏洞推理、漏洞表征及其影响分析等问题主要由它处理。它是遵循 DL 知识工程方法论构建的。遵循了 Fenz et al. (2008) 提出的设计标准，即本体清晰性、连贯性、可扩展性、最小编码偏见和最小本体论承诺。它建立在 `CVE`（通用漏洞披露）及其相关协议和标准的基础之上，如 `CWE`（通用弱点枚举）、`CPE`（通用平台枚举）和 `CAPEC`（通用攻击模式枚举与分类）。基本的漏洞表征表达被表示为 OVM 架构的高层概念。它包含十二个顶层概念：`Vulnerability`（漏洞）、`Introduction Phase`（引入阶段）、`Active Location`（活动位置）、`IT Product`（IT 产品）、`IT Vendor`（IT 厂商）、`Product Category`（产品类别）、`Attack`（攻击）、`Attack Intent`（攻击意图）、`Attack Method`（攻击方法）、`Attacker`（攻击者）、`Consequence`（后果）和 `Countermeasure`（对策）。这些概念中的每一个都包含一个子系统层级，包含不同的子类和关键概念。OVM 还提供了实用工具和一个集中式存储库，可用于系统安全领域所有参与者之间的共享与通信。

**图 1. 漏洞本体的概念模型**

![979-8-3693-9225-6.ch001.f01](img/979-8-3693-9225-6.ch001.f01.png)

(Wang & Guo, 2009)

它支持有限的自动化和查询。它是发布在漏洞领域的最早本体之一，并在信息安全自动化计划（ISAP）下发布。总体而言，它可被归类为领域特定本体。

##### 1.3.1.1 OVM 的优点

*   高互操作性和各方间更好的交换
*   结构良好的架构
*   易于融入现有概念
*   增强的自动化

##### 1.3.1.2 OVM 的缺点

*   有限的推理和查询
*   难以融入不存在的概念
*   通用目的的适用范围有限
*   复杂性较高 (Wang & Cui, 2019)

#### 1.3.2 结构化威胁信息表达（STIX）

第二个被分析的本体方法是 STIX 标准。虽然根据教科书定义它不是一个本体，但 STIX 尽管类似于一种语言或标准，却遵循系统化方法并以结构化方式表示数据。因此，在本文的范围内，它被视为一个本体。必须注意的是，整篇论文中提到 STIX 时，均指 Barnum (2012) 论文中发布的本体以及 MITRE 公司旗下的本体。STIX 的突出之处在于，它更侧重于一种社区驱动的方法，而非建立一个必须融入新信息的僵化结构。它更侧重于灵活性、表达性、可扩展性、自动化能力和可读性。它为网络威胁信息提供了通用机制和统一架构。它包含一组核心的必需指导原则，即表达性、可集成性、灵活性、可扩展性、自动化能力、可读性和架构。STIX 结构由可观测对象、指标、事件、战术技术与程序（TTP）、活动、威胁行为者、利用目标和行动方案（COA）组成。由于其灵活的方法，它拥有比其他本体更多的用例，以及更长的生命周期。它最常与可信自动化情报信息交换（TAXII）一起使用。尽管两者完全独立，但协同工作时能产生最佳效果。

**图 2. 结构化威胁信息表达（STIX）架构 v0.3**

![979-8-3693-9225-6.ch001.f02](img/979-8-3693-9225-6.ch001.f02.png)

(Barnum, 2012)

**图 3. STIX 关键构造与关键相互关系**

![979-8-3693-9225-6.ch001.f03](img/979-8-3693-9225-6.ch001.f03.png)

(STIX 项目 [`stixproject.github.io/about/`](https://stixproject.github.io/about/))

##### 1.3.2.1 STIX 的优点

*   灵活性和可扩展性
*   自动化能力
*   部分实现
*   多样化的用例

##### 1.3.2.2 STIX 的缺点

*   复杂性和计算开销
*   互操作性和集成问题
*   匿名性和隐私担忧

#### 1.3.3 安全工具箱：攻击与对策本体（STAC）

第三个被研究的本体是 STAC 本体，由 Gyrard et al. (2013) 在第 22 届国际万维网会议论文集中开发。旨在为非安全专家创建一个本体，帮助他们设计安全应用并了解多个领域的安全概念和风险，STAC 融合了 `Application`（应用）、`Requirement`（需求）、`Domain`（领域）、`Attack`（攻击）、`Countermeasures`（对策）、`Feature`（特性）、`SecurityProperty`（安全属性）和 OSI 模型的概念。这些概念之间的关系及其结构在 STAC 中定义明确。除了这些主要概念外，它还包含子概念、方法和属性。它采用 `OWL`（Web 本体语言）框架表示。其 UI 利用以下技术：`Java`、`REST Web Services` (Jersey)、`Google Application Engine` (GAE)、`Jena framework`、`SPARSQL` 语言、`HTML5`、`CSS3`、`Javascript` 和 `AJAX`。STAC 支持的用例包括：针对攻击和对策的领域特定查询、额外信息检索（如对策的优缺点及满足的安全属性）、针对特定 OSI 模型层的攻击和对策搜索。

**图 4. STAC 本体的顶层部分**

![979-8-3693-9225-6.ch001.f04](img/979-8-3693-9225-6.ch001.f04.png)

(Gyrard et al., 2013)

它融合了来自各种来源的信息。STAC 的构建方式使得第三方难以修改，这使其略显不适合即时添加关于新型网络安全概念、攻击和对策的信息。它的特定目的是帮助新手软件开发人员以更稳健可靠的方式开发安全软件。

##### 1.3.3.1 STAC 的优点

*   域外高度互操作
*   开源框架利用
*   支持领域特定检索

##### 1.3.3.2 STAC 的缺点

*   临时更新过程困难
*   特定范围
*   领域密集型任务的用例有限
*   实现复杂 (Gong & Tian, 2020)

#### 1.3.4 通过关联上下文观测进行态势与威胁理解（STUCCO）本体
