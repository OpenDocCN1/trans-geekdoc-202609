
`return feerate * vsize / 1000`

**Program 12.5:** Program to calculate transaction fee

We call the preceding method with the fee-rate estimation we got using Bitcoin Core CLI and `vsize` we got after dividing weight by 4:

`feerate = 0.00075062`

`vsize = 208`

`fee = calculateTransactionFee(vsize, feerate)`

`print('Estimated Minimum Fee in bitcoin = ', fee)`

We get following result:

![](images/Figure-12.12.jpg)

**Figure 12.12:** Calculated transaction fee based on recommended fee rate and vsize

In US Dollars, this comes to $4.75 as current market price of 1![](images/Bitcoin.jpg)is $30425.

# New standard scripts

Segregated witnesses introduced four new standard scripts. The scripts are defined in BIP 143 and can be found at the following URL:

[https://github.com/bitcoin/bips/blob/master/bip-0143.mediawiki](https://github.com/bitcoin/bips/blob/master/bip-0143.mediawiki)

In the next section, we will understand each of these scripts and build programs to verify the transaction on mainnet blockchain.

# Native SegWit transaction scripts

SegWit transaction, in addition to protecting fund transfer from transaction malleability, provides direct monetary benefit in terms of reduced transaction fee.

A native SegWit transaction looks as follows:

`Previous scriptPubKey: <1-byte witness version> <2-40 bytes witness program>`

`ScriptSig: (empty)`

`Witness Data: <witness data>`

We can see that the `previous scriptPubKey` consists of two parts: witness version and witness program. This suggests that each witness version can have different programs. This is a scalable structure and allows future enhancements. In this chapter, we are discussing the scripts introduced in the first version of Segwit enhancement. The next version is used for Taproot and Schnorr signatures.

# Native P2WPKH

As the name suggests, P2WPKH is the SegWit alternate to the P2PKH script, which we already covered in *[Chapter 10, Create and Validate Transactions](#c10.xhtml)*.

The P2WPKH transaction is as follows:

`Previous scriptPubKey: 0 <20-byte-PublicKeyHash>`

`ScriptSig: (empty)`

`Witness data:`

`<Signature>`

`<PublicKey>`

We can see that witness data is the same as `scriptSig` in P2PKH. So, we only need to make small modifications in the script execution. We need to do the following:

1.  Convert `previous scriptPubKey` to P2PKH standard script.
2.  Add witness data to the stack before processing `previous scriptPubKey`.

We modified the program used in P2SH in *[Chapter 10, Create and Validate Transactions](#c04.xhtml)* to perform this exact activity to include the verification of P2WPKH transactions.

We modify `verifyScript` to include a check for P2WPKH by following these steps.

1.  If `scriptsig_b` is an empty string, add all elements of witness data corresponding to the required input index:

```
if scriptsig_b == b'':
    # native segwit
    print('native segwit')
    witness_l = getWitnessList(tx, inp_index)
    pushWitnessData(witness_l)
else:
    execScript(scriptsig_b, inp_index, tx)
```

2.  Convert `Previous scriptPubKey` to standard P2PKH script:

```
if isP2WPKH(prev_scriptpubkey_b) == True:
    print('P2WPKH')
    # convert 0 <20-byte PKH> to OP_DUP OP_HASH160 <PKH> OP_EQUALVERIFY
    prev_scriptpubkey_b = bytes([0x76, 0xa9, 0x14]) + prev_scriptpubkey_b[2:] + bytes([0x88, 0xac])
    is_segwit = True
```

The following is the definition of all the methods used in the preceding changes:

```
def pushWitnessData(witness_l: list):
    for data in witness_l:
        st.append(bytes.fromhex(data['witness']))

def getWitnessList(tx: dict, inp_index: int):
    return tx['inputs'][inp_index]['witnesses']

def isP2WPKH(prev_scriptpubkey_b: bytes):
    #0014<20 bytes>
    if len(prev_scriptpubkey_b) == 22 and prev_scriptpubkey_b[0:2] == b'\x00\x14':
        return True
    return False
```

**Program 12.6:** Updates in program to verify P2WPKH script

Here's the code to call `verifyScript` to verify P2WPKH script:

```
#txid :: 808767ec8b388a7d6c34b9658e573e39034831fea49f0f22911393d6f8e195fb
tx_s = '0100000000010240fc776263b1a4104da05cf069c8e7b0aeb7f7e4c686062906df9ab5d384716f0100000000ffffffff86ab7969a4d661aeaf8845f49eb2e5d30f6fb657d7694b8289224658158a62870000000000ffffffff02ea430000000000001976a9145d57c599fd94fce0cec607e15716f46468cb281b88aca47e000000000000160014f57aed6b1c121a10bec610987cbf414fb168778402483045022100eb6c3485c4ff17390dfbe35be9940b442783bd103095219c285331372b18913b02205bcbc7ce889823af020030d075832f314d1cc905269edf295e813dc7238dc37301210359522a87dc9c907d1669811b7254faf96d7ffcb1f22736bfcd0168fb19b9c98602483045022100acefd6d2ad0b56ad5837cd9d75b49c9f36f5deb6b12e290bbdc14076a38017cd02207a1add2928912d900756874e487d49b49defc7fc6f9805e9777afa929de5ffcb012102948374b79fa597475cab313e63d61d3d546288e6b9b3f80bd1ecc1a514dc382a00000000'
tx_b = bytes.fromhex(tx_s)
tx_m = bytes2Mmap(tx_b)
tx = getTransactionInfo(tx_m)
verifyScript(tx, 0)
```

We will cover signature verification later in the chapter. Signature verification is defined in detail in BIP 143. We execute the preceding program, which verifies script, and we get the following results:

![](images/Figure-12.13.jpg)

**Figure 12.13:** Executing the Python program shows that the signature is valid

Though the result says signature is valid, we haven't discussed in this subtopic and should be ignored.

# Native P2WSH

P2WSH is SegWit alternative to P2SH. The P2WSH transaction is as follows:

`Previous scriptPubKey: 0 <32-byte Redeem-Script-Hash>`

`ScriptSig: (empty)`

`Witness:`

`<Signature 1>`

`<Signature 2>`

`...`

`<redeemScript>`

Here, P2SH-P2WSH uses a hash256 hashing algorithm. So, we convert `previous scriptPubKey` to the following script:

`OP_SHA256 <32-byte-redeemScriptHash> OP_EQUAL`

We modify `verifyScript` to include check for P2WSH:

```
if isP2WSH(prev_scriptpubkey_b) == True:
    print('P2WSH')
    prev_scriptpubkey_b = bytes([0xa8, 0x20]) + prev_scriptpubkey_b[2:] + bytes([0x87])
```

Here's the implementation of `isP2WSH`:

```
def isP2WSH(prev_scriptpubkey_b: bytes):
    #0020<32 bytes>
    if len(prev_scriptpubkey_b) == 34 and prev_scriptpubkey_b[0:2] == b'\x00\x20':
        return True
    return False
```

We also need to handle OP_SHA256. We need to add a check to the `execScript` method, as follows:

```
def opSha256():
    v = st.pop()
    h = hashlib.sha256(v).digest()
    st.append(h)

def execScript(script_b: bytes, inp_index: int, tx: dict):
    l = len(script_b)
    script_m = bytes2Mmap(script_b)
    while script_m.tell() < l:
        v = script_m.read(1)
        b = int.from_bytes(v, byteorder='big')
        if b in g_pushdata:
            script_m.seek(-1, 1)
            b = decodePushdata(script_m)
            d = script_m.read(b)
            pushdata(d)
        elif v == b'\x76':
            opDup()
        elif v == b'\xa8':
            opSha256()
        elif v == b'\xa9':
            opHash160()
        elif b in g_pushnumber:
            opNum(b)
        elif v == b'\x87':
            opEqual()
        elif v == b'\x88':
            opEqualVerify()
        elif v == b'\xac':
            opCheckSig(script_b, inp_index, tx)
        elif v == b'\xae':
            opCheckMultisig(script_b, inp_index, tx)
```

**Program 12.7:** Updates in program to verify P2WSH script

We call the program with changes, as follows:

`#txid :: dffe1dc8f36cbc39c0f40b090912c5a00da13e3534f97aec0ef5bfe552019897`
