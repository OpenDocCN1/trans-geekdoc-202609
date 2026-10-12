
# 传统发布-订阅与分布式替代方案

传统上，正如上所述，发布-订阅是使用客户端-服务器方法实现的，即发布和订阅客户端与托管在服务器上的代理进行通信（图 5.10）。在供应链背景下，可能有许多组织部署了物联网和其他数据流设备，并且需要以可信的方式共享数据流，这种中心化方法并不总是合适。一种提议的方法是用一组通过共识过程维护一致状态的分布式代理来取代单一的中心代理。一个能够提供此类能力的知名发布-订阅系统是 `Apache Kafka`，它包含一个名为 `Apache Zookeeper` 的组件，该组件提供共识，更具体地说是一种称为原子广播的能力，在多个节点之间进行，以便每个节点都保证以相同的顺序提供数据。`Apache Zookeeper` 以一种能够抵御少于 N/2 次崩溃故障（节点离开网络）的方式提供原子广播。一种更强形式的可信发布-订阅可以通过使用拜占庭容错共识协议连接由不同联盟成员托管的分布式传统发布-订阅代理来提供。`Trinity`（Ramachandran *et al*, 2018a）（图 5.10）就是这样一个最近提出并演示的系统，它将不同的 `MQTT` 发布-订阅代理连接到基于 `Tendermint` 拜占庭容错共识的许可区块链，以保证每个代理的订阅者都能看到来自发布者到任何/所有代理的相同经验证的信息流，且一致、顺序相同。`Trinity` 可以通过智能合约逻辑进行增强，允许单个节点根据物联网设备测量结果做出自主决策。

![图 5.10 带有区块链的分布式发布-订阅代理](img/M05NF010.jpg)

图 5.10 带有区块链的分布式发布-订阅代理

## 物联网数据的去中心化市场

# 流式数据支付协议与去中心化物联网市场

通过为数字数据和流启用微支付，区块链技术开始允许不同组织在供应链联盟中的提供方和消费方（可能是不同参与方）之间交换数据，其中数据可能跨越信任边界，并以无缝方式进行交换。

**流式数据支付协议（SDPP）**（图 1）是一个支付通道无关且分布式账本技术无关的应用层协议示例，它允许数据流的买方和卖方就该数据进行全面交易，采用定期微支付（使用加密货币或传统电子支付轨道），并利用区块链存储包括订单、发票和收据在内的记录（Radhakrishnan and Krishnamachari, 2018）。

**Ocean Protocol**（Ocean Protocol 白皮书）以及南加州大学的去中心化数据市场项目（Ramachandran *et al*, 2018b）等努力，提出了允许卖方使用智能合约发布注册表的方法，买方可浏览这些注册表以确定并获取其感兴趣的数据流。

此类去中心化物联网市场的其他要素，如动态定价、搜索以及使用代币策展注册表的去中心化推荐系统等，仍处于研究和开发的早期阶段。

### 图 1：流式数据支付协议

![流式数据支付协议](img/M05NF011.jpg)

*图 1：流式数据支付协议*

## 参考文献

*   Armbrust, M, Fox, A, Griffith, R, Joseph, A D, Katz, R, Konwinski, A and Zaharia, M (2010) A view of cloud computing, *Communications of the ACM*, 53 (4), pp 50–8

*   Augustin, A, Yi, J, Clausen, T and Townsley, W M (2016) A study of LoRa: Long range and low power networks for the Internet of Things, *Sensors*, 16 (9), p 1466

*   Banks, A and Gupta, R (2014) MQTT Version 3.1.1, *OASIS Standard*, 29

*   Baronti, P, Pillai, P, Chook, V W, Chessa, S, Gotta, A and Hu, Y F (2007) Wireless sensor networks: A survey on the state of the art and the 802.15.4 and ZigBee standards, *Computer Communications*, 30 (7), pp 1655–95

*   Centenaro, M, Vangelista, L, Zanella, A and Zorzi, M (2016) Long-range communications in unlicensed bands: The rising stars in the IoT and smart city scenarios, *IEEE Wireless Communications*, 23 (5), pp 60–7

*   Chen, J, Hu, K, Wang, Q, Sun, Y, Shi, Z and He, S (2017) Narrowband Internet of Things: Implementations and applications, *IEEE Internet of Things Journal*, 4 (6), pp 2309–14

*   Dada, A and Thiesse, F (2008) Sensor applications in the supply chain: The example of quality-based issuing of perishables. In *The Internet of Things*, Springer, Berlin, Heidelberg, pp 140–54

*   Dean, J and Ghemawat, S (2008) MapReduce: Simplified data processing on large clusters, *Communications of the ACM*, 51 (1), pp 107–13

*   EPCIS and CBV Implementation Guideline, GS-1, (2017). [Online] <https://www.gs1.org/docs/epc/EPCIS_Guideline.pdf> (archived at <https://perma.cc/G4TN-UCB5>)

*   Erl, T (2005) *Service-Oriented Architecture*, volume 8, Pearson, India

*   Fielding, R T and Taylor, R N (2002) Principled design of the modern Web architecture, *ACM Transactions on Internet Technology (TOIT)*, 2 (2), pp 115–50

*   Gao, X, Xiang, Z, Wang, H, Shen, J, Huang, J and Song, S (2004) An approach to security and privacy of RFID system for supply chain. In *E-Commerce Technology for Dynamic E-Business*, 2004, IEEE International Conference, September, pp 164–68

*   Gomez, C, Oller, J and Paradells, J (2012) Overview and evaluation of Bluetooth low energy: An emerging low-power wireless technology, *Sensors*, 12 (9), 11734–53

*   Han, J, Haihong, E, Le, G and Du, J (2011) Survey on NoSQL database. In *Pervasive computing and applications (ICPCA)*, 2011 6th IEEE international conference, October, pp 363–66

*   Hightower, J and Borriello, G (2001) Location systems for ubiquitous computing, *Computer*, 34 (8), pp 57–66

*   Jagadeesan, N A and Krishnamachari, B (2017) A unifying Bayesian optimization framework for radio frequency localization. *IEEE Transactions on Cognitive Communications and Networking*, 4 (1), pp 135–45

*   Kelleher, J D, Mac Namee, B and D’Arcy, A (2015) *Fundamentals of Machine Learning for Predictive Data Analytics: Algorithms, worked examples, and case studies*, MIT Press, Cambridge, MA

*   Keshav, S (1997) *An Engineering Approach to Computer Networking: ATM networks, the internet, and the telephone network*, volume 1, Addison-Wesley, Reading

*   Lai, Y L and Cheng, J (2014) A cloud-storage RFID location tracking system, *IEEE Transactions on Magnetics*, 50 (7), pp 1–4

*   Mehrabi, N, Morstatter, F, Saxena, N, Lerman, K and Galstyan, A (2021) A survey on bias and fairness in machine learning. *ACM Computing Surveys (CSUR)*, 54 (6), 1–35

*   Misra, P and Enge, P (2006) *Global Positioning System: Signals, measurements and performance second edition*, Ganga-Jamuna Press

*   Müller, A C and Guido, S (2016) *Introduction to Machine Learning with Python: A guide for data scientists*, O’Reilly Media, Inc, Sebastopol, CA

*   Ocean Protocol Whitepaper: *Tools for the Web 3 Data Economy* [Online] <https://oceanprotocol.com/tech-whitepaper.pdf> (archived at <https://perma.cc/385V-B5V3>)

*   Pang, Z, Chen, Q, Han, W and Zheng, L (2015) Value-centric design of the Internet-of-Things solution for food supply chain: Value creation, sensor portfolio and information fusion, *Information Systems Frontiers*, 17 (2), pp 289–319

*   Provost, F and Fawcett, T (2013) Data science and its relationship to big data and data-driven decision making, *Big Data*, 1 (1), pp 51–9

*   Radhakrishnan, R and Krishnamachari, B (2018) Streaming data payment protocol (SDPP) for the Internet of Things, *Proceedings of the 1st International Workshop on Blockchain for the Internet of Things* (BIoT), held in conjunction with IEEE Blockchain, Halifax, Canada

*   Ramachandran, G, Wright, K-L, Zheng, L, Naveed, M, Krishnamachari, B and Dhaliwal, J, (2018a) Trinity: A Byzantine fault-tolerant distributed publish-subscribe system with immutable blockchain-based persistence, IEEE International Conference on Blockchain and Cryptocurrency (ICBC), Seoul, May 2019.

*   Ramachandran, G S, Radhakrishnan, R and Krishnamachari, B (2018b) Towards a decentralized data marketplace for smart cities. Invited paper at 1st International Workshop on Blockchain Enabled Sustainable Smart Cities (BLESS 2018), Kansas City, MO, USA, held in conjunction with the 4th IEEE Annual International Smart Cities Conference (ISC2)

*   Rose, S, Borchert, O, Mitchell, S and Connelly, S (2020) *Zero trust architecture* (No. NIST Special Publication (SP) 800-207), National Institute of Standards and Technology

*   Sornin, N, Luis, M, Eirich, T, Kramp, T and Hersent, O (2015) *Lorawan Specification*, LoRa Alliance, Fremont, CA

*   Unemyr, M (2017) *The Internet of Things – The Next Industrial Revolution Has Begun: How IoT, big data, predictive analytics, machine learning and AI will change our lives forever*, Amazon Digital Services, November

*   Zaharia, M, Xin, R S, Wendell, P, Das, T, Armbrust, M, Dave, A and Ghodsi, A (2016) Apache spark: A unified engine for big data processing, *Communications of the ACM*, 59 (11), pp 56–65

# Deliver 联盟演变与数字码头愿景

自 2019 年 5 月本书出版以来，Deliver 经历了大规模转型，其中包括两家创始公司退出联盟（ABN-AMRO 和 Samsung SDS）。随着仅剩鹿特丹港一家成员，关键问题是 Deliver 是否以及如何继续下去。然而，在我们深入探讨现在称为 Naviporta^(1) 的愿景、原则和架构之前，我们简要回顾一下 2019 年 2 月至 2021 年 12 月期间发生的事件。

2019 年 2 月，联盟完成了一个概念验证，成功实现了集装箱从门到门的全程跟踪追溯，并在釜山港与位于荷兰蒂尔堡的 Samsung SDS 仓库（鹿特丹港，2019）之间实现了即时融资。该 PoC 证明，通过以以太坊公链作为通用参考框架，可以实现运行不同区块链协议的两个不同区块链生态系统之间的互操作性。

该 PoC 随后扩展至其他贸易航线。2019 年 5 月至 2020 年 4 月期间，追踪了从中国以及美国发往荷兰的各类出口货物。此外，原始 PoC 的功能进一步扩展，以支持这些额外的试点；然而，从技术角度来看，重点是敲定平台首个企业级发布版本的未来状态架构（FSA）。此延长试点阶段的主要目标是展示价值验证（PoV）。特别是，重点在于确定 Deliver 平台以及平台上的生产者和消费者的商业案例。这是通过对现有流程进行广泛分析来完成的，特别是发货处理时间和成本，以及不合格和不合规的成本。这种方法植根于本书第 2 章提出的框架。虽然在此阶段结束时已成功展示了价值验证，但某些外部因素对两个联盟成员 ABN-AMRO 和 Samsung SDS 发生了重大变化。对于前者，这一决定是由几家大宗商品贸易商的倒闭引发的，在冠状病毒危机后发现了欺诈实例（Reuters，2020），导致 ABN-AMRO 完全退出大宗商品和贸易融资领域，而这正是该平台的预期用途。Samsung SDS 退出的决定是由于战略重新调整，优先考虑其 Cello 平台的进一步开发。

## 数字码头的理由
