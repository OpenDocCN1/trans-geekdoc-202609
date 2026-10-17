
# 图 1.5：区块链三难困境

*   **去中心化：** 创建一个避免中央控制点的区块链。
*   **可扩展性：** 区块链必须能够处理不断增加的用户和交易数量。
*   **安全性：** 区块链必须按预期运行，并能抵御攻击、漏洞和其他不可预见的问题。¹⁸

Cardano 旨在通过以下方法解决这些维度中的每一个：

*   通过确保保护网络的权益池可以使用普通硬件和典型的互联网连接运行，来促进去中心化。
*   通过侧链、加密汇总和并行性（流水线）来解决可扩展性问题，提高交易处理的速度。
*   为了实现高保证的软件和安全性，采用科学方法，包括同行评审流程和对 `Ouroboros Proof-of-Stake` 协议的形式化验证。

## 代币经济学

本章的最后一个主题是对代币经济学的简要回顾。加密货币代币对于建立加密货币生态系统的价值至关重要。这一点很重要，因为运行和维护网络需要现实世界的资源和成本。因此，了解初始代币分配和货币政策（如最大供应量和通货膨胀率）以及它们如何影响价格和市值至关重要。最后，与股票市场一样，价格和价值经常是错位的。因此，在根据加密货币代币的价格评估生态系统时要保持谨慎。价格可能与该生态系统的效用或价值关系不大，而更多地与价格操纵和市场情绪有关。

## 代币分配

Cardano 的原生代币是 `Ada`，目前流通供应量为 35,125,959,544 `ADA`，最大供应量为 45,000,000,000 `ADA`。¹⁹ Cardano 的 `ICO` 于 2015 年 10 月至 2017 年 1 月期间完成，²⁰ 分配情况如 *图 1.6* 所示。

![](img/Figure-1.6.jpg)

**图 1.6：** 初始代币分配

Cardano 有三个创始实体：²¹

*   **IOHK (IOG)** 是一家研究和工程公司及风险工作室，构建区块链和 Web3 产品，以赋能每个人、无处不在。²²
*   **Emurgo** 是营利性分支机构，负责开发、支持和孵化商业机会，并帮助企业集成到 Cardano 区块链系统中。
*   **Cardano 基金会** 是一个独立的、总部位于瑞士的非营利组织，致力于为金融和社会系统推广和发展 Cardano 平台。

## 代币分布

由于 `Ada` 有最大供应量上限，我们可以随时查看代币分布情况。这有助于与其他加密货币进行比较，因为如果大量代币未在流通供应中，那么当这些代币释放给公众时，可能会对价格造成下行压力。

![](img/Figure-1.7.jpg)

**图 1.7：** Ada 代币分布²³

**储备** 是用于**质押**奖励和资助金库的 `Ada` 数量，如 *图 1.7* 所示。金库用于支付生态系统的改进和维护费用。权益证明网络使用质押机制，允许用户质押其 `Ada` 以帮助保护网络。作为回报，他们将获得与用户质押的 `Ada` 占网络中总质押 `Ada` 比例成正比的奖励。质押奖励和金库资金还包括网络活动产生的交易费用。

## 代币分配对比

*图 1.8* 对比了截至 2023 年 9 月 27 日按市值排名的前十大加密货币的初始代币分配。有趣的是，随着加密货币发布时间的推移，内部人士 + 基金会的初始分配量呈上升趋势。

![](img/Figure-1.8.jpg)

**图 1.8：** 市值前十加密货币初始代币分配对比²⁴

## 通货膨胀率

我们将要查看的最后一个指标是 Cardano 0.3% 的通货膨胀率。²⁵ 这是指通过质押和资助金库，从储备中释放到活跃供应中的 `Ada` 数量。Cardano 的通货膨胀率与 `Bitcoin` 相似，在启动时处于最高水平，随后随时间呈指数级下降，如 *图 1.9* 所示。

![](img/Figure-1.9.jpg)

**图 1.9：** Cardano 通货膨胀率

## Cardano 路线图

Cardano 路线图被组织为五个主题或阶段：`Byron`、`Shelley`、`Goguen`、`Basho` 和 `Voltaire`。²⁶ 每个主题专注于一组将跨多个代码版本交付的功能。²⁷ 每个开发主题包含一个或多个时代，每个时代都有特定的账本规则，如 *表 1.1* 和 *1.2* 所示。

| **阶段** | **主题** | **账本时代** | **描述** |
| --- | --- | --- | --- |
| `Byron` | 基础 | `Byron` | 使用 `Ouroboros Proof-of-Stake` 协议的联邦制 Cardano 区块链的第一个版本²⁸ |
| `Shelley` | 去中心化 | `Shelley` | 推出改进去中心化并引入质押委托和奖励的升级²⁹ |
| `Goguen` | 智能合约 | `Allegra` | 引入代币锁定支持 |
| | | `Mary` | 启用原生代币和多资产 |
| | | `Alonzo` | 推出智能合约功能 |
| | | `Babbage` | 实现内联数据、引用脚本和引用输入等功能 |
| `Basho` | 扩展 | `N/A` | 提高 Cardano 网络的可扩展性和互操作性³⁰ |
| `Voltaire` | 治理 | `Conway` | 允许 Cardano 区块链成为一个自我维持的系统，网络参与者利用其质押的 `Ada` 和投票权影响网络的未来发展³¹ |

**表 1.1：** Cardano 路线图³²

| **日期** | **阶段** | **时代** | **纪元编号** | **共识机制** |
| --- | --- | --- | --- | --- |
| 2017/09 | `Byron` | `Byron` | 0 | `Ouroboros Classic` |
| 2020/02 | `Byron` | `Byron` | 176 | `Ouroboros BFT` |
| 2020/07 | `Shelley` | `Shelley` | 208 | `Ouroboros Praos` |
| 2020/12 | `Goguen` | `Allegra` | 236 | `Ouroboros Praos` |
| 2021/03 | `Goguen` | `Mary` | 251 | `Ouroboros Praos` |
| 2021/09 | `Goguen` | `Alonzo` | 290 | `Ouroboros Praos` |
| 2021/10 | `Goguen` | `Alonzo` | 298 | `Ouroboros Praos` |
| 2022/09 | `Goguen` | `Babbage` | 365 | `Ouroboros Praos` |
| 2023/02 | `Goguen` | `Babbage` | 394 | `Ouroboros Praos` |

**表 1.2：** Cardano 时间线³³

## 区块链用例

为了结束本介绍性章节，了解一些展示区块链技术潜力的区块链用例会很有帮助：

*   **资本市场**：更高效的资本流动³⁴
*   **代币化**：代表黄金、股票、债券、房产或法定货币等资产
*   **奖励**：利用奖励或积分激励行为的能力
*   **去中心化交易所 (DEX)**：用于资产和衍生品互换的非托管交易所
*   **市场**：用于买卖代币化资产
*   **金融产品**：如借贷
*   **身份系统**：自主身份 (`SSI`) 解决方案
*   **保险**：使用智能合约和数据馈送进行理赔处理
*   **媒体和娱乐**：追踪并变现真实数字内容的生命周期和分发³⁵
*   **去中心化存储**：利用代币激励模型实现点对点去中心化存储
*   **去中心化自治组织 (DAO)**：用于治理和投票

## 结论

我们现在应该对区块链技术的演变有了高层级的理解，从分布式账本的起源到 Charles Hoskinson 的著名白板视频，概括了 Cardano 的目的和目标。我们介绍了比特币和以太坊白皮书，并将在下一章更详细地研究工作量证明和权益证明共识模型。此外，我们回顾了区块链三难困境、代币经济学、Cardano 路线图和区块链用例等基本区块链概念。在下一章中，我们将更深入地从技术角度探讨密码学和共识算法，并探索它们如何使区块链安全。

## 重点回顾

*   网络可以是中心化的，也可以是去中心化的。
*   去中心化网络的难点在于它不得拥有中央权威。
*   拜占庭错误是指网络节点不可用或试图损害网络。
*   网络使用共识算法就网络的正确状态达成一致。
*   51% 攻击发生在单个实体控制去中心化账本网络中大多数节点时。
*   比特币白皮书同时解决了两个问题：
    *   提供了一个简单高效的共识算法。
    *   任何人都可以参与共识算法，消除了对中央权威的需求。
*   以太坊白皮书引入了可以访问账本全局状态的图灵完备脚本的概念。
*   Cardano 被认为是第三代区块链，其目标是解决可扩展性、互操作性和可持续性问题。
*   代币的价格和价值经常错位，因此在评估加密货币时，考虑去中心化、安全性和可扩展性等基本原则很重要。
*   Cardano 有五个开发主题或阶段：Byron、Shelley、Goguen、Basho 和 Voltaire。

## 多项选择题

1.  哪种网络不需要中央权威？
    1.  中心化
    2.  去中心化
    3.  分布式
    4.  匿名

2.  Wei Dai 发布了什么创新概念，至今仍被比特币使用？
    1.  通过解谜进行计算工作
    2.  通过 CPU 算力进行计算工作
    3.  通过网络算力进行计算工作
    4.  通过共识进行计算工作

3.  为什么 Hal Finney 的“可重复使用的工作量证明”没有被广泛采用？
    1.  它基于工作量证明 (POW)
    2.  它不是去中心化的
    3.  依赖受信任的后端
    4.  密码学不安全

4.  比特币的工作量证明之所以创新，是因为它是：
    1.  基于时间的共识算法
    2.  基于哈希的共识协议
    3.  基于时间和哈希的共识协议
    4.  高效且开放的共识协议

5.  为什么图灵完备脚本未在比特币中使用？
    1.  当时没有合适的计算机语言来编写它
    2.  存在无限循环的风险
    3.  它需要是一种函数式编程语言
    4.  比特币不使用脚本

6.  第一代和第二代区块链的三个关键痛点是什么？
    1.  可扩展性、互操作性、可持续性
    2.  可扩展性、去中心化、可持续性
    3.  去中心化、可扩展性、共识
    4.  可持续性、共识、可编程性

7.  区块链三难困境的三个维度是什么？
    1.  安全性、共识、去中心化
    2.  可编程性、安全性、共识
    3.  去中心化、可扩展性、安全性
    4.  安全性、可扩展性、可编程性

## 答案

1.  b
2.  a
3.  c
4.  d
5.  b
6.  a
7.  c

## 问题

1.  去中心化账本试图解决什么问题？
2.  为什么去中心化对共识协议如此关键？
3.  什么是拜占庭错误，如何缓解它？
4.  比特币白皮书的动机是什么？
5.  为什么 Vitalik Buterin 要撰写以太坊白皮书？
6.  Cardano 的目标是什么？
7.  为什么代币经济学很重要？

## 关键术语

*   **归属：** 发送者和接收者的身份。
*   **BFT：** 拜占庭容错
*   **CFT：** 故障容错
*   **合规：** KYC 和反洗钱。
*   **共识：** 网络节点就网络状态达成一致的能力。
*   **去中心化：** 没有中央权威的网络。
*   **元数据：** 交易背后的故事。
*   **储备：** 随时间推移用于质押奖励的加密货币数量。
*   **可扩展：** 区块链系统扩展网络交易的能力。
*   **安全：** 区块链保持可信的能力。
*   **归属**：发送者和接收者的身份。
*   **质押：** 使用 `Ada` 协助保护 Cardano 区块链并获得 `Ada` 奖励。
*   **金库：** 用于维护和升级的 `Ada` 数量。

____________________________________

¹ Lyn Alden, "Broken Money," 1-2.

² Stuart Haber et al., "How to Time-Stamp a Digital Document."

³ Leslie Lampor et al., "The Byzantine Generals Problem."

⁴ David Mazieres et al., "Building Secure File Systems Out of Byzantine Storage."

⁵ Wei Dai, "b-money."

⁶ Hal Finney, "RPOW - Reusable Proofs of Work."

⁷ Vitalik Buterin, "A Next-Generation Smart Contract and Decentralized Application Platform," 4.

⁸ Vitalik Buterin, "A Next-Generation Smart Contract and Decentralized Application Platform," 4.

⁹ Satoshi Nakamoto, "Bitcoin: A Peer-to-Peer Electronic Cash System," 8.

¹⁰ Satoshi Nakamoto, "Bitcoin: A Peer-to-Peer Electronic Cash System," 1.

¹¹ Vitalik Buterin, "A Next-Generation Smart Contract and Decentralized Application Platform," 4.

¹² Vitalik Buterin, "A Next-Generation Smart Contract and Decentralized Application Platform," 4.

¹³ Vitalik Buterin, "A Next-Generation Smart Contract and Decentralized Application Platform," 13.

¹⁴ Vitalik Buterin, "A Next-Generation Smart Contract and Decentralized Application Platform," 13.

¹⁵ Vitalik Buterin, "A Next-Generation Smart Contract and Decentralized Application Platform," 13.

¹⁶ Charles Hoskinson, “Cardano whiteboard; overview with Charles Hoskinson.”

¹⁷ Cryptopedia, “The Blockchain Trilemma: Fast, Secure, and Scalable Networks.”

¹⁸ [`medium.com/certik/the-blockchain-trilemma-decentralized-scalable-and-secure-e9d8c41a87b3`](https://medium.com/certik/the-blockchain-trilemma-decentralized-scalable-and-secure-e9d8c41a87b3)

¹⁹ [`coinmarketcap.com/currencies/cardano/#About`](https://coinmarketcap.com/currencies/cardano/#About)

²⁰ [`cardano.org/genesis/#audit`](https://cardano.org/genesis/#audit)

²¹ [`cardano.org/partners/`](https://cardano.org/partners/)

²² [`cardano.org/partners?tab=iog`](https://cardano.org/partners?tab=iog)

²³ cardanians.io, “There is 1.23B ADA in Cardano’s.”

²⁴ Source data from:

[`www.investopedia.com/what-is-xrp-6362550#toc-xrp-ledger-and-xrp`](https://www.investopedia.com/what-is-xrp-6362550#toc-xrp-ledger-and-xrp)

[`coinmarketcap.com/currencies/dogecoin/#About`](https://coinmarketcap.com/currencies/dogecoin/#About)

[`www.coingecko.com/en/coins/ethereum/tokenomics`](https://www.coingecko.com/en/coins/ethereum/tokenomics)

[`coinmarketcap.com/currencies/cardano/#About`](https://coinmarketcap.com/currencies/cardano/#About)

[`www.coingecko.com/en/coins/polkadot/tokenomics`](https://www.coingecko.com/en/coins/polkadot/tokenomics)
