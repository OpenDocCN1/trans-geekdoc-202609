
大多数关于错误检测码的研究仅适用于字符集大小为素数幂的情况，而 58 不是。

Base58 解码既复杂又相对缓慢。

bech32 字符串最长 90 个字符，由以下部分组成：

*   **人类可读部分** 用于向读者传达数据类型或其他任何相关信息。此部分必须包含 1-83 个 US-ASCII 字符，每个字符的值在 `[33-126]` 范围内。特定应用可能会进一步限制 HRP 的有效性。
*   **分隔符** 始终为 `1`。如果 `1` 允许出现在人类可读部分中，则字符串中的最后一个 `1` 为分隔符。
*   **数据部分** 至少 6 个字符长，仅由字母数字字符组成，不包括 `1`、`b`、`i` 和 `o`。

我们将使用以下 Python 库进行 bech32 编码和解码：

![](images/Figure-12.18.jpg)

**图 12.18：** 新 Segwit 地址所需的 PIP 包

正如我们所了解的，在原生 SegWit 交易中，`previous scriptPubKey` 具有以下格式：

`<1-byte witness version> <2-40 bytes witness program>`

当前版本为 0，对于 P2WPKH，见证程序为 20 字节；对于 P2WSH，见证程序为 32 字节。

以下是我们在前面章节中讨论的原生 P2WPKH 交易示例中的 previous scriptPubkey：

`Previous scriptPubkey: 0x0014122bf8b77dceee01c0fa1f2b36d155fea2a5b016`

`=> witness version = 0x00`

`=> witness program size = 0x14 = 20-bytes`

`=> witness program = 0x122bf8b77dceee01c0fa1f2b36d155fea2a5b016`

以下程序对见证程序进行编码并打印地址：

```
import bech32

witprog = bytes.fromhex('122bf8b77dceee01c0fa1f2b36d155fea2a5b016')
witver = 0x00
hrp = 'bc'
address = bech32.encode(hrp, witver, witprog)
print(address)
```

**程序 12.13：** 为原生 SegWit 地址生成 bech32 地址

在上述程序中，`hrp` 代表 **human-readable-part**。以下是对应网络的 HRP 代码：

| **HRP codes** | **Network** |
| --- | --- |
| bc | Mainnet |
| tb | Testnet |
| tb | Regtest |

**表 12.1：** 比特币网络的 HRP 代码

运行程序后，我们得到以下地址：

![](images/Figure-12.19.jpg)

**图 12.19：** 从私钥生成的 bech32 地址

我们可以通过使用 Bitcoin Core 客户端在区块链中查看对应的交易来检查地址是否正确。以下是 `txid 6f7184d3b59adf06290686c6e4f7b7aeb0e7c869f05ca04d10a4b1636277fc40` 的输出索引 1：

![](images/Figure-12.20.jpg)

**图 12.20：** 显示交易输出中的 bech32 地址

现在，我们将为原生 P2WSH 执行相同操作。我们使用前面章节示例中使用的 P2WSH 交易，其中：

`Previous scriptPubkey = 0020d0862d6e40d240ea1711f6d897f5e7b07e974a593704077edffb7b67fd34b091`

因此，

`witness version = 0x00`

`=> witness program size = 0x20 = 32-bytes`

`=> witness program =`

`0xd0862d6e40d240ea1711f6d897f5e7b07e974a593704077edffb7b67fd34b091`

这是获取对应 P2WSH 的 bech32 地址的程序：

```
witprog = bytes.fromhex('d0862d6e40d240ea1711f6d897f5e7b07e974a593704077edffb7b67fd34b091')
witver = 0x00
hrp = 'bc'
address = bech32.encode(hrp, witver, witprog)
print(address)
```

这将给我们以下地址：

![](images/Figure-12.21.jpg)

**图 12.21：** 从私钥生成的 bech32 地址

在上述程序中，我们查看的是 `txid` 索引 0 处的前一个 `txid`：

`dffe1dc8f36cbc39c0f40b090912c5a00da13e3534f97aec0ef5bfe552019897`

通过使用 Bitcoin Core 客户端查看前一个 `txid` 的 `outindex`，我们得到以下 previous scriptPubkey 和对应地址：

![](images/Figure-12.22.jpg)

**图 12.22：** 显示交易输出中的 bech32 地址

以下是解密 bech32 地址的代码：

```
witver, witprog_l = bech32.decode(address[:2], address)
witprog_b = bytes(witprog_l)
scriptpubkey_b = bytes([witver]) + bytes([len(witprog_b)]) + witprog_b
print('scriptpubkey = ', scriptpubkey_b.hex())
```

**程序 12.14：** 解码 bech32 地址以获取 scriptpubkey

使用它来解码以下执行中 P2WPKH 的 bech32 地址：

![](images/Figure-12.23.jpg)

**图 12.23：** 解码 bech32 地址以获取 scriptpubkey

并使用它来解码以下执行中 P2WSH 的 bech32 地址：

![](images/Figure-12.24.jpg)

**图 12.24：** 解码 bech32 地址以获取 scriptpubkey

这标志着本章的结束，我们很可能已经涵盖了隔离见证增强的所有方面。

# 结论

在本章中，您了解了隔离见证增强。您学习了它为何重要以及它对整个比特币的影响。此外，您还了解了随此增强发生的几项变更，例如我们改变了查看网络增强的方式。本章涵盖了新的地址编码算法，并教您如何编码和解码地址。您学习了验证 SegWit 引入的新标准交易脚本，了解了交易结构，并验证了它们及签名。

在下一章中，我们将介绍闪电网络，它既是比特币的一部分，又是一个独立的发展。它是一个第二层协议，可以提供比特币设计上所缺乏的速度。这是可扩展性方面的一项重要发展。

# 要点回顾

*   比特币最初存在多个交易延展性漏洞。
*   BIP62 是解决交易延展性问题的原始变通方案，实现起来很繁琐。
*   交易延展性使得未确认交易即使对交易签名者也是不可靠的。
*   隔离见证通过将签名移出交易 ID 计算解决了所有交易延展性问题。不参与交易 ID 计算的部分称为见证数据。
*   隔离见证作为软分叉实施。
*   SegWit 激活遵循 BIP 9。
*   创建了 BIP 148，以便在算力多数不激活与隔离见证相关的 BIP（即 BIP 141、BIP 143 和 BIP 147）时强制部署 SegWit。这是首次使用 **用户激活软分叉** (**UASF**) 来强制功能激活。
*   UASF 是由经济多数而非算力多数强制执行的激活规则。
*   隔离见证 Merkle 根是通过获取区块中所有交易的完整交易哈希、在哈希前添加 32 字节零并计算 Merkle 根来得出的。
*   计算出的隔离见证 Merkle 根哈希与 witness-reserve-value（由矿工在币基交易的第一个输入中提供）拼接后的哈希决定了 commitment-hash，它位于币基交易的输出之一中。
*   SegWit 允许区块大于 1 MB，因为见证数据中的字节按其大小的四分之一计算。因此，比特币软件改变了计算字节的方式。在这种计算中，大小保持在 1 MB 以内，即使实际大小可能超过 1 MB。
*   使用隔离见证创建交易可减少所需的网络费用。
*   SegWit 引入了四种新的标准脚本：P2WPKH、P2WSH、P2SH-P2WPKH 和 P2SH-P2WSH。
*   原生 SegWit 脚本哈希和公钥哈希使用 bech32 编码。
*   SegWit 地址具有可扩展的方案，包含版本，当前版本为 0。
*   SegWit 交易签名使用与非 SegWit 交易不同的消息格式生成。此消息格式定义在 BIP143 中。

# 问题
