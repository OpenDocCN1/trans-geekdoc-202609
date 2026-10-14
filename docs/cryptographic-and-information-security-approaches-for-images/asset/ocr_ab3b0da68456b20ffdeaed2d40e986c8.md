```
<ScriptPubKey=OP_DUP OP_HASH160<Public KeyHash> OP_EQUAL
OP_CHECKSIG
ScriptSig= <Signature><Public Key>
```

Execution of The ScriptPubKey and ScriptSig takes place in the following manner:

```
Validation=<Signature><Public Key>OP_DUP OP_HASH160<Public
KeyHash> OP_EQUAL OP_CHECKSIG
```

If the result of the above statement is 1 then it shows that the transaction is valid. The process executes from left to right and addition in stack takes place in *Last In First Out* order.

First, the signature is pushed into the stack, then the public key is pushed on top of the stack. The top is duplicated by the OP_DUP operator and Hash 160 function does the hashing of the top item (public key) in the stack. It turns the public key into a hash. The OP_EQUAL operator is used to check whether the hashed values of public key are equal. Verification of the signature is done by the OP_CHECKSIG operator.

# 25.5.2 Genesis Block

Genesis block of a blockchain is the first block in a chain. Nowadays, it is also called as block 0, although early versions named it as block 1. Every cryptocurrency has a genesis block. Since it’s the first block created, every block after the genesis block can trace back to it and its previous ancestor bocks using the linkage in the block header. Meaning, if we start from any block and move in a backward direction, we will eventually find ourselves at genesis block. Each node knows the hash of genesis block, its time of creation and the only transaction it contains. Table 25.3, shows the hash details about the genesis block (block 0) of a blockchain. Since it is the first ever block created, hence, its height is zero. The timestamp will be the time when it was created.

# Table 25.3 Hashes of Blocks After a Transaction

| Hashes |  |
|---|---|
| Hash | 2866f114d3c5ec5ab073f90179223cf6e70a6f7bf6908bbe1583cc6d591c33ad |
| Previous Block | 00000000000000000000000000000000000000000000000000000000000000000000000000 |
| Next Block Hash | 75a11da44c802486bc6f65640aa48a730f0f684c5c07a42ba3cd1735eb3fb070 |
| Merkle Root | 828c5202934ead693783ea3f0e9da029999b541822c0e80eb92f35008dad82b3 |