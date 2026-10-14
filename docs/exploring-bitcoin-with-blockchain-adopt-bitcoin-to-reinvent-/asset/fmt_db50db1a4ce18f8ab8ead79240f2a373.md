
*   Planned contribution within a group

# Objectives

The objective of this chapter is to help you understand the broader scope of Bitcoin scripting language. Additionally, it will help you learn to create transactions for different scenarios, including smart contract and other useful transactions that were not covered in the previous chapters.

# Script opcodes

In the previous chapter, we used only a few opcodes that are used in standard P2PKH and m-of-n-multisig P2SH scripts. While these are sufficient for basic money transfers between individuals and groups, a more complex script might be needed. In this chapter, we will use a few more opcodes.

# Digital property

Digital asset or digital property is the digital representation of an asset. The property can be represented as QR code or identifier or hash of specification or value. The asset ownership can be changed by the owner of the asset. It can also be lent or rented online. Using Bitcoin transaction and scripting language, we can implement some of those features. Timestamping is one of the important properties of digital asset management, which we will cover in this subtopic.

# Document timestamping

Timestamping a document is necessary for it to be legally binding and for it to be part of a contract. Transactions in a block can be associated with the timestamp of the block, and it is immutable. If a transaction holds hash of the content of a document, then we can consider the document as timestamped. However, for this to be legally binding, governments need to recognize Bitcoin blockchain as both immutable and having the correct timestamp.

The following is a short story written by my daughter, for which we are generating a hash and will add it to a transaction:

Best Friend Lunch Party: One day two best friends, a monkey and a crocodile decided to have lunch together in a farm. The next day, they passed the river and reached the farm. After a heavy meal the monkey got up and started growling loudly. The frightened crocodile pleaded the monkey to stop. But the monkey said, ‘I have a habit of growling after every meal, I cannot help it’. The monkey was on the crocodile’s back while crossing the river back home. When they were halfway through the river, the crocodile took a dip in the water. When the monkey was frightened, the crocodile said, ‘I have a habit of taking a dip in the water after every meal, I cannot help it’. Monkey understood his mistake.

SHA256 of this story:

`3365b392ee14def189190638a532f6042446b74c98f186e9b595f77e47817e05`

The following is the code to get the hash of the preceding story:

```
def contentHash(story: str):
    content_h = hashlib.sha256(story.encode('ascii')).digest()
    return content_h
```

To add this to a transaction, we need to pay a small network fee, transfer bitcoins from one address to another, and use `OP_RETURN` to capture the above hash.

We generate the first block and send the newly mined bitcoins to an address as shown in Figure 11.1:

![](images/Figure-11.1.jpg)

**Figure 11.1:** Generated Block hash

The following are the transactions included in the newly mined block:

![](images/Figure-11.2.jpg)

**Figure 11.2:** Transaction ID of coinbase transaction

In Chapter 10, Create and Validate Transactions under the topic Building P2PKH transaction, we have created P2PKH transaction with two inputs and two outputs. We modify the code to also support `OP_RETURN` output.

This is the code that provides transaction structure to the transaction builder program:

```
def createTransactionStruct():
    txn = {}
    txn['version'] = 1
    txn['input_count'] = 1
    txn['inputs'] = []
    input0 = {}
    input0['prevtxn'] = '5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f'
    input0['prevtxnindex'] = 0
    input0['script_type'] = 'P2PKH'
    input0['privkeys'] = ['KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53']
    input0['script_pubkey'] = '76a91481d7033c19dcec645cb3f86ce41678756850ba4d88ac'
    input0['hash_type'] = SIGHASH_ALL
    txn['inputs'].append(input0)
    txn['out_count'] = 2
    txn['outputs'] = []
    output0 = {}
    output0['satoshis'] = 4999900000
    output0['script_type'] = 'P2PKH'
    output0['address'] = 'mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ'
    txn['outputs'].append(output0)
    output1 = {}
    output1['satoshis'] = 0
    output1['script_type'] = 'OP_RETURN'
    output1['content_hash256'] = '3365b392ee14def189190638a532f6042446b74c98f186e9b595f77e47817e05'
    txn['outputs'].append(output1)
    txn['locktime'] = 0
    return txn
```

**Program 11.1:** Transaction structure definition of document timestamping

The following is the value of `OP_RETURN` opcode:

`OP_RETURN = 0x6a`

In Chapter 10, Create and Validate Transactions under topic Building transactions we have defined method `createSignaturePreimage and createSignedTransaction`. We add following lines to the method to handle OP_RETURN script type:

```
if outp['script_type'] == 'OP_RETURN':
    content_b = bytes.fromhex(outp['content_hash256'])
    scriptPubkey_b = bytes([OP_RETURN]) \
     + getWithPushdata(content_b)
```

As we did in Chapter 10, Create and Validate Transactions, we execute this program and get raw transaction hex code, as shown in Figure 11.3:

![](images/Figure-11.3.jpg)

**Figure 11.3:** Hex code of transaction created for document stamping

The following is the output of the newly created transaction:

![](images/Figure-11.4.jpg)

**Figure 11.4:** Output of transaction created for document timestamping

Now, we need to mine another 100 blocks so that the mined bitcoins we are using are ready for transfer:

![](images/Figure-11.5.jpg)

**Figure 11.5:** Next 100 blocks are mined

Now, publish the newly created transaction:

![](images/Figure-11.6.jpg)

**Figure 11.6:** Publish transaction for document timestamping

Now, we mine a single block again to add the transaction to the newly mined block:

![](images/Figure-11.7.jpg)

**Figure 11.7:** Mine the next block to include published transaction

The following in the newly mined block. We can see that the block contains the newly added transaction:

![](images/Figure-11.8.jpg)

**Figure 11.8:** Published transaction appears in the new block

# Time locked transactions

Bitcoin allows you to lock a transaction for certain time or block height. It allows transactions to be locked in a fixed time or time relative to the funding transaction.

In the following subsections, we will cover a use case for both fixed and the relative timelock.

# Time locked payment

We can also create transactions that cannot be spent before given timestamp. This is done by setting the `nLockTime` field in a transaction. The `nLockTime` field can either be set to denote block height or to denote Unix epoch time. In the case of epoch time, it denotes mean time past instead of the block’s timestamp.

The `nLockTime` field has the following rules:

*   `nLockTime` < 500000000 denotes block-height
*   Otherwise, it denotes median time past

It is recommended that `nLockTime` is not set to zero or past block height or past block-time.

*Median time past = Medium of (Tn-1, Tn-2, Tn-3, Tn-4, … Tn-10, Tn-11)*

The following code provides transaction structure to the transaction builder program:

```
def createTransactionStruct():
    txn = {}
    txn['version'] = 1
    txn['input_count'] = 1
    txn['inputs'] = []
    input0 = {}
    input0['prevtxn'] = '5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f'
    input0['prevtxnindex'] = 0
    input0['script_type'] = 'P2PKH'
    input0['privkeys'] = ['KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53']
    input0['script_pubkey'] = '76a91481d7033c19dcec645cb3f86ce41678756850ba4d88ac'
    input0['hash_type'] = SIGHASH_ALL
    txn['inputs'].append(input0)
    txn['out_count'] = 1
```
