

# 参考文献

Minoli, D., & Occhiogrosso, B. (2018). Blockchain mechanisms for IoT security. *Internet of Things*, 1-2, 1–13. doi:10.1016/j.iot.2018.05.002

Ocheja, P., Flanagan, B., Ueda, H., & Ogata, H. (2019). Managing lifelong learning records through blockchain. *Research and Practice in Technology Enhanced Learning*. doi:10.1186/s41039-019-0097-0

Pustišeka. (2018). Approaches to Front-End IoT Application Development for the Ethereum Blockchain. *Procedia Computer Science*, 129, 410–419.

Ryu, Sharma, Jo, & Park. (2019). A blockchain-based decentralized efficient investigation framework for IoT digital forensics. *Springer Science+Business Media, LLC*.

Shahzad. (2019). Trustworthy Electronic Voting Using Adjusted Blockchain Technology. *IEEE Access: Practical Innovations, Open Solutions*, 7, 24477–24488.

Turkanovic. (2018, January 5). EduCTX: A Blockchain-Based Higher Education Credit Platform. *IEEE Access: Practical Innovations, Open Solutions*, 5112–5127.

Wang, B., Sun, J., He, Y., Pang, D., & Lu, N. (2018). Large-scale Election Based On Blockchain. *Procedia Computer Science*, 129, 234–237. doi:10.1016/j.procs.2018.03.063

Zhou, L., Wang, L., Sun, Y., & Lv, P. (2018). BeeKeeper: A Blockchain-Based IoT System With Secure Storage and Homomorphic Computation. *IEEE Access: Practical Innovations, Open Solutions*, 6, 43472–43488. doi:10.1109/ACCESS.2018.2847632

# 第8章

**Harsha Kundan Patil**

[![Orcid Image](i/orcid.svg)https://orcid.org/0000-0002-1801-4086](https://orcid.org/0000-0002-1801-4086)

Ashoka Center for Business and Computer Studies, Nashik, India

## 摘要

“Blockchain”（区块链）顾名思义即区块的链条。它是通过公共数据库（链）连接的数字信息块（区块）组成的片段。这无非是文件组织的新版本。区块存储数字信息，如交易的实际记录、交易涉及实体的详细信息、时间戳以及交易的其他元数据。区块还拥有唯一标识符，称为哈希值。

区块链技术基于点对点网络构建。网络上的任何人都可以访问区块。不存在控制区块链的中心化社区。它由矿工运营，即那些将其计算能力借给网络以解决复杂计算算法问题的人。这些区块存储在多台计算机中。由于其分布式和去中心化特性，验证过程具有广播性质，这赋予了它“可信方法”的特性。区块链为数据存储和智能合约提供了安全性和防篡改能力。节点或用户在区块中尝试的任何数据篡改都会改变该区块的哈希值。区块链技术有能力应对在线风险和安全顾虑问题并提供解决方案。2008年，有远见的中本聪发表了一篇神秘的白皮书《比特币：一种点对点的电子现金系统》，从而诞生了区块链的概念。本章详细解释了区块链技术的结构，并阐述了使区块链技术成为当今世界安全概念的各个方面。

## 引言

“Blockchain”（区块链）顾名思义即区块的链条。通过公共数据库（链）连接的数字信息块（区块）。这无非是文件组织的新版本。区块存储数字信息，如交易的实际记录、交易涉及实体的详细信息、时间戳以及交易的其他元数据。区块还拥有称为哈希值的唯一标识符。

区块链技术基于点对点网络构建。网络上的任何人都可以访问区块。不存在控制区块链的中心化社区。它由矿工运营；即那些将其计算能力借给网络以解决复杂计算算法问题的人。这些区块存储在多台计算机中。图1展示了区块链的逐步工作原理。

*   **步骤1：** 当发生任何在线交易（如通过Amazon购买）并成功完成时，会记录交易详情。
*   **步骤2：** 下一步是验证。通过计算机网络验证交易详情。成千上万台通过全球网络连接的计算机被用于验证过程。这涉及对购买商品详情、交易时间戳、成本及涉及各方的验证。
*   **步骤3：** 交易详情验证后，连同相关方的数字签名一起存储在区块中。一个区块可包含多笔已验证交易。该区块还拥有赋予其唯一标识的哈希键。随后该区块被添加到现有的区块链中。就这样区块链不断增长。一旦区块被添加到区块链，它将公开可用。

| 图1. 区块链生成 |
| --- |
| ![Figure978-1-7998-2414-5.ch008.f01](i/ch008.f01.png) |
| --- |

连接到区块链网络的每台计算机都拥有自己的区块链副本，每当新区块被添加时，每台计算机的副本都会更新。这意味着区块链网络中所有计算机拥有相同的网络副本，每当访问或添加任何区块时，所有连接的计算机都会进行验证。众所周知，瞒过一双眼睛容易，但瞒过所有人的眼睛却很难。公共网络这种360度的验证使区块链非常安全。

## 区块链技术的概念及其出现

作为加密货币底层技术的区块链，其起源可追溯至20世纪80年代末和90年代初数字时间戳验证问题。1990年，Haber & Stornetta发表了题为《如何为数字文档加盖时间戳》的论文。在该论文中，他们提出通过将发布的时间戳链接在一起创建哈希链，从而防止文档被前向或后向加盖日期。

随后，著名研究者Wei Dai引入了b-money的概念，该概念通过解决计算谜题和去中心化共识来创造货币。但该提案缺乏实现细节。Hal Finney引入了“可重复使用的工作量证明”概念。该概念结合了b-money的思想和Adam Back计算困难的哈希现金谜题，用于创建加密货币。

由于无需中介即可交换价值单元的特性，区块链技术受到电子商务开发者的关注。它允许我们在市场上保护数字资产（如艺术品或传感器数字数据），或允许财产所有者在无需公证人的情况下转让土地。该技术还被用于解决其他几个科学问题，如同行评审过程中恶意行为形式的信任问题、研究设计缺乏质量和冗余，以及科学出版物自由获取受限等问题。

## 区块链概念

