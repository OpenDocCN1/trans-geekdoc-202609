

### 图 19. 块详细信息

| 属性 | 值 |
|---|---|
| 通道名称： | mychannel |
| 块编号 | 19 |
| 创建时间 | 2019-02-15T14:31:50.559Z |
| 交易数量 | 1 |
| 块哈希 | c5601c3092dad2fe5e6ca3a996b05baed3f89e37126f8e5124e8c3ed1b139f0f |
| 数据哈希 | 9c7b0faae5d33ab080ac1e6110e17b0365f880d07227a73b405cab688d6d468 |
| 预哈希 | 7c44b2fc000ac8abe5795ed767ec17632ebb77a7629673b6f572bcafc6044597 |

### 图 20. 交易详细信息

| 属性 | 值 |
|---|---|
| 交易 ID： | e3866f332cfd7bb9996ad597772fb3b21d84f8fd2c2782266e1340a9e143af5e7 |
| 验证代码： | VALID |
| 有效载荷提案哈希： | e324fc0e592098598fa036618d5df06aa419621a9519e14a6edd1139e5f3f7c |
| 创建者 MSP： | Org2MSP |
| 背书人： | ["Org1MSP","Org1MSP","Org2MSP","Org2MSP"] |
| 链码名称： | trade-network |
| 类型： | ENDORSER_TRANSACTION |
| 时间： | 2019-02-15T14:31:50.559Z |
| 读取： | root: [] 2 items<br>&gt; 0: {} 2 keys<br>&gt; 1: {} 2 keys |
| 写入： | root: [] 2 items<br>&gt; 0: {} 2 keys<br>&gt; 1: {} 2 keys |

本章利用 Hyperledger Fabric 实现了一个供应链用例，并阐述了与食品供应行业、可追溯性、物品召回、交易拥塞、监管合规、必要标准等相关的从农场到餐桌流程。此外，作者强调了实现复杂供应链所需的改进，包括连接位于不同国家的监管机构、与 IoT 系统集成、管理冗余数据以及管理大量交易。

值得注意的是，当前的区块链架构和键值数据存储并不直接支持资产的端到端可追溯性、物品召回，且缺乏必要的标准。因此，开发人员应当参与并开发必要的工作流。作者提出了一种私有通道概念，以在区块链网络中定位监管机构，最大限度地减少数据冗余并确保审计。然而，在实时复杂的区块链应用中，仍需持续改进以管理块拥塞、交易验证和补偿管理。

## 致谢

这份出版物部分源自爱尔兰科学基金会（SFI）和爱尔兰政府农业、食品与海洋部在资助编号 SFI 16/RC/3835（VistaMilk）下提供的研究资助，以及 SFI 在资助编号 SFI 12/RC/2289_P2（Insight）下提供的研究资助，两项资助均由欧洲区域发展基金共同资助。

## 参考文献

- Benhamouda, F., Halevi, S., & Halevi, T. (2018). 基于安全多方计算在 Hyperledger Fabric 上支持私有数据。载于 2018 年 IEEE 云工程国际会议（IC2E）。Orlando, FL: IEEE. 10.1109/IC2E.2018.00069
- Bitcoin. (2020). Bitcoin 开发者。检索自 学习比特币并开始构建基于比特币的应用程序：https://developer.bitcoin.org/
- Composer. (2020 年 6 月 23 日). 典型的 Hyperledger Composer 解决方案架构。检索自 Hyperledger Composer：https://hyperledger.github.io/composer/v0.19/introduction/solution-architecture
- Consensys. (2020). 区块链用例 - 供应链管理中的区块链。检索自 https://consensys.net/blockchain-use-cases/supply-chain-management/
- Cooper, M. C., Lambert, D. M., & Pagh, J. D. (1997). 供应链管理：不仅仅是物流的新名称。国际物流管理杂志, 8(1), 1–14. doi:10.1108/09574099710805556
- Davor, D., & Domagoj, S. (2018). 供应链中的区块链应用。SMART 供应网络, 21–46.
- Esteban Koberg, A. L. (2018). 全球供应链中可持续供应链管理的系统综述。清洁生产杂志, 1084–1098.
- Ethereum. (2020 年 6 月 23 日). Ethereum 是一个面向去中心化应用的全球开源平台。检索自 ethereum.org：https://ethereum.org/
- Gao, Z., Xu, L., Chen, L., Zhao, X., Lu, Y., & Shi, W. (2018). CoC: 基于统一分布式账本的供应链管理系统。计算机科学与技术杂志, 237–248.
- Hyperledger. (2020a, 6 月 23 日). Hyperledger Fabric。检索自 Hyperledger：https://www.hyperledger.org/use/fabric
- Hyperledger. (2020b, 6 月 23 日). 私有数据。检索自 Hyperledger Fabric：https://hyperledger-fabric.readthedocs.io/en/release-2.0/private-data/private-data.html
- Kenton, W. (2020 年 6 月 24 日). Hyperledger Fabric。检索自 Investopedia：https://www.investopedia.com/terms/h/hyperledger-fabric.asp
- Ko, K., Lee, C., Jeong, T., & Hong, J. W.-K. (2018). 基于 RPC 的区块链监控代理设计。载于 2018 年信息通信技术融合国际会议（ICTC）。韩国济州: IEEE. 10.1109/ICTC.2018.8539456
- Kshetri, N. (2018). 区块链在实现关键供应链管理目标中的作用。国际信息管理杂志, 39, 80–89. doi:10.1016/j.ijinfomgt.2017.12.005
- Li, W., Sforzin, A., Fedorov, S., & Karame, G. (2017). 面向可扩展和私有工业区块链。载于 BCC '17: ACM 区块链、加密货币和合约研讨会论文集（第 9-14 页）。ACM. 10.1145/3055518.3055531
- Litecoin. (2020 年 6 月 23 日). 用于支付的加密货币：基于区块链技术。检索自 https://litecoin.org/
- Martin, S. (2017). 食品可追溯性和控制的区块链用例。瑞典郡议会和地区: Kairos Future。检索自 Kairos Future: https://tinyurl.com/y7hh6nup
- Meyvaert, E. (2020 年 6 月 22 日). Siemens Mindsphere 和 SettleMint 的分布式中间件：完美匹配！。检索自 Medium: https://updates.settlemint.io/siemens-mindsphere-and-settlemints-distributed-middleware-the-perfect-match-b1ce77335c09
- Modi, R. (2018). Solidity 编程精要。Packt 出版社。
- Nakamoto, S. (2008). Bitcoin: 一种点对点电子现金系统。www.bitcoin.org
- Perboli, G., Musso, S., & Rosano, M. (2018). 物流和供应链中的区块链：设计现实世界用例的精益方法。IEEE Access: 实用创新, 开放解决方案, 6, 62018–62028. doi:10.1109/ACCESS.2018.2875782
- Quorum. (2020 年 6 月 23 日). 面向企业的经过验证的区块链解决方案。检索自 与 Quorum 共同发展: https://www.goquorum.com/
- Siemens. (2019). 可信可追溯性 - 区块链和物联网。德国纽伦堡: 西门子 AG 2019。检索自 https://assets.new.siemens.com/siemens/assets/api/uuid:de496ba4-0081-48f5-965b-4963879b2d43/version:1557493248/vrfb-b10033-00-7600sbbblockchainfb-144.pdf
- Thummavet, P. (2020 年 6 月 22 日). 揭秘 Hyperledger Fabric: Fabric 架构。检索自 Medium: https://tinyurl.com/y9yn33k5
- Westerkamp, M., Victor, F., & Küpper, A. (2018). 基于区块链的供应链可追溯性：代币配方模型制造流程。载于 IEEE/ACM 网络、物理和社会计算国际会议（CPSCom）。加拿大哈利法克斯: IEEE Xplore. 10.1109/Cybermatics_2018.2018.00267
- Yiannas, F. (2018). 由区块链驱动的食品透明度新时代。创新: 技术, 治理, 全球化, 12(1-2), 46–56. doi:10.1162/inov_a_00266
- Zheng, Z., Xie, S., Dai, H., Chen, X., & Wang, H. (2017). 区块链技术概述：架构、共识和未来趋势。载于 2017 年 IEEE 大数据国际大会（BigData Congress）。檀香山, HI: IEEE. 10.1109/BigDataCongress.2017.85

## 延伸阅读

- Ahamed, N. N. K. P, S. P. Anandaraj 和 V. R. 使用区块链的海鲜供应链管理。第六届先进计算与通信系统国际会议（ICACCS）, 2020, pp. 473-476.
- Du, M., Chen, Q., Xiao, J., Yang, H., & Ma, X. (2020). 使用区块链的供应链金融创新。IEEE 工程管理期刊, doi:10.1109/TEM.2020.2971858
- Hastig, G. M., & Sodhi, M. S. (2019). 用于供应链可追溯性的区块链：业务要求和关键成功因素。生产与运营管理, 935–954.
- Jabbar, A., & Dani, S. (2020). 调查区块链环境中交易成本与计算成本之间的联系。国际生产研究杂志, 58(11), 3423–3436. doi:10.1080/00207543.2020.1754487
- Li, Z., Guo, H., & Ali Vatankhah Barenji, W. M. (2020). 基于区块链、LSTM 和层次分析法的供应链网络可持续生产能力评价机制。国际生产研究杂志, 58(24), 1–21. doi:10.1080/00207543.2020.1740342
- Subramanian, N, Chaudhuri, A, & Kayikci, Y. (2020). 食品供应链中的区块链应用。区块链与供应链物流, 21-29. Springer.
- Subramanian, N, Chaudhuri, A, & Kayikci, Y. (2020). 医疗保健供应链中的区块链应用。区块链与供应链物流, 31-38. Springer.

## 关键术语和定义

- **数字孪生**: 数字孪生是指潜在和实际物理资产、流程、人员、地点、系统和设备的数字副本，可用于各种目的。
- **从农场到餐桌**: 该阶段涉及食品的种植、加工和消费——即从供应商到客户餐桌的整个食品链条。
- **物联网 (IoT)**: 物联网是一套相互关联的计算设备、机械和数字机器系统，这些设备拥有唯一标识符，并能够在无需人与人或人与计算机交互的情况下通过网络传输数据。
- **矿工**: 矿工验证新的区块链交易并将其记录在区块链上。矿工竞争解决基于加密哈希算法的困难数学问题。
- **对等 (P2P)**: P2P 计算是一种分布式应用架构，它在对等体之间划分任务。对等体在应用程序中享有同等权限。
- **REST API**: 表述性状态转移 (REST) 是一种用于创建 Web 服务的软件架构风格，定义了一组约束。应用程序编程接口 (API) 定义接口函数。
- **射频识别 (RFID)**: 射频识别 (RFID) 利用电磁场自动识别和跟踪附加到对象上的标签。

