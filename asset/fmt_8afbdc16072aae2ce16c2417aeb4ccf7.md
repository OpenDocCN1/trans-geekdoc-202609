
### Mithril

Mithril 是区块链可扩展性、钱包和 Stake Pool Operators (`SPO`) 的重要发展。它是一种解决方案，允许客户端在无需从创世区块下载并重放所有交易的情况下获取区块链的当前状态。³⁶ Mithril 的核心创新在于使用基于权益的阈值多重签名³⁷ (`STM`) 由诚实的大多数利益相关者创建证书，证明 Cardano 快照的有效性。使用此证书，轻客户端或 `SPO` 可以验证快照，其安全属性类似于完全同步的节点。³⁸

### Input Endorsers

Input Endorsers 正如 Ouroboros Leios 文档所述，是 Cardano Ouroboros 协议的一项雄心勃勃且深远的设计扩展。³⁹ 特别地，它专注于通过并行化区块生产和交易选择来最大化网络利用率。⁴⁰ 这将在最大程度减少对网络额外资源需求的同时，显著提高区块生产吞吐量。Figure 11.24 说明了 Cardano 网络当前的利用不足情况及优化领域。

![](img/Figure-11.24.jpg)

**Figure 11.24:** Network Utilization⁴¹

Ouroboros Leios 引入了三种新的区块类型：

*   Input Blocks
*   Endorsement Blocks
*   Ranking Blocks

从高层来看，Input Blocks 包含从区块生产节点的内存池中获取的交易列表。正如 Figure 11.24 所示，这可以在空闲期间异步完成。Endorsement Blocks 随后生成有效 Input Blocks 的证书。Ranking Blocks 然后使用 Endorsement 证书并形成 Endorsement Blocks 链。账本状态随后基于 Ranking Blocks 的顺序。值得注意的是，Input Endorsers 不会改变确定最长链的共识机制。⁴² 关于 Input Endorsers 更详细和彻底的描述，请参阅 Ouroboros Leios 研究论文。⁴³

### Conclusion

我们现在应该对如何测试智能合约并将其作为整体测试框架的一部分有了很好的理解。我们使用 `Vitest` 和 `fast-check` 等工具考察了传统测试和基于属性的测试。接下来，我们回顾了真实审计中的代码示例以及如何避免常见的智能合约漏洞。最后，我们讨论了扩展以及一些工具和技术，例如避免 UTXO 争用、Reference Scripts、`Hydra` 和 `Mithril`。我们还回顾了使用 Input Endorsers 的第 1 层可扩展性改进，这将在保持安全性和最大程度减少额外网络资源需求的同时，显著增加区块生产。在下一章中，我们将回顾编写 Cardano 智能合约时可使用的故障排除工具和技术。

### Points to Remember

*   测试智能合约很困难，因为代码在网络中的分布式节点上执行。
*   应用程序设计最佳实践将 UI 代码与链下和后端代码分离。
*   测试策略可以包括传统测试和基于属性的测试。
*   安全性是智能合约开发最重要的方面。
*   Double Satisfaction 漏洞涉及在仅验证（满足）一个输入条件的情况下花费两个或更多输入。
*   Invalid Datum 漏洞发生在并非所有 datum 字段都被检查和验证时。
*   Token Leakage 涉及铸造多个唯一的 Thread 或 Validity token。
*   审计是生产就绪的关键部分，应用于审查智能合约源代码。
*   应用程序扩展技术包括避免 UTXO 争用和利用 Reference Scripts。
*   `Hydra` 是第 2 层扩展解决方案，但会影响安全性和去中心化属性。
*   Input Endorsers 是 Cardano 第 1 层扩展解决方案，可显著提高区块生产吞吐量。

### Multiple Choice Questions

1.  What techniques would you use to debug a Smart Contract in production?

    1.  Use VS Code debugger
    2.  Open a support ticket
    3.  Enable tracing in production
    4.  Restart the Cardano node

2.  Property testing test is used for?

    1.  Testing unexpected inputs
    2.  Testing expected inputs
    3.  Regression testing
    4.  Non-functional testing

3.  Where can Token leakage occur?

    1.  Minting script only
    2.  Validator or Minting scripts
    3.  Validator scripts only
    4.  None of the above

4.  Reference Scripts are only possible because of \_\_\_\_\_\_\_.

    1.  Native Assets
    2.  Determinism
    3.  Shelly Hard Fork
    4.  Reference Inputs

5.  What statement about Hydra is correct?

    1.  Only a limited number of Hydra heads can be opened
    2.  An unlimited number of Hydra heads can be opened
    3.  Joining a Hydra head is permissionless
    4.  Minted tokens on a Hydra network will be created in the base layer

### Answers

1.  c
2.  a
3.  b
4.  d
5.  a

### Questions

1.  What are other approaches to testing Smart Contracts?
2.  Can you list three other documented vulnerabilities and describe what was involved in the exploit?
3.  What are some other use cases for Hydra?
4.  What else can Mithril be used for?
5.  What are some of the potential risks of Input Endorsers?

### Key Terms

*   `UPLC`: Untype Plutus Core，由 Helios 或 Aiken 生成的编译语言。
*   `Map`: 包含键值对列表的字典数据类型。
*   `PKH`: Public Key Hash
*   `NFT`: Non-Fungible Token
*   `SPO`: Stake Pool Operator
*   `STM`: Stake-based Threshold Multi-signatures
*   `UI`: User Interface
*   `UTXO`: Unspent Transaction Output

___________________________________

¹ [`vitest.dev/`](https://vitest.dev/)
² [`jestjs.io/`](https://jestjs.io/)
³ Gabriel Lebec, “The Magic of Generative Testing: Fast-Check in JavaScript”
⁴ John Hughes, “Testing smart contracts with QuickCheck by John Hughes”
⁵ [`fast-check.dev/`](https://fast-check.dev/)
⁶ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts)
⁷ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts)
⁸ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts)
⁹ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts)

## 第 12 章：故障排除

### 简介

本章旨在介绍 Helios 和 Lucid + Aiken 的调试工具和技术。我们将探讨如何为交易生成 CBOR 并将数据类型与正式规范进行比对。我们将解决如何降低超出执行预算的 Plutus 脚本的计算开销。我们还将检查编译器错误，以及交易构建器如何提供强大的错误处理支持。此外，还将讨论 Cardano 节点错误，以及发生这些错误时的最佳理解策略。最后，本章将简要回顾基于浏览器的钱包错误。

### 结构

在本章中，我们将讨论以下主题：

*   追踪与打印
    *   Helios
    *   Aiken
*   CBOR 分析
    *   Helios
    *   Lucid + Aiken
*   执行预算错误
*   编译器错误
*   交易构建器错误
*   Cardano 节点错误
*   钱包错误

### 追踪与打印

当您的智能合约无法正常工作时，排查故障的最佳方法（撰写时）是在智能合约内部使用打印和追踪。这允许您写入控制台日志，查看智能合约中执行了什么内容。我们将重点介绍本书中使用的 Helios 和 Lucid + Aiken 智能合约开发工具包。

#### Helios

以 Helios 为例，您可以使用 `print` 和 `show` 函数打印出特定交易中铸造的值。必须将 Helios 的 `optimize` 标志设置为 false 以启用追踪。

```
func main(redeemer: Redeemer, ctx: ScriptContext) -> Bool {
    tx: Tx = ctx.tx;
    print("tx.minted: " + tx.minted.show());
}
```

## 参考文献

¹⁰ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.property.test.ts`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.property.test.ts)
¹¹ [`www.hyperion-bt.org/helios-book/api/reference/classes/FuzzyTest.html`](https://www.hyperion-bt.org/helios-book/api/reference/classes/FuzzyTest.html)
¹² [`aiken-lang.org/language-tour/tests`](https://aiken-lang.org/language-tour/tests)
¹³ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/double-satisfaction-exploit/buy.hl`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/double-satisfaction-exploit/buy.hl)
¹⁴ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/double-satisfaction-fix/buy.hl`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/double-satisfaction-fix/buy.hl)
¹⁵ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/invalid-datum-exploit/multisig.hl`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/invalid-datum-exploit/multisig.hl)
¹⁶ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/invalid-datum-exploit/multisig.hl`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/invalid-datum-exploit/multisig.hl)
¹⁷ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/invalid-datum-fix/multisig.hl`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/invalid-datum-fix/multisig.hl)
¹⁸ [`minswap.org/`](https://minswap.org/)
¹⁹ [`www.wingriders.com/`](https://www.wingriders.com/)
²⁰ [`www.tweag.io/blog/2022-03-25-minswap-lp-vulnerability/`](https://www.tweag.io/blog/2022-03-25-minswap-lp-vulnerability/)
