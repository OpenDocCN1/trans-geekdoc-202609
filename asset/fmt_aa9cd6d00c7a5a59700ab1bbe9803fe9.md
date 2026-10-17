
²² [`github.com/cardano-foundation/CIPs/tree/master/CIP-1694`](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694)

²³ Taras Zharun, “Wyoming LLC as a DAO Legal Wrapper: What You Need to Know

²⁴ [`docs.intersectmbo.org/intersect-overview/intersects-structure`](https://docs.intersectmbo.org/intersect-overview/intersects-structure)

²⁵ [`docs.intersectmbo.org/intersect-overview/intersects-structure/intersect-governance/governing-board-meetings`](https://docs.intersectmbo.org/intersect-overview/intersects-structure/intersect-governance/governing-board-meetings)

²⁶ [`www.intersectmbo.org/join`](https://www.intersectmbo.org/join)

²⁷ [`roadmap.cardano.org/en/voltaire/`](https://roadmap.cardano.org/en/voltaire/)

²⁸ [`github.com/cardano-foundation/CIPs/tree/master/CIP-1694`](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694)

²⁹ [`sancho.network/`](https://sancho.network/)

³⁰ [`www.essentialcardano.io/infographic/cip-1694-in-a-nutshell`](https://www.essentialcardano.io/infographic/cip-1694-in-a-nutshell)

³¹ [`github.com/cardano-foundation/CIPs/tree/master/CIP-1694#the-constitutional-committee`](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#the-constitutional-committee)

³² [`github.com/cardano-foundation/CIPs/tree/master/CIP-1694#governance-actions`](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#governance-actions)

³³ [`pooltool.io/`](https://pooltool.io/)

³⁴ [`adastat.net/pools`](https://adastat.net/pools)

³⁵ [`cexplorer.io/pool`](https://cexplorer.io/pool)

³⁶ [`adapools.org/pool`](https://adapools.org/pool)

## 第 14 章：结束语

### 简介

本章将回顾 Cardano 的精神内核，以及它如何与同行评审流程和形式化方法相关联。我们将考察软件行业标准，以及这些标准为何在高保障软件方面显得力不从心。我们将了解半形式化方法是如何被用于构建 Cardano 的，以及像 `IACR` 这样的密码学协会是如何促进同行评审流程的。接下来，我们将结合现实案例，探讨利用 Cardano 实现社会公益的潜力。我们还将讨论监管与合规风险，以及需要注意的事项。随后，我们将回顾技术采纳的五个阶段，以及它们如何应用于区块链。最后，我们将探讨 Cardano 的发展历程及通往此处的道路。

### 结构

在本章中，我们将讨论以下主题：

*   Cardano 精神内核
*   软件行业标准
    *   区块链风险
    *   半形式化方法
    *   IACR
*   社会公益潜力
*   监管与合规风险
*   技术采用
*   Cardano 的发展历程

### Cardano 精神内核

开放与透明是 Cardano 的精神内核¹，也是为何如此重视同行评审和形式化方法的原因之一。国际密码学研究协会（`IACR`）²等组织的同行评审流程采用双盲机制，使作者和评审者彼此匿名³。这有助于消除偏见，并在评审过程中促进公平与透明。除了同行评审流程，`IOG`（`IOHK`）还应用形式化方法，严格运用数学技术确保软件按预期运行⁴。例如，用 Haskell 编写的 Cardano 账本代码可以追溯到已通过同行评审的形式化规范。这种可追溯性和透明度在区块链行业中是无与伦比的，通常仅见于航天、航空和金融行业的高保障软件中⁵。

从根本上说，区块链技术旨在赋予边缘（用户）自主权和自我控制权。赋能边缘（个人或员工）的益处在于提高生产力、增强参与度并改善社会成果⁶。然而，由于底层加密货币代币可自由交易，这必然会导致投机。这种投机常被滥用，区块链（及项目）伪装成无许可和去中心化，其主要目的却是榨取价值。自比特币早期 ICO 时代起，这便是一个问题⁷。因此，建议与专注于服务他人的区块链和项目保持一致，这最终将导致正确的价格发现、价值与市场契合度。

### 软件行业标准

质量、韧性和无缺陷通常与大多数软件无关，尤其是近期发布的软件。这种“行业标准”门槛很低，通常通过定期软件更新来逐步提高软件质量。这种方法不适用于区块链！区块链本质上是不可变的，一旦部署，*真正*去中心化和无许可的区块链无法被中央权威停止、重置或修补。此外，区块链可能涉及数百万美元的价值，这些价值可能因利用软件中发现的漏洞而被窃取。

### 区块链风险

让我们首先看看设计和部署区块链时可能出现的问题。以下是可能发生的问题列表⁸：

*   协议设计缺陷
*   设计实现错误
*   典型软件错误
*   业余密码学实现
*   错过性能期限
*   负载下崩溃
*   扩展失败
*   DoS 故障
*   易受经济攻击
*   社会或投票崩溃
*   宏观经济崩溃
*   以及更多……

### 半形式化方法

正如我们所见，在设计和构建无许可且去中心化的区块链时，存在许多陷阱。**IOG**（**IOHK**）通过将半形式化规范、Haskell 规范和 Haskell 实现代码关联起来，缓解了这些问题，如*图 14.1*所示。

![](img/Figure-14.1.jpg)

**图 14.1：** 证据链⁹

账本的半形式化规范定义了转换类型和转换规则，这使其具有形式化特性，但未经过机器检查。¹⁰ 通过创建 Haskell 规范，可以运行测试用例，将规范可执行文件的输出与实现可执行文件生成的输出进行比较。如果两个输出匹配，我们就可以合理地高度确信实现代码实现了半形式化规范。**IOG** 持续改进形式化验证流程，并最近发布了一篇题为“*Formal specification of the Cardano blockchain ledger, mechanized in Agda*（Cardano 区块链账本的形式化规范，在 Agda 中实现机械化）”的论文。¹¹ 目标是今后使用 Agda 创建形式化规范，进行中的版本位于 GitHub 上。¹²

### IACR

国际密码学研究协会（**IACR**）是一个非营利科学组织，致力于推进密码学及相关领域的发展。¹³ 它组织三场领先的会议，供该领域的学者发表和评审科学论文：

*   Crypto（密码学会议）
*   Eurocrypt（欧洲密码学会议）
*   Asiacrypt（亚洲密码学会议）

**IACR** 还举办四场额外的专业会议、一个研讨会，以及一系列密码学培训学校。¹⁴ 《密码学杂志》是 **IACR** 的旗舰期刊，为现代信息安全领域的原创成果发表提供了论坛。¹⁵

### 社会公益潜力

Cardano 为无银行账户者提供银行服务的使命，可追溯到 Charles Hoskinson 于 2014 年的 TED 演讲，那时 Cardano 甚至尚未诞生。¹⁶ Cardano 诞生于一个愿景：一个没有中介的世界，个人掌控自己的数据以及交易方式。¹⁷ 这引起了 Cardano 社区许多人的共鸣，也是为什么与 World Mobile 等公司存在巨大协同效应的原因，后者致力于连接未连接的人群。¹⁸ 立志成为世界的金融操作系统，¹⁹ Cardano 拥有巨大的社会公益潜力。

### World Mobile

全球有近 30 亿人未接入网络，其中 40% 的发展中国家人口无法接入移动网络。²⁰ World Mobile 正在为电信创建一个共享经济，这仅因区块链而成为可能。²¹ 用户可以购买 World Mobile 节点，并从网络交易费和代币质押中获得 World Mobile 代币 (WMT)，这激励了网络建设。该移动网络是一个 Cardano 侧链，使用去中心化标识符（**DID**s）进行配置和计费。²² World Mobile 已在坦桑尼亚和桑给巴尔等国家部署了网络。²³

### Empowa

由于借贷成本高昂（45%），非洲大多数人无法负担购房，这反过来又导致住房供应短缺。²⁴ Empowa 是一个去中心化的房地产开发和收藏品平台，为非洲服务不足的社区提供小额融资。²⁵ Empowa 已利用 Cardano 区块链为莫桑比克的经济适用房提供融资。²⁶

### 加密绿色研究

从 **ESG** 角度来看，Cardano 是得分最高的区块链之一。²⁷ 它的能源消耗和电子垃圾极低。在透明治理方面属于最佳级别，代币资产分布良好，准入门槛低。²⁸ 因此，Cardano 在以下区块链指标上得分优异。

*   **环境：** A-
*   **社会：** A-
*   **治理：** A+

### 社会公益项目

以下是利用 Cardano 造福社会的更多示例：

*   **IOG**（**IOHK**）向埃塞俄比亚学生发放数字身份，作为与埃塞俄比亚教育部合作的试点项目。²⁹
*   **WADA** 等社区团体专注于加纳和喀麦隆的区块链教育中心，并计划未来扩展到西非和中非的其他国家。³⁰
*   一个名为“气候中立 Cardano”的利益池运营商社区承诺使用 100% 可再生能源。³¹
*   联合国难民署 (UNHCR) 表彰 Cardano 基金会和瑞士，认可其将 80% 的质押奖励用于急需帮助的难民。³²
*   Sustainable Ada 维护着一个 Cardano 社会影响力项目的资源库。³³
*   AdaFilms 拥有一系列短纪录片，记录了使用 Cardano 区块链的真实、有影响力的用例。³⁴

### 监管与合规风险

美国的监管环境对位于那里的所有区块链公司来说都特别困难且充满挑战。这就是为什么大多数区块链公司或基金会将总部设在美国境外、对加密货币友好的司法管辖区（如瑞士）的原因。随着合法用例的实现和区块链优势的倡导，监管清晰度在过去几年中有所改善，并将继续改善。

合规风险，特别是 KYC（了解你的客户）和 AML（反洗钱）法规，并不总是与假名的、去中心化的、无许可的区块链兼容。Cardano 区块链是一个工具箱，拥有许多工具，可以满足各种功能性和非功能性需求，包括在需要时的 KYC 和 AML。因此，请始终了解用户的监管环境，并相应地定制解决方案。此外，请注意，某些司法管辖区可能有报告要求，或完全禁止持有加密货币资产。

### 技术采用

区块链似乎遵循着与手机、互联网和社交媒体等其他颠覆性创新相似的轨迹，如*图 14.2*所示。创新者最先进入这个领域，开创并推动技术的首次迭代。随后是早期采用者，他们看到了潜力并宣传其优势。接下来，预期早期大众将到来，这将开启大规模采用的新时代。

![](img/Figure-14.2.jpg)

**图 14.2：** 技术采用曲线

不幸的是，事情并非如此发展，而是出现了“鸿沟”。早期的兴趣和热情消退，许多人将该技术视为昙花一现的时尚而抛弃。但建设者们在这一阶段坚持建设，坚信这项新技术具有巨大潜力。在未来的某个时刻，会诞生出能够实现这项新技术独特价值主张的“杀手级”应用。它从根本上改变了社会对先前无法解决的问题的解决方案的看法。此时，早期大众到来，大规模采用发生。到了晚期大众阶段，该技术不再新颖，被接受为新常态。最后，将会有落后者，他们仍对该技术持怀疑态度，但别无选择，只能使用它以与世界其他地方保持联系。

### Cardano 的征程

对于参与构建和部署 Cardano 区块链的团队来说，通往今天的道路并不平坦。延迟、挫折、重置和战略调整造成了大量的摩擦和挫败感。对于新的、复杂的、高度集成的系统来说，这并不罕见。使该项目和其他加密货币项目比大多数项目更具挑战性的是，它是在公开环境下构建的，且许多人在结果上拥有直接的财务利益。然而，贯穿始终，**IOG** (**IOHK**)³⁵ 和 Charles Hoskinson³⁶ 在 YouTube 和博客文章上提供了定期更新。他们不断地驳斥悲观论者，回应批评者，并向社区保证进展正在取得。能够参与这段旅程，实时见证并参与其中，并展望未来，这真是令人惊叹。

### 结论

在本章中，我们回顾了 Cardano 的精神内核，以及为何如此强调同行评审流程和形式化方法。我们详细考察了软件行业标准，以及当前的质量缓解措施为何不适用于区块链。我们探讨了半形式化方法如何被用于将高可信软件关联回形式化规范。我们还考察了像 **IACR** 这样的密码学协会如何通过会议和出版物促进和推进密码学研究。接下来，我们结合现实案例，探讨了 Cardano 在社会公益方面的巨大潜力。我们讨论了创建基于区块链的应用程序时面临的监管和合规风险。我们还回顾了技术采用的五个阶段及其在区块链中的应用。最后，我们将通往今天的道路作为 Cardano 旅程的一部分进行了讨论。

### 要点回顾
