

# 第 15 章：去中心化安全推文平台的实现

## 推文应用的安全性

**作者：**
- Sumathi Pawar，信息科学与工程，NMAMIT，Nitte，印度
- K. Suma，曼加罗尔理工与管理学院，Moodabidri，印度
- Ankitha P.，信息科学与工程，NMAMIT，Nitte，印度
- Vandana B. S.，信息科学与工程，NMAMIT，Nitte，印度
- RajaLakshmi Samaga，信息科学与工程，NMAMIT，Nitte，印度

## 摘要

去中心化安全推文平台利用区块链技术将控制权和数据分布在参与者网络中，挑战了中心化模式。它提供了增强的隐私、减少的内容操纵，以及对用户内容中心化控制的抵抗力。该系统代表了一个去中心化的推文社交媒体平台，旨在为用户提供一个既安全又以透明为特征的通信环境。通过集成智能合约，用户可以直接且安全地进行交易，而无需中介。`ReactJS` 赋能了响应式且用户友好的界面，促进用户间的实时交互，以创建一个去中心化社交媒体平台，将安全性和透明度提升至前所未有的水平。区块链技术确保数据被安全存储、不可篡改且透明。所提系统使用户能够发布推文、关注其他用户、点赞和评论帖子，并进行实时消息传递。本文还展示了该系统的实现。

## 引言

本文旨在利用区块链 Web 3.0 开发一个安全的推文应用，采用 `Solidity`、`Next.js` 和 `Sanity.io`。该系统模仿 Twitter 的功能，为推文提供一个安全的平台。它将控制权和数据所有权重新分配给用户，避免了日常社交媒体中审查和数据泄露的风险。去中心化系统利用分布式账本技术、智能合约和点对点网络，确保以用户为中心的数字社交媒体应用。前端使用 `Next.js` 构建，并采用 `Tailwind CSS` 进行样式设计。此外，还使用 `Solidity` 创建了自定义智能合约。正如 Zheng 等人（2017）所指出的，区块链作为加密货币的主要网络支持该应用，而 Twitter 仍然是加密货币爱好者通过短帖子分享想法的热门社交媒体平台。

使用区块链为推文应用创建智能合约涉及使用 `Solidity` 编写合约，`Solidity` 是以太坊的编程语言。实现部分给出了一个基本智能合约的示例，该合约使用户能够发布和检索推文。该合约包含发布和查看推文的基本功能。根据 Valeti Deepika 和 Lalitha Bhaskari（2020）的研究，`Truffle` 被用于在 `Ubuntu (Debian)` 操作系统上部署智能合约。与标准 Twitter 应用相比，该项目提供了增强的安全性。智能合约作为可编程的数字协议，改善了通信并促进了长期资产追踪。它们对于维护与消费者的关系也很有价值。

在该应用中，创建了一个 `Web3 API` 实例以连接到本地区块链网络。该系统还使用 `Web3 API` 通过创建合约实例并调用其方法来与智能合约交互，以创建推文、点赞推文和检索推文。

`Web3.js` 是一个 JavaScript 库，旨在促进与以太坊区块链的交互。Sumathi 和 Manjula（2023）强调了 `Web3.js` 提供的开源 API，用于连接区块链、发起交易和与智能合约交互。`Ethers.js` 是另一个允许与以太坊区块链交互的 JavaScript 库。与 `Web3.js` 相比，它提供了更简单的 API，并对 `TypeScript` 有更好的支持。

`IPFS`（星际文件系统）是一个用于文件的分布式存储系统，支持在计算机分布式网络中存储和共享。它提供了一个 API，便于从 `IPFS` 网络存储和检索文件。`Solidity` 是在以太坊区块链上编写智能合约所需的编程语言。它用于定义应用的业务逻辑，并在 `以太坊虚拟机 (EVM)` 上执行。该应用使用 `Solidity API` 来定义代表推文的推文结构智能合约，并提供创建推文、点赞推文和检索推文的方法。

`Open Zeppelin` 是一个可复用智能合约库，为应用提供安全性和模块化。它提供从简单的所有权合约到复杂的多签名钱包等一系列智能合约。该应用使用 `React-Bootstrap` 创建表单、按钮和列表组等 UI 组件。

在本文中，第 2 节讨论文献综述，第 3 和 4 节涵盖保护该应用的各种方法，第 4 和 5 节侧重于实现和结果。

## 文献综述

去中心化推文系统的目标是应对中心化平台带来的算法偏见、隐私问题和数据泄露（Marx & Cheong, 2023）。社交媒体平台的去中心化在采用、控制、隐私、运营和安全方面带来了新的困难。去中心化通过将信任从封闭的企业规则转移到开放的区块链技术，为消费者和内容创作者提供了安全性和稳定性（Bhusare et al., 2023）。由于缺乏单一的数据聚合点，去中心化系统失去了中心方提供的部分隐私保护，这增加了通过元数据进行隐私入侵的风险（Greschbach et al., 2012）。

## 参考文献

Tournier, J., Lesueur, F., Le Moue¨l, F., Guyon, L., & Ben-Hassine, H. (2021). A survey of IoT protocols and their security issues through the lens of a generic IoT stack. *Internet of Things: Engineering Cyber Physical Human Systems*, 16, 100264. DOI: [10.1016/j.iot.2020.100264](http://dx.doi.org/10.1016/j.iot.2020.100264)

Venkatraman, S., & Overmars, A. (2020, November). IoT Authentication and Security Challenges. In *Proceedings of the 3rd International Conference on Research in Applied Science*, Munich, Germany (pp. 6-8).

Wang, N., Wang, P., Alipour-Fanid, A., Jiao, L., & Zeng, K. (2019). Physical-layer security of 5G wireless networks for IoT: Challenges and opportunities. *IEEE Internet of Things Journal*, 6(5), 8169–8181. DOI: [10.1109/JIOT.2019.2927379](http://dx.doi.org/10.1109/JIOT.2019.2927379)

Yu, D., Zhang, L., Chen, Y., Ma, Y., & Chen, J. (2020). Large-scale IoT devices firmware identification based on weak password. *IEEE Access: Practical Innovations, Open Solutions*, 8, 7981–7992. DOI: [10.1109/ACCESS.2020.2964646](http://dx.doi.org/10.1109/ACCESS.2020.2964646)

Yu, M., Zhuge, J., Cao, M., Shi, Z., & Jiang, L. (2020). A survey of security vulnerability analysis, discovery, detection, and mitigation on IoT devices. *Future Internet*, 12(2), 27. DOI: [10.3390/fi12020027](http://dx.doi.org/10.3390/fi12020027)

Yugha, R., & Chithra, S. (2020). A survey on technologies and security protocols: Reference for future generation IoT. *Journal of Network and Computer Applications*, 169, 102763. DOI: [10.1016/j.jnca.2020.102763](http://dx.doi.org/10.1016/j.jnca.2020.102763)

