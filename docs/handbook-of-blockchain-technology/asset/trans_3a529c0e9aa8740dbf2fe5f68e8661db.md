
除了上述两大类之外，我们还观察到第三类，称为混合类。混合共识算法（CA）旨在结合基于证明和基于投票两种方法的优势。委托权益证明（DPoS）将权益证明（PoS）特性与投票机制相结合，允许利益相关者选出固定数量的个体来负责验证交易（Snider等，2018）。该技术提高了交易吞吐量和能源效率，同时保持了去中心化。然而，它可能仍然容易受到代表之间共谋和中心化问题的影响。另一个混合示例是DPBFT，它结合了pBFT和由基于PoS的方法定义的动态验证者集合（Hao等，2018b）。然而，这类混合系统的实现复杂性可能会限制其广泛使用。

对上述算法的初步分析揭示了以下发现：

- **实际应用：** 比特币和以太坊等不同区块链平台，为PoW和PoS的实际应用提供了实践案例研究。其运行特征、优势和挑战可为未来共识算法的开发与采用提供洞见。
- **监管与法律影响：** 区块链的持续扩展使其与监管体系的结合变得至关重要。一些共识算法，特别是那些具有中心化倾向的算法，可能面临严格评估。例如，DPoS算法因其验证者集合有限，可能被视为中心化的推动者，需要监管关注。
- **稳定性与采用：** PoW等传统算法已经展现出持久性，支撑着比特币等加密货币。相比之下，新兴算法尽管具有潜在优势，却面临采用障碍。算法的稳定性通常与其网络规模相关，更大、更分散的网络通常更安全。
- **安全性影响：** 大多数共识算法将安全性置于优先位置，但缺陷依然存在。例如，PoW容易遭受至少51%攻击，尤其是在计算能力较弱的网络中。PoS变体可能面临“无利害关系”挑战，即验证者缺乏抑制其验证多个区块链分叉的机制。
- **用户参与与包容性：** 区块链的基本理念倡导去中心化和包容性。像PoW这样具有高处理需求的算法，可能会无意中排除那些没有先进挖矿基础设施的参与者。另一方面，PoS及其衍生算法营造了更具包容性的环境，用户可根据其网络权益来验证交易。
- **未来潜力与方向：** 许多共识算法仍处于早期发展阶段。随着区块链技术日益成熟，我们可以期待这些算法得到迭代优化，变得更加高效和通用，以满足更广泛的应用需求。
- **共识算法评估：** 需要一个评估框架来进一步研究关键特征并分析区块链共识算法。这样的框架将使我们能够收集和分析相关数据，并与社区分享结果。为了满足这一需求，我们提出了一个合适的框架，如表9.2所示。在框架的开发过程中，我们主要依赖前面章节的讨论以及规范性文献。我们的目标是通过分析来自参与上述共识算法的区块链专家的经验数据，来评估所提出的共识算法框架。目前，我们正在遴选潜在专家，并将在未来几个月内开展一项调查并报告结果。

## 表9.2 共识算法评估框架

| 标准 | 描述 |
|---|---|
| 去中心化 | 决策权在网络节点间的分布程度。 |
| 可扩展性 | 算法在网络增长时有效处理不断增加的工作负载的能力。 |
| 安全性 | 算法对潜在攻击、漏洞和故障场景的韧性。 |
| 能源效率 | 算法在能源消耗方面的资源需求。 |
| 公平性 | 网络中所有节点获得平等机会参与共识过程。 |

## 9.5 结论

本章首先聚焦于区块链的演化阶段，并报告了其属性及对众多行业领域的影响。在此过程中，我们通过将最后一个演化阶段分为两个阶段来完善现有分类：新的区块链5.0阶段基于Web 3.0技术，聚焦于去中心化；而区块链6.0阶段则侧重于央行数字货币（CBDC）。

与区块链演化阶段相关的重要参数包括可扩展性、性能和去中心化。对这些参数的分析将我们的注意力引向对区块链共识算法的审视。目前，这一领域仍存在混乱，许多关于共识算法的质量、性能、评估等问题尚不明确。本章阐明了最常用的共识算法，并提出了一个用于评估其主要参数（如去中心化、可扩展性、安全性、公平性和能源效率）的框架。

我们未来的步骤包括在实际领域测试所提出的框架，并计划与该领域的关键利益相关者开展一项调查，以检验该框架。

## 参考文献

Anderson, S., Felici, M. and Littlewood, B. (Eds). (2003). Computer Safety, Reliability, and Security: 22nd International Conference… – Google Books, available at: https://books.google.com.cy/books?id=SaJqCQAAQBAJ&pg=PA243&lpg=PA243&dq=Honeywell+MMFCS&source=bl&ots=HwBGsdulutT&sig=ACfFU3U2hVwo_-3BArBVMOanu7WsLInvA8JQ&hl=en&sa=X&ved=2ahUKEwiZj_q35abqAhXSGewKHfb_D0EQ6AEwAHoECAkQAQ#v=onepage&q=Honeywell+MMFCS&f=false (accessed 29 June 2020).

Angrish, A., Craver, B., Hasan, M. and Starly, B. (2018). “A Case Study for Blockchain in Manufacturing: ‘FabRec’: A Prototype for Peer-to-Peer Network of Manufacturing Nodes.” *Procedia Manufacturing*, 26, pp. 1180–1192.

Baliga, A. (2017). Understanding Blockchain Consensus Models, Whitepaper, pp. 1–14.

Bentov, I., Lee, C., Mizrahi, A. and Rosenfeld, M. (2014). “Proof of Activity: Extending Bitcoin’s Proof of Work via Proof of Stake.” *ACM SIGMETRICS Performance Evaluation Review*, 42(3), 34–37.

Borge, M., Kokoris-Kogias, E., Jovanovic, P., Gasser, L., Gailly, N. and Ford, B. (2017). “Proof-of-Personhood: Redemocratizing Permissionless Cryptocurrencies”, *2017 IEEE European Symposium on Security and Privacy Workshops* (EuroS&PW), pp. 23–26.

Buterin, V. (2014). “A Next-Generation Smart Contract and Decentralized Application Platform.” *White Paper*, 3(37), pp. 2–1.

Chen, S. and Liu, C.C. (2017). “From Demand Response to Transactive Energy: State of the Art”, *Journal of Modern Power Systems and Clean Energy*, 5(1), 10–19. doi: 10.1007/s40565-016-0256-x.

Christodoulou, K., Iosif, E., Inglezakis, A. and Themistocleous, M. (2020). “Consensus Crash Testing: Exploring Ripple’s Decentralization Degree in Adversarial Environments”, *Future Internet*, MDPI AG, 12(3), 53. doi: 10.3390/fi12030053.

Compare, P. (2018). “What Is Proof of Weight? | CoinCodex.” Available at: https://coincodex.com/article/2617/what-is-proof-of-weight/ (accessed 30 September 2020).

Cunha, P. R., Soja, P. and Themistocleous, M. (2021). “Blockchain for Development: A Guiding Framework.” *Information Technology for Development*, 27(3), 417–438. https://www.tandfonline.com/doi/full/10.1080/02681102.2021.1935453

Cunha, P., Soja, P. and Themistocleous, M. (2020). “Blockchain for Development: Preliminary Insights from a Literature Review”, *In Proceedings of the twenty-sixth Americas Conference on Information Systems (AMCIS 2020)*, Virtual Conference, August 10–14, 2020. https://core.ac.uk/download/pdf/326836039.pdf

Deloitte. (2019). *Deloitte’s 2019 Global Blockchain Survey*.

Driscoll, K., Hall, B., Sivencrona, H. and Zumsteg, P. (2003). “Byzantine Fault Tolerance, from Theory to Reality.” In S. Anderson, M. Felici, and B. Littlewood (Eds), *Computer Safety, Reliability, and Security*. SAFECOMP 2003. Lecture Notes in Computer Science, vol 2788. Springer, Berlin, Heidelberg. DOI: 10.1007/978-3-540-39878-3_19.

Dziembowski, S. (2015). “Introduction to Cryptocurrencies”, *Proceedings of the 22nd ACM SIGSAC Conference on Computer and Communications Security*, Association for Computing Machinery, New York, NY, USA, pp. 1700–1701. doi: 10.1145/2810103.2812704.

Egorova, M. A. and Kozhevina, O. V. (2020). “Legal Issues of Using Blockchain Technology in the Issue and Circulation of Cryptocurrency.” In *Advances in Social Science, Education and Humanities Research*, volume 498, Proceedings of the XIV European-Asian Law Congress “The Value of Law” (EAC-LAW 2020).

Fu, X., Wang, H., Shi, P. and Mi, H. (2018). “PoPF: A Consensus Algorithm for JCLedger.” In *Proceedings – 12th IEEE International Symposium on Service-Oriented System Engineering, SOSE 2018 and 9th International Workshop on Joint Cloud Computing*, JCC 2018, Institute of Electrical and Electronics Engineers Inc., pp. 204–209, doi: 10.1109/SOSE.2018.00034.

Gilad, Y., Hemo, R., Micali, S., Vlachos, G. and Zeldovich, N. (2016). “Algorand”, Association for Computing Machinery (ACM), 51–68. doi: 10.1145/2932734.2932757.

Reis, G.A., Chang, J., Vachharajani, N., Rangan, R. and August, D.I., 2005, March. SWIFT: Software implemented fault tolerance. In *International Symposium on Code Generation and Optimization* (pp. 243–254). IEEE.

Hao, X., Yu, L., Zhiqiang, L., Zhen, L. and Dawu, G. (2018a). “Dynamic Practical Byzantine Fault Tolerance”, *2018 IEEE Conference on Communications and Network Security* (CNS), pp. 1–8.

Hao, X., Yu, L., Zhiqiang, L., Zhen, L. and Dawu, G. (2018b). “Dynamic Practical Byzantine Fault Tolerance”, *2018 IEEE Conference on Communications and Network Security*, CNS 2018, Institute of Electrical and Electronics Engineers Inc., doi: 10.1109/CNS.2018.8433150.

Harðarson, A. (2018). *Can Ripple Disrupt the Global Payments Market?* skemman.is.

Iredale, G. (2018). “Top 10 Blockchain Adoption Challenges | 101 Blockchains.” Available at: https://101blockchains.com/blockchain-adoption-challenges/#prettyPhoto (accessed 29 June 2020).

Hopkins, A.L., Smith, T.B. and Lala, J.H. (1978). “FTMP: A Highly Reliable Fault-tolerant Multiprocessor for Aircraft.” *Proceedings of the IEEE*, 66(10), 1221–1239.

Huang, D., Ma, X. and Zhang, S. (2018). “Performance Analysis of the Raft Consensus Algorithm for Private Blockchains”, *ArXiv*, 50(1), 172–181.
