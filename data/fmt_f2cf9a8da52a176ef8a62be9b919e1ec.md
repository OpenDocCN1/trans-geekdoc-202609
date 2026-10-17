
# Program 10.15: 使用给定的 locktime 返回 sequence

以下是后续方法中使用的实用方法：

```python
def createVarInt(i: int):
    if i < 0xfd:
        return bytes([i])
    elif i < 0xffff:
        return b'\xfd' + struct.pack('<H', i)
    elif i < 0xffffffff:
        return b'\xfe' + struct.pack('<L', i)
    elif i < 0xffffffffffffffff:
        return b'\xff' + struct.pack('<Q', i)

def address2PubkeyHash(address: str):
    pkh = base58checkDecode(address)
    return pkh

def encodePushdata(length: int):
    if length <= 0x4b:
        return bytes([length])
    if length <= 0xff:
        return bytes([OP_PUSHDATA1, length])
    if length <= 0xffff:
        return bytes([OP_PUSHDATA2]) + struct.pack('<H', length)
    if length <= 0xffffffff:
        return bytes([OP_PUSHDATA4]) + struct.pack('<L', length)

def getScriptTypeFromAddress(address: str):
    if address[0] in ['m', 'n'] or address[0] == '1':
        return "P2PKH"
    elif address[0] == '2' or address[0] == '3':
        return "P2SH"
```

# Figure 10.16: 构建交易所需的实用方法

以下是创建交易时方法使用的操作码：

```
OP_0 = 0x00
OP_DUP = 0x76
OP_EQUAL = 0x87
OP_EQUALVERIFY = 0x88
OP_HASH160 = 0xa9
OP_CHECKSIG = 0xac
OP_CHECKMULTISIG = 0xae
```

签名预镜像是使用发送方私钥签名的消息。以下方法使用前面的方法生成签名预镜像：

```python
def createSignaturePreimage(txn_struct: dict,
                            script_b: bytes,
                            inp_index: int):
    preimage_b = b''
    preimage_b += struct.pack('<L', txn_struct['version'])
    preimage_b += createVarInt(txn_struct['input_count'])
    for i in range(txn_struct['input_count']):
        inp = txn_struct['inputs'][i]
        preimage_b += bytes.fromhex(inp['prevtxn'])[::-1]
        preimage_b += struct.pack('<L', inp['prevtxnindex'])
        if i == inp_index:
            preimage_b += createVarInt(len(script_b))
            preimage_b += script_b
        else:
            preimage_b += b'\x00'
        preimage_b += getSequence(txn_struct)
    preimage_b += createVarInt(txn_struct['out_count'])
    for out in range(txn_struct['out_count']):
        satoshis = txn_struct['outputs'][out]['satoshis']
        preimage_b += struct.pack('<Q', satoshis)
        address = txn_struct['outputs'][out]['address']
        scriptPubkey_b = getScriptPubkeyFromAddress(address)
        preimage_b += createVarInt(len(scriptPubkey_b))
        preimage_b += scriptPubkey_b
    preimage_b += struct.pack('<L', txn_struct['locktime'])
    hashtype = txn_struct['inputs'][inp_index]['hash_type']
    preimage_b += struct.pack('<L', hashtype)
    print('preimage = ', preimage_b.hex())
    return preimage_b
```

# Program 10.17: 准备签名预镜像

我们通过使用私钥对签名预镜像进行签名来生成签名。签名后附加 `hash_type`。

代码如下：

```python
from ecdsa import SigningKey, SECP256k1
from ecdsa.util import sigencode_der_canonize

def signMessage(preimage_b: bytes,
                privkey_wif: str,
                hash_type: int):
    hash_preimage = hash256(preimage_b)
    privkey_s, network, compress = privkeyWif2Hex(privkey_wif)
    if privkey_s.__len__() % 2 == 1:
        privkey_s = "0{}".format(privkey_s)
    if compress == True:
        print('compress is true')
        privkey_b = bytes.fromhex(privkey_s)[:-1]
    else:
        privkey_b = bytes.fromhex(privkey_s)
    sk = SigningKey.from_string(privkey_b, curve=SECP256k1)
    sig_b = sk.sign_digest(hash_preimage,
                           sigencode=sigencode_der_canonize) \
        + bytes([hash_type])
    return sig_b
```

# Program 10.18: 签名消息的方法

在前面的代码中，我们调用了 `ecdsa` 包中的以下方法：

```python
sk.sign_digest(hash_preimage,
               sigencode=sigencode_der_canonize)
```

此方法使用预镜像的哈希值和私钥生成签名。我们知道生成的签名由 R 和 S 组成。由于比特币使用椭圆曲线算法 `SECP256k1`，该算法关于 X 轴对称，因此可以使用 -S 获得相同的签名。这意味着同一个私钥和消息存在两个有效签名。由于签名是交易的一部分，这会导致两个交易 ID 代表同一笔交易，这是一个安全问题，也称为**交易延展性**。交易延展性还有其他发生方式。为避免此问题，我们使用 S 和 -S 中较小的一个。这就是我们向该方法传递 `sigencode_der_canonize` 参数的原因，它仅生成**低 S 值**。

正如我们所见，`ScriptSig` 具有以下结构：

* **P2PKH:** `<Signature> <Public Key>`
* **P2SH:** `OP_0 <Signature 1><Signature 2> … <Signature N> <Redeem Script>`

我们为每个资金交易输出创建 `scriptSig`：

```python
def getSignaturesAndExecScripts(txn_struct: dict):
    signgrp_l = []
    script_l = []
    for inp_index in range(txn_struct['input_count']):
        inp = txn_struct['inputs'][inp_index]
        script_b = getExecutionScript(txn_struct, inp_index)
        preimage_b = createSignaturePreimage(txn_struct, script_b, inp_index)
        inp = txn_struct['inputs'][inp_index]
        signgrp = []
        for privkey in inp['privkeys']:
            hashtype = inp['hash_type']
            sign_b = signMessage(preimage_b, privkey, hashtype)
            signgrp.append(sign_b)
        signgrp_l.append(signgrp)
        script_l.append(script_b)
    return txn_struct, signgrp_l, script_l
```

# 程序 10.19: 准备签名列表和脚本的方法

我们使用 `scriptSig` 列表和交易结构来准备所需的交易，如下所示：

```python
def getWithPushdata(data_b: bytes):
    pushdata_b = encodePushdata(len(data_b))
    return pushdata_b + data_b

def createScriptSigForMultiSig(signgrp: list, script_b: bytes):
    scriptSig_b = bytes([OP_0])
    for sign_b in signgrp:
        scriptSig_b += getWithPushdata(sign_b)
    scriptSig_b += getWithPushdata(script_b)
    return scriptSig_b

def createScriptSigForP2PKH(txn_input: dict, signgrp: list):
    sign_b = signgrp[0] # it’s not a group.. just one signature
    scriptSig_b = getWithPushdata(sign_b)
    privkey = txn_input['privkeys'][0]
    pubkey_b = privkeyWif2pubkey(privkey)
    scriptSig_b += getWithPushdata(pubkey_b)
    return scriptSig_b

def createSignedInput(txn_input: dict, signgrp, script_b: bytes):
    prevtxn = txn_input['prevtxn']
    prevtx_rb = bytes.fromhex(prevtxn)[::-1]
    prevtxnindex = txn_input['prevtxnindex']
    sgntxnin_b = prevtx_rb + struct.pack('<L', prevtxnindex)
    if txn_input['script_type'] == 'P2SH_Multisig':
        scriptSig_b = createScriptSigForMultiSig(signgrp, script_b)
    elif txn_input['script_type'] == 'P2PKH':
        scriptSig_b = createScriptSigForP2PKH(txn_input, signgrp)
    sgntxnin_b += createVarInt(len(scriptSig_b)) + scriptSig_b
    return sgntxnin_b

#### In P2PKH script scriptSig is signature + pubkey
def scriptSigFromSignNPubkey(sign_b: bytes, pubkey_b: bytes):
    scriptSig_b = getWithPushdata(sign_b)
    scriptSig_b += getWithPushdata(pubkey_b)
    return scriptSig_b

def createSignedTransaction(txn_struct: dict, signgrp_l: list, script_l: list):
    sgntxn_b = b''
    sgntxn_b += struct.pack('<L', txn_struct['version'])
    sgntxn_b += createVarInt(txn_struct['input_count'])
    for i in range(txn_struct['input_count']):
        txn_input = txn_struct['inputs'][i]
        sgntxn_b += createSignedInput(txn_input, signgrp_l[i], script_l[i])
    sgntxn_b += getSequence(txn_struct)
    sgntxn_b += createVarInt(txn_struct['out_count'])
    for out in range(txn_struct['out_count']):
        satoshis = txn_struct['outputs'][out]['satoshis']
        sgntxn_b += struct.pack('<Q', satoshis)
        address = txn_struct['outputs'][out]['address']
        scriptPubkey_b = getScriptPubkeyFromAddress(address)
        sgntxn_b += createVarInt(len(scriptPubkey_b))
        sgntxn_b += scriptPubkey_b
    sgntxn_b += struct.pack('<L', txn_struct['locktime'])
    return sgntxn_b
```

# 程序 10.20: 创建已签名交易

现在，我们可以为 P2PKH 和 P2SH 创建交易，并将其发布到比特币网络。为此，我们需要私钥、公钥和地址。

我们使用*第 9 章，钱包和地址*中描述的方法，**在****子主题** *私钥、公钥和地址的格式与生成* **下** 生成密钥和地址。

我们将使用以下私钥、公钥和地址：

| **私钥** | **公钥** | **地址** |
| --- | --- | --- |
| KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53 | 0281238fc6d981efce6aa1b3ccb8556a1b115a40f8ab3315c003f415ceedc3defe | msMV395AdBAk2SfdDhBLq4uJZRS7doCn5T |
| L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ | 037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7 | n1WvYkKU9i5RymcHeKFT4UworwqS6BKFSf |
| KxR8HHyfAwFPidCw2vXThXqT4vSMNeufirHFapnfCfkzLaohtujG | 02fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d0 | miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo |
