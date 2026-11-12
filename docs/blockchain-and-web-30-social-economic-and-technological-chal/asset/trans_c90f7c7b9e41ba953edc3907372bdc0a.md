

[SM16] Guido Salvaneschi 和 Mira Mezini. 带有响应式检查器的响应式编程调试. 软件工程伴随会议第 38 届国际会议论文集, ICSE ’16, 第 728–730 页. ACM Press, 纽约, NY, 美国, 2016.

[SR14] Venkatesh Srinivasan 和 Thomas Reps. 从机器代码中恢复类层次结构和组成关系, 第 61–84 页. Springer Berlin Heidelberg, 柏林, 海德堡, 2014.

[TDMO18] R. Tonelli, G. Destefanis, M. Marchesi 和 M. Ortu. 智能合约软件度量: 一项初步研究. ArXiv e-prints, 2018 年 2 月.

[TNM08] Ewan Tempero, James Noble 和 Hayden Melton. Java 程序如何使用继承? Java 软件中继承的实证研究. 在 ECOOP ’08: 第 22 届面向对象编程欧洲会议论文集, 第 667–691 页. Springer-Verlag, 柏林, 海德堡, 2008.

[TVI+18] S. Tikhomirov, E. Voskresenskaya, I. Ivanitskiy, R. Takhaviev, E. Marchenko 和 Y. Alexandrov. Smartcheck: 以太坊智能合约的静态分析. 在 2018 IEEE/ACM 第 1 届区块链软件工程新兴趋势国际研讨会 (WETSEB) 上, 第 9–16 页, 2018 年 5 月.

## 使用 Fabric Hyperledger 区块链技术管理 CRM

Dario Puligheddu, Roberto Tonelli 和 Michele Marchesi

### 引言

新区块链技术提供的可能性不仅涉及金融应用，而且由于新一代支持智能合约和 dApp 开发的区块链的出现，目前可以跨越至目前为止仅限于软件系统的所有应用。

直到几年前，区块链一词仅与比特币相关联，比特币是由研究人员中本聪 (Nakamoto, 比特币白皮书) 创建的去中心化加密货币系统，他提供了方案和软件 (https://github.com/bitcoin/bitcoin)，用于在互联网上运行区块链地址所有者之间的虚拟货币交换，利用通过数字密码学（如数字签名和哈希）获得的最新结果。

尽管该项目最初的目的是为互联网用户发明并提供一个不受中央机构控制的无需信任现金系统，但最终结果是一种新的软件技术，它更广泛地实现了跨网络的信息管理和交换，并能够授予信息管理所需和期望的透明性、不可篡改性、匿名性、完整性及其他受欢迎的功能。

自那以后，区块链技术迅速发展和改进，现在有用于最不同目的的各种区块链品牌和解决方案。最主要的改进肯定是在区块链环境中运行原生计算机程序的可能性，即所谓的智能合约，它们是部署在区块链上的软件代码片段，并由于运行在图灵完备、使用区块链相关指令集的虚拟机上，从而允许执行普通计算机执行的任何类型的计算。典型的著名示例是以太坊和超级账本区块链系统（以太坊白皮书；超级账本白皮书）。前者在无许可公共区块链上运行（即使可以设置私有区块链），支持一种加密货币（以太币 Ether）和一种用于开发智能合约的编程语言 Solidity，是比特币之后第二流行的区块链。后者在明确设计用于支持商业组织管理其自身业务逻辑的许可私有区块链上运行，提供决定所需区块链设置的选项，并使用各种编程语言（主要是 GO (https://golang.org/)）运行“链码”（智能合约的等价物）。

这个新场景打开了利用之前报告过的区块链固有的信息透明性、不可篡改性、匿名性和完整性特性来开发去中心化软件应用的可能性。然而，区块链技术并非只有好消息；主要由于它还处于早期阶段，不同研究领域（如软件工程（Ortu, Destefanis, Swift 和 Marchesi, 2016; Ortu, Destefanis, Kassab 和 Marchesi, 2015; Ortu, Destefanis, Adams, Murgia, Marchesi 和 Tonelli, 2015; Ortu, Destefanis, Kassab, Counsel, Marchesi 和 Tonelli, 2015; Mantyla, Adams, Destefanis, Graziotin 和 Ortu, 2016; Ortu, Destefanis, Counsel, Swift, Tonelli 和 Marchesi, 2016）、社交网络和开发者态度（Ortu, Murgia, Destefanis, Tourani, Tonelli, Marchesi 和 Adams, 2016; Destefanis, Ortu, Counsel, Swift, Tonelli 和 Marchesi, 2017; Destefanis, Ortu, Counsel, Swift, Stephen, Michele 和 Tonelli, 2016; Destefanis, Tonelli, Concas 和 Marchesi, 2012）以及微模式（Concas, Destefanis, Marchesi, Ortu 和 Tonelli, 2013））中存在各种正在调查的缺点。

在 Tonelli, Pinna, Baralla 和 Iba (2018) 中，介绍了一种基于在以太坊区块链上部署的智能合约的架构来实现微服务的方法。该架构有两个级别。第一个级别为软件应用程序提供 ABI（以太坊应用程序二进制接口）以及嵌入 ABI 的用户界面。第二个层由在区块链上运行的智能合约集合组成。在该模型中，每个微服务通过原子智能合约实现。级别之间的通信通过远程过程调用进行，使用 Web3 以太坊库 3，其中包括区块链事务的执行。

在 Lenarduzzi, Tonelli, Marchesi 和 Lunesu (2018) 中，通过区块链应用程序设计了 Scrum/Kanban 敏捷软件项目的管理。项目负责人认证结果正确性的职责被委托给部署在以太坊区块链上并用 Solidity 编写的一个或多个智能合约。在该模型中，与客户的协议允许智能合约自动启用付款，并根据结果引入处罚或补助。产品负责人的职责和工作因此可以得到减轻，从而将资源分配给更有利可图和更高效的任务。

在 Marchesi, Ortu, Tonelli, Destefanis, Bracciai 和 Hierons (2018) 中，考察了由 Parity 生产的用于在以太坊区块链中持有和交换区块链地址和账户之间的以太币的数字钱包，调查了可能与特定智能合约功能一起出现的问题。该论文分析了一个案例研究，其中在智能合约库中发现的一个错误，也许还有“不安全”编程，允许对 Parity（一个钱包应用程序）发起攻击，导致 2017 年 11 月大约 500,000 个以太币（约 1.5 亿美元）被冻结。

在 Bragagnolo, Rocha, Denker 和 Ducasse (2018) 中，一个名为 SmartInspect 的应用程序允许基于其源代码检查已知合同，重点关注交互性和分布式调试属性。这种反思方法允许用户查看给定源代码的任何合同实例的内容，而无需重新部署或开发任何临时代码来解码内存表示。

在 Sousa, Bessani 和 Vukolic (2018) 中，为 Hyperledger 实现了一个拜占庭容错 (BFT) 排序服务，构建在 BFT-SMART 状态机复制/共识库之上，并针对广域部署进行了优化。结果表明，排序服务每秒可处理多达一万笔交易，并在半秒钟内将交易不可撤销地写入区块链，即使节点分布在不同大洲。

在 Hulea, Rosu, Miron 和 Astilean (2018) 中，提出了一种使用分布式账本技术进行制药冷链管理的解决方案。提出了一种基于 Hyperledger Sawtooth 分布式账本框架的应用程序框架，用于货物追踪，在制药产品分销阶段向所有利益相关者提供信息。该解决方案包括自定义交易族和传感器网关，用于自动从温度追踪设备收集数据。

在 Kinkelin, Hauner, Niedermayer 和 Carle (2018) 中，提出了一种拜占庭容错配置管理系统 (CMS)，它对管理员提供控制，限制其权限并强制执行关注点分离。配置管理过程要求对关键配置进行多方授权，以防止个别恶意管理员执行不想要的操作，并且在 Hyperledger Fabric 上得到支持。

在本章中，我们将注意力集中在将区块链技术应用于涉及商业和研究的 CRM（客户关系管理）系统上。我们讨论了一种管理基础设施的实现模型，该模型设计即安全，并能通过适当配置支持商业组织的需求和流程。该模型通过区块链技术在应用层采用软件产品的去中心化。后端基于开源平台 Hyperledger 以支持企业对企业和企业对客户的交易，前端中，商业信息由区块链协议提供的加密技术原生保护，以减少攻击面。

### 客户关系管理系统

客户关系管理是商业和企业采用分析方法获取和使用大量数据以提高绩效的解决方案 (Barton, 2012)。它已

