

`tx_s = ‘010000000001024e453d886f11e3af494ce6073956b0de6eaed80865529ab45f778d660459907e2500000023220020ffc74359d1e79a79b94319a1695a68810e439e4c32e4c1be2b0b7c915ca78536ffffffff4e453d886f11e3af494ce6073956b0de6eaed80865529ab45f778d660459907e29000000232200207a21661b84ac4a34a6afc034030faba8ce8344635ebaf34cde31083f186bf871ffffffff02b02a02000000000017a9147b60c1eebfc2c78c9993668dab556344bf1f78d187d9df0500000000002200206f50cccbc64ea3f6cc434d5878bbe45a609e5592026ce6704f586a0e795a6ae40300483045022100d168fa78728fda205eee72ad7b789bc3153adeec982b2588a1526509aa1e2ae8022010443c0652848492dad4904f45258f5452256bfe23d9c715bf052d908154de6e0125512102972c9ea94bfcd5956220f2e99776b3c5ebcca9373a2eccb3fb5fff8bbc9f999451ae03004830450221009691361fa2953e54bc5287306c023fc2d098aa6e85ed1a66d3369e93781260b102201fb639437128d361a12ea385a61bd49247d25c254d1efc03d5272dd368c0acfa01255121027c6cbed24ad235fe147413272ba92cfd61d5ab338c4dabd74cbfb7d11746da5451ae00000000’`

`tx_b = bytes.fromhex(tx_s)`

`tx_m = bytes2Mmap(tx_b)`

`tx = getTransactionInfo(tx_m)`

`verifyScript(tx, 0)`

运行上述代码得到以下结果：

![](images/Figure-12.16.jpg)

**图 12.16：** 执行 Python 程序显示 P2SH_P2WSH 脚本有效

我们了解到，通过对 P2PKH/P2SH 交易验证程序进行简单修改，我们也可以验证隔离见证交易。我们仍然没有学习如何为签名验证创建正确的消息，因此我们将在下一个主题中探讨这一点。

# 签名验证

在本节中，我们将理解 BIP 143 以创建正确的签名预映像。所有具有相同 sighash 类型的隔离见证交易都具有相同的签名预映像创建方法。

签名预映像具有以下结构：

![](images/Figure-12.17.jpg)

**图 12.17：** 隔离见证交易的签名预映像结构

预映像的每个部分定义如下：

考虑到，

*   **TxIDprev**：上一笔交易的 TxID
*   **TxOutIndexprev**：输入中上一笔交易的输出索引
*   **output**：交易的输出
*   **‖**：拼接
*   **Hash256**：双重 SHA256 哈希

对于 sighash 类型 `SIGHASH_ALL`，我们有签名预映像每个部分的以下定义：

*   `hashPrevouts = Hash256(‖(TxID_prev∥ TxOutIndex[prev] ))`
*   `hashSequence = Hash256(‖(nSequence))`
*   `outpoint = TxID[prev] TxOutIndex[prev]`
*   `scriptCode = 正在执行的脚本`
*   `hashOutputs = Hash256(‖(output))`

我们利用这些信息修改 [第 10 章，创建和验证交易](#c10.xhtml) 中编写的 P2SH 交易验证方法，以包含隔离见证交易。具体操作如下：

```
def setVarInt(n: int):
    if n < 0xfd:
        n_h = '%02x' % n
    elif n > 0xfd and n < 0xffff:
        n_h = 'fd%04x' % n
    elif n > 0xffff and n < 0xFFFFFFFF:
        n_h = 'fe%08x' % n
    else:
        n_h = 'ff%016x' % n
    return bytes.fromhex(n_h)

def getAmountFromPrevout(prev_tx_hash_b: bytes, prev_tx_out_index_b: bytes):
    prevtx = findTransaction(prev_tx_hash_b, txindex_db_g)
    prevtx_outindex = int.from_bytes(prev_tx_out_index_b, byteorder='little')
    prevAmount = prevtx['outs'][prevtx_outindex]['satoshis']
    amount_b = struct.pack("<Q", prevAmount)
    return amount_b

def createMsgForSigForSegwit(tx: dict, script_b: bytes, inp_index: int, sighash_type: int):
    version_b = bytes.fromhex(tx['version'])[::-1]
    inp_cnt = tx['inp_cnt']
    prevouts_b = b''
    sequences_b = b''
    for i in range(inp_cnt):
        tx_inp = tx['inputs'][i]
        prev_tx_hash_b = bytes.fromhex(tx_inp['prev_tx_hash'])[::-1]
        prev_tx_out_index_b = struct.pack('<L', tx_inp['prev_tx_out_index'])
        sequences_b += struct.pack('<L', tx_inp['sequence'])
        prevouts_b += prev_tx_hash_b + prev_tx_out_index_b
        if i == inp_index:
            outpoint_b = prev_tx_hash_b + prev_tx_out_index_b
            print('script = ', script_b.hex())
            scriptCode_b = bytes.fromhex('%x' % len(script_b)) + script_b
            amount_b = getAmountFromPrevout(prev_tx_hash_b, prev_tx_out_index_b)
            sequence_b = struct.pack('<L', tx_inp['sequence'])
    out_cnt = tx['out_cnt']
    outputs_b = b''
    for o in range(out_cnt):
        tx_out = tx['outs'][o]
        satoshis_b = struct.pack('<Q', tx_out['satoshis'])
        bytes_scriptpubkey_b = setVarInt(tx_out['bytes_scriptpubkey'])
        scriptpubkey_b = bytes.fromhex(tx_out['scriptpubkey'])
        outputs_b += satoshis_b + bytes_scriptpubkey_b + scriptpubkey_b
    locktime_b = struct.pack('<L', tx['locktime'])
    hashPrevouts_b = hash256(prevouts_b)
    hashSequence_b = hash256(sequences_b)
    hashOutputs_b = hash256(outputs_b)
    hashType_b = struct.pack('<L', sighash_type)
    msg_b = version_b + hashPrevouts_b + hashSequence_b + outpoint_b + scriptCode_b + amount_b + sequence_b + hashOutputs_b + locktime_b + hashType_b
    return msg_b
```

**程序 12.11：** 为隔离见证交易创建签名预映像

如果交易具有隔离见证，则从以下 `sigcheck` 方法调用该方法：

```
def uncompressPubkey(pubkey_b: bytes):
    pubkey_P = PublicKey.decode(pubkey_b)
    pubkey_b = PublicKey.encode(pubkey_P, compressed=False)
    return pubkey_b

def sigcheck(sig_b: bytes, pubkey_b: bytes,
             script_b: bytes, inp_index: int, tx: dict):
    sighash_type = sig_b[-1]
    if tx['is_segwit'] == True:
        msg_b = createMsgForSigForSegwit(tx, script_b, inp_index, sighash_type)
    else:
        msg_b = createMsgForSig(tx, script_b, inp_index, sighash_type)
    print('sig = %s' % sig_b.hex())
    print('pubkey = %s' % pubkey_b.hex())
    print('msg = %s' % msg_b.hex())
    msg_h = hashlib.sha256(msg_b).digest()
    print('msg_h = %s' % msg_h.hex())
    prefix = pubkey_b[0:1]
    if prefix == b"\x02" or prefix == b"\x03":
        fullpubkey_b = uncompressPubkey(pubkey_b)[1:]
    elif prefix == b"\x04":
        fullpubkey_b = pubkey_b[1:]
    rs_b = getRandSFromSig(sig_b)
    print('rs = %s' % rs_b.hex())
    vk = ecdsa.VerifyingKey.from_string(fullpubkey_b, curve=ecdsa.SECP256k1)
    if vk.verify(rs_b, msg_h, hashlib.sha256) == True:
        print("Signature is Valid")
        return b'\x01'
    else:
        print("Signature is not Valid")
        return b'\x00'
```

**程序 12.12：** 验证隔离见证交易中的签名

对于其他 sighash 类型，我们使用以下数学表达式：

*   **对于 sighash 类型 SIGHASH_NONE：**
    *   `hashPrevouts = Hash256(‖(TxID[prev] TxOutIndex[prev] ))`
    *   `hashSequence = 32 字节的零值`
    *   `hashOutputs = 32 字节的零值`
*   **对于 sighash 类型 SIGHASH_SINGLE：**
    *   `hashPrevouts = Hash256(‖(TxID[prev] TxOutIndex[prev] ))`
    *   `hashSequence = 32 字节的零值`
    *   `hashOutputs = Hash256(output[inputindex] )`
*   **对于 sighash 类型 SIGHASH_ALL|SIGHASH_ANYONECANPAY：**
    *   `hashPrevouts = 32 字节的零值`
    *   `hashSequence = 32 字节的零值`
    *   `hashOutputs = Hash256(‖(output))`
*   **对于 sighash 类型 SIGHASH_NONE|SIGHASH_ANYONECANPAY：**
    *   `hashPrevouts = 32 字节的零值`
    *   `hashSequence = 32 字节的零值`
    *   `hashOutputs = 32 字节的零值`
*   **对于 sighash 类型 SIGHASH_SINGLE|SIGHASH_ANYONECANPAY：**
    *   `hashPrevouts = 32 字节的零值`
    *   `hashSequence = 32 字节的零值`
    *   `hashOutputs = Hash256(output[inputindex] )`

正如我们已经学会为 `SIGHASH_ALL` 创建签名预映像，我们可以同样使用上述信息为其他 sighash 类型构建预映像。

# 地址格式与生成

隔离见证引入了一种基于 bech32 算法的更短地址格式。BIP 173 提供了比特币隔离见证寻址中使用的 bech32 格式的信息。以下是 bech32 相对于非隔离见证交易中使用的 base58check 算法的几个优势：

*   Base58 在二维码中需要大量空间，因为它无法使用*字母数字模式*。
*   Base58 中的大小写混合使得可靠地记录、在手机键盘上输入或大声朗读变得不便。
*   双重 SHA256 校验和速度慢且没有错误检测保证。

