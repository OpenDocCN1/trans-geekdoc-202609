
# 章节概览

## Chapter 1. Blockchain Evolution
本章将介绍区块链和分布式账本技术，重点关注先前的实现和需要克服的挑战。我们将查看 Bitcoin 和 Ethereum 白皮书，以及它们如何为第三代区块链 Cardano 铺平道路。将研究区块链不可能三角，并回顾代币经济学和 Cardano 的原生货币 Ada。最后，我们将通过讨论 Cardano 路线图和区块链用例来结束本章。

## Chapter 2. Cryptography and Consensus Algorithms Overview
本章将简要介绍密码学及其在区块链技术中的应用。我们将首先查看使用 `Proof of Work` 共识协议保护区块链的方法。然后，我们将查看 `Proof of Stake` 及其相对于 `Proof of Work` 的优势。最后，我们将回顾 Cardano 使用的 `Ouroboros` 权益证明共识协议。

## Chapter 3. Transactions
本章将检查 Cardano 地址和 `UTXO` 架构。它还将介绍智能合约并解释它们如何被执行和评估。我们将看到 `Redeemers` 和 `Datums` 如何将数据传递给 Plutus 脚本，以及 `Datums` 如何用于数据存储和持久化。最后，我们将检查交易 `Witness Set` 以及它如何授权交易输入的支出。

## Chapter 4. Plutus
在本章中，我们将检查用于执行 Cardano 智能合约的 Plutus 核心规范 `Untyped Plutus Core (UPLC)`。我们还将探索 Plutus 中使用的不同数据结构，以及如何使用简洁二进制对象表示 (`CBOR`) 格式对它们进行序列化。接下来，我们将使用 Plutus 成本模型计算 CPU 和内存单元，并解释为什么需要在交易中包含抵押品。

## Chapter 5. Transaction Builder
本章将结合我们对链上 Plutus 脚本的知识，以及如何使用链下代码将 Ada 锁定到智能合约中。我们将查看 Cardano 钱包，这是与区块链和智能合约交互的入口。接下来，我们将查看有助于构建和提交交易的工具，如 `Demeter.run`。然后，我们将使用两种流行的方法制作一个简单的归属智能合约：`Helios` 和 `Lucid + Aiken`。

## Chapter 6. Validators
在本章中，我们将详细查看什么是验证器以及为什么它们如此重要。我们将展示如何花费锁定在验证器脚本地址上的 `UTXOs`，以及如何访问 `Redeemer` 或 `Datum` 中提供的数据。接下来，我们将深入了解 `ScriptContext` 是什么以及如何使用它来访问与交易关联的所有输入和输出。本章将使用两种不同的方法回顾链上和链下代码示例：`Helios` 和 `Lucid + Aiken`。

## Chapter 7. Minting
本章将检查 Cardano 原生资产以及它们与使用 `ERC-20` 标准创建的 Ethereum 代币有何不同。我们将讨论代币包的概念以及如何优化币选择。然后，我们将深入研究铸造 Cardano 原生代币，`Non-Fungible Tokens (NFTs)` 和 `Fungible Tokens (FTs)` 之间的区别，以及元数据标准 `CIP-25` 和 `CIP-68`。我们将结合一个工作的铸造策略用例和演示。

## Chapter 8. Tooling
在本章中，我们将回顾可用于链下开发的工具和服务提供商。我们将查看 Cardano 区块链 API 提供商，如 `Blockfrost`、`Maestro`、`Koios` 和 `Dandelion`。然后，我们将查看使用 `Demeter.run` 设置 `Cardano Node`、`Ogmios` 和 `Kupo` 等服务的托管环境。最后，我们将查看如何使用 `Yaci DevKit` 设置本地 `Devnet` 以进行快速开发和原型设计。

## Chapter 9. Ticket Application Design
本章回顾利用 `UTXO` 架构的智能合约设计模式。也会检查反模式，应避免这些模式，因为它们会导致应用程序性能不佳和 `UTXO` 争用。我们将查看 Cardano 改进提案 (`CIPs`) 以及它们如何应用于应用程序设计。接下来，我们将创建状态机图来模拟活动门票应用程序，查看成功交易所需的输入和输出。最后，我们将通过回顾序列图来结束本章，展示每个用例中系统组件之间的交互。

## Chapter 10. Ticket Application Implementation
在本章中，我们将演练门票应用程序的实现，包括区块链集成。我们将查看应用程序堆栈，包括 `CharkraUI`、`Next.js`、`Redis DB` 和 `Blockfrost`。接下来，我们将检查用于构建和提交交易的前端链下代码。然后，我们将回顾相应的智能合约链上代码、业务逻辑和验证规则。最后，我们将演示应用程序的端到端演示。

## Chapter 11. Testing, Security, and Scaling
本章将展示如何测试智能合约并将其包含在流行的测试框架（如 `Vitest`）中。我们将查看传统测试和基于属性的测试方法。接下来，我们将专注于安全性，并回顾在真实 Cardano 应用程序审计中发现的漏洞。我们将查看代码示例，说明如何使您的智能合约更健壮、更能抵御此类攻击。最后，我们将通过讨论扩展以及一些提高 dApp 性能的工具和技术来结束本章。

## Chapter 12. Troubleshooting
本章将演练 `Helios` 和 `Aiken` 的调试工具和技术。我们将查看如何为交易生成 `CBOR` 并根据正式规范比较数据类型。我们将查看减少超出执行预算的 Plutus 脚本计算开销的技术。我们还将检查编译器错误以及交易构建器如何提供强大的错误处理支持。最后，我们将查看 `Cardano Node` 和浏览器钱包错误以及如何相应地诊断它们。

## Chapter 13. Cardano Ecosystem
本章将回顾 Cardano 的现状以及包含所有 Cardano 源代码和规范的 GitHub 存储库。我们将查看 Cardano 改进流程 (`CIP`) 以及如何对 Cardano 区块链进行更改和改进。接下来，我们将探索 Voltaire 时代和关于 Cardano 治理的 `CIP-1694`。我们还将回顾 `Project Catalyst`，这是最大的去中心化创新平台之一，为 Cardano 项目提供资助。最后，我们将查看 Cardano 合作伙伴链框架，如 `Midnight`，一个数据保护区块链。

## Chapter 14. Closing Remarks
本章将回顾 Cardano 的精神。我们将检查软件行业标准以及这些标准为何在高保证软件方面不足。我们将看到 `IOG` (`IOHK`) 如何使用半形式化方法构建 Cardano，以及像 `IACR` 这样的密码学协会如何促进同行评审。通过现实世界的例子，我们将探索 Cardano 推动积极社会变革的潜力。我们还将讨论监管和合规风险。最后，我们将回顾技术采用的五个阶段和 Cardano 的历程。

# Downloading the code bundles and colored images

Please follow the link or scan the QR code to download the **Code Bundles and Images** of the book:

- [https://github.com/ava-orange-education/Ultimate-Cardano-Smart-Contracts](https://github.com/ava-orange-education/Ultimate-Cardano-Smart-Contracts)

![QR Code](images/qr.jpg)

The code bundles and images of the book are also hosted on:

- [https://rebrand.ly/ad614f](https://rebrand.ly/ad614f)

![QR Code](images/qr1.jpg)
