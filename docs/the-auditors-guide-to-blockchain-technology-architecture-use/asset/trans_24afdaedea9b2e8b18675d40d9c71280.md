

# Corda：一种智能合约平台

Corda 是一种基于 Java 编程语言的智能合约平台。合约可以用 `Java` 或 `Kotlin` 编写。在 Corda 中，每个状态都由一个智能合约管辖。智能合约以涉及其状态的交易作为输入，并使用智能合约中指定的规则来评估该交易是否有效。要在 Corda 中得到确认，交易必须被认定为既真实又独特。交易的有效性由相关方决定。交易的唯一性约束旨在确保没有状态被花费两次。Corda 节点只能看到其作为参与者的支付和状态，因此它们无法验证交易的唯一性。为了解决这一过程，Corda 区块链采用了一个公证人网络，他们必须对一项活动进行签名，该活动才能生效。每个节点的分布式账本副本中的每个状态都会被分配一个证书。只有当公证人是其所有先前输入状态的指定公证人时，才会授权一笔交易。如果指定的公证人拒绝传输或签名，Corda 中的资产和交易可能会被挟持。恶意公证人可能允许双重支付攻击，使区块链难以协调。因此，在使用 Corda 区块链时，公证人的信任和安全至关重要。

## Corda 安全措施

Corda 的安全性主要基于其“需知”概念和公证人网络。由于用户只能观察和参与他们有利益关系的交易，因此数据泄露的后果得以缓解。与早期的区块链不同，Corda 使用点对点 TLS 加密连接，而不是点对点广播（表 13.5）[[26]]。

### 表 13.5：Ethereum、Hyperledger Fabric 和 Corda 的比较

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

针对这些攻击的防御技术也有介绍，有助于缓解各种潜在的区块链漏洞。此外，还重点介绍了 Hyperledger、Corda 和 Ethereum 平台的固有安全措施。

本章展示并讨论了许多现实生活中的攻击场景。组织的新目标应是更加专注于为各种区块链技术实施更强的安全措施，以便有效且安全地利用区块链技术。

## 核心概念

*   尽管区块链技术是一种具有卓越安全特性的不断发展的技术，但它由各种核心组件组成，攻击者可针对这些组件发起攻击。

*   用户级攻击是因用户交互而发生的攻击。用户的疏忽、私钥被盗或恶意软件的存在都可能导致区块链安全漏洞。硬件、纸质和云钱包等缓解技术有助于保护密钥免遭盗窃或泄露，同时配合组织的密钥轮换策略。此外，使用杀毒产品进行例行系统和网络扫描有助于降低或防止基于恶意软件的攻击的可能性。

*   节点与用户一样脆弱。但节点本身也可能受到共享和/或成员服务提供商配置错误漏洞的影响。共享漏洞是指攻击者窃取私钥并获取目标节点，旨在同时危害区块链上的其他节点。成员服务提供商配置错误漏洞是由区块链上的控制弱点导致的，引发 DoS/DDoS 攻击。为了额外的保护，可以定期更新和修补软件，从而缓解任何潜在漏洞。

*   攻击者寻找网络弱点进行利用，并采用各种网络级攻击。例如，当攻击者试图通过向网络注入大量交易来延迟或停止网络时，就会发生 DDoS 攻击。在女巫攻击中，攻击者控制许多虚假身份。在 51% 攻击中，矿工获得网络大部分算力的控制权。此类攻击可通过实施许可区块链成员服务提供商服务、PirlGuard 和/或合并挖矿来缓解。

*   区块链系统级攻击发生在区块链基础设施的系统层。这些攻击是由系统后端的编码错误和代码操纵产生的。应尽职尽责，并利用工具避免此类错误。此外，将资源限制在用户需求范围内、锁定时间框架的上限以及使用内存安全编程语言，是应对此类攻击的一些技术。系统级攻击需要大量的故障排除，但在专家和称职开发人员的帮助下，这是一项可控的任务。

*   区块链多年来发展迅速。一些强大的技术进步包括 Ethereum、Hyperledger Fabric 和 Corda 平台。Ethereum 智能合约中的机密交易，以及信息认证和传输数据保护；Hyperledger 通过 Gossip 协议实现数据私有化的能力，以及身份认证和可测试性；Corda 的公证人系统，都是目前这些区块链结构中现有增强功能的示例。

## 促进理解的活动

读者可能想了解更多关于本章讨论的一些攻击。表 13.6 提供了一些相关 YouTube 视频的标题和链接，可作为补充学习资源。

### 表 13.6：补充学习资源

| **攻击** 类型 | 视频标题 | 直接链接 |
| --- | --- | --- |
| 重放攻击 | *Blockchain 101 Ep 67 – What is a Replay Attack?* | [https://www.youtube.com/watch?v=KWJTvnal8j4&ab_channel=HuobiGlobal](https://www.youtube.com/watch?v=KWJTvnal8j4&ab_channel=HuobiGlobal) |
| 女巫攻击 | *What are Sybil Attacks/Explained for Beginners* | [https://www.youtube.com/watch?v=-EKhIBUQjcA](https://www.youtube.com/watch?v=-EKhIBUQjcA) |
| 缓冲区溢出 | *Ethical Hacking: Buffer Overflow Basics* | [https://www.youtube.com/watch?v=SOoJcrR4Ijo&ab_channel=NationalConsortiumforMissionCriticalOperations](https://www.youtube.com/watch?v=SOoJcrR4Ijo&ab_channel=NationalConsortiumforMissionCriticalOperations) |
| 竞争条件 | *Race Conditions and How to Prevent Them – A Look at Dekker’s Algorithm* | [https://www.youtube.com/watch?v=MqnpIwN7dz0&ab_channel=SpanningTree](https://www.youtube.com/watch?v=MqnpIwN7dz0&ab_channel=SpanningTree) |

## 参考文献

