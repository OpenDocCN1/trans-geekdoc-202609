
The preceding figure shows how the signature is created by using the message and private key. In the case of `SIGHASH_ALL`, we create the message by taking all the elements of the new transaction. We then replace `scriptSig` and `scriptSig` length with the executing script, which, in the case of P2PKH, is the previous `scriptPubKey` and `scriptPubKey` length for the input index to be signed. For the other inputs, `scriptSig` length is replaced with zero as those inputs are not getting signed. For P2SH script, `scriptSig` and its length are replaced with redeem script and its length. At the end of the message, we add sighash type.

## Hash type – SIGHASH_NONE, SIGHASH_SINGLE, SIGHASH_ANYONECANPAY

The following illustration shows the message structure to be signed for other sighash types:

![](images/Figure-10.5.jpg)

**Figure 10.5:** Signature preimage for sighash types other than SIGHASH_ALL

In the case of `SIGHASH_ANYONECANPAY`, only the signed input is part of the message to be signed, and other inputs are not included. In the case of `SIGHASH_NONE`, none of the outputs are included, and in the case of `SIGHASH_SINGLE`, only one output is included. We can observe that the output index in the case, `SIGHASH_SINGLE`, corresponds to the input that is being signed. This means, if input 0 is signed, then output 0 is included and output 1 is excluded. If input 1 is signed, then output 1 is included and output 0 is excluded. If the excluded output is not the last output of the message, then we need to keep the excluded output as a placeholder by just having `0xFFFFFFFFFFFFFFFF` and `0x00` as is in the figure. In both `SIGHASH_NONE` and `SIGHASH_SINGLE`, the sequences of inputs that are not signed are replaced by `0x00000000`.

## Standard Bitcoin script - P2PK

P2PK is not recommended for use. P2PK stands for **Pay-2-Public-Key**.

In this script, `scriptSig` is:

` <Signature>`

and `scriptPubKey` is:

` <Public Key> OP_CHECKSIG`

It has simple execution: first, `scriptSig` gets executed, in which signature is pushed into stack, and then `scriptPubKey` gets executed, which pushes public-key to stack, and then `OP_CHECKSIG` checks the signature by popping out the signature and the public-key and pushes back the result to the stack.

This script had a few drawbacks:

*   Compressed Public Keys are 32-bytes long, while the hash used by the P2PKH script is 20-byte long, so its hex is 40-character long, which is much easier to type. An address generated from 20-bytes using base58check encoding is 34-character long.

*   If quantum computers can utilize a quantum technique called Shor’s algorithm, it is expected that they will be able to derive private keys from public keys. For Bitcoin to remain secure in the future, we should not expose our public keys on the networks that are still holding bitcoins. By having a public key hash, we have multiple levels of security to secure our funds.

Since this script is not recommended, there is no point in going deeper into understanding it.

## Standard Bitcoin script – P2PKH

P2PKH is the most widely used Bitcoin script. P2PKH stands for **Pay-2-Public-Key-Hash**. In the script, the sender locks the transaction output using the hash of the public key, and it requires the receiver to provide the public key when it needs to use the funds locked in transaction output. The hash is 20-byte long, which is smaller than the 32-byte long compressed public key. And it generates a 34-character long address, which includes a checksum. This makes it easier to type, and since it contains a checksum, it is not possible to accidentally type the wrong address.

The `scriptSig` in P2PKH is:

` <Signature> <Public Key Hash>`

and the `scriptPubKey` is:

` OP_DUP OP_HASH160 <20-byte pubkey hash> OP_EQUALVERIFY OP_CHECKSIG`

Since `<Signature>` and `<Public Key Hash>` both are data, both go into the stack. Once `scriptSig` is executed, `scriptPubKey` is executed.

The following illustration shows the execution of P2PKH:

![](images/Figure-10.6.jpg)

**Figure 10.6:** Execution of P2PKH

## Prepare signature preimage

All messages include sighash type at the end. Once the message is signed, the sighash type is appended to the signature to help the verifying node reconstruct the message before verification.

Now, we are ready to verify a real transaction script. We take following transaction ID:

`83eeaecaf531e5239ffc3ba7ff583c696f7dbe3610f0d672d41e0b9443632c82`

Since the transaction is in the Bitcoin blockchain, we get the raw transaction by calling `getrawtransaction` in Bitcoin Core CLI, as follows:

![](images/Figure-10.7.jpg)

**Figure 10.7:** Shows the Bitcoin Core CLI command for getting transaction bytes

This gives us the following raw transaction:

![](images/Figure-10.8.jpg)

**Figure 10.8:** Shows the hex data of the traansaction-ID

We can use the transaction and parse it using the `getTransactionInfo` method written in *[Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml),* under the topic *Transactions* and the subtopic *Other transaction* in *Program 6.15,* to get `scriptSig`.

This gives us the following information:

`Transaction = {‘version’: ‘00000001’, ‘inp_cnt’: 2, ‘inputs’: [{‘prev_tx_hash’: ‘15b91bcf8b2b9ea46d0daab60aaa2e99b15a5fb37d9d4568d4c060e515e13130’, ‘prev_tx_out_index’: ‘00000001’, ‘bytes_scriptsig’: 106, ‘scriptsig’: ‘47304402205535a9ac25844514828bff3580120d5add488e09b7a6e62018fc265aabf95fe302200b66d4eb23fc348b31d58729b479ae73db9dfc467edf38f8dfd927c48cb46b5801210219fbee4b9cc12188598f244ff0ee352b124cbf9046180a1b25e020c0258f9d64’, ‘sequence’: ‘ffffffff’}, {‘prev_tx_hash’: ‘840ac7a55498c6746b9d7460a348f79e2f35db4a9696bef762d975e7e1deeff2’, ‘prev_tx_out_index’: ‘0000000c’, ‘bytes_scriptsig’: 106, ‘scriptsig’: ‘47304402203a28d10c786907fcb71c7bf69c507d58884ea9af2e7fa3b413d4e2867eca601502205fb253d82e4daa2672842ec031584ea7a215774422aa7de3cf8928c240e2faa60121030be5aa6d5de8c6dd89d6ac4d0e2a112caf5b12801349ab30fbdf2b205f0b94b8’, ‘sequence’: ‘ffffffff’}], ‘out_cnt’: 2, ‘outs’: [{‘satoshis’: 69302, ‘bytes_scriptpubkey’: 25, ‘scriptpubkey’: ‘76a914f133f0339987cd84b6017517de2a93f009728d7e88ac’}, {‘satoshis’: 12900349, ‘bytes_scriptpubkey’: 25, ‘scriptpubkey’: ‘76a91406c3bc40cde01312e2b24f8d2c23e68ea7d572f888ac’}], ‘locktime’: 0}`

The following program further parses `scriptSig` to get signature, `sighash` type, and public key:

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

**Program 10.2:** Scriptsig parser

We call the preceding method as follows:
