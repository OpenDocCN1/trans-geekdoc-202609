
证明思路。我们需要证明两个属性：公平性和完备性。

### 公平性。

首先，我们证明法官 $J$ 在 $\mathcal{E} | \mathcal{A} | \mathbb{P}_\text{Fr}$ 的一次运行中不会做出错误裁决，即裁决必须评估为 $\text{true}$（可忽略的运行集除外）。这主要源自第 6.2 节给出的推理，以及根据 $\mathcal{F}_\text{sig}$ 的定义，对手无法为诚实方伪造签名的事实。请注意，这里我们受益于块切割算法 CUTBLOCK 的构造，它允许从包含在该块中的 Kafka 消息流中确定性地重新计算块。因此，来自诚实排序节点的所有块都将与法官的重新计算相同。因此，诚实的对等节点和排序节点不会被意外指责。

然而，有一种特殊情况需要进一步关注：Kafka 集群不会直接对消息签名，而是构建一个 Merkle 树并对其根签名。因此，如果对手找到具有相同 Merkle 根的不同消息体和 Merkle 证明，或者能够为相同消息体和 Merkle 根创建不同的 Merkle 证明，他可以重用诚实 Kafka 集群的签名来创建不一致的 Kafka 流消息，从而导致错误裁决。然而，可以将这两种情况归约为随机预言机中的碰撞（参见，例如，[17]）。由于对于多项式时间系统，碰撞的概率只有可忽略的概率，法官做出错误裁决的概率最多为可忽略的概率。

### 完备性。

我们需要证明，如果 $\mathcal{E} | \mathcal{A} | \mathbb{P}_\text{F}$ 的一次运行属于 $\alpha = \bigcup_{i=1}^4 \alpha_i$，那么法官 $J$ 做出的裁决至少会指责对等节点、排序节点或 Kafka 集群中的某一个。请注意，根据评判程序，法官的所有裁决都直接指责某个单一方或 Kafka 集群。

如第 6.2 节所述，如果运行在 $\bigcup_{i=1}^3 \alpha_i$ 中，则法官会注意到这一点并指责导致违规的对等节点。如果运行在 $\alpha_4$ 中，即在基本正确性成立的前提下违反了一致性，那么要么法官指责 Kafka 集群分发了不同的消息，要么我们知道一个冲突块中的 Kafka 消息流是另一个块的 Kafka 消息流的（真）前缀。这基本上源自基本正确性（特别是，我们需要链中包含的 Kafka 消息流没有间隙）以及这是第一个不一致块 ID 的事实。因此，块不一致仅仅是因为它们在 Kafka 消息流的不同点结束。根据 CUTBLOCK 的定义，两个排序节点都应该在相同的端点处切断流（因为它们同意相同的 Kafka 消息流前缀）。这意味着法官的最终检查至少对一个排序节点失败，该排序节点随后被指责。

我们所有的安全结果均针对理想签名功能 $\mathcal{F}_\text{sig}$ 进行展示。在附录 D 中，我们表明如果将 $\mathcal{F}_\text{sig}$ 替换为其实现 $\mathcal{P}_\text{sig}$（参见 [46]），所有结果均可迁移，其中签名使用 EUF-CMA 安全签名方案（_选择消息攻击下的存在性不可伪造性_）进行。虽然此结果使用了 $\mathcal{P}_\text{sig}$ 按通常 UC 意义实现 $\mathcal{F}_\text{sig}$（参见，例如，[46]），但该结果并不直接从 UC 组合定理中得出。

## 7. 相关工作

大多数关于区块链安全的既有文献（参见，例如，[8]、[9]、[11]、[19]、[24]、[35]、[36]、[53]）不使用问责制或密切相关的隐蔽对手概念 [5]、[7]。虽然有几篇作品将问责制作为区块链的一个概念予以提及 [12]、[14]、[18]、[22]、[23]、[33]、[34]、[54]，但它们都没有形式化，更不用说证明问责制了。或许最接近我们工作的是 Karame 等人 [34] 的工作，他们通过识别行为不当的各方来建议针对比特币双重支出的对策。虽然这项工作利用了问责制的基本直觉——即识别行为不当的参与者——来展示关于双重支出的正式陈述，但他们并未以正式方式使用问责制本身的概念。

如第 3.3 节详细讨论的那样，Haeberlen 等人 [28] 引入了 PeerReview，以在任意（确定性）协议之上添加问责制。PeerReview 有几个缺点，通常使得针对特定协议定制的解决方案更可取（参见第 3.3 节）。此外，Haeberlen 等人未为其系统提供正式的安全证明。

## 8. 结论

本文提出了对（许可型）区块链和分布式账本问责制的正式处理。作为与严格安全概念正交的属性，一方面，问责制可以作为区块链和分布式账本的额外安全层。另一方面，作为一种独立的属性，问责制为分析和构建安全区块链和分布式账本开辟了替代且有趣的途径，这些途径基于其他（部分较弱）假设（例如，无最终消息传递和无诚实多数派）以及在某些方面更强的安全目标。

我们通过对 Hyperledger Fabric（一个改进的实例）的严格分析，成功地说明了这种方法，Hyperledger Fabric 是工业界非常成功且广泛使用的区块链。除了对问责制的正式处理之外，鉴于该区块链的广泛应用，我们案例研究中获得的结果具有独立的意义。我们期望这种方法也能证明对分析广泛现有（许可型）区块链和分布式账本有用，例如基于 Tendermint 的区块链 [1] 和 Corda [13]。

总的来说，问责制的正式处理是一种强大的工具，为区块链（安全）研究开辟了新的选择。我们的方法还为形式化和证明许多区块链规范中常见的非正式问责主张提供了正式基础。

## 致谢

本研究部分由德国巴登-符腾堡州科学部资助，用于“服务计算”博士项目。5

5. http://www.services-computing.de/

## 参考文献

- [1] All In Bits, Inc., “区块链共识 - Tendermint,” https://tendermint.com/, 2019, (访问于 06/05/2019).
- [2] E. Androulaki, A. Barger, V. Bortnikov, C. Cachin, K. Christidis, A. D. Caro, D. Enyeart, C. Ferris, G. Laventman, Y. Manevich, S. Muralidharan, C. Murthy, B. Nguyen, M. Sethi, G. Singh, K. Smith, A. Sorniotti, C. Stathakopoulou, M. Vukolic, S. W. Cocco, and J. Yellick, “Hyperledger Fabric：面向许可型区块链的分布式操作系统,” in 第十三届 EuroSys 会议论文集，EuroSys 2018，葡萄牙，波尔图，2018 年 4 月 23-26 日。ACM，2018，pp. 30:1-30:15.
- [3] Apache 软件基金会, “Apache Kafka,” https://kafka.apache.org/, 2017, (访问于 04/01/2019).
- [4] —, “Apache ZooKeeper,” https://zookeeper.apache.org/, 2018, (访问于 04/01/2019).
- [5] G. Asharov and C. Orlandi, “揪出作弊者：带公开可验证性的隐蔽安全,” in 密码学进展 - ASIACRYPT 2012 - 第 18 届密码学与信息安全理论与应用国际会议论文集，北京，中国，2012 年 12 月 2-6 日。计算机科学讲义，第 7658 卷。Springer，2012，pp. 681-698.
- [6] N. Asokan, V. Shoup, and M. Waidner, “用于乐观公平交换的异步协议,” in IEEE 安全与隐私研究研讨会论文集。IEEE 计算机学会，1998，pp. 86-99.
- [7] Y. Aumann and Y. Lindell, “针对隐蔽对手的安全：面向现实对手的高效协议,” in 第 4 届密码学理论会议（TCC 2007）论文集，计算机科学讲义，S. P. Vadhan 编，第 4392 卷。Springer，2007，pp. 137-156.
- [8] C. Badertscher, P. Gazi, A. Kiayias, A. Russell, and V. Zikas, “Ouroboros Genesis：具有动态可用性的可组合权益证明区块链,” in 2018 年 ACM SIGSAC 计算机与通信安全会议论文集，CCS 2018，加拿大，安大略省，多伦多，2018 年 10 月 15-19 日。ACM，2018，pp. 913-930.
- [9] C. Badertscher, U. Maurer, D. Tschudi, and V. Zikas, “比特币作为交易账本：一种可组合处理,” in 密码学进展 - CRYPTO 2017 - 第 37 届年度国际密码学会议论文集，第一部分，计算机科学讲义，第 10401 卷。美国，加利福尼亚州，圣巴巴拉，2017 年 8 月 20-24 日。Springer，2017，pp. 324-356.
- [10] C. Baum, I. Damgård, and C. Orlandi, “公开可审计的安全多方计算,” in 网络安全与密码学 - 第 9 届国际会议，SCN 2014，意大利，阿马尔菲，2014 年 9 月 3-5 日。计算机科学讲义，第 8642 卷。Springer，2014，pp. 175-196.
- [11] I. Bentov, R. Pass, and E. Shi, “Snow White：可证明安全的权益证明,” IACR 密码学 ePrint 档案，第 2016 卷，p. 919，2016。
- [12] A. Boudguiga, N. Bouzerra, L. Granboulan, A. Olivereau, F. Quesnel, A. Roger, and R. Sirdey, “通过区块链实现 IoT 更新的更高可用性和问责制,” in 2017 年 IEEE 欧洲安全与隐私研讨会，EuroS&P Workshops 2017，法国，巴黎，2017 年 4 月 26-28 日。IEEE，2017，pp. 50-58.
- [13] M. Brown and R. G. Brown, “Corda：一种分布式账本,” https://www.r3.com/reports/corda-technical-whitepaper/, 2019, (访问于 11/11/2019).
- [14] V. Buterin and V. Griffith, “Casper 友好最终性小工具,” CoRR, vol. abs/1710.09437, 2017.
- [15] R. Canetti, “普遍可组合安全：密码学协议的新范式,” in 第 42 届计算机科学基础年度研讨会论文集（FOCS 2001）。IEEE 计算机学会，2001，pp. 136-145.
- [16] M. Castro and B. Liskov, “实用拜占庭容错与主动恢复,” ACM Trans. Comput. Syst., vol. 20, no. 4, pp. 398-461, 2002.
- [17] C. Coronado, “关于 Merkle 签名方案的安全性和效率,” IACR Cryptology ePrint Archive, vol. 2005, p. 192, 2005.
- [18] G. D’Angelo, S. Ferretti, and M. Marzolla, “基于区块链的云问责制飞行数据记录器,” in 分布式系统加密货币和区块链第 1 届研讨会论文集，CRYBLOCK@MobiSys 2018，德国，慕尼黑，2018 年 6 月 15 日。ACM，2018，pp. 93-98.
- [19] B. David, P. Gazi, A. Kiayias, and A. Russell, “Ouroboros Praos：一种自适应安全的半同步权益证明区块链,” in 密码学进展 - EUROCRYPT 2018 - 第 37 届年度国际密码技术理论与应用会议论文集，第二部分，计算机科学讲义，第 10821 卷。以色列，特拉维夫，2018 年 4 月 29 日 - 5 月 3 日。Springer，2018，pp. 66-98.
- [20] M. del Castillo, “区块链 50：十亿美元的宝贝,” https://www.forbes.com/sites/michaeldelcastillo/2019/04/16/blockchain-50-billion-dollar-babies/, 2019, (访问于 05/01/2019).
- [21] T. T. A. Dinh, J. Wang, G. Chen, R. Liu, B. C. Ooi, and K. Tan, “BLOCKBENCH：分析私有区块链的框架,” in 2017 年 ACM 数据管理国际会议论文集，SIGMOD 2017 会议，美国，伊利诺伊州，芝加哥，2017 年 5 月 14-19 日。ACM，2017，pp. 1085-1100.
- [22] 以太坊基金会, “以太坊企业版,” https://www.ethereum.org/enterprise/, 2019, (访问于 11/13/2019).
- [23] E. Funk, J. Riddell, F. Ankel, and D. Cabrera, “区块链技术：一种改善卫生专业教育中信息交换的有效性、信任和问责制的数据框架,” Academic Medicine, vol. 93, no. 12, pp. 1791-1794, 2018.
- [24] J. A. Garay, A. Kiayias, and N. Leonardos, “比特币骨干协议：分析与应用,” in 密码学进展 - EUROCRYPT 2015 - 第 34 届年度国际密码技术理论与应用会议论文集，第二部分，计算机科学讲义，第 9057 卷。保加利亚，索菲亚，2015 年 4 月 26-30 日。Springer，2015，pp. 281-310.
- [25] P. Gazi, A. Kiayias, and A. Russell, “权益证明区块链上的质押流血攻击,” IACR Cryptology ePrint Archive, vol. 2018, p. 248, 2018.
- [26] S. Goldwasser, S. Micali, and R. Rivest, “一种针对自适应选择消息攻击安全的数字签名方案,” SIAM Journal on Computing, vol. 17, no. 2, pp. 281-308, 1988.
- [27] C. Gorenflo, S. Lee, L. Golab, and S. Keshav, “FastFabric：将 Hyperledger Fabric 扩展到每秒 20,000 笔交易,” in IEEE 区块链和加密货币国际会议，ICBC 2019，韩国（南部），首尔，2019 年 5 月 14-17 日。IEEE，2019，pp. 455-463.
- [28] A. Haeberlen, P. Kouznetsov, and P. Druschel, “PeerReview：分布式系统的实用问责制,” in 第 21 届 ACM 操作系统原理研讨会 2007 论文集，SOSP 2007，T. C. Bressoud 和 M. F. Kaashoek 编。ACM，2007，pp. 175-188.
- [29] P. Hunt, M. Konar, F. P. Junqueira, and B. Reed, “ZooKeeper：面向互联网规模系统的无等待协调,” in 2010 年 USENIX 年度技术会议，美国，马萨诸塞州，波士顿，2010 年 6 月 23-25 日。USENIX 协会，2010。
- [30] Hyperledger 项目, “fabricdocs：排序服务,” https://hyperledger-fabric.readthedocs.io/en/latest/orderer/ordering_service.html, 2018, (访问于 07/24/2019).
- [31] —, “Hyperledger Fabric,” https://www.hyperledger.org/projects/fabric, 2018, (访问于 03/02/2019).
- [32] —, “fabricdocs：架构起源,” https://hyperledger-fabric.readthedocs.io/en/latest/arch-deep-dive.html, 2019, (访问于 01/29/2019).
- [33] IBM, “Hyperledger Fabric：关于为 IBM 区块链提供支持的框架需要知道的事项,” https://www.ibm.com/blogs/blockchain/2018/08/hyperledger-fabric-what-you-need-to-know-about-the-framework-that-powers-ibm-blockchain/, 8, 2018, (访问于 11/11/2019).
