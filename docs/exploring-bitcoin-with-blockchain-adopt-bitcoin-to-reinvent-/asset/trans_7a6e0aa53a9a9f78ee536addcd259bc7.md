
上图展示了如何使用消息和私钥创建签名。对于 `SIGHASH_ALL`，我们通过获取新交易的所有元素来创建消息。然后我们将 `scriptSig` 和 `scriptSig` 长度替换为正在执行的脚本，对于 P2PKH 而言，即待签名输入索引的前一个 `scriptPubKey` 和 `scriptPubKey` 长度。对于其他输入，`scriptSig` 长度被替换为零，因为这些输入未被签名。对于 P2SH 脚本，`scriptSig` 及其长度被替换为赎回脚本及其长度。在消息末尾，我们添加 sighash 类型。

## 哈希类型 – SIGHASH_NONE、SIGHASH_SINGLE、SIGHASH_ANYONECANPAY

下图展示了其他 sighash 类型待签名消息的结构：

![](images/Figure-10.5.jpg)

**图 10.5：** 除 SIGHASH_ALL 之外的 sighash 类型的签名预映像

对于 `SIGHASH_ANYONECANPAY`，只有被签名的输入是待签名消息的一部分，其他输入不包含在内。对于 `SIGHASH_NONE`，不包含任何输出；对于 `SIGHASH_SINGLE`，仅包含一个输出。我们可以观察到，在 `SIGHASH_SINGLE` 的情况下，输出索引与正在被签名的输入相对应。这意味着，如果签名输入 0，则包含输出 0 并排除输出 1。如果签名输入 1，则包含输出 1 并排除输出 0。如果被排除的输出不是消息的最后一个输出，则我们需要通过保留 `0xFFFFFFFFFFFFFFFF` 和 `0x00`（如图所示）来将被排除的输出作为占位符保留。在 `SIGHASH_NONE` 和 `SIGHASH_SINGLE` 中，未被签名的输入的序列号被替换为 `0x00000000`。

## 标准比特币脚本 - P2PK

不推荐使用 P2PK。P2PK 代表 **Pay-2-Public-Key（付款至公钥）**。

在此脚本中，`scriptSig` 为：

` <签名>`

而 `scriptPubKey` 为：

` <公钥> OP_CHECKSIG`

其执行过程简单：首先执行 `scriptSig`，将签名压入栈中；然后执行 `scriptPubKey`，将公钥压入栈中，接着 `OP_CHECKSIG` 通过弹出签名和公钥进行验证，并将结果压回栈中。

该脚本有几个缺点：

*   压缩公钥长 32 字节，而 P2PKH 脚本使用的哈希长 20 字节，其十六进制表示为 40 个字符，输入起来容易得多。使用 base58check 编码从 20 字节生成的地址长 34 个字符。

*   如果量子计算机能利用一种称为 Shor 算法的量子技术，预计它们将能从公钥推导出私钥。为了让比特币在未来保持安全，我们不应在仍持有比特币的网络上暴露公钥。通过使用公钥哈希，我们拥有了多层安全机制来保护资金。

由于不推荐使用此脚本，因此深入了解它已无意义。

## 标准比特币脚本 – P2PKH

P2PKH 是最广泛使用的比特币脚本。P2PKH 代表 **Pay-2-Public-Key-Hash（付款至公钥哈希）**。在该脚本中，发送方使用公钥哈希锁定交易输出，要求接收方在需要使用交易输出中锁定的资金时提供公钥。该哈希长 20 字节，比 32 字节的压缩公钥更短。它生成一个 34 字符长的地址，其中包含校验和。这使得输入更容易，且由于包含校验和，不可能意外输入错误的地址。

P2PKH 中的 `scriptSig` 为：

` <签名> <公钥哈希>`

而 `scriptPubKey` 为：

` OP_DUP OP_HASH160 <20字节公钥哈希> OP_EQUALVERIFY OP_CHECKSIG`

由于 `<签名>` 和 `<公钥哈希>` 均为数据，两者均入栈。`scriptSig` 执行完毕后，执行 `scriptPubKey`。

下图展示了 P2PKH 的执行过程：

![](images/Figure-10.6.jpg)

**图 10.6：** P2PKH 的执行

## 准备签名预映像

所有消息末尾均包含 sighash 类型。消息签名完成后，sighash 类型会被追加到签名中，以帮助验证节点在验证前重建消息。

现在，我们准备验证一个真实的交易脚本。我们选取以下交易 ID：

`83eeaecaf531e5239ffc3ba7ff583c696f7dbe3610f0d672d41e0b9443632c82`

由于该交易在比特币区块链上，我们通过在 Bitcoin Core CLI 中调用 `getrawtransaction` 来获取原始交易，如下所示：

![](images/Figure-10.7.jpg)

**图 10.7：** 显示用于获取交易字节的 Bitcoin Core CLI 命令

这将给我们以下原始交易：

![](images/Figure-10.8.jpg)

**图 10.8：** 显示交易 ID 的十六进制数据

我们可以使用交易并通过 *[第 6 章，区块链、交易与挖矿](#c06.xhtml)* 中 *Transactions* 主题下 *Other transaction* 子主题的 *Program 6.15* 中编写的 `getTransactionInfo` 方法对其进行解析，以获取 `scriptSig`。

这将给我们以下信息：

`Transaction = {‘version’: ‘00000001’, ‘inp_cnt’: 2, ‘inputs’: [{‘prev_tx_hash’: ‘15b91bcf8b2b9ea46d0daab60aaa2e99b15a5fb37d9d4568d4c060e515e13130’, ‘prev_tx_out_index’: ‘00000001’, ‘bytes_scriptsig’: 106, ‘scriptsig’: ‘47304402205535a9ac25844514828bff3580120d5add488e09b7a6e62018fc265aabf95fe302200b66d4eb23fc348b31d58729b479ae73db9dfc467edf38f8dfd927c48cb46b5801210219fbee4b9cc12188598f244ff0ee352b124cbf9046180a1b25e020c0258f9d64’, ‘sequence’: ‘ffffffff’}, {‘prev_tx_hash’: ‘840ac7a55498c6746b9d7460a348f79e2f35db4a9696bef762d975e7e1deeff2’, ‘prev_tx_out_index’: ‘0000000c’, ‘bytes_scriptsig’: 106, ‘scriptsig’: ‘47304402203a28d10c786907fcb71c7bf69c507d58884ea9af2e7fa3b413d4e2867eca601502205fb253d82e4daa2672842ec031584ea7a215774422aa7de3cf8928c240e2faa60121030be5aa6d5de8c6dd89d6ac4d0e2a112caf5b12801349ab30fbdf2b205f0b94b8’, ‘sequence’: ‘ffffffff’}], ‘out_cnt’: 2, ‘outs’: [{‘satoshis’: 69302, ‘bytes_scriptpubkey’: 25, ‘scriptpubkey’: ‘76a914f133f0339987cd84b6017517de2a93f009728d7e88ac’}, {‘satoshis’: 12900349, ‘bytes_scriptpubkey’: 25, ‘scriptpubkey’: ‘76a91406c3bc40cde01312e2b24f8d2c23e68ea7d572f888ac’}], ‘locktime’: 0}`

以下程序进一步解析 `scriptSig` 以获取签名、 `sighash` 类型和公钥：

```
OP_PUSHDATA1 = 0x4c

OP_PUSHDATA2 = 0x4d

OP_PUSHDATA4 = 0x4e

SIGHASH_ALL = 0x01

SIGHASH_NONE = 0x02

SIGHASH_SINGLE = 0x03

SIGHASH_ANYONECANPAY = 0x80

def getHashTypeInWords(hashtype: int):
    hashtype_s = ""
    if hashtype & SIGHASH_SINGLE == 0x03:
        hashtype_s = "SIGHASH_SINGLE"
    elif hashtype & SIGHASH_NONE == 0x02:
        hashtype_s = "SIGHASH_NONE"
    elif hashtype & SIGHASH_ALL == 0x01:
        hashtype_s = "SIGHASH_ALL"
    if hashtype & SIGHASH_ANYONECANPAY == 0x80:
        hashtype_s = hashtype_s + "|" + "SIGHASH_ANYONECANPAY"
    return hashtype_s

def decodePushdata(script_m: mmap):
    length = int.from_bytes(script_m.read(1), byteorder='little')
    if length == OP_PUSHDATA1:
        length = int.from_bytes(script_m.read(1), byteorder='little')
    elif length == OP_PUSHDATA2:
        length = int.from_bytes(script_m.read(2), byteorder='little')
    elif length == OP_PUSHDATA4:
        length = int.from_bytes(script_m.read(4), byteorder='little')
    return length

def parseScriptSig(script_m: mmap):
    scriptsig = {}
    scriptsig['bytes_sig'] = decodePushdata(script_m)
    scriptsig['sig'] = script_m.read(scriptsig['bytes_sig'] - 1).hex()
    scriptsig['hash_type'] = int.from_bytes(script_m.read(1), byteorder='little')
    scriptsig['hash_type_name'] = getHashTypeInWords(scriptsig['hash_type'])
    scriptsig['bytes_pubkey'] = decodePushdata(script_m)
    scriptsig['pubkey'] = script_m.read(scriptsig['bytes_pubkey']).hex()
    return scriptsig
```

**程序 10.2：** Scriptsig 解析器

我们按如下方式调用上述方法：
