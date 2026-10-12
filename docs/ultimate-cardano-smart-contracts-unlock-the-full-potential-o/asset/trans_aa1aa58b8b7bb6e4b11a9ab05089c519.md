

将这些内容综合在一起，得到一个简化的图表（不含交易手续费），如*[图 3.6](#c03.xhtml#fig3_6)*所示，展示了使用 `Plutus Script` 创建交易的输入和输出，该脚本花费 2 Ada。

![](images/Figure-3.6.jpg)

**图 3.6：** 简化脚本交易

# [见证集](#toc.xhtml#s69a)

所有交易都包含一个见证集，其中包含花费 UTXO 所需的见证。在本章中，我们重点关注了以下类型的见证：

*   `Signature`（签名）
*   `Redeemer`（赎回者/兑换者）
*   `Datum`（数据/基数）
*   `Plutus Script`（Plutus 脚本）

因此，在查看账本规范时[⁹](#c03.xhtml#ftn9)，所有交易必须具有以下高层结构：

```
transaction =
[ transaction_body
, transaction_witness_set
, bool
, auxiliary_data / null
]
```

其中：

*   `Transaction_body`（交易主体）除其他内容外，还包含手续费、UTXO 输入和输出、元数据哈希、脚本哈希以及铸造价值（如果有）。
*   `Transaction_witness_set`（交易见证集）包含花费 UTXO 输入所需的任何见证。
*   `Bool`（布尔值）指示这是否为有效交易。
*   `Auxiliary_data`（辅助数据）可选地包含交易元数据。

# [结论](#toc.xhtml#s70a)

我们回顾了不同类型的 Cardano 地址及其构建和解构方式。我们研究了 UTXO 架构、输入和输出的使用方式，以及 UTXO 如何被锁定在某个地址上。我们查看了交易元数据的示例，以及它是如何存储并链接到链上交易的。接着，我们探讨了 `Datum` 和 `Redeemer`，以及它们如何作为交易的一部分向 `Plutus script` 提供信息。最后，我们回顾了 `Witness Set`（见证集）的概念，它允许交易花费 UTXO 输入。在下一章中，我们将更详细地研究 `Plutus scripts` 及其在交易中的使用方法。

# [重点回顾](#toc.xhtml#s71a)

*   共有三种主要地址类型：`Base`（基础）、`Enterprise`（企业）和 `Reward`（奖励）。
*   交易头类型决定了地址的类型。
*   交易网络标签决定了交易关联的网络（`Mainnet` 主网或 `Testnet` 测试网）。
*   交易包含一个 `Payment Part`（支付部分）和一个可选的 `Delegation Part`（委托部分）。
*   `Payment`（支付）或 `Delegation Part`（委托部分）可以是 `PaymentKeyHash`（支付密钥哈希/公钥哈希）或 `ScriptHash`（脚本哈希）。
*   `Reward Address`（奖励地址）是一种特殊的基于账户的地址，仅用于质押奖励。
*   交易消耗一个或多个 `UTXOs` 作为输入，并必须产生一个或多个 `UTXOs` 作为输出。
*   `Signature`（签名）是交易由正确私钥签名的证明。
*   交易输入包含一个索引，因为给定交易可能存在多个输出 `UTXO`。
*   `Datum`（数据）用于在链上存储持久化数据，并包含在 `UTXO` 中。
*   `Datum` 值可以作为哈希存储，也可以作为 `Inline datum`（内联数据）完整存储。
*   `Plutus Core Evaluator`（Plutus 核心求值器）对 `Plutus script` 进行求值，以查看其是否返回 true。
*   `Plutus script` 通常是花费（验证器）脚本或铸造脚本。
*   `Plutus spending (validator) script`（Plutus 花费/验证器脚本）花费锁定在脚本地址上的 `UTXOs`。
*   `Plutus minting script`（Plutus 铸造脚本）用于铸造或销毁 Cardano 原生代币。
*   `UTXO` 也可以是 `Reference script`（参考脚本），一种不可花费的只读 `UTXO`。
*   `Redeemer`（赎回者）在交易求值期间向脚本提供信息。
*   `Witness Set`（见证集）可能包含 `Signature`、`Redeemer`、`Datum` 或 `Plutus scripts`。

# [多项选择题](#toc.xhtml#s72a)

1.  以下哪项不是有效的 Cardano 地址？

    1.  `Base`
    2.  `Enterprise`
    3.  `Reward`
    4.  `UTXO`

2.  脚本地址源自？

    1.  公钥哈希
    2.  `Plutus script hash`（Plutus 脚本哈希）
    3.  私有质押密钥哈希
    4.  私钥哈希

3.  签名证明了什么？

    1.  交易使用有效公钥签名
    2.  交易使用有效质押密钥签名
    3.  交易使用有效私钥签名
    4.  交易使用有效奖励密钥签名

4.  Plutus 脚本求值结果为？

    1.  布尔值
    2.  二进制值
    3.  十六进制值
    4.  非零值

5.  什么是 `Redeemer`？

    1.  用于识别参考脚本
    2.  用于交易平衡
    3.  在运行时向脚本提供信息
    4.  如果为假则停止交易

# [答案](#toc.xhtml#s73a)

1.  d
2.  b
3.  c
4.  a
5.  c

# [问题](#toc.xhtml#s74a)

1.  为什么不能将 `UTXO` 锁定在 `Reward Address` 上？
2.  领取质押奖励的流程是什么？
3.  为什么要在 `Witness Set` 中包含 `Plutus script` 作为见证，它能证明什么？
4.  为什么不将所有元数据都存储在链上，而只存储元数据哈希？
5.  为什么 `Plutus spending script` 也被称为验证器？

# [关键术语](#toc.xhtml#s75a)

*   **Base Address（基础地址）：** 同时包含支付密钥和质押密钥的地址。
*   **Datum（数据/基数）：** 用于在链上存储数据哈希。
*   **Enterprise Address（企业地址）：** 仅包含支付密钥的地址。
*   **Inline datum（内联数据）：** 用于在链上存储实际数据值。
*   **Metadata（元数据）：** 描述交易的数据。
*   **Minting script（铸造脚本）：** 用于铸造或销毁 Cardano 原生代币的 `Plutus script`。
*   **NFT：** 非同质化代币。
*   **PaymentKeyHash（支付密钥哈希）：** 公钥的哈希摘要。
*   **Plutus Core Evaluator（Plutus 核心求值器）：** 节点中对 `Plutus script` 进行求值的组件。
*   **Plutus script（Plutus 脚本）：** 在节点上执行的图灵完备语言。
*   **Redeemer（赎回者/兑换者）：** `Redeemer` 用于在运行时将信息传递给脚本。
*   **Reference script（参考脚本）：** 一种不可花费的只读 `UTXO`。
*   **Reward Address（奖励地址）：** 用于分发和接收质押奖励。
*   **ScriptHash（脚本哈希）：** `Plutus script` 的哈希摘要。
*   **Signature（签名）：** 交易哈希的加密哈希签名。
*   **Spending (validator) script（花费/验证器脚本）：** 用于花费锁定在脚本地址上的 `UTXOs` 的 `Plutus script`。
*   **UTXO：** 未花费交易输出。
*   **Witness（见证）：** 提供证明交易可以花费 `UTXO` 输入的凭证。

_____________________________________

[¹](#c03.xhtml#ftn1a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0019](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0019)

[²](#c03.xhtml#ftn2a) [https://docs.cardano.org/learn/cardano-addresses/](https://docs.cardano.org/learn/cardano-addresses/)

[³](#c03.xhtml#ftn3a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0019](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0019)

[⁴](#c03.xhtml#ftn4a) [https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl](https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl)

[⁵](#c03.xhtml#ftn5a) [https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl](https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl)

[⁶](#c03.xhtml#ftn6a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0025](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0025)

[⁷](#c03.xhtml#ftn7a) [https://preprod.cexplorer.io/tx/33767caa19d9dd1eaef3eab06264b1f909ecf726f074913855b7ca84fa7fb31e](https://preprod.cexplorer.io/tx/33767caa19d9dd1eaef3eab06264b1f909ecf726f074913855b7ca84fa7fb31e)

[⁸](#c03.xhtml#ftn8a) [https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl](https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl)

[⁹](#c03.xhtml#ftn9a) [https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl](https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl)

# [第 4 章](#toc.xhtml#c04)

# [Plutus](#toc.xhtml#c04)

# [简介](#toc.xhtml#s76a)

