
`txn['inputs'].append(input0)`

`txn['out_count'] = 2`

`txn['outputs'] = []`

`output0 = {}`

`output0['satoshis'] = 10*(10**8)`

`output0['script_type'] = 'P2PKH'`

`output0['address'] = 'mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ'`

`txn['outputs'].append(output0)`

`output1 = {}`

`output1['satoshis'] = 399999*(10**4)`

`output1['script_type'] = 'P2PKH'`

`output1['address'] = 'miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo'`

`txn['outputs'].append(output1)`

`txn['locktime'] = 0 # block height`

`return txn`

**Program 11.8:** Method to create transaction for True condition

To the redeem script, we need to provide public keys of both Alice and Bob as in the normal multi-sig script. Here, we also need to provide `OP_1` or True to the script.

So, the `scriptSig` with included redeem script is as follows:

```
#OP_0
#<Alice’s Signature>
#<Bob’s Signature>
#OP_1 (True)
#IF
# OP_2 <Alice’s pubkey> <Bob’s pubkey> OP_2 CHECKMULTISIG
#ELSE
# 105 CHECKSEQUENCEVERIFY DROP
# <Alice’s pubkey> CHECKSIG
#ENDIF
```

We further add the following condition in the method `createSignedInput` to handle `script_type` `P2SH_Condition` for the preceding conditional scripts:

```
elif txn_input['script_type'] == 'P2SH_Condition':
    scriptSig_b = createScriptSigForCond(signgrp,
                                         script_b,
                                         txn_input['condition'])
```

We also create `scriptSig` for custom condition, as follows:

```
OP_FALSE = 0x00
OP_TRUE = 0x51
#########################
#True Case
#OP_0
#<Alice’s Signature>
#<Bob’s Signature>
#OP_TRUE (True)
#########################
#False Case
#<Alice’s Signature>
#OP_FALSE (False)
#########################
#Needs to be customized based on use case
def createScriptSigForCond(signgrp: list,
                           script_b: bytes,
                           cond: bool):
    if cond:
        scriptSig_b = bytes([OP_0])
        for sign_b in signgrp:
            scriptSig_b += getWithPushdata(sign_b)
        scriptSig_b += bytes([OP_TRUE])
        scriptSig_b += getWithPushdata(script_b)
    else:
        scriptSig_b = encodePushdata(len(signgrp[0])) + signgrp[0]
        scriptSig_b += bytes([OP_FALSE])
        scriptSig_b += encodePushdata(len(script_b)) + script_b
    return scriptSig_b
```

**Program 11.9:** ScriptSig for condition handling

On executing the code, we get the following signed raw transaction:

![](images/Figure-11.26.jpg)

**Figure 11.26:** Create transaction hex code for payment with relative locktime

We decode the preceding script and get the following decoded script:

![](images/Figure-11.27.jpg)

**Figure 11.27:** ScriptSig in the transaction for payment with relative lock

We publish the transaction we just created as follows:

![](images/Figure-11.28.jpg)

**Figure 11.28:** Transaction for payment with relative lock is published

This shows how the script works in normal conditions. In the condition of dispute, the `OP_ELSE` condition gets executed, and we need to hold the transaction in the mempool till the `OP_CHECKSEQUENCEVERIFY` condition is met. If we publish the transaction before the due time, it gets rejected. For this, we need to additionally set sequence greater than 105.

So, we modify the transaction structure as follows:

```
#2-of-2-multisig with condition
def createTransactionStruct():
    txn = {}
    txn['version'] = 2
    txn['input_count'] = 1
    txn['inputs'] = []
    input0 = {}
    input0['prevtxn'] = \
    '624d92839eb89104d0909df89f95785cb8bb77f0fec66c6c40cf3ad2804a3966'
    input0['prevtxnindex'] = 0
    input0['script_type'] = 'P2SH_Condition'
    input0['condition'] = False
    input0['privkeys'] = \
    ['L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ']
    input0['redeem_script'] = '635221037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f72102fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d052ae670169b27521037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7ac68'
    input0['hash_type'] = SIGHASH_ALL
    input0['sequence'] = 110
    input0['sequence_type'] = 'block'
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
```

**Program 11.10:** Method to create transaction for False condition

On executing the modified code, we get the following signed transaction:

![](images/Figure-11.29.jpg)

**Figure 11.29:** Transaction for payment with relative lock is published

If we try to execute this script before 106 blocks are mined, we get the following error:

![](images/Figure-11.30.jpg)

**Figure 11.30:** Payment with relative lock fails to publish before required block height

But once 110 blocks are mined, we can publish it, as shown in the following screenshot:

![](images/Figure-11.31.jpg)

**Figure 11.31:** Payment with relative lock published after the required block height

You learnt how you can have conditional payments in the contract. Conditionals are an important part of a contract, and by learning this, we can think about more complex smart contracts.

## Payments involving escrow

If both parties are not trustworthy, we need a trusted third party to resolve the dispute. This is like decentralized exchanges in which the buyers and seller gets into a trade, and when the payment is received by the seller, it releases bitcoin.

The following flowchart shows the steps and conditions involved in the entire payment process:

![](images/Figure-11.32.jpg)

**Figure 11.32:** Flow chart for payment involving escrow

For programming this, we only need to have 2-of-3-multisig instead of 2-of-2-multisig with relative timeout, which we discussed in the previous subtopic.

So, the new redeem script will be as follows:

```
#IF
# OP_2 <Alice’s pubkey><Bob’s pubkey><escrow’s pubkey> OP_3 OP_CHECKMULTISIG
#ELSE
# 105 CHECKSEQUENCEVERIFY DROP
# <Alice’s pubkey> CHECKSIG
#ENDIF
```

We will have this as an assignment for the readers.

## Payment involving secret identifier

Consider a case where a secret agent is on a mission in the enemy territory. Some items need to be transferred to them so that the mission can be carried out. If they receive that package, then the mission is carried out; otherwise, it is aborted. To carry out the mission, they need to be paid. So, they can only claim the payment when they have received the package.

In this case, a contract needs to be created with a relative locktime and in successful condition, the agent needs to reveal the secret.

The following is the redeem script for the contract:

```
#IF
# OP_SHA256 <secret_hash> OP_EQUALVERIFY
# <Agent’s pubkey> CHECKSIG
#ELSE
# 105 CHECKSEQUENCEVERIFY DROP
# <Agency’s pubkey> CHECKSIG
#ENDIF
```

The following are the opcodes and their hex values:

`OP_2 = 0x52`

`OP_IF = 0x63`

`OP_ELSE = 0x67`

`OP_ENDIF = 0x68`

`OP_CHECKSEQUENCEVERIFY = 0xb2`

`OP_EQUALVERIFY = 0x88`

`OP_DROP = 0x75`

`OP_SHA256 = 0xa8`

`OP_CHECKSIG = 0xac`

**Program 11.11:** Opcodes used in redeem script for payment with secret

The following is the code to generate redeem-script:

```
def createRedeemScriptWithSecretHash(pubkey_agency: str, pubkey_agent: str, secret_h: bytes):
    redeem_script_b = bytes([OP_IF, OP_SHA256])
    redeem_script_b += createVarInt(len(secret_h)) + secret_h
    redeem_script_b += bytes([OP_EQUALVERIFY])
    pubkey_b = bytes.fromhex(pubkey_agent)
    redeem_script_b += createVarInt(len(pubkey_b)) + pubkey_b
    redeem_script_b += bytes([OP_CHECKSIG])
    redeem_script_b += bytes([OP_ELSE, 0x01,
                              105, # after 105 blocks
                              OP_CHECKSEQUENCEVERIFY, OP_DROP])
    pubkey_b = bytes.fromhex(pubkey_agency)
    redeem_script_b += createVarInt(len(pubkey_b)) + pubkey_b
```
