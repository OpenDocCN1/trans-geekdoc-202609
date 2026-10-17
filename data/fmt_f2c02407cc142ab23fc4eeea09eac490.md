
| KyWeQEcM2YdirR2E7JwxSRjfgNuWyt4DR3v4sGtPvmeZqhTxWVrp | 02d50250aa629914e3146a 5123a362a516c8aa95e5f0a6f3a078bd31fabe383abc | msV23rBcHAtQWSkWV9ph91DV65VduWi1Vt |

| Ky5CYfpeMkfFku7K4FvzeEwRmTJhWqD2eFiMnjLT7uw2oUVMgyg6 | 0319b4b9ab4732e78dab0e48c2c54fd57dd35350a0269f8c041807c3b798aa1872 | mnhWcUMqe9J1G4t3NMqNmLUqxfPTgwv7NK |

| L1cnATDVZyvuo9m6tprCmbr14vm3JeCbkc4Z2397ZM7P96N3d8GA | 039d5dbb6e052631c46e046c6d11fb95d257eae5093117d2c265aeb784dba4acf6 | mtRkMmpT6uhM9LXVPRk4ck9Gcaz9iuQgmZ |

| KyP1xynRgwrCUThXATVy5kbKqteAxisDFY74zrHozSGhb75hJ3M6 | 02dfa818542ab4685284f7c222d541e218aed0712fc9e63ca2802b15bb418383c9 | n2DfL6uEmPiwJBYjJRzyqUYDSTqxF8XSNS |

**表 10.3：** 一些测试地址、公钥和私钥

我们启动用于 `regtest` 的 Bitcoin Core 守护进程，如下所示：

```
bitcoind -regtest -printtoconsole –rpcuser=test –rpcpassword=test -txindex=1
```

### 构建 P2PKH 交易

然后我们连接守护进程并生成两个区块，将比特币发送到特定的 `regtest` 地址。

为此，使用带有 `regtest` 选项的 Bitcoin Core CLI 运行，提供可选参数 `rpcuser` 和 `rpcpassword`。`rpcuser` 和 `rpcpassword` 选项允许客户端建立 `rpc` 连接。使用 Python 包连接时需要此项，但使用 CLI 连接时不需要。

在以下 CLI 语句中，我们生成两个区块，每个新创建的区块向给定地址支付 50![](img/Bitcoin.jpg)。支付交易是包含在每个生成区块中的币基交易。

![](img/Figure-10.12.jpg)

**图 10.12：** 显示向给定地址支付的生成区块

我们从区块哈希中获取币基交易：

![](img/Figure-10.13.jpg)

**图 10.13：** 显示生成区块的币基交易

因此，我们现在有两笔交易，每笔持有 50 个 regtest 比特币：

`5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f`

`53793974d074e57305575d711fd0acd1d39f406264de234e686542ad2d0ddbfb`

我们还从第一笔交易输出中获取 `scriptPubKey`，如下所示：

![](img/Figure-10.14.jpg)

**图 10.14：** 显示从资金交易的第一个输出获得的 scriptPubKey

现在，区块链中有两个区块，每个区块有 50![](img/Bitcoin.jpg)。有一条规则规定币基交易在接下来的 100 个区块内不能被花费。如果网络遭受攻击，或者存在严重漏洞，需要重组比特币区块链，这条规则很有用。这意味着我们需要使挖掘近期区块的旧版软件失效，并部署修复问题的新软件。我们可能还需要使已挖出的某些区块失效。100 个区块给开发者近 16 小时来修复网络。过去，比特币开发者不得不执行两次重组，一次在 2010 年，一次在 2013 年。这显然会影响网络的可信度，我们不希望再次发生这种情况。

我们将直接再挖掘 100 个区块，如下所示，以便能够使用上述交易：

![](img/Figure-10.15.jpg)

**图 10.15：** 显示执行生成 100 个区块的命令

我们将使用这两笔交易中的锁定比特币，将它们发送到两个不同的地址，并留出 0.0001 个 regtest 比特币作为网络手续费。我们首先创建一个未签名的原始交易。以下代码定义了原始交易的结构：

```
def createTransactionStruct():
    txn = {}
    txn['version'] = 1
    txn['input_count'] = 2
    txn['inputs'] = []
    input0 = {}
    input0['prevtxn'] = \
```

### 构建 P2SH 交易

在本节中，我们将创建一笔交易并将其发布。为此，我们需要生成一个支付给 P2SH 地址的区块。P2SH 地址是通过生成赎回脚本的 hash160 来生成的。

我们使用以下方法生成赎回脚本：

```
OP_CHECKMULTISIG = 0xae

def createRedeemScript(pubkey_l: list, sigcount: int):
    redeem_script_b = bytes([0x50 + sigcount])
    for pubkey in pubkey_l:
        pubkey_b = bytes.fromhex(pubkey)
        redeem_script_b += encodePushdata(len(pubkey_b)) + pubkey_b
    redeem_script_b += bytes([0x50 + len(pubkey_l), OP_CHECKMULTISIG])
    return redeem_script_b
```

**程序 10.22：** 用于创建多重签名赎回脚本的方法

我们正在创建一个赎回脚本，它需要使用与三个公钥相关的私钥提供两个签名。因此，我们将使用 2-of-3 `multisig`。

我们在以下代码中传入三个公钥，所需的签名数量为 2：

```
if __name__ == '__main__':
    pubkey_l = ['037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7', '02fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d0', '02d50250aa629914e3146a5123a362a516c8aa95e5f0a6f3a078bd31fabe383abc']
    redeem_script_b = createRedeemScript(pubkey_l, 2)
    print('redeem script = %s' % redeem_script_b.hex())
    sh = hash160(redeem_script_b)
    address = sh2address(sh)
    print('P2SH address = %s' % address)
```

执行上述代码行后，我们得到以下结果：

![](img/Figure-10.23.jpg)

**图 10.23：** 显示使用赎回脚本生成的 P2SH 地址

我们使用前面的地址生成一个区块并接收比特币，如下所示：

![](img/Figure-10.24.jpg)

**图 10.24：** 显示支付给 P2SH 地址的生成区块

接下来，我们使用前面的 Bitcoin Core CLI 命令中的区块哈希来获取 coinbase 交易的交易 ID：

![](img/Figure-10.25.jpg)

**图 10.25：** 显示将支付给 P2SH 交易的 coinbase 交易

我们需要获取生成的交易结构，因为我们需要在交易中使用交易输出。

我们通过执行以下命令获取原始交易：

![](img/Figure-10.26.jpg)

**图 10.26：** 显示支付给 P2SH 地址的 coinbase 交易的十六进制数据

通过执行以下命令，我们从原始交易中获取交易结构：

![](img/Figure-10.27.jpg)

**图 10.27：** 显示获取交易十六进制数据内容的命令

以下是从前面的命令生成的原始交易的结构：

![](img/Figure-10.28.jpg)

**图 10.28：** 显示解码后的交易数据

我们使用为 P2SH 交易生成的交易的交易 ID 创建交易结构，如下所示：

```
def createTransactionStruct():
    txn = {}
    txn['version'] = 1
    txn['input_count'] = 1
    txn['inputs'] = []
    input0 = {}
    input0['prevtxn'] = \
    'de32b06aeb0103381df84d2cc5ea80a35b60bce0c6393bd9436cb395e3f47a5d'
    input0['prevtxnindex'] = 0
    input0['script_type'] = 'P2SH_Multisig'
    input0['privkeys'] = \
    ['L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ',
     'KxR8HHyfAwFPidCw2vXThXqT4vSMNeufirHFapnfCfkzLaohtujG']
    input0['redeem_script'] = '5221037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f72102fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d02102d50250aa629914e3146a5123a362a516c8aa95e5f0a6f3a078bd31fabe383abc53ae'
    input0['hash_type'] = SIGHASH_ALL
    txn['inputs'].append(input0)
    txn['out_count'] = 2
    txn['outputs'] = []
    output0 = {}
    output0['satoshis'] = 10*(10**8)
    output0['script_type'] = 'P2PKH'
    output0['address'] = 'mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ'
    txn['outputs'].append(output0)
    output1 = {}
    output1['satoshis'] = 399999*(10**4)
    output1['script_type'] = 'P2PKH'
    output1['address'] = 'miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo'
    txn['outputs'].append(output1)
    txn['locktime'] = 0 # block height
    return txn

if __name__ == '__main__':
    txn_struct = createTransactionStruct()
    txn_struct, signgrp_l, script_l = getSignaturesAndExecScripts(txn_struct)
    signed_txn_b = createSignedTransaction(txn_struct, signgrp_l, script_l)
    print(signed_txn_b.hex())
```

**程序 10.23：** 创建用作 P2SH 交易创建输入的交易结构的方法

这给出了以下签名交易：

![](img/Figure-10.29.jpg)

**图 10.29：** 显示将比特币从 P2SH 地址转移的签名交易

我们需要挖掘 100 个区块，然后才能从 Coinbase 交易输出中为交易提供资金，因此我们将再次执行 CLI 命令 `generatetoaddress`。在发布交易之前，我们可以测试交易是否有效。我们可以通过运行以下 Bitcoin CLI 命令来实现：

![](img/Figure-10.30.jpg)

**图 10.30：** 显示交易是否有效且可被内存池接受

我们可以看到该交易有效，如果发送，将被内存池接受。如果我们在真实的 Bitcoin 网络上工作，此命令可以通过验证一切正常来保护我们。

现在，我们可以按如下方式发布交易：

![](img/Figure-10.31.jpg)

**图 10.31：** 显示从 P2SH 地址移动比特币的交易已发布

我们得到了交易 ID `66ce54d909c9309d8bee5035b261c639ee8e274947b15a6ea2d540a12beea5d2`。因此，我们成功构建并发布了 P2SH 交易。

在本节中，您学习了如何使用交易结构中提供的信息来构建和发布交易。

这标志着本章的结束。

## 结论

在本章中，您了解了 Bitcoin 脚本语言、其特性及其执行过程。您学习了脚本语言如何用于交易验证。您了解了 Bitcoin 使用的不同脚本类型，并理解了 Bitcoin 脚本的原理和机制。此外，您还学习了如何创建交易并将其发布到 Bitcoin 网络。本章涉及相当多的编码工作。

在下一章中，您将学习并创建智能合约和其他有用的交易。

## 要点回顾

*   Bitcoin 交易通过包含哈希值的锁定脚本进行保护，如果我们想使用该交易为新创建的交易提供资金，则需要提供相应的脚本或公钥。
*   要创建新交易，我们还需要根据脚本类型和哈希类型的要求，通过对消息进行签名来提供签名。
*   Bitcoin 脚本语言基于`逆波兰表示法`（`Reverse Polish Notation`）。
*   当节点接收到新创建的交易时，它需要根据共识规则进行验证，并需要验证用于解锁 `scriptPubKey` 锁定资金的 `scriptSig`。
*   对于 P2PKH 脚本，`scriptSig` 首先执行，然后使用相同的堆栈执行来自前一个交易输出的 `scriptPubKey`。结果位于堆栈顶部。
*   对于 P2SH 脚本，在第一遍中执行 `scriptSig`，然后执行 `scriptPubKey`。在第三遍中，签名首先被压入堆栈，然后执行赎回脚本。
*   新创建的交易可以通过使用 Bitcoin Core 命令 `sendrawtransaction` 发布到 Bitcoin 网络。
*   如果您不想维护全节点，仍然可以使用 SPV 软件发布新创建的交易。此外，还有几个在线网站可以推送新交易。
*   在发送交易之前，我们可以使用 Bitcoin Core 命令 `decoderawtransaction` 对其进行解码，从而允许我们手动验证创建的交易。
*   我们还可以通过使用 Bitcoin Core 命令 `testmempoolaccept` 来检查创建的交易是否有效。
*   P2PKH 和 P2SH 脚本在锁定的资金被用于交易之前会隐藏公钥。
*   脚本语言提供了大量可用于编写复杂智能合约的操作码，但 P2SH 将这些复杂性对发送方隐藏。

## 问题

1.  编写程序以创建交易：
    1.  创建一个 P2PKH 交易，包含三个输入和三个输出；所有输入的 sighash 类型均为 `SIGHASH_ALL|SIGHASH_ANYONECANPAY`。
    2.  创建一个 P2PKH 交易，包含三个输入和三个输出。两个输入的 sighash 类型为 `SIGHASH_NONE|SIGHASH_ANYONECANPAY`，第三个输入的 sighash 类型为 `SIGHASH_ALL`。
    3.  创建一个 P2PKH 交易，包含三个输入和三个输出。两个输入的 sighash 类型为 `SIGHASH_SINGLE|SIGHASH_ANYONECANPAY`，第三个输入的 sighash 类型为 `SIGHASH_ALL`。

2.  编写一个通用程序，将任意 Bitcoin 交易脚本的十六进制代码转换为可读脚本。

3.  为什么所有交易至少要有一个输入使用 `SIGHASH_ALL` 签名？

4.  计算一笔交易的手续费，该交易从之前的交易中解锁两个 P2PKH 输出，并锁定两个 P2PKH 脚本输出，假设交易费率为 10 satoshi/字节。

5.  选择正确的 sighash 类型：
    1.  `SIGHASH_NONE|SIGHASH_ANYONECANPAY`
    2.  `SIGHASH_SINGLE|SIGHASH_ANYONECANPAY`
    3.  `SIGHASH_ALL|SIGHASH_ANYONECANPAY`
    1.  Renuka 在另一个国家找到了工作。她的朋友们计划共同出资，从一家接受比特币支付的商店购买一块手表。
    2.  一个社会服务组织正在为地震受害者购买衣物和食物。它要求人们通过提供已签名的交易输入来捐款。
    3.  一所学校想派其优秀学生参加全国学术会议。参会费用高昂，学校希望通过补贴参会费用来帮助家长分担成本。

6.  判断正误：
    1.  1-of-1 多签的 P2SH 脚本无效。
    2.  P2PKH 不允许使用未压缩公钥。
    3.  创建签名时，我们会得到两个 S 值，我们选择较小的 S 值。

7.  填空：
