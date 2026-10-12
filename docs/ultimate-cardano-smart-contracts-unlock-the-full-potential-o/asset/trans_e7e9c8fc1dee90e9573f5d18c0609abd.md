
6. 交易所需签名者的 CDDL 规范标识符是什么？

# 关键术语

*   **辅助数据：** 关于交易的元数据，仅元数据哈希存储在链上。
*   **Blake2b：** 一种基于字节输入生成哈希的哈希算法。
*   **蓝图：** 一个由 Aiken 生成的文件，包含 Plutus 脚本元数据和类型定义。
*   `Blockfrost`：区块链数据的 API 提供商。
*   `ByteArray`：使用十六进制格式编码的字节数组。
*   **合约参数：** 链上变量，可在编译时或运行时更新。
*   `Enum`：可枚举并用于 switch/case 语句的数据类型。
*   `ScriptContext`：包含当前正在评估的交易的所有信息，辅助数据除外。
*   `Spending` **脚本：** 用于在脚本地址锁定 UTXO 的验证器类型。
*   `Switch` **语句：** 用于评估不同的 Enum 组合。
*   `VerificationKey`：对应私钥的公钥。

---

[¹](#c06.xhtml#ftn1a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/contracts/vesting.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/contracts/vesting.hl)

[²](#c06.xhtml#ftn2a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/contracts/vesting.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/contracts/vesting.hl)

[³](#c06.xhtml#ftn3a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/components/Unlock.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/components/Unlock.tsx)

[⁴](#c06.xhtml#ftn4a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx)

[⁵](#c06.xhtml#ftn5a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx)

[⁶](#c06.xhtml#ftn6a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/api/vestingUtxo.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/api/vestingUtxo.ts)

[⁷](#c06.xhtml#ftn7a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx)

[⁸](#c06.xhtml#ftn8a) [https://preprod.cexplorer.io/address/addr_test1wp4gwgtnyp8grwhzjj47qy7k60hxfv9p2wymjcwkzgw6r9cp0ctvs/tx#data](https://preprod.cexplorer.io/address/addr_test1wp4gwgtnyp8grwhzjj47qy7k60hxfv9p2wymjcwkzgw6r9cp0ctvs/tx#data)

[⁹](#c06.xhtml#ftn9a) [https://aiken-lang.org/installation-instructions](https://aiken-lang.org/installation-instructions)

[^(10)](#c06.xhtml#ftn10a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/contracts/validators/vesting.ak](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/contracts/validators/vesting.ak)

[^(11)](#c06.xhtml#ftn11a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/contracts/validators/vesting.ak](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/contracts/validators/vesting.ak)

[^(12)](#c06.xhtml#ftn12a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/pages/index.tsx)

[^(13)](#c06.xhtml#ftn13a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/pages/index.tsx)

# 第 7 章

# 铸造

# 简介

在本章中，我们将探讨 Cardano 原生资产，以及它们与使用 ERC-20 和 ERC-721 标准在以太坊上创建的代币有何不同。我们将讨论代币包的概念以及如何优化币选择。接下来，我们将深入探讨 Cardano 原生代币的铸造方式，以及非同质化代币 (NFT) 和同质化代币 (FT) 之间的区别。我们还将回顾 NFT 和 FT 元数据标准 CIP-25 和 CIP-68，以及在铸造时如何实现它们。最后，我们将介绍 Cardano 代币注册表，并探讨其对最终用户钱包体验的益处。我们将通过一个可工作的铸造策略用例和演示将所有这些内容串联起来。

# 结构

在本章中，我们将讨论以下主题：

*   代币
    *   原生资产
    *   代币包
*   铸造策略
    *   同质化代币
    *   非同质化代币
    *   代币注册表
    *   NFT 元数据标准
        *   CIP-25
        *   CIP-68
*   币选择
    *   铸造策略用例

# 代币

2021 年 3 月 1 日，作为 Mary 硬分叉的一部分，Cardano 升级为多资产账本。这是一个重大事件，因为自定义原生代币现在可以利用 Ada（Cardano 的原生货币）所使用的安全、经过同行评审的账本规则。这与以太坊截然不同，后者要求遵循 ERC-20 或 ERC-721 标准的每种代币都需要自定义账本代码。此外，跟踪与 Cardano 原生资产相关的交易，不需要特殊费用或额外的事件处理逻辑。[¹](#c07.xhtml#ftn1)

# 原生资产

原生资产是 Cardano 上的自定义代币，其运作方式与基础层货币 Ada 相同。唯一的要求是原生资产必须始终包含最小数量的 Ada。CIP-55[²](#c07.xhtml#ftn2) 简化了最小 Ada 计算，使用 UTXO 的 CBOR 字节数，其中包括锁定在特定 UTXO 中的所有原生资产。

资产代表价值，例如 1 Ada (1,000,000 lovelace) 或 100 枚金币。每个资产代币始终由三个组成部分构成^(*)：

*   **策略标识符 (ID)：** 唯一标识符，即铸造策略 Plutus 脚本的哈希值。
*   **资产名称：** 特定铸造策略下链上不可变的代币名称。
*   **数量：** 记账单位。

^(*) Ada 是唯一策略 ID 为空字符串的资产代币。

# 代币包

代币包是一组代币的集合，这些代币可能相同也可能不同。代币包将代币组织成一种特定结构，以正确定义铸造策略 ID、代币名称以及**集合**中每个代币的数量。让我们看看下面的例子：

```
{
  "lovelace": "1646420",
  "assets": {
    "Game Monetary Policy ID": {
      "Gold": "100",
      "Silver": "1,000",
      "Bronze": "10,000"
    },
    "Game Character Policy ID": {
      "Dracula": "1"
    }
  }
}
```
