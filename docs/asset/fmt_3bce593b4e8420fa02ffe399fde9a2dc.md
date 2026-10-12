
84a80082825820d9b02da5897bd1ff9e2fdab008334d2804ea1accab
c7c3962e33771ed9f1a8d500825820d9b02da5897bd1ff9e2fdab008334d2804ea1a
ccabc7c3962e33771ed9f1a8d501018182581d606d04be153546d63c8a33
e0c11ec44cf790803f31c2f893fc241529531a05eb1244021a0002
d9250b582031e6c463846e3c0afe2aebfc9993355dbe8ce4dab892a7
af0e397a75df3509b90d81825820d9b02da5897bd1ff9e2fdab008334d2804ea1a
ccabc7c3962e33771ed9f1a8d5010e81581c6d04be153546d63c8a33e0c11e
c44cf790803f31c2f893fc241529531082581d606d04be153546d63c8a33e0c11
ec44cf790803f31c2f893fc241529531a05d9dd11111a000445b8a30081825820
fc6500742705cfe8c2f0822e73e2ab09c43285973adffe8aa06bd12d1fa6051f584
0ec7f53a69852e6daa868a3f221114435544ab2851bc6f2f42abe9772507b30064a1
f012ddab23153644703047ea2faf9132390e91937b82389626404d7adfd0105818
40000d8799f4d48656c6c6f2c20576f726c6421ff821977151a009daaac068158f258
f0010000323232323232323222232325333008323232533300b002100114a066446
46600200200644a66602200229404c8c94ccc040cdc78010028a511330040040013
014002375c60240026eb0c038c03cc03cc03cc03cc03cc03cc03cc03cc020c008c0
20014dd71801180400399b8f375c6002600e00a91010d48656c6c6f2c20576f726
c6421002300d001149858c94ccc020cdc3a400000226464a66601a601e0042930b1ba
e300d00130060041630060033253330073370e90000089919299980618070010a4
c2c6eb8c030004c01401058c01400c8c014dd5000918019baa0015734aae7555cf2a
b9f5742ae89f5f6

当我们使用 [`cbor.nemo157.com/`](https://cbor.nemo157.com/) 将其解码为诊断格式时，可以看到交易详情，如 *图 4.3* 和 *4.4* 所示。*图 4.3* 显示了该交易的 UTXO 输入、输出以及所需签名：

![](img/Figure-4.3.jpg)

**图 4.3：** CBOR 交易第 1 部分

*图 4.4* 显示了所需的抵押品、公钥、Redeemer（赎回者）以及 Plutus 脚本见证。该交易不包含辅助数据或元数据，且交易有效性标志设置为 true。

![](img/Figure-4.4.jpg)

**图 4.4：** CBOR 交易第 2 部分

### Redeemer（赎回者）

要获得 Redeemer 的人类可读版本，我们需要将十六进制 ByteString 转换为 UTF-8 字符串。然而，Plutus 在脚本执行期间将直接使用 ByteString。以下是使用 `xxd` 将十六进制编码的 ByteString 转换为普通字符串的示例：

```
$ echo 48656c6c6f2c20576f726c6421 | xxd -p -r
$ Hello, World!
```

### Plutus 脚本

Plutus 脚本经过双重编码（CBOR + flat），这意味着我们需要反序列化两次才能将其转换为 UPLC。因此，第一步是使用 CBOR 解码器对其进行解码，¹⁵ 并将其保存到名为 `plutus.flat` 的文件中：

```
$ cat plutus.flat
010000323232323232323222232325333008323232533300b002100114a066446466002
00200644a66602200229404c8c94ccc040cdc78010028a511330040040013014002375c
60240026eb0c038c03cc03cc03cc03cc03cc03cc03cc03cc020c008c020014dd7180118
0400399b8f375c6002600e00a91010d48656c6c6f2c20576f726c6421002300d0011498
58c94ccc020cdc3a400000226464a66601a601e0042930b1bae300d0013006004163006
0033253330073370e900000089919299980618070010a4c2c6eb8c030004c01401058c0
1400c8c014dd5000918019baa0015734aae7555cf2ab9f5742ae8
```

接下来，我们需要使用 Aiken 实用工具将其从十六进制转换为 UPLC 以进行解码：

```
$ aiken uplc decode --hex plutus.flat
(program
1.0.0
[
(lam
i_0
[
(lam
i_1
…
)
(force (builtin headList))
]
)
(force (builtin tailList))
]
)
```

### Datum（数据项）

接下来，我们将使用 `cexplorer.io` 查看 *图 4.5* 中的 Datum：¹⁶

![](img/Figure-4.5.jpg)

**图 4.5：** Datum 示例

*图 4.5* 中的 Datum 是一个内联 Datum，因此该值存储在链上，并锁定在我们想要花费的 UTXO 上。如果我们查看该 UTXO，将看到该值以 CBOR 十六进制格式编码：

`d8799f581c6d04be153546d63c8a33e0c11ec44cf790803f31c2f893fc24152953ff`

当我们解码 Datum 的 CBOR 十六进制值时，会得到以下字节数组输出：

```
121_0([_
h'6d04be153546d63c8a33e0c11ec44cf790803f31c2f893fc24152953',
])
```

在本例中，Datum 值代表一个公钥哈希。

### Plutus 执行预算

查看 *图 4.4* 中交易的 Redeemer 见证，我们会注意到附带的 Plutus 脚本有一个执行预算：

`[30485_1, 10332844_2]`

这些值指的是内存和 CPU（步数）执行单元，它们在 Plutus 账本规范中定义：

`ex_units = [mem: uint, steps: uint]`

`mem` 和 `steps` 随交易一起计算并提交，然后由 Plutus 核心求值器在脚本执行期间进行验证。如果在脚本执行期间任一值超出最大限制，则会引发错误：

```
Error: The budget when the machine terminated was:\n({ cpu: -84834\n| mem: 17553\n}
```

在本例中，`cpu/steps` 值超限并导致负数。结果，执行被终止，验证失败。要计算给定 Plutus 脚本的 `mem` 和 `cpu/step` 成本，会使用 `cost model`（成本模型）¹⁷ 来映射每个 Plutus 操作的 `execution cost`（执行成本）。成本模型位于网络协议参数中，并可通过网络更新随时间变化。要查看 `protocol parameters`（协议参数），可以使用 `cardano-cli` 工具：

```
$ cardano-cli query protocol-parameters --testnet-magic 1
{
"collateralPercentage": 150,
"costModels": {
…
"PlutusScriptV2": {
"addInteger-cpu-arguments-intercept": 205665,
"addInteger-cpu-arguments-slope": 812,
"addInteger-memory-arguments-intercept": 1,
"addInteger-memory-arguments-slope": 1,
…
"maxTxExecutionUnits": {
"memory": 14000000,
"steps": 10000000000
},
"maxTxSize": 16384,
…
```

除其他内容外，协议参数还指定了每个 Plutus 操作的执行成本、每笔交易的最大 `memory` 和 `steps` 单元，以及最大整体交易大小（`maxTxSize`），单位为 KB。

### 抵押品

我们将要讨论的最后一个主题是交易中包含的抵押品。抵押品是一小笔 Lovelace（1.5 × 交易费），如果发生第 2 阶段 Plutus 脚本失败，将会用到它。¹⁸ 抵押品输入中剩余的零钱将退还给用户，称为 **抵押品返还**。然而，Plutus 脚本评估通常在提交到网络之前在本地完成。这将捕获并防止无效 Plutus 脚本的提交。抵押品的作用是帮助保护网络免受恶意或垃圾交易的侵害。

## 结论

读者现在应该理解 Plutus 核心规范以及用于 Plutus 脚本执行和评估的 **UPLC** 代码。我们检查了一个 **CBOR** 交易，如何反序列化它，并查看了交易详情。我们还研究了 Plutus 脚本执行预算以及如何使用 **成本模型** 计算它。最后，我们讨论了抵押品，它在阶段 2 Plutus 脚本评估失败时使用。下一章将探讨用于创建和提交交易的链下代码。我们还将查看用户钱包，它是与 Cardano 区块链和智能合约交互的入口。

## 要点回顾

*   Cardano 上的第一代脚本是原生脚本，在账本内部进行评估。
*   Plutus 脚本是阶段 2 脚本，在账本外部进行评估。
*   无类型 Plutus 核心或 **UPLC** 是一种 Lambda 演算形式。
*   **UPLC** 是在节点上执行的低级语言。
*   编写智能合约使用生成低级 **UPLC** 的高级语言完成。
*   **UPLC** 程序必须是封闭的，所有项都已正确定义。
*   **UPLC** 程序可以利用 Lambda 演算中发现的惰性求值。
*   **CBOR** 是一种用于序列化和反序列化数据结构的二进制标准。
*   Cardano 交易在提交到网络时序列化为 **CBOR**，在 Cardano 节点验证期间反序列化。
*   交易中的 **Redeemer** 包含脚本将消耗的内存和步数/CPU 单元。
*   在 Plutus 脚本评估期间，如果内存或步数/CPU 单元超过允许的最大单元，脚本将停止并失败。
*   网络参数中的 **成本模型** 包含每个 Plutus 操作的成本以及交易中允许的最大内存和步数/CPU 单元。
*   交易中必须提供 **抵押品**，旨在保护网络免受恶意和垃圾交易的侵害。

## 多项选择题

1.  Cardano 上的第一代脚本是什么？

    1.  PlutusV1
    2.  PlutusV2
    3.  **原生脚本**
    4.  智能脚本

2.  关于原生脚本和 Plutus 脚本，哪项陈述是错误的？

    1.  两者都必须评估为真才能花费由脚本锁定的 UTXO
    2.  两者都可以创建多签脚本地址
    3.  **两者都是图灵完备的**
    4.  原生脚本是阶段 1 脚本

3.  **UPLC** 中的 `lam` 是什么？

    1.  **Lambda 函数抽象**
    2.  Lambda 函数应用
    3.  Lambda 函数排列
    4.  Lambda 函数关联

4.  为什么惰性求值是可取的？

    1.  代码执行效率较低
    2.  **代码执行效率较高**
    3.  强制评估所有声明的变量
    4.  无法创建无限数据结构

5.  当前的 Plutus **成本模型** 位于何处？

    1.  节点配置
    2.  Plutus 脚本配置
    3.  Plutus 评估器配置
    4.  **协议参数**

### 答案

1.  c
2.  c
3.  a
4.  b
5.  d

## 问题

1.  Lambda 演算有什么优势？
2.  图灵完备和 Lambda 演算程序在形式上等价吗？
3.  **CBOR** 和扁平编码有什么区别？
4.  为什么交易中的 **Redeemer** 要包含内存和 CPU/步数单元？
5.  阶段 1 和阶段 2 脚本有什么相似点和不同点？
6.  哪些输入可用作抵押品？

## 关键术语

*   **CBOR**：Concise Binary Object Representation（简洁二进制对象表示）
*   **抵押品找零**：如果交易期间使用了抵押品，返回的 Ada 找零金额。
*   **CDDL**：Concise Data Definition Library（简洁数据定义库）
*   **成本模型**：每个 Plutus 操作的执行成本参数。
*   **反序列化**：从二进制格式解码代码和数据结构的过程。
*   **执行成本**：每个 Plutus 操作使用的内存和 CPU/步数单元数量。
*   **高级编程**：允许使用更复杂的函数和数据结构以使代码更具可读性的语言。
*   **Lambda 演算**：用于定义函数和应用的最小语言。
*   **惰性求值**：仅实例化代码执行中使用的变量。
*   **原生脚本**：用于阶段 1 评估的简单脚本。
*   **协议参数**：网络使用的包含参数和设置的文件。
*   **序列化**：将代码和数据结构编码为二进制格式的过程。
*   **UPLC**：Untyped Plutus Core（无类型 Plutus 核心）

---

¹ [`github.com/cardano-foundation/CIPs/tree/master/CIP-0029`](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0029)

² Plutus Core Team, “Formal Specification of the Plutus Core Language.” 24.

³ Andre Knispel, et al., “A Formal Specification of the Cardano Ledger integrating Plutus Core,” 3.

⁴ Philip Wadler, “Functional smart contracts on Cardano.”

⁵ James Chapman, et al., “System F in Agda, for fun and profit.”

⁶ Gabriel Lebec, “Lambda Calculus - Fundamentals of Lambda Calculus & Functional Programming in JavaScript.”

⁷ Plutus Core Team, “Formal Specification of the Plutus Core Language,” 26.

⁸ [`aiken-lang.org/uplc/syntax#primitive-types`](https://aiken-lang.org/uplc/syntax#primitive-types)

⁹ Plutus Core Team, “Formal Specification of the Plutus Core Language,” 6.

¹⁰ Plutus Core Team, “Formal Specification of the Plutus Core Language,” 11.

¹¹ [`aiken-lang.org/uplc/syntax#delay--force`](https://aiken-lang.org/uplc/syntax#delay--force)

¹² Plutus Core Team, “Formal Specification of the Plutus Core Language,” 6

¹³ [`www.rfc-editor.org/rfc/rfc8949.html`](https://www.rfc-editor.org/rfc/rfc8949.html)

¹⁴ [`github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl`](https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl)

¹⁵ [`cbor.nemo157.com/`](https://cbor.nemo157.com/)
