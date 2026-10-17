
1. 交易平台作为买卖双方的托管方。卖家锁定他们的比特币，使得如果买家、卖家和托管方中任意两方同意卖家已收到款项，则比特币释放给买家。该平台实现了 `m-of-n` 多签。

2. 可以通过查看地址的 **前缀** 来判断该地址与 P2PKH 还是 P2SH 脚本相关，主网 P2PKH 为 `1`，主网 P2SH 脚本为 `3`。

3. P2SH 脚本在执行 `scriptSig` 和 `scriptPubKey` 之外，还通过执行 **赎回脚本** 进行验证。

# 第 11 章：智能合约和其他有用的交易

在上一章中，您学习了如何验证和创建交易。您还学习了如何在发布前检查其输入、输出和正确性，并了解了发布交易的不同方式。在本章中，您将更深入地学习脚本。您将学习如何使用脚本语言和 Bitcoin 交易的其他属性来实现简单但有趣的用例。

当我们想到智能合约时，我们会想到 Ethereum、Cardano、Binance Smart Chain 等。我们忽略了率先开创智能合约的网络，即 Bitcoin。Bitcoin 是最安全的加密货币网络。由于智能合约和数字资产可能非常有价值，如果在技术上可行，在 Bitcoin 网络上保护它们可能是最佳选择。

在本章中，我们将更深入地探讨脚本，并使用 Bitcoin 脚本语言为一些有用的智能合约构建用例。我们还将实现一些不是当事人之间合约但有助于解决实际需求的用例。

## 结构

在本章中，我们将涵盖以下主题：

* 脚本操作码
* 数字资产
    * 文档时间戳
* 时间锁定交易
    * 时间锁定支付
    * 具有相对锁定时间的支付
* 智能合约
    * 支付中的信任问题解决方案
        * 简单多签支付
        * 改进的相对锁定时间支付
        * 涉及托管的支付
    * 涉及秘密标识符的支付
* 协作交易
    * 慈善用例
    * 补贴用例
* 团体内的计划性贡献

## 目标

本章旨在帮助您理解比特币脚本语言的更广泛范围。此外，它将帮助您学习为不同场景创建交易，包括智能合约和前几章未涵盖的其他实用交易。

## 脚本操作码

在上一章中，我们仅使用了标准 P2PKH 和 m-of-n 多重签名 P2SH 脚本中使用的少数操作码。虽然这些对于个人和团体之间的基本资金转账已足够，但更复杂的脚本可能需要更多操作码。在本章中，我们将使用更多操作码。

### 数字资产

数字资产或数字财产是资产的数字化表现形式。该财产可表示为二维码、标识符、规格哈希或价值哈希。资产所有权可由资产所有者变更。也可在线出借或出租。利用比特币交易和脚本语言，我们可以实现其中一些功能。时间戳记是数字资产管理的重要属性之一，我们将在本子主题中介绍。

#### 文档时间戳记

为文档加盖时间戳记是使其具有法律约束力并成为合同一部分的必要条件。区块中的交易可与该区块的时间戳记相关联，且不可篡改。如果一笔交易包含文档内容的哈希值，则可视为该文档已加盖时间戳记。然而，要使其具有法律约束力，政府需要承认比特币区块链既不可篡改，又拥有正确的时间戳记。

以下是我女儿写的一篇短篇故事，我们将为其生成哈希值并将其添加到交易中：

> **好朋友午餐派对**：一天，两个好朋友——一只猴子和一只鳄鱼——决定在农场一起吃午餐。第二天，它们过河到达农场。饱餐一顿后，猴子站起来大声咆哮。受惊的鳄鱼恳求猴子停下来。但猴子说：“我饭后咆哮是个习惯，我控制不了。” 返程过河时，猴子骑在鳄鱼背上。游到河中央时，鳄鱼突然潜入水中。猴子吓坏了，鳄鱼说：“我饭后潜水是个习惯，我控制不了。” 猴子明白了自己的错误。

该故事的 SHA256 哈希值：

`3365b392ee14def189190638a532f6042446b74c98f186e9b595f77e47817e05`

以下是获取上述故事哈希值的代码：

```python
def contentHash(story: str):
    content_h = hashlib.sha256(story.encode('ascii')).digest()
    return content_h
```

要将其添加到交易中，我们需要支付少量网络费，将比特币从一个地址转移到另一个地址，并使用 `OP_RETURN` 来记录上述哈希值。

我们生成第一个区块，并将新挖出的比特币发送到一个地址，如图 11.1 所示：

![](img/Figure-11.1.jpg)

**图 11.1：** 生成的区块哈希

以下是新挖出区块中包含的交易：

![](img/Figure-11.2.jpg)

**图 11.2：** Coinbase 交易的交易 ID

在第 10 章“创建和验证交易”的“构建 P2PKH 交易”主题中，我们创建了一个包含两个输入和两个输出的 P2PKH 交易。我们修改代码以同时支持 `OP_RETURN` 输出。

以下代码为交易构建程序提供交易结构：

```python
def createTransactionStruct():
    txn = {}
    txn['version'] = 1
    txn['input_count'] = 1
    txn['inputs'] = []
    input0 = {}
    input0['prevtxn'] = '5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f'
    input0['prevtxnindex'] = 0
    input0['script_type'] = 'P2PKH'
    input0['privkeys'] = ['KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53']
    input0['script_pubkey'] = '76a91481d7033c19dcec645cb3f86ce41678756850ba4d88ac'
    input0['hash_type'] = SIGHASH_ALL
    txn['inputs'].append(input0)
    txn['out_count'] = 2
    txn['outputs'] = []
    output0 = {}
    output0['satoshis'] = 4999900000
    output0['script_type'] = 'P2PKH'
    output0['address'] = 'mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ'
    txn['outputs'].append(output0)
    output1 = {}
    output1['satoshis'] = 0
    output1['script_type'] = 'OP_RETURN'
    output1['content_hash256'] = '3365b392ee14def189190638a532f6042446b74c98f186e9b595f77e47817e05'
    txn['outputs'].append(output1)
    txn['locktime'] = 0
    return txn
```

**程序 11.1：** 文档时间戳记的交易结构定义

`OP_RETURN` 操作码的值如下：

`OP_RETURN = 0x6a`

在第 10 章“创建和验证交易”的“构建交易”主题中，我们定义了 `createSignaturePreimage()` 和 `createSignedTransaction()` 方法。我们向该方法添加以下行以处理 OP_RETURN 脚本类型：

```python
if outp['script_type'] == 'OP_RETURN':
    content_b = bytes.fromhex(outp['content_hash256'])
    scriptPubkey_b = bytes([OP_RETURN]) \
     + getWithPushdata(content_b)
```

正如我们在第 10 章“创建和验证交易”中所做的那样，我们执行此程序并获取原始交易十六进制代码，如图 11.3 所示：

![](img/Figure-11.3.jpg)

**图 11.3：** 为文档加盖时间戳记而创建的交易十六进制代码

以下是新创建交易的输出：

![](img/Figure-11.4.jpg)

**图 11.4：** 为文档时间戳记创建的交易输出

现在，我们需要再挖掘 100 个区块，以便我们使用的挖矿比特币准备好进行转账：

![](img/Figure-11.5.jpg)

**图 11.5：** 挖掘接下来的 100 个区块

现在，发布新创建的交易：

![](img/Figure-11.6.jpg)

**图 11.6：** 发布文档时间戳记交易

现在，我们再次挖掘一个区块，将交易添加到新挖出的区块中：

![](img/Figure-11.7.jpg)

**图 11.7：** 挖掘下一个区块以包含已发布的交易

以下是新挖出的区块。我们可以看到该区块包含新添加的交易：

![](img/Figure-11.8.jpg)

**图 11.8：** 已发布的交易出现在新区块中

### 时间锁定交易

比特币允许您将交易锁定特定时间或区块高度。它允许交易按固定时间或相对于资金交易的相对时间进行锁定。

在以下小节中，我们将介绍固定时间锁和相对时间锁的用例。

#### 时间锁定支付

我们还可以创建在给定时间戳之前无法花费的交易。这是通过设置交易中的 `nLockTime` 字段来完成的。`nLockTime` 字段既可以设置为表示区块高度，也可以设置为表示 Unix 纪元时间。在纪元时间的情况下，它表示过往时间中位数，而非区块的时间戳。

`nLockTime` 字段遵循以下规则：

* `nLockTime` < 500000000 表示区块高度
* 否则，表示过往时间中位数

建议不要将 `nLockTime` 设置为零、过去的区块高度或过去的区块时间。

> *过往时间中位数 = (Tn-1, Tn-2, Tn-3, Tn-4, … Tn-10, Tn-11) 的中位数*

以下代码为交易构建程序提供交易结构：

```python
def createTransactionStruct():
    txn = {}
    txn['version'] = 1
    txn['input_count'] = 1
    txn['inputs'] = []
    input0 = {}
    input0['prevtxn'] = '5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f'
    input0['prevtxnindex'] = 0
    input0['script_type'] = 'P2PKH'
    input0['privkeys'] = ['KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53']
    input0['script_pubkey'] = '76a91481d7033c19dcec645cb3f86ce41678756850ba4d88ac'
    input0['hash_type'] = SIGHASH_ALL
    txn['inputs'].append(input0)
    txn['out_count'] = 1
    txn['outputs'] = []
    output0 = {}
    output0['satoshis'] = 4999900000
    output0['script_type'] = 'P2PKH'
    output0['address'] = 'mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ'
    txn['outputs'].append(output0)
    txn['locktime'] = 1624196667
    return txn
```

**程序 11.2：** 时间锁定支付的交易结构定义

我们得到以下已签名交易，用于前述交易结构：

![](img/Figure-11.9.jpg)

**图 11.9：** 创建时间锁定支付的交易

为了能够发布前述交易，新创建区块中的比特币需要可用于花费。为此，我们再创建 100 个区块。

我们现在尝试发布交易，如图 11.10 所示：

![](img/Figure-11.10.jpg)

**图 11.10：** 发布时间锁定交易失败

发布交易失败，因为区块中位时间戳小于我们在交易中设置的锁定时间：

![](img/Figure-11.11.jpg)

**图 11.11：** 当前时间戳和上一个区块的时间戳

中位时间戳是通过取最近 11 个区块中区块时间戳的中位数来计算的。为了获得一个大于交易中设置的锁定时间的中位时间戳值，我们等待几分钟并再创建 11 个区块：

![](img/Figure-11.12.jpg)

**图 11.12：** 挖掘接下来的十一个区块以改变中位时间

现在，最近生成区块的中位时间如下：

![](img/Figure-11.13.jpg)

**图 11.13：** 获取中位时间

此时间戳大于 1624196667：

![](img/Figure-11.14.jpg)

**图 11.14：** 中位时间与日期的对比

我们再次尝试发布交易：

![](img/Figure-11.15.jpg)

**图 11.15：** 现在发布交易成功

我们可以看到，在最新区块的中位时间戳不小于或等于锁定时间之前，该交易无效。

#### 相对锁定时间的支付

交易中的 `nLockTime` 字段设置为静态区块高度或静态纪元时间。如果新创建的交易需要等待相对于依赖区块的区块计数或时间戳的时间或区块计数，则我们使用 `OP_CHECKSEQUENCEVERIFY`。

相对锁定时间合约是通过将 `OP_CHECKSEQUENCEVERIFY` 操作码作为脚本来实现的，因此我们使用带有赎回脚本的 P2SH。该操作码要求为相应的交易输入设置序列号。

相对锁定时间是一个软分叉，要求交易的版本号设置为 2。它还导致了 `nSequence` 评估方式的变化。

软分叉之前：

* 如果 `nSequence` 为 `0xFFFFFFFE`，表示设置了 `nLockTime`。
* 如果 `nSequence` 为 `0xFFFFFFFF`，表示未设置 `nLockTime`。

下图显示了软分叉后 `nSequence` 的评估方式：

![](img/Figure-11.16.jpg)

**图 11.16：** nSequence 评估示意图

以下是需要根据其设置序列值的条件：

* 如果 `nSequence` > `0xEFFFFFFF`，则未定义，因此交易可以包含在任何区块中。
* 如果 `nSequence` <= `0xEFFFFFFF`，则第 22 位决定第 0-15 位表示区块高度还是时间戳。
    * 如果第 22 位被设置，则第 0-15 位表示区块高度。
    * 如果第 22 位未被设置，则第 0-15 位表示中位时间。

这在以下代码中实现：

```python
def getSequence(txn_struct: dict, i: int):
    inp = txn_struct['inputs'][i]
    if 'sequence_type' in inp:
        if inp['sequence_type'] == 'time':
            sequence = inp['sequence'] | (1 << 22)
        else:
            sequence = inp['sequence']
        sequence_b = struct.pack('<L', sequence)
    else:
        if txn_struct['locktime'] > 0:
            # sequence
            sequence_b = bytes([0xfe, 0xff, 0xff, 0xff])
        else:
            # sequence
            sequence_b = bytes([0xff, 0xff, 0xff, 0xff])
    return sequence_b
```

**程序 11.3：** 计算 nSequence 的方法

为了用相对锁定时间实现一个简单的用例，在我们的用例中，新创建的交易只能在资金交易确认后的 105 个区块之后被挖掘。

这是该交易的赎回脚本：

```
105 OP_CHECKSEQUENCEVERIFY OP_DROP
<Alice pubkey> CHECKSIG
```

这是该交易所需的操作码：

`OP_CHECKSEQUENCEVERIFY = 0xb2`
`OP_DROP = 0x75`
`OP_CHECKSIG = 0xac`

以下代码用于生成赎回脚本十六进制代码：
