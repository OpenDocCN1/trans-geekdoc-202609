
⁸ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts)

⁹ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts)

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

²⁰ [`www.tweag.io/blog/2022-03-25`](https://www.tweag.io/blog/2022-03-25)

²¹ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/token-leakage-exploit`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/token-leakage-exploit)

²² [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/token-leakage-fix`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/token-leakage-fix)

²³ [`github.com/cardano-foundation/CIPs/tree/master/02`](https://github.com/cardano-foundation/CIPs/tree/master/02)

²⁴ [`github.com/vacuumlabs/cardano-ctf/main`](https://github.com/vacuumlabs/cardano-ctf/main)

²⁵ [`github.com/vacuumlabs/audits`](https://github.com/vacuumlabs/audits)

²⁶ [`www.tweag.io/blog/2022-03-25`](https://www.tweag.io/blog/2022-03-25)

²⁷ [`library.mlabs.city/common-plutus-vulnerabilities`](https://library.mlabs.city/common-plutus-vulnerabilities)

²⁸ [`github.com/cardano-foundation/CIPs/tree/master/01`](https://github.com/cardano-foundation/CIPs/tree/master/01)

²⁹ [`github.com/cardano-foundation/CIPs/tree/master/03`](https://github.com/cardano-foundation/CIPs/tree/master/03)

³⁰ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/vesting-reference-script/contracts/off-chain/lock.ts`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/vesting-reference-script/contracts/off-chain/lock.ts)

³¹ [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/vesting-reference-script/contracts/off-chain/lock.ts`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/vesting-reference-script/contracts/off-chain/lock.ts)

当你的智能合约无法正常工作时（在本文编写时），最好的故障排除方法是在智能合约内部使用`print`和追踪功能（traces）。这允许你编写`console log`并查看你的智能合约中执行了哪些内容。我们将重点介绍书中使用的 Helios 和 Lucid + Aiken 智能合约开发工具包。

# Helios

以 Helios 为例，你可以使用`print`和`show`函数打印特定交易中铸造的值。必须将 Helios 的`optimize`标志设置为`false`以启用追踪。

```
func main(redeemer: Redeemer, ctx: ScriptContext) -> Bool {
tx: Tx = ctx.tx;
print("tx.minted: " + tx.minted.show());
```

在运行 Plutus 脚本时，这将生成以下输出。

```
INFO (ticket:13:10) tx.minted: lovelace: 0
INFO (ticket:13:10) 0af9021a0…d93cba53ecf15.54687265616420546f6b656e: 2
```

Helios 脚本的行号也会显示在`INFO`括号中。`trace()`函数也可用于输出以测试布尔条件。

```
value_minted.contains_policy(mph).trace("TTP3: ")
```

执行 Plutus 脚本时，这将生成评估输出。

```
INFO (ticket:33:52) TTP3: true
```

如果智能合约失败并返回 false 布尔值，将在图 12.1 中生成堆栈追踪，让你看到是在何处以及为何失败的。

![](img/Figure-12.1.jpg)

**图 12.1:** Helios Trace()

# Aiken

当你构建 Aiken 脚本时，可以指定想要包含的追踪类型，正如图 12.2 所示。

![](img/Figure-12.2.jpg)

**图 12.2:** Aiken Build Trace Options

要输出`print`语句，请使用`trace`函数。

```
trace "redeemer message: "
trace string.from_bytearray(msg)
```

当条件被评估为 false 时输出追踪，你可以使用`?`运算符。

```
some_expression_a? && some_expression_b?
```

在这个示例中，它可以帮助隔离哪个表达式失败了，因为如果任何一个条件评估为 false，整个脚本将失败。

输出`trace`信息的示例见图 12.3。

![](img/Figure-12.3.jpg)

**图 12.3:** Aiken Traces

验证器脚本使用`-t`标志编译。

```bash
$ aiken build -t verbose
```

当脚本失败时，将生成以下输出，如图 12.4 所示。

![](img/Figure-12.4.jpg)

**图 12.4:** Aiken Traces

# CBOR 分析

正如我们在之前的章节中学到的，`CBOR`是存储数据的格式。验证器脚本使用`-t`标志编译。执行脚本时将生成以下输出。

# Helios

Helios 对`CBOR`有极佳的支持，你可以轻松查看交易的任何部分。

# Lucid + Aiken

Lucid `diagnostic()`来帮助你查看`CBOR`表示。

# 执行错误

当你遇到脚本大小或 CPU 和内存执行限制错误时，错误信息将告诉你发生了什么错误以及错误发生的位置。

```
tx = ctx.tx;
```

`图 12.7`显示了错误信息，其中列出了错误类型、脚本名称和行号。

![](img/Figure-12.7.jpg)

**图 12.7:** Helios 构建器错误

这是一个 Aiken 无效变量赋值的示例。

```javascript
let { transaction, purpose } = context
```

这将生成一个错误，并指示行号和错误原因（请参考`图 12.8`）。

![](img/Figure-12.8.jpg)

**图 12.8:** Aiken 构建器错误

# 交易构建器错误

Helios 和 Lucid 都拥有良好的交易构建错误信息，并且有很多错误条件以及导致错误的不同原因。最常见的错误是资金不足，因为交易未平衡。这可能是因为 Ada 不足以覆盖交易费用，或者铸造的令牌不足以匹配输出。幸运的是，这些错误可以使用本地调试器进行调试，你应该能够识别问题。如果仍然存在问题，请相应在 Cardano Stack Exchange⁴ 上搜索并提问，或者在 Helios⁵ 以及 Lucid/Translucent⁶ Discord 频道询问。

# Cardano Node 错误

遗憾的是，Cardano Node（Ledger）错误最难诊断。这是因为你会看到格式不佳的陌生错误信息，导致它们难以阅读⁷和理解。`图 12.9`提供了一个你在交易失败时可能会看到的 Cardano Node 错误示例。

![](img/Figure-12.9.jpg)

**图 12.9:** Cardano Node 错误

为了更好地理解这些错误信息的含义，你可能需要参考用 Haskell 编写的 Cardano Ledger⁸ 源代码。你将看到可以解释错误发生原因的代码和注释。`图 12.9`中的示例非常直观，是一个执行预算错误。还有其他错误并不那么明显，可能需要查看代码来理解错误的含义。幸运的是，这些错误现在大多数都被离链交易构建器捕获，因此遇到 Cardano Node 错误不再以前那么常见了。

## 钱包错误

我们将回顾的最后一种错误是钱包错误。这些错误在使用浏览器扩展钱包时发生，并列在`表 12.1`中。

| **错误类型** | **错误名称** | **描述** | **值** |
| --- | --- | --- | --- |
| API 错误 | `InvalidRequest` | 输入无效且不符合 CIP-0030 规范 | -1 |
| | `InternalError` | 请求期间发生内部错误 | -2 |
| | `Refused` | dApp 未被批准访问浏览器钱包 | -3 |
| | `AccountChange` | 钱包账户已更改 | -4 |
| 数据签名错误 | `ProofGeneration` | 钱包无法签名数据 | 1 |
| | `AddressNotPK` | 地址无效且不是公钥哈地址 | 2 |
| | `UserDeclined` | 用户拒绝签名数据 | 3 |
| 分页错误 | `maxSize` | 分页支持的最大大小。如果请求的数量超过了限制，将返回支持的数量 | maxSize |
| 交易发送错误 | `Refused` | 钱包拒绝发送交易（例如，可能是由于速率限制） | 1 |
| | `Failure` | 钱包无法发送交易 | 2 |
| 交易签名错误 | `ProofGeneration` | 钱包无法签名交易 | 1 |
| | `UserDeclined` | 用户拒绝签名交易 | 2 |

**表 12.1:** 浏览器扩展钱包错误⁹

## 结论
