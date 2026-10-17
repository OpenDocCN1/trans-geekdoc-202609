
We require a safe, quick, and dependable foundation in order to build a workflow management application. All of our application’s needs are satisfied by blockchain. Additionally, we chose the proof-of-authority consensus for the blockchain since it complemented our application model the best. However, the first blockchain network we chose, called Ethereum, switched from proof-of-work consensus in its main network to proof-of-stake consensus in all of its test networks. The hyperledger fabric was then introduced to us. Given that identity management is our primary requirement, Ethereum and hyperledger fabric have various methods and capabilities.

### Architecture

Smart contracts, which are self-executing contracts between buyers and sellers that are directly programmed into the system, are made possible by Ethereum. Public-private key cryptography is used for user administration, which is account-based. To sign transactions and communicate with the network, users generate a set of public and private keys. Each Ethereum account is identified by a public key, or a hash of the public key, known as an address, which may be accessed with the associated private key. Users are responsible for maintaining their own keys, which are often kept in a wallet or software client.

A blockchain platform for private and authorized contexts is called hyperledger fabric. Its default option makes use of the PBFT consensus mechanism. However, because to hyperledger fabric’s adaptability, it may be customized, including by altering the consensus algorithm as necessary. With their own distinct identities and rights, it enables many organizations to take part in a blockchain network. A membership service provider (`MSP`) manages users in hyperledger fabric. The tasks of managing identities, verifying users, and allowing access to resources fall under the purview of an `MSP`. The `MSP` for each organization taking part in a hyperledger fabric network is in charge of maintaining the identities of the users inside that organization. Cryptographic keys are given to users and held in their individual wallets where they are used to sign transactions.

### Data security and integrity

For network security, Ethereum employs a public key cryptography method. To validate transactions and stop unauthorized access to the network, it employs a digital signature. Additionally, Ethereum stores transaction data in a Merkle tree data structure, guaranteeing data integrity. However, as Ethereum is a public blockchain, anyone can examine all the data.

All network participants in the hyperledger fabric network are recognized and validated using a permissioned mechanism. It makes use of a distinctive identity system that makes it possible to set access control on a per-user basis. By limiting network access to just those that is permitted, this method improves data security. To protect data from prying eyes, there are solutions.

### Cost

A specific number of ether is required for the deployment and interaction of contracts on the Ethereum public network. The price of ether is 1,878.50 US dollars (USD) or 1,54,458.59 Indian rupees (INR) at the time of writing, although this value is subject to daily change. A “gas fee” is another charge users on the network must make in order for their transactions to be successful. Gas costs 1.75 USD or 142 INR at this moment in time. The accompanying charges for each transaction can accumulate to a significant amount over time.

However, since the hyperledger fabric network is set up on a server owned by our organization, transaction fees are not required. However, it is important to consider the costs of upkeep.

## Summary

While Ethereum is a public blockchain platform appropriate for decentralized apps and coin creation utilizing smart contracts. Hyperledger fabric is made for usage in business applications that need authenticity, confidentiality, integrity, and scalability. Businesses who want a private blockchain network for secure transactions and data sharing can use it because of its permissioned approach. For identity management, hyperledger fabric is a fantastic alternative and is used in sectors including finance, healthcare, and supply chain management. As a result, we developed a blockchain-based workflow management application using hyperledger fabric. The purpose of this program is to facilitate a simple and secure workflow among network users.

## Building the prototype

### Basic design

原型应用旨在创建一个工作流程管理系统，用于前文提到的案例研究。该应用将致力于简化学术机构的工作流程，实现更快且安全的文档批准。

该应用需要拥有一个易于使用的交互式前端。前端充当网络与用户之间的通信门户，使用户能够发送交易。此外，该应用还需要一个后端服务器，用于路由用户的所有请求，连接前端、数据库和网络。随后，需要一个数据库来存储所有请求和待批准的事项。文档还会进行哈希处理，获取其哈希值。最终，采用 Hyperledger Fabric 网络用于验证并存储文档的哈希值，通过发送交易实现。

该应用的核心工作流程如 Figure 41.2 所示。需要获取文档签名的用户（例如学生）首先需在应用中上传所需的文件。应用随后等待签署人（例如教师）批准。一旦签署人批准，程序即存储文件，并向网络广播文件的哈希值和签名。为便于后续检索，网络会将其与时间戳以及对应的键一起存储。

![Figure 41.2 Prototype application basic design](img/fig41_2_B.jpg)

Figure 41.2 Prototype application basic design

### 使用的工具

本应用使用 `React.js` 和 `node.js` 作为前端和后端框架，分别。`MongoDB` 被选为用于存储信息的数据库。采用 Hyperledger Fabric 测试网络包用于部署测试网络，以便在我们的原型上进行开发。用于用户间交互的链码编写在 `Golang` 中。

### 部署测试网络

Hyperledger 的网站公开提供了 fabric 示例、二进制文件和 Docker 镜像。我们下载并运行该网络，并启动 peer、client 和组织节点的 Docker 容器。随后，我们在两个组织之间创建一个通道以实现通信。此外，我们还利用 fabric ca-client 功能创建包含每个用户私钥和公钥的个人钱包。这些钱包后续将用于签署和验证文档。

### 配置链码

链码负责管理账本状态。它通过我们的应用提交的交易来实现此功能。除了其他用于与网络交互的函数外，本应用在链码中使用 `PutState` 函数来存储提交的文档的签名和时间戳。

> “`APIstub.PutState(args[0], dataInBytes)`”

其中，`dataInBytes` 是一个结构体，包含签名和时间戳；`args[0]` 是一个唯一键，后续用于检索签名。

### 开发应用

应用的前端采用 `React.js` 的多种库，使其简洁、直观且易用。当用户提交文档用于批准时，文档会被存储在存储中，相关信息则存储在 `MongoDB` 数据库中。在网络和链码就位后，服务器在文档获批后向网络发送必要数据。网络随后存储必要数据，以便后续验证时检索。

## 结论

总之，本研究强调工作流程管理对于维持组织的效能和效率至关重要。显然，工作流程管理对于自动化流程、减少人工操作、降低人为错误以及整体提升生产力具有关键作用。

现有的解决方案，往往基于纸质或依赖在线应用，必须在技术上进行升级，以完全满足当前期望。鉴于区块链技术在成本效益、可扩展性和安全性方面满足重要标准，被视为前景广阔的解决方案。其固有的公钥基数字签名、密码散列函数以及去中心化架构基础，促使这种契合。

我们作为调查的一部分，开发了基于 Hyperledger Fabric 的原型解决方案。通过支持可配置的共识流程，这一设计为我们的工作流程管理系统提供了更大的灵活性，并简化了在其受控框架内将公钥与身份关联。

其影响范围超出此特定情境，表明类似的区块链基于系统可用于满足各类组织需求。这尤其适用于当对公钥基数字验证、强健且可扩展的解决方案的需求与分布式架构原则相碰撞时。

将区块链技术纳入工作流程管理，为在当前重塑组织环境的技术发展背景下实现操作效率提供了实际途径。随着组织对运营改进、安全增强和成本节约的强烈动机，探索和部署基于区块链的解决方案具有强大的吸引力。本研究为工作流程管理的持续创新与质量提升贡献了相关讨论。

## 参考文献

* Reijers, H. A., Vanderfeesten, I., and Van Der Aalst, (2016). The effectiveness of workflow management systems: A longitudinal study. Int. J. Inform. Manag., 36(1), 126–141. [`doi.org/10.1016/J.IJINFOMGT.2015.08.003`](https://doi.org/10.1016/J.IJINFOMGT.2015.08.003).

* Wu, D. T. Y., Barrick, L., Ozkaynak, M., Blondon, K., and Zheng, K. (2022). Principles for designing and developing a workflow monitoring tool to enable and enhance clinical workflow automation. Appl. Clin. Inform., 13(1), 132–138.

* Shrabani, S., Karforma, S., Bose, R., Roy, S., Djebali, S., and Bhattacharyya, D. (2024). Enhancing identity and access management using hyperledger fabric and OAuth 2.0: A blockchain-based approach for security and scalability for healthcare industry. Internet of Things Cyber-Phy. Sys., 4.

* Fridgen, G, Urbach, N., Radszuwill, S., and Utz, L. (2018). Cross-organizational workflow management using blockchain technology – towards applicability, auditability, and automation. Proc. Ann. Hawaii Int. Conf. Sys. Sci. 2018, 3507–3516. doi: [10.24251/HICSS.2018.444](http://dx.doi.org/10.24251/HICSS.2018.444).

* Almadani, Mwaheb S., Suhair Alotaibi, Hada Alsobhi, Omar K. Hussain, and Farookh Khadeer Hussain. (2023). Blockchain-based multi-factor authentication: A systematic literature review. Internet of Things: 100844, 23, [`doi.org/10.1016/j.iot.2023.100844`](https://doi.org/10.1016/j.iot.2023.100844).

* Hukkinen, Taneli, Juri Mattila, and Timo Seppälä. (2017). Distributed workflow management with smart contracts. No. 78. ETLA Report.
