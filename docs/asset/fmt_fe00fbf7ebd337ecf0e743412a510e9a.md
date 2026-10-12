
| 攻击类型 | 缓解措施 |
| --- | --- |
| 整数/缓冲区溢出攻击 | • 开发人员应使用地址空间布局随机化（ASLR）和位置无关代码（PIE） [[10]](#ch21.xhtml#r456)。 |
| 时间戳攻击 | • 使用节点的系统时间代替网络时间，以确保区块的上限得以保持。<br>• 在时间戳的情况下，应仅使用受信任的对等节点 [[22]](#ch21.xhtml#r468)。 |
| 竞态条件攻击 | • 安全并发以及锁定资源有助于缓解此类攻击 [[19]](#ch21.xhtml#r465)。 |
| 缓冲区越界攻击 | • 缓解此类问题最简单的方法之一是使用不允许此类问题的语言开发代码。<br>• 需要使用安全的缓冲区处理函数来缓解缓冲区越界攻击的影响 [[35]](#ch21.xhtml#r481)。 |

### 固有安全措施

目前，`Hyperledger`、`以太坊`和 `Corda` 是一些最著名的区块链平台。`以太坊`和 `Hyperledger` 各自拥有特定的用例，但 `Corda R3` 主要应用于金融服务领域 [14]。鉴于它们的各种应用，本简要综述将尝试解释这三种区块链应用，它们也在本书的其他几个章节中进行了讨论。

#### 以太坊

仅次于比特币，`以太坊`是按市值计算的第二大加密货币。然而，与比特币不同，`以太坊`的设计初衷并非作为一种数字货币运作。相反，`以太坊`的创建者旨在创建一种新型的全球去中心化计算平台，将区块链的安全性和开放性扩展到广泛的应用中。在`以太坊`区块链上，从金融工具和游戏到复杂的数据库，一切已在运行。而只有开发者的想象力可能限制其未来的可能性。根据非营利组织`以太坊基金会`的说法，“`以太坊`可用于将几乎任何事物编码化、去中心化、保护和交换。”

`以太坊`区块链现在保护 `ETH` 的方式，正如比特币区块链保护比特币一样。每笔交易都由网络上所有机器提供的海量算力进行验证和保护，这使得任何第三方极难介入。加密货币的底层概念保障了其安全性；这些系统无需许可，且软件开源，允许大量计算机科学家和密码学家分析其网络安全的各个方面。

另一方面，运行在`以太坊`区块链上的应用程序，其安全性仅取决于其创建者如何保障。因此，任何拟使用的去中心化应用都应经过彻底测试。

2021 年，`以太坊`协议进行了更新，以使其更快、更安全。`以太坊 2.0`（也称为 `ETH2`）是对`以太坊`网络的重大升级。它旨在帮助`以太坊`网络扩展，同时提高安全性、性能和效率 [9]。`以太坊`也是首个智能合约平台，允许开发者使用图灵完备的区块链平台来创建智能合约 [26]。

##### 以太坊智能合约

`以太坊虚拟机`是执行`以太坊`智能合约的场所。合约使用 `Solidity` 编程语言编写（专为`以太坊`创建），每条`以太坊虚拟机`指令都有关联的燃气值。包含一定数量燃气（以太币的小数部分）的交易，用于支付运行代码执行智能合约所需的计算工作。

`以太坊虚拟机`目前缺乏并行化能力，这意味着区块中的所有交易都是按顺序处理的。如果`以太坊`增加分片功能，允许与分布式账本不同数据区域交互的交易并行运行，这种情况在未来可能会改变 [26]。

##### 以太坊安全措施

`以太坊`目前提供基本的内置隐私和安全功能。其主要内置功能是使用公钥进行身份管理，为用户提供一定程度的伪匿名性。

然而，高级安全功能（如机密交易）可以通过`以太坊`中的智能合约来实现。对零知识证明（如 `zkSNARKS`，零知识简洁非交互式知识论证）所用数学运算的支持，也计划在`以太坊`的未来发展中加入 [26]。

#### Hyperledger Fabric

`Hyperledger Fabric` 目前是最具前景的 `Hyperledger` 区块链。它提供了一个由 `IBM` 创建、由 `Linux 基金会` 管理的智能合约平台。`Hyperledger Fabric` 旨在作为一个面向企业的区块链平台。`Hyperledger` 区块链的特征如下。网络安全性为私有，基于许可，使用 `X.509` 证书进行身份管理，并提供可插拔的共识算法（目前提供交易排序，计划提供完整的 BFT 解决方案） [26]。

`Hyperledger Fabric` 允许不同的公司和网络参与者选择自己的证书颁发机构，因此可以采用多种加密技术进行签名、验证和身份认证。这是通过在排序服务或通道层面运行的 `MSP` 过程来实现的 [32]。

##### Hyperledger 智能合约

`Hyperledger` 区块链上的智能合约（也称为链码）可用 `Node.js` 或 `Go` 编写，并在 `Docker` 容器中执行。它们由与区块链交互的第三方程序控制。在交易验证和执行方面，`Hyperledger` 采取的方法与`以太坊`和其他智能合约平台略有不同。

其控制流程为执行、排序和验证。进一步解释：节点运行代码，验证其有效性，若合法则背书。交易通过共识协议排序成区块。验证阶段确保交易符合背书策略。每笔交易可以有一组必需的背书人，仅当条件满足时才会被处理。

`Hyperledger` 的控制流程提供了一些重要优势。首先，在执行阶段，交易可以并行验证，而非顺序验证。其次，验证和排序是两个独立的步骤，节点可根据需要专门负责其中之一。由于代码可由专业节点轻松评估和排序，且背书规则可根据企业需求制定，`Hyperledger` 智能合约旨在吸引企业用户 [26]。

##### Hyperledger 安全措施

`Hyperledger` 中有几个特性旨在增强其安全性。可插拔的身份管理支持传统方法，如 `LDAP` 和 `OpenID Connect`。从逻辑上讲，不同的区块链可根据工作职能需要，选择让节点属于多个通道。数据也可通过其 `gossip protocol`（流言协议）私密共享，该协议仅按需知原则向节点发送数据，并存储在独立的客户端数据库中（链下） [26]。

#### Corda

`Corda` 是一个兼容智能合约的平台，用于记录和处理金融协议，它使用分布式账本 [6]。`Corda` 与典型区块链不同之处在于，区块链网络中的任何一方都无法完全查看账本。只有参与交易的各方才能按需知原则访问信息。从节点的角度来看，区块链网络中的每个节点都存储分布式账本当前状态的自己的副本。节点的账本由许多不可逆状态的链组成。交易消费并生成状态，每个节点都维护其所有状态的当前和历史版本的完整记录 [26]。`Corda` 智能合约根据现行和新兴法律，跟踪两个或多个可识别方之间金融协议及其他数据交换的进展 [6]。

##### Corda 智能合约

##### Corda：一种智能合约平台

`Corda` 是一种基于 `Java` 编程语言的智能合约平台。合约可以用 `Java` 或 `Kotlin` 编写。在 `Corda` 中，每个状态都由一个智能合约管辖。智能合约以涉及其状态的交易作为输入，并使用智能合约中指定的规则来评估该交易是否有效。要在 `Corda` 中得到确认，交易必须被认定为既真实又独特。交易的有效性由相关方决定。交易的唯一性约束旨在确保没有状态被花费两次。`Corda` 节点只能看到其作为参与者的支付和状态，因此它们无法验证交易的唯一性。为了解决这一过程，`Corda` 区块链采用了一个公证人网络，他们必须对一项活动进行签名，该活动才能生效。每个节点的分布式账本副本中的每个状态都会被分配一个证书。只有当公证人是其所有先前输入状态的指定公证人时，才会授权一笔交易。如果指定的公证人拒绝传输或签名，`Corda` 中的资产和交易可能会被挟持。恶意公证人可能允许双重支付攻击，使区块链难以协调。因此，在使用 `Corda` 区块链时，公证人的信任和安全至关重要。

##### Corda 安全措施

`Corda` 的安全性主要基于其“需知”概念和公证人网络。由于用户只能观察和参与他们有利益关系的交易，因此数据泄露的后果得以缓解。与早期的区块链不同，`Corda` 使用点对点 `TLS` 加密连接，而不是点对点广播（表 13.5）[[26]]。

#### 表 13.5：Ethereum、Hyperledger Fabric 和 Corda 的比较

| **安全** 措施 | Ethereum | Hyperledger Fabric | Corda |
| --- | --- | --- | --- |
| 机密性 | | X | X |
| 运行能力 | X | | |
| 传输数据保护 | X | | |
| 身份认证 | | X | X |
| 信息认证 | X | X | X |
| 系统完整性 | X | | |
| 跨平台工作 | | X | X |
| 访问控制 | X | X | X |
| 可测试性 | | X | X |
| 日志记录 | | X | X |
| 可定制性 | X | X | X |

## 总结与结论

本章系统地探讨了各种区块链攻击向量。一些可能导致区块链攻击的潜在漏洞源于区块链基础设施、架构设计和应用场景。对于促成因素，各种攻击按类型概述，包括各种节点级、系统级、网络级和用户级攻击。节点级攻击包括成员配置错误和共享漏洞。网络级攻击包括 51% 攻击、女巫攻击、重放攻击等。系统级攻击包括缓冲区越界、竞争条件和时间戳。用户级攻击包括恶意软件和私钥被盗。

针对这些攻击的防御技术也有介绍，有助于缓解各种潜在的区块链漏洞。此外，还重点介绍了 `Hyperledger`、`Corda` 和 `Ethereum` 平台的固有安全措施。

本章展示并讨论了许多现实生活中的攻击场景。组织的新目标应是更加专注于为各种区块链技术实施更强的安全措施，以便有效且安全地利用区块链技术。

## 核心概念

*   尽管区块链技术是一种具有卓越安全特性的不断发展的技术，但它由各种核心组件组成，攻击者可针对这些组件发起攻击。

*   用户级攻击是因用户交互而发生的攻击。用户的疏忽、私钥被盗或恶意软件的存在都可能导致区块链安全漏洞。硬件、纸质和云钱包等缓解技术有助于保护密钥免遭盗窃或泄露，同时配合组织的密钥轮换策略。此外，使用杀毒产品进行例行系统和网络扫描有助于降低或防止基于恶意软件的攻击的可能性。

*   节点与用户一样脆弱。但节点本身也可能受到共享和/或成员服务提供商配置错误漏洞的影响。共享漏洞是指攻击者窃取私钥并获取目标节点，旨在同时危害区块链上的其他节点。成员服务提供商配置错误漏洞是由区块链上的控制弱点导致的，引发 DoS/DDoS 攻击。为了额外的保护，可以定期更新和修补软件，从而缓解任何潜在漏洞。

*   攻击者寻找网络弱点进行利用，并采用各种网络级攻击。例如，当攻击者试图通过向网络注入大量交易来延迟或停止网络时，就会发生 DDoS 攻击。在女巫攻击中，攻击者控制许多虚假身份。在 51% 攻击中，矿工获得网络大部分算力的控制权。此类攻击可通过实施许可区块链成员服务提供商服务、`PirlGuard` 和/或合并挖矿来缓解。

*   区块链系统级攻击发生在区块链基础设施的系统层。这些攻击是由系统后端的编码错误和代码操纵产生的。应尽职尽责，并利用工具避免此类错误。此外，将资源限制在用户需求范围内、锁定时间框架的上限以及使用内存安全编程语言，是应对此类攻击的一些技术。系统级攻击需要大量的故障排除，但在专家和称职开发人员的帮助下，这是一项可控的任务。

*   区块链多年来发展迅速。一些强大的技术进步包括 `Ethereum`、`Hyperledger Fabric` 和 `Corda` 平台。`Ethereum` 智能合约中的机密交易，以及信息认证和传输数据保护；`Hyperledger` 通过 `Gossip` 协议实现数据私有化的能力，以及身份认证和可测试性；`Corda` 的公证人系统，都是目前这些区块链结构中现有增强功能的示例。

## 促进理解的活动

读者可能想了解更多关于本章讨论的一些攻击。表 13.6 提供了一些相关 YouTube 视频的标题和链接，可作为补充学习资源。

### 表 13.6：补充学习资源

| **攻击** 类型 | 视频标题 | 直接链接 |
| --- | --- | --- |
| 重放攻击 | *Blockchain 101 Ep 67 – What is a Replay Attack?* | [`www.youtube.com/watch?v=KWJTvnal8j4&ab_channel=HuobiGlobal`](https://www.youtube.com/watch?v=KWJTvnal8j4&ab_channel=HuobiGlobal) |
| 女巫攻击 | *What are Sybil Attacks/Explained for Beginners* | [`www.youtube.com/watch?v=-EKhIBUQjcA`](https://www.youtube.com/watch?v=-EKhIBUQjcA) |
| 缓冲区溢出 | *Ethical Hacking: Buffer Overflow Basics* | [`www.youtube.com/watch?v=SOoJcrR4Ijo&ab_channel=NationalConsortiumforMissionCriticalOperations`](https://www.youtube.com/watch?v=SOoJcrR4Ijo&ab_channel=NationalConsortiumforMissionCriticalOperations) |
| 竞争条件 | *Race Conditions and How to Prevent Them – A Look at Dekker’s Algorithm* | [`www.youtube.com/watch?v=MqnpIwN7dz0&ab_channel=SpanningTree`](https://www.youtube.com/watch?v=MqnpIwN7dz0&ab_channel=SpanningTree) |

## 参考文献

*   **区块链真的那么安全吗？如何攻击与防范攻击。** (2020 年 9 月 24 日)。[`www.seba.swiss/research/are-blockchains-safe-how-to-attack-them-and-prevent-attacks`](https://www.seba.swiss/research/are-blockchains-safe-how-to-attack-them-and-prevent-attacks)

*   **币安学院。** (2020 年 10 月 21 日)。*什么是 51% 攻击？* 币安学院。[`academy.binance.com/en/articles/what-is-a-51-percent-attack`](https://academy.binance.com)

*   **Agcaoili, J.** (2019 年 6 月 5 日)。*挖掘门罗币的恶意软件 PCASTLE 使用无文件技术。* [`www.trendmicro.com/en_ca/research/19/f/monero-mining-malware-pcastle-zeroes-back-in-on-china-now-uses-multilayered-fileless-arrival-techniques.html`](https://www.trendmicro.com)

*   **Batabyal, A.** (2020 年 4 月 30 日)。*比特币纸钱包*。2020 年 3 款最佳 BTC 纸钱包。[`coinswitch.co/news/bitcoin-paper-wallet`](https://coinswitch.co)

*   **Bisson, D.** (2021 年 2 月 19 日)。*PCASTLE 恶意软件攻击以 XMRig 为目标瞄准中国系统。* 安全现状。[`www.tripwire.com/state-of-security/security-data-protection/pcastle-malware-attacks-targeting-china-based-systems-with-xmrig/`](https://www.tripwire.com)

*   **Brown, R. G.**, Carlyle, J., Grigg, I., & Hearn, M. (2016 年 8 月)。*Corda：简介*。ResearchGate。[`www.researchgate.net/publication/308636477_Corda_An_Introduction`](https://www.researchgate.net)

*   **Cao, T.**, Yu, J., Decouchant, J., & Esteves-Verissimo, P. (2018 年 6 月 25 日)。*重审区块链网络上的网络层级攻击*。[`orbilu.uni.lu/bitstream/10993/38142/1/bcrb18-cao.pdf`](https://orbilu.uni.lu)

*   **Cimpanu, C.** (2021 年 1 月 5 日)。*黑客利用新型 ElectroRAT 恶意软件攻击加密货币用户。* [`www.zdnet.com/article/hackers-target-cryptocurrency-users-with-new-electrorat-malware/`](https://www.zdnet.com)。

*   **Coinbase。** (2021)。*什么是以太坊？* [`www.coinbase.com/learn/crypto-basics/what-is-ethereum`](https://www.coinbase.com)。

*   **Constantin, L.** (2020 年 1 月 20 日)。*什么是缓冲区溢出？黑客如何利用这些漏洞。* [`www.csoonline.com/article/3513477/what-is-a-buffer-overflow-and-how-hackers-exploit-these-vulnerabilities.html`](https://www.csoonline.com)。

*   **CWE 内容团队。** (2009 年 10 月 21 日)。*通用弱点枚举。* CWE。[`cwe.mitre.org/data/definitions/787.html`](https://cwe.mitre.org)。
