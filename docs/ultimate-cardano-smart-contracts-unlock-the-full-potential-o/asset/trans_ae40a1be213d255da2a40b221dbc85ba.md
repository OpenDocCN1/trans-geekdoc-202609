

# 第 3 章：交易

## 简介

在本章中，我们将首先了解 Cardano 地址，它们是如何构建的，以及其中包含的数据。接下来，我们将探讨 UTXO 架构，并展示交易是如何创建的，以及可选的元数据。我们还将介绍智能合约（称为 Plutus 脚本）是如何执行和评估的。我们将看到 Redeemer（赎回者）如何将数据传递给 Plutus 脚本，以及 Datum（数据项）如何用于数据存储和持久化。最后，我们将了解交易 Witness Set（见证集）以及它如何授权交易输入的支出。

## 结构

在本章中，我们将讨论以下主题：

*   地址
    *   网络标签
    *   基础地址
    *   企业地址
    *   奖励（质押）地址
*   UTXO
    *   交易输入
    *   交易输出
*   元数据
*   Plutus 脚本
*   Datum
*   Redeemer
*   Witness Set

## 地址

Cardano (Shelley) 地址是使用 Bech32 编码的字节序列。[¹](#c03.xhtml#ftn1) 在 Cardano 上，您通常会与以下三种类型的地址进行交互：

*   基础地址
*   企业地址
*   奖励（质押）地址

Cardano 地址的结构如**图 3.1**所示：

![](images/Figure-3.1.jpg)

**图 3.1：** Cardano 地址结构

头部类型指示地址（或载荷）的类型，网络标签指示该地址关联的网络。

### 网络标签

| **头部位** | **网络** |
| --- | --- |
| `xxxx0000` | 测试网 |
| `xxxx0001` | 主网 |

**表 3.1：** 网络标签

### 基础地址

基础地址是最常见的地址类型，如**表 3.2**所示。当支付部分为 `PaymentKeyHash` 时，交易必须使用该地址对应的私钥进行签名。当支付部分为 `ScriptHash` 时，必须执行并评估哈希值匹配的脚本，且结果为 true，才能从该地址支出。委托部分与支付部分类似，但用于注册（并委托）该地址锁定的 Ada 的质押证书。正如我们在上一章回顾的那样，质押是帮助保障权益证明区块链安全并因之获得奖励的机制。

| **头部位** | **支付部分** | **委托部分** |
| --- | --- | --- |
| `0000xxxx` | `PaymentKeyHash` | `StakeKeyHash` |
| `0001xxxx` | `ScriptHash` | `StakeKeyHash` |
| `0010xxxx` | `PaymentKeyHash` | `ScriptHash` |
| `0011xxxx` | `ScriptHash` | `ScriptHash` |

**表 3.2：** 基础地址

### 企业地址

企业地址类似于基础地址，区别在于没有委托部分。企业地址的头部类型列于**表 3.3**。

| **头部位** | **支付部分** | **委托部分** |
| --- | --- | --- |
| `0110xxxx` | `PaymentKeyHash` | N/A |
| `0111xxxx` | `ScriptHash` | N/A |

**表 3.3：** 企业地址

### 奖励（质押）地址

奖励地址用于在权益证明协议中分发质押奖励，具有以下属性：[²](#c03.xhtml#ftn2)

*   它采用账户式记账模型，而非 UTXO。
*   账户余额仅在分发质押奖励时增加。
*   要转出奖励地址锁定的 Ada，需要一种提款类型的交易来释放资金并将奖励地址的余额归零。
*   已注册的质押密钥与奖励账户地址之间存在一对一关系。

| **头部位** | **质押引用** |
| --- | --- |
| `1110xxxx` | `StakeKeyHash` |
| `1111xxxx` | `ScriptHash` |

**表 3.4：** 奖励（质押）地址

为了将所有内容串联起来，以下输出由 `cardano-address address inspect` 命令行工具生成。请注意，地址中可能存在链指针，指向包含质押密钥注册证书的链上位置。[³](#c03.xhtml#ftn3) 然而，指针很少使用，在以下示例中，我们可以看到 `stake_reference` 为 "by_value"，表明质押证书位于此质押地址，而非指针。

**Shelley 基础地址 (base 32)：**

`addr_test1qqq40ucy70wms9p7tku6ntcamzuuxnsaejal7p82qcahh3ryswkc5djr3z37lhv3zjytgyfpf8en2pa4cfuvqdz4za8syv5dnc`

```
$ echo addr_test1qqq40ucy70wms9p7tku6ntcamzuuxnsaejal7p82qcahh3ryswkc5djr3z37lhv3zjytgyfpf8en2pa4cfuvqdz4za8syv5dnc | cardano-address address inspect
{
  "address_style": "Shelley",
  "address_type": 0,
  "network_tag": 0,
  "spending_key_hash": "0157f304f3ddb8143e5db9a9af1dd8b9c34e1dccbbff04ea063b7bc4",
  "spending_key_hash_bech32": "addr_vkh1q9tlxp8nmkupg0jahx5678wch8p5u8wvh0lsf6sx8daug8cyak6",
  "stake_key_hash": "6483ad8a364388a3efdd911488b4112149f33507b5c278c03455174f",
  "stake_key_hash_bech32": "stake_vkh1vjp6mz3kgwy28m7ajy2g3dq3y9ylxdg8khp83sp525t57tzwkxk",
  "stake_reference": "by value"
}
```

转换带有粗体头部位的原始基础地址 (base 16)：

```
$ bech32 <<< addr_test1qqq40ucy70wms9p7tku6ntcamzuuxnsaejal7p82qcahh3ryswkc5djr3z37lhv3zjytgyfpf8en2pa4cfuvqdz4za8syv5dnc
000157f304f3ddb8143e5db9a9af1dd8b9c34e1dccbbff04ea063b7bc46483ad8a364388a3efdd911488b4112149f33507b5c278c03455174f
```

转换带有粗体头部位的原始质押地址 (base 16)：

```
$ bech32 <<< stake_test1upjg8tv2xepc3gl0mkg3fz95zys5nue4q76uy7xqx323wncxv6f68
e06483ad8a364388a3efdd911488b4112149f33507b5c278c03455174f
```

| **十六进制** | **二进制** | **十六进制** | **二进制** | **十六进制** | **二进制** | **十六进制** | **二进制** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 0 | 4 | 100 | 8 | 1000 | C | 1100 |
| 1 | 1 | 5 | 101 | 9 | 1001 | D | 1101 |
| 2 | 10 | 6 | 110 | A | 1010 | E | 1110 |
| 3 | 11 | 7 | 111 | B | 1011 | F | 1111 |

**表 3.5：** 十六进制转换

## UTXO

Cardano 和 Bitcoin 使用相似的未花费交易输出 (UTXO) 模型，而像 Ethereum 这样的区块链则使用基于账户的模型。在 UTXO 模型中，一笔交易消耗一个或多个 UTXO 作为输入，并产生一个或多个 UTXO 作为输出，每个 UTXO 都锁定在一个地址上。一个 UTXO 只能被花费（使用）一次，如果它已被用作交易输入，则不再是*未花费*的交易输出。某地址上的资产总量是该特定地址上所有 UTXO 的总和。此外，只有 Alice 可以花费 Alice 地址上的 UTXO，因为她拥有私钥，可以创建 `signature` 来证明这一点。

![](images/Figure-3.2.jpg)

**图 3.2：** UTXO 模型

在**图 3.2**中，Alice 拥有一个包含 10 Ada 的 UTXO，并想向 Bob 发送 2 Ada。创建一笔交易，将包含 10 Ada 的 UTXO 用作输入，并创建 2 个新的 UTXO 作为输出。包含 2 Ada 的 UTXO 将发送到 Bob 的地址，0.17 Ada 用于支付交易费用，剩余的 Ada（找零）将作为 UTXO 返回给 Alice。这与在实体钱包中用一张 10 美元的钞票在商店购买一瓶 2 美元的水的工作方式相同。

