
* **P2PKH:** `<Signature> <Public Key>`
* **P2SH:** `OP_0 <Signature 1><Signature 2> … <Signature N> <Redeem Script>`

We create the `scriptSig` for each funding transaction output:

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

**Program 10.19:** Method for preparing a list of signatures and scripts

We use the list of `scriptSig` and transaction structure to prepare the required transaction, as follows:

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

**Program 10.20:** Create signed transaction

Now, we can create a transaction for both P2PKH and P2SH and publish it on the Bitcoin network. For this, we will require private keys, public keys, and addresses.

We generate the keys and addresses using the method described in *[Chapter 9, Wallets and Addresses](#c09.xhtml)*, **under** the **subtopic** *Format and generation of private key, publickey, and address*.

We will use the following private key, public key, and addresses:

| **Private Keys** | **Public Keys** | **Addresses** |
| --- | --- | --- |
| KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53 | 0281238fc6d981efce6aa1b3ccb8556a1b115a40f8ab3315c003f415ceedc3defe | msMV395AdBAk2SfdDhBLq4uJZRS7doCn5T |
| L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ | 037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7 | n1WvYkKU9i5RymcHeKFT4UworwqS6BKFSf |
| KxR8HHyfAwFPidCw2vXThXqT4vSMNeufirHFapnfCfkzLaohtujG | 02fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d0 | miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo |
| KyWeQEcM2YdirR2E7JwxSRjfgNuWyt4DR3v4sGtPvmeZqhTxWVrp | 02d50250aa629914e3146a 5123a362a516c8aa95e5f0a6f3a078bd31fabe383abc | msV23rBcHAtQWSkWV9ph91DV65VduWi1Vt |
| Ky5CYfpeMkfFku7K4FvzeEwRmTJhWqD2eFiMnjLT7uw2oUVMgyg6 | 0319b4b9ab4732e78dab0e48c2c54fd57dd35350a0269f8c041807c3b798aa1872 | mnhWcUMqe9J1G4t3NMqNmLUqxfPTgwv7NK |
| L1cnATDVZyvuo9m6tprCmbr14vm3JeCbkc4Z2397ZM7P96N3d8GA | 039d5dbb6e052631c46e046c6d11fb95d257eae5093117d2c265aeb784dba4acf6 | mtRkMmpT6uhM9LXVPRk4ck9Gcaz9iuQgmZ |
| KyP1xynRgwrCUThXATVy5kbKqteAxisDFY74zrHozSGhb75hJ3M6 | 02dfa818542ab4685284f7c222d541e218aed0712fc9e63ca2802b15bb418383c9 | n2DfL6uEmPiwJBYjJRzyqUYDSTqxF8XSNS |

**Table 10.3:** Few test addresses, public keys, and private keys

We start the Bitcoin Core daemon for `regtest` as shown here:

```
bitcoind -regtest -printtoconsole –rpcuser=test –rpcpassword=test -txindex=1
```

### Building P2PKH transaction

We then connect the daemon and generate two blocks, sending bitcoin to a particular `regtest` address.

To do this, run Bitcoin Core CLI with the `regtest` option, giving optional parameters `rpcuser` and `rpcpassword`. The `rpcuser` and `rpcpassword` options allow a client to make `rpc` connections. This is required for connecting using Python package but not for connecting using CLI.

In the following CLI statement, we are generating two blocks, and each newly created block pays 50![](images/Bitcoin.jpg)to the given address. The payment transactions are coinbase transactions that are included in each generated block.

![](images/Figure-10.12.jpg)

**Figure 10.12:** Shows the generated blocks that pay to the given address

We get the coinbase transactions from the block hashes:

![](images/Figure-10.13.jpg)

**Figure 10.13:** Shows the coinbase transactions of the generated blocks

So, we have two transactions now holding 50 regtest bitcoins each:

`5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f`

`53793974d074e57305575d711fd0acd1d39f406264de234e686542ad2d0ddbfb`

We also get `scriptPubKey` from the first transaction output as follows:

![](images/Figure-10.14.jpg)

**Figure 10.14:** Shows the scriptPubKey obtained from the first output of funding transaction

Now, we have two blocks in the blockchain each with 50![](images/Bitcoin.jpg). There is a rule that a coinbase transaction cannot be spent for the next 100 blocks. This rule is useful if there is an attack on the network or if there is any critical bug and it becomes necessary to reorg the Bitcoin blockchain. This means we need to invalidate the previous version of the software, which has mined recent blocks, and deploy the new software, which fixes the issue. We may also need to invalidate some blocks that are already mined. The 100 blocks give nearly 16 hours to developers to fix the network. In the past, Bitcoin developers had to perform reorg twice once in 2010 and once in 2013. This obviously affects the creditability of the network, and we don’t want it to happen again.

We will just mine another 100 blocks, as follows, to be able to use the preceding transactions:

![](images/Figure-10.15.jpg)

**Figure 10.15:** Shows the commpand executed to generate 100 blocks

We will use the locked bitcoins in two transactions and send them to two different addresses and leave 0.0001 regtest bitcoins as network fees. We first create a raw transaction without a signature. The following code defines the structure of the raw transaction:

```
def createTransactionStruct():
    txn = {}
    txn['version'] = 1
    txn['input_count'] = 2
    txn['inputs'] = []
    input0 = {}
    input0['prevtxn'] = \
```
