

# 区块链网络类型与药品追踪概述

## 区块链网络的三大类型

主要有三种区块链网络：**公有链**、**私有链**和**联盟链**。

**公有链**对所有人开放，任何人都可以作为用户、矿工、开发者或社区成员加入。它面向大众终端用户，无限制且无需许可，任何拥有互联网接入的人都可以加入公有链网络并成为其节点。公有链的例子包括 **Bitcoin (BTC)** 和 **Ethereum (ETH)** [[17](#C_019_c14.xhtml#r14_17)]。

**私有链**在单一实体控制的受限环境中运行。只有拥有加入网络权限的节点才能加入私有链网络；因此，它也被称为**许可链**。**Hyperledger** 和 **Ripple (XRP)** 是私有链广为人知的例子。

**联盟链**兼具公有链和私有链的特性。来自多个组织的成员在联盟链网络上协作 [[18](#C_019_c14.xhtml#r14_18)]。现有节点控制联盟链中的共识机制。三种区块链的区别如 [表 14.1](#C_019_c14.xhtml#t14_1) 所示。

### 表 14.1 区块链类别的差异

| Property | Public [[17](#C_019_c14.xhtml#r14_17)] | Private [[18](#C_019_c14.xhtml#r14_18)] | Consortium [[18](#C_019_c14.xhtml#r14_18)] |
| :--- | :--- | :--- | :--- |
| Type of governance | Public | Single owner | Set of owners |
| Example | Ripple, Bitcoin, Ethereum | Hyperledger, Quorum | Multi-chain |
| Consensus algorithm | PoW, PoS, etc. | PoA, PBFT, etc. | Tendermint, etc. |
| Infrastructure | Highly decentralized | Distributed | Decentralized |
| Transaction reading | Any node | Any node/list of predefined node | Any node/list of predefined node |
| Immutability of data | Yes | Yes | Yes |
| Network scalability | High | Low to medium | Low to medium |
| Throughput of transaction | Low | High | High |

区块链技术的选择取决于手头的工作类型。例如，小企业的会计管理由其他机构管理，该场景的另一种选择是创建一个私有链网络，在该网络中，名为分布式账本的分布式区块集合是真实信息的唯一来源。而在供应链系统的另一场景中，客户希望追溯产品的一切信息，则适用联盟网络的方法。因此，参与者能够读取产品数据，但要确保只有真实的参与者（如供应商、制造商和原材料供应商）才能写入数据 [[19](#C_019_c14.xhtml#r14_19)]。

## 14.3 医疗领域药品追踪概述

本节重点关注药品供应链（PSC）中与药品可追溯性相关的问题。PSC 遵循从收集原材料到向最终用户（患者）供应成品的端到端供应流程。供应链的主要目标是在正确的时间提供正确且优质的药品，因为人们的生命安全至关重要。当前的 PSC 存在许多漏洞，且缺乏可追溯性和透明度。由于利益相关者的非一致性，不存在清晰的所有权，这也使得交易验证更加困难。缺乏对整个系统的单一视图，导致需要中央权威来管理整个系统 [[20](#C_019_c14.xhtml#r14_20)]。

PSC 包含存储、包装、拆包、重新包装等多个流程，以及供应商、制造商、经销商、销售人员、药店和患者等多个利益相关者，这使得药品追踪变得困难。许多因素导致供应链系统中出现篡改药品；例如，未经行政机关许可从其他国家购买劣质药品、不良的制造和储存习惯、盗窃和不合格药品的泄露 [[21](#C_019_c14.xhtml#r14_21)]。为了提高供应链的可追溯性和透明度，已应用了大量补救措施，如序列化、条形码、射频识别（RFID）等，但它们在隐私、安全性和透明度方面都存在一些局限性。

区块链在供应链、运输、物流和交通控制系统中得到广泛应用，因为它为互不信任的利益相关者之间存储交易数据提供了一个不可篡改、安全、可验证且透明的环境 [[22](#C_019_c14.xhtml#r14_22)]。区块链的主要特性是利用哈希函数将包含交易数据的区块与前一个区块连接起来。这确保了数据的不可变性并便于追溯。区块链技术提供了一种结构化且经济的解决方案，可用于多种药品追踪功能和方法，以确保正确的查找、追踪和培训。区块链技术的优势可与现有的防伪解决方案（如 RFID、近场通信 NFC、质量风险与合规 QRC 和电子溯源）相结合，提供互操作且改进的集成解决方案 [[23](#C_019_c14.xhtml#r14_23)]。[图 14.1](#C_019_c14.xhtml#f14_1) 展示了药品供应链系统中所有中间利益相关者之间的关系。

![图 14.1 药品供应链利益相关者之间的关系](images/Fig14_01.jpg)

**图 14.1** 药品供应链利益相关者之间的关系。

区块链技术允许授权的私有网络追踪 PSC 中的事件，并提供每笔交易的时间密封历史记录。事件样本包括执行者、所有者、交易时间、地点及相关利益相关者 [[24](#C_019_c14.xhtml#r14_24)]。这保持了药品的可靠性、完整性、有效性、透明度和安全性。该方法减少了药品供应链系统中的障碍，实现了互不信任的利益相关者之间的协作，并创建了一个安全且防篡改的分布式药品追踪系统 [[25](#C_019_c14.xhtml#r14_25)]。这些优势通过共享知识交换，为跨越多个国家和药品监管机构提供了标准化和指导性监管，以获得由食品药品监督管理局（FDA）和欧洲药品管理局（EMA）等众多监管机构支持的切实可行的解决方案。在下一部分中，将对 PSC 中产品追踪的三种区块链架构进行比较和解释。制药行业对基于区块链技术解释的广泛接受，明显建立在涉及主要利益相关者的一些当前项目基础之上，如 [表 14.2](#C_019_c14.xhtml#t14_2) 所示。

### 表 14.2 基于区块链的药品可追溯性及初始参与者

| Products and Initials Participants [[26](#C_019_c14.xhtml#r14_26)] | Solutions Types Based on Blockchain [[26](#C_019_c14.xhtml#r14_26)] | Platform [[26](#C_019_c14.xhtml#r14_26)] |
| :--- | :--- | :--- |
| SAP multi-chain Merck, Ameri-source, Bergen, GSK, Amgen, Boehringer Ingellheim, McKesson, Novo Nordisk | Authentication of copies along with tracing of profitable revenues | Multi-chain |
| IBM, KPMG, Merck, Walmart ID Logiq | Proper tracking and authentication of intelligent medication management on a regular basis | Hyperledger private platform |
| Indiana university health, Wakemed health, and hospitals | Tracking of special medicine inside as well as outside of providers or networks | Private platform |

