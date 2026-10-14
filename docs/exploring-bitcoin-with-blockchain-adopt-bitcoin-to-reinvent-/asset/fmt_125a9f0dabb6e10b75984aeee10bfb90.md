
`tx_s = ‘010000000001024e453d886f11e3af494ce6073956b0de6eaed80865529ab45f778d660459907e2500000023220020ffc74359d1e79a79b94319a1695a68810e439e4c32e4c1be2b0b7c915ca78536ffffffff4e453d886f11e3af494ce6073956b0de6eaed80865529ab45f778d660459907e29000000232200207a21661b84ac4a34a6afc034030faba8ce8344635ebaf34cde31083f186bf871ffffffff02b02a02000000000017a9147b60c1eebfc2c78c9993668dab556344bf1f78d187d9df0500000000002200206f50cccbc64ea3f6cc434d5878bbe45a609e5592026ce6704f586a0e795a6ae40300483045022100d168fa78728fda205eee72ad7b789bc3153adeec982b2588a1526509aa1e2ae8022010443c0652848492dad4904f45258f5452256bfe23d9c715bf052d908154de6e0125512102972c9ea94bfcd5956220f2e99776b3c5ebcca9373a2eccb3fb5fff8bbc9f999451ae03004830450221009691361fa2953e54bc5287306c023fc2d098aa6e85ed1a66d3369e93781260b102201fb639437128d361a12ea385a61bd49247d25c254d1efc03d5272dd368c0acfa01255121027c6cbed24ad235fe147413272ba92cfd61d5ab338c4dabd74cbfb7d11746da5451ae00000000’`

`tx_b = bytes.fromhex(tx_s)`

`tx_m = bytes2Mmap(tx_b)`

`tx = getTransactionInfo(tx_m)`

`verifyScript(tx, 0)`

Running the preceding code gives us the following result:

![](images/Figure-12.16.jpg)

**Figure 12.16:** Executing the Python program shows that P2SH_P2WSH Script is valid

We learned that with simple modifications to the P2PKH/P2SH transaction verification program, we can also verify SegWit transactions. We still haven’t learned to create the right message for signature verification, so we will look at that in the next topic.

# Signature verification

In this section, we will understand BIP 143 to create the correct signature preimage. All SegWit transactions with the same sighash type have the same method of creating a signature preimage.

A signature preimage has the following structure:

![](images/Figure-12.17.jpg)

**Figure 12.17:** Signature preimage structure for SegWit transaction

Each part of the preimage is defined as follows:

Considering,

*   **TxIDprev**: TxID of previous transaction
*   **TxOutIndexprev**: Output index of previous transaction in inputs
*   **output**: output of the transaction
*   **‖**: concatenation
*   **Hash256**: double SHA256 hash

We have the following definition of each part of a signature preimage for sighash type `SIGHASH_ALL`:

*   `hashPrevouts = Hash256(‖(TxID_prev∥ TxOutIndex[prev] ))`
*   `hashSequence = Hash256(‖(nSequence))`
*   `outpoint = TxID[prev] TxOutIndex[prev]`
*   `scriptCode = executing script`
*   `hashOutputs = Hash256(‖(output))`

We use this information to modify the P2SH transaction verification method written in [Chapter 10, Create and Validate Transactions](#c10.xhtml) in order to include SegWit transactions. This is done as follows:

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

**Program 12.11:** Create a signature preimage for SegWit transaction

The method is called from the following `sigcheck` method if the transaction has segregated witness:

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

**Program 12.12:** Verify signature in SegWit transaction

For other sighash types, we use the following mathematical expressions:

*   **For sighash type SIGHASH_NONE:**
    *   `hashPrevouts = Hash256(‖(TxID[prev] TxOutIndex[prev] ))`
    *   `hashSequence = 32 byte of zeroes`
    *   `hashOutputs = 32 byte of zeroes`
*   **For sighash type SIGHASH_SINGLE:**
    *   `hashPrevouts = Hash256(‖(TxID[prev] TxOutIndex[prev] ))`
    *   `hashSequence = 32 bytes of zeroes`
    *   `hashOutputs = Hash256(output[inputindex] )`
*   **For sighash type SIGHASH_ALL|SIGHASH_ANYONECANPAY:**
    *   `hashPrevouts = 32 bytes of zeroes`
    *   `hashSequence = 32 bytes of zeroes`
    *   `hashOutputs = Hash256(‖(output))`
*   **For sighash type SIGHASH_NONE|SIGHASH_ANYONECANPAY:**
    *   `hashPrevouts = 32 bytes of zeroes`
    *   `hashSequence = 32 bytes of zeroes`
    *   `hashOutputs = 32 bytes of zeroes`
*   **For sighash_type SIGHASH_SINGLE|SIGHASH_ANYONECANPAY:**
    *   `hashPrevouts = 32 bytes of zeroes`
    *   `hashSequence = 32 bytes of zeroes`
    *   `hashOutputs = Hash256(output[inputindex] )`

As we have learned to create signature preimage for `SIGHASH_ALL`, we can similarly build preimage using the preceding information for other sighash types.

# Address format and generation

Segregated witnesses introduced a shorter address format based on the bech32 algorithm. The BIP 173 provides information about the bech32 format used in Bitcoin SegWit addressing. Listed here are a few advantages of bech32 over the base58check algorithm used in non-SegWit transactions:

*   Base58 needs a lot of space in QR codes, as it cannot use the *alphanumeric mode*.
*   The mixed case in base58 makes it inconvenient to reliably write down, type on mobile keyboards, or read out loud.
*   The double SHA256 checksum is slow and has no error-detection guarantees.
