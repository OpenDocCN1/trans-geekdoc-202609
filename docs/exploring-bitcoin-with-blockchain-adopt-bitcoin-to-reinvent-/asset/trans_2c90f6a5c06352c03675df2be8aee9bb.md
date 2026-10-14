
* **P2PKH:** `<Signature> <Public Key>`
* **P2SH:** `OP_0 <Signature 1><Signature 2> … <Signature N> <Redeem Script>`

我们为每个资金交易输出创建 `scriptSig`：

```
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

**程序 10.19：** 准备签名列表和脚本的方法

我们使用 `scriptSig` 列表和交易结构来准备所需的交易，如下所示：

```
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

# In P2PKH script scriptSig is signature + pubkey
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

**程序 10.20：** 创建已签名交易

现在，我们可以为 P2PKH 和 P2SH 创建交易，并将其发布到比特币网络。为此，我们需要私钥、公钥和地址。

我们使用 *[第 9 章，钱包和地址](#c09.xhtml)* 中描述的方法，**在** **子主题** *私钥、公钥和地址的格式与生成* **下** 生成密钥和地址。

我们将使用以下私钥、公钥和地址：

| **私钥** | **公钥** | **地址** |
| --- | --- | --- |
| KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53 | 0281238fc6d981efce6aa1b3ccb8556a1b115a40f8ab3315c003f415ceedc3defe | msMV395AdBAk2SfdDhBLq4uJZRS7doCn5T |
| L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ | 037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7 | n1WvYkKU9i5RymcHeKFT4UworwqS6BKFSf |
| KxR8HHyfAwFPidCw2vXThXqT4vSMNeufirHFapnfCfkzLaohtujG | 02fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d0 | miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo |
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

在以下 CLI 语句中，我们生成两个区块，每个新创建的区块向给定地址支付 50![](images/Bitcoin.jpg)。支付交易是包含在每个生成区块中的币基交易。

![](images/Figure-10.12.jpg)

**图 10.12：** 显示向给定地址支付的生成区块

我们从区块哈希中获取币基交易：

![](images/Figure-10.13.jpg)

**图 10.13：** 显示生成区块的币基交易

因此，我们现在有两笔交易，每笔持有 50 个 regtest 比特币：

`5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f`

`53793974d074e57305575d711fd0acd1d39f406264de234e686542ad2d0ddbfb`

我们还从第一笔交易输出中获取 `scriptPubKey`，如下所示：

![](images/Figure-10.14.jpg)

**图 10.14：** 显示从资金交易的第一个输出获得的 scriptPubKey

现在，区块链中有两个区块，每个区块有 50![](images/Bitcoin.jpg)。有一条规则规定币基交易在接下来的 100 个区块内不能被花费。如果网络遭受攻击，或者存在严重漏洞，需要重组比特币区块链，这条规则很有用。这意味着我们需要使挖掘近期区块的旧版软件失效，并部署修复问题的新软件。我们可能还需要使已挖出的某些区块失效。100 个区块给开发者近 16 小时来修复网络。过去，比特币开发者不得不执行两次重组，一次在 2010 年，一次在 2013 年。这显然会影响网络的可信度，我们不希望再次发生这种情况。

我们将直接再挖掘 100 个区块，如下所示，以便能够使用上述交易：

![](images/Figure-10.15.jpg)

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
