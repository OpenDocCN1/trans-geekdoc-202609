
# Building P2SH Transaction

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

**Program 10.22:** Method to create redeem scripts for multisig

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

![](images/Figure-10.23.jpg)

**Figure 10.23:** Shows the P2SH address generated using redeem script

我们使用前面的地址生成一个区块并接收比特币，如下所示：

![](images/Figure-10.24.jpg)

**Figure 10.24:** Shows the generated block that pays to the P2SH address

接下来，我们使用前面的 Bitcoin Core CLI 命令中的区块哈希来获取 coinbase 交易的交易 ID：

![](images/Figure-10.25.jpg)

**Figure 10.25:** Shows the coinbase transaction that will pay to the P2SH transaction

我们需要获取生成的交易结构，因为我们需要在交易中使用交易输出。

我们通过执行以下命令获取原始交易：

![](images/Figure-10.26.jpg)

**Figure 10.26:** Shows the hex data of the coinbase transaction that pays to the P2SH address

通过执行以下命令，我们从原始交易中获取交易结构：

![](images/Figure-10.27.jpg)

**Figure 10.27:** Shows the command to get content in the transaction hex data

以下是从前面的命令生成的原始交易的结构：

![](images/Figure-10.28.jpg)

**Figure 10.28:** Shows the decoded transaction data

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

**Program 10.23:** Method creating transaction structure to be used as input for P2SH transaction creation

这给出了以下签名交易：

![](images/Figure-10.29.jpg)

**Figure 10.29:** Shows the signed transaction moving bitcoin from P2SH address
