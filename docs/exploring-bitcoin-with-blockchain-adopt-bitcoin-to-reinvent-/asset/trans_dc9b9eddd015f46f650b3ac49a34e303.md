

# 扩展公钥和私钥

如果我们拥有根密钥的密钥和链码，就可以为密钥派生层级中的特定深度和索引生成 xpub 和 xprv。

在以下代码中，我们为给定的深度和索引生成 xprv 和 xpub：

```python
XPUB_VERSION = '0488B21E'
XPRV_VERSION = '0488ADE4'
TPUB_VERSION = '043587CF'
TPRV_VERSION = '04358394'

def getMasterXPrv(chaincode_b: bytes, privkey: int):
    version_b = bytes.fromhex(TPRV_VERSION)
    depth_b = b'\x00'
    fingerprint_p_b = bytes(4)
    index_b = bytes(4)
    privkey_b = bytes.fromhex('%066x' % privkey)
    raw_xprv = depth_b + fingerprint_p_b + index_b + chaincode_b + privkey_b
    xprv = base58checkEncode(version_b, raw_xprv)
    return xprv

def getMasterXPub(chaincode_b: bytes, pubkey: str):
    version_b = bytes.fromhex(TPUB_VERSION)
    depth_b = b'\x00'
    fingerprint_p_b = bytes(4)
    index_b = bytes(4)
    pubkey_b = bytes.fromhex(pubkey)
    raw_xpub = depth_b + fingerprint_p_b + index_b + chaincode_b + pubkey_b
    xpub = base58checkEncode(version_b, raw_xpub)
    return xpub
```

**程序 9.17：** 派生主 XPrv 和主 XPub 的程序

我们按如下方式调用该方法：

```python
xprv = getMasterXPrv(chaincode, privkey)
print('xprv=%s' % xprv)
pubkey_b = privkeyHex2pubkey(privkey_s, True)
xpub = getMasterXPub(chaincode, pubkey_b.hex())
print('xprv=%s' % xpub)
```

我们得到以下主 xpub 和 xprv：

![](images/Figure-9.26.jpg)

**图 9.26：** 显示主密钥的 xprv 和 xpub

在以下代码中，我们为给定的深度和索引生成 xprv 和 xpub：

```python
def getXPrv(p_pubkey: str,
            chaincode_b: bytes,
            privkey: int,
            depth: int,
            index: int):
    version_b = bytes.fromhex(TPRV_VERSION)
    p_pubkey_b = bytes.fromhex(p_pubkey)
    privkey_b = bytes.fromhex('%066x' % privkey)
    depth_b = bytes([depth])
    p_fingerprint_b = hash160(p_pubkey_b)[0:4]
    index_b = struct.pack('>L', index)
    raw_xprv = depth_b + p_fingerprint_b + index_b + chaincode_b + privkey_b
    xprv = base58checkEncode(version_b, raw_xprv)
    return xprv

def getXPub(p_pubkey: str,
            chaincode_b: bytes,
            pubkey: str,
            depth: int,
            index: int):
    version_b = bytes.fromhex(TPUB_VERSION)
    p_pubkey_b = bytes.fromhex(p_pubkey)
    pubkey_b = bytes.fromhex(pubkey)
    depth_b = bytes([depth])
    p_fingerprint_b = hash160(p_pubkey_b)[0:4]
    index_b = struct.pack('>L', index)
    raw_xpub = depth_b + p_fingerprint_b + index_b + chaincode_b + pubkey_b
    xpub = base58checkEncode(version_b, raw_xpub)
    return xpub
```

**程序 9.18：** 为给定深度和索引生成 XPub 和 XPrv 的程序

我们按如下方式调用该方法：

```python
# 我们正在为 index=1 和 depth=1 进行计算
child_xprv = getXPrv(pubkey_b.hex(), child_chaincode, child_privkey_i, 1, 1)
print('child xprv:')
print(child_xprv)
child_xpub = getXPub(pubkey_b.hex(), child_chaincode, child_pubkey_b.hex(), 1, 1)
print('child xpub:')
print(child_xpub)
```

我们得到给定密钥的以下 xprv 和 xpub：

![](images/Figure-9.27.jpg)

**图 9.27：** 显示子 xprv 和子 xpub

我们可以将 `xpub` 注册到钱包中，以便监控涉及生成地址的交易。`BitcoinJ` 就是接受 `xpub` 用于监控地址的钱包之一。生成的 `xprv` 可用于生成子私钥公钥对以签署交易。你永远不应该在任何地方暴露或使用 `xprv`，甚至应避免使用 `xpub`。始终在私密环境下生成这些地址，并将单个地址注册到钱包中以进行监控。这将防范丢失比特币的风险。

# 密钥派生路径

正如我们现在所知，分层确定性钱包的优势在于我们可以确定性地在任意深度和任意索引派生密钥。为了能够在层级结构中定位密钥，HD 钱包使用一种称为密钥派生路径的表示法。

以下是密钥派生路径的表示法：

*   主密钥用 `m` 表示。
*   普通密钥用索引号 `0` 到 `2^(31)-1` 表示。
*   加固密钥用索引号 `2^(31)` 到 `2^(32)-1` 表示。
*   深度分隔符是正斜杠 `/`。

例如，密钥派生路径可能如下所示：

`m/45/78'/56/9'`

这里，`78'` 和 `9'` 是加固密钥，而 `45` 和 `56` 是普通密钥。

下图展示了包含加固密钥的密钥派生：

![](images/Figure-9.28.jpg)

**图 9.28：** 带加固密钥的密钥派生

在上一节中，你了解到加固密钥更安全，但也更不方便使用。

> **提示：** 为了降低风险，我们可以将底层设为普通派生，这意味着 `xpub` 将有助于生成子索引。然而，我们也将父级设为加固派生，因此如果一个子私钥暴露，它将暴露同一父级下其他子密钥的密钥。但由于父级是加固的，它将不允许派生父级深度处其他索引的私钥。我们可以将每个父级下的子密钥数量限制在较小的数字，如 20。因此，每次私钥暴露，我们只会丢失 20 个地址。我们可以进一步仅在每个地址中保留有限的比特币，使得丢失它们不算大的损失。
>
> 这可能是一个方便的折中方案，但它不是比特币的好选择，因为比特币是一种高价值且高网络手续费的加密货币。这意味着以极小数量存储成本很高，即使丢失小面额也是重大损失。简而言之，比特币不适合小额交易、交易和低安全性场景。这种策略可能适用于网络手续费不高的其他加密货币。

# 结论

在本章中，你首先了解了钱包的必要性。然后你学习了对钱包进行分类的不同方式，并专注于根据 `BIP32` 规范实现分层确定性钱包。在实现过程中，你了解了私钥的生成和结构。你学会了派生公钥和地址，并为 `mainnet` 和 `testnet` 生成 `P2PKH` 和 `P2PSH` 地址。你还学会了生成易于记忆、保存和书写的密码，称为助记词列表。你使用助记词通过派生路径确定性地生成私钥。在本章中，我们还讨论了如何权衡安全性和便利性。我们没有讨论椭圆曲线密码学，因为我们将在后续章节中更详细地探讨它。

在下一章中，你将学习创建最广泛使用的交易类型。你将学习对交易进行签名并验证接收到的交易。验证过程将涉及查看存储在 `LevelDB` 数据库中的内存池和 UTXO。

# 要点回顾

*   钱包是一种存储私钥、公钥和地址，或具有按需生成它们能力的软件程序。
*   钱包可以显示一个人持有的比特币数量，也可以在将交易发布到网络之前对其进行签名。
*   助记词列表可以是 12/18/24 个单词。记忆和输入 12 个单词更容易，但 24 个单词的代码更安全。
*   要生成安全的助记词，我们需要生成一个良好的随机数。要生成良好的随机数，我们需要找到合适的熵源。
*   `Pbkdf2` 是一个密钥派生的迭代过程，迭代次数越多，派生出的密钥对暴力破解攻击就越安全。
*   推荐的 `Pbkdf2` 迭代次数大于 10000，但次数越多，生成所需的时间就越长。
*   扩展密钥提供了一种编码方法，如果受支持，可以允许钱包使用给定的扩展密钥生成所需的私钥或公钥。
*   `BIP32` HD 钱包支持普通密钥和加固密钥的派生。

