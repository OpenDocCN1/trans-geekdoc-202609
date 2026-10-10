
# Blockchain in P2P Networks

Blockchain operates in a peer-to-peer (P2P) fashion (i.e., it depends on its network constituents for its resources and computation). There is no central authority here, but a collective mechanism is employed over its constituents: the nodes. This is so that system nodes can work together and secure the blockchain from adversaries. Although double spending has been a problem for a long time in both centralised and decentralised payment protocols, the blockchain makes it infeasible unless and until an adversary or a group of adversaries gain control of 51% computational power of the network [9].

After the genesis block, the succeeding blocks have to be mined by miners. Mining is the process of adding new blocks to the blockchain, thereby increasing its size. Miners are volunteers who provide their resources for the blockchain to operate. For each block to be mined, the miners have to solve a cryptographical puzzle and find a desired target. They do so by following a distributed consensus algorithm, proof-of-work.

The most widespread use of blockchains is in cryptocurrencies such as Bitcoin [10]. However, many applications have adopted blockchains to provide decentralised and trust-free solutions [11]. Another use of blockchains is with computer programs (smart contracts) such as Ethereum [12]. One of the advantages of using blockchains with IoT environments is that it allows IoT devices to transact freely without relying on third parties. However, scalability along with standardisation in IoT and blockchains remain key developmental concerns [13].

## 4.1.2.1 Transaction

A transaction, `tx`, is a set of instructions which changes the ownership of tokens or digital assets from one user to another. A token is a virtually valued currency. The ownership of these tokens or assets is changed by digitally signing a transaction which contains these tokens or assets with a unique private key and then broadcasting it in the network. The network can then verify this transaction signature using the corresponding public key. Mathematically, a transaction can be formulated as:

```
tx = t[in]Num || t[in] || t[out]Num || t[out] || nonce || data || t
```
(4.3)

where `t[in]` and `t[out]` are the input and output vectors of a transaction that represent both the sender and recipient. These consist of tuples of elements and are used when the ownership of tokens is digitally transferred from one user to another one. Here, `t[in]Num` and `t[out]Num` are the total number of incoming and outgoing transactions relative to a timestamp `t`, respectively. The `nonce` field contains the challenge for miners to mine the transaction and validate it, whereas the `data` field contains information.

All transactions relative to a timestamp are collated together which form tuples of transactions to be mined. When a transaction occurs and is broadcast in the network successfully, the ownership of tokens or assets changes and the new owner is announced by the sender. The network participants trace the transaction history and verify its signature before mining.

## 4.1.2.2 Signing a Transaction

Before a transaction, `tx`, can be stored, it has to be validated to prove its authenticity. Authenticity in a `tx` is achieved by digitally signing it with a private key for encrypting and then validating it by decrypting with the corresponding public key. For a user, `i`, it can mathematically be formulated as:

```
sign[i] = f(private[key[i]], payload)
```
(4.4)

```
verify[i] = f(public[key[i]], payload)
```
(4.5)

where `sign[i]` represents the signature of user `i` and is a function of `private[key[i]]` and `payload`, which are the private key of and data to be signed by user `i`, respectively. Similarly, `verify` is a function of `public[key[i]]` and the same payload. The only way a user can verify the signature `sign[i]` is with the help of the corresponding public key of user `i`.

## 4.1.2.3 Reaching Consensus: Proof-of-Work

The proof-of-work (PoW) is a distributed consensus mechanism whose main function is to present a puzzle (an exceptionally difficult mathematical problem) to miners each time a block is verified. The puzzle has a target value, `v`, which is a 256-bit number with specific `n` number of zeros as significant digits. The choice of `n` defines the difficulty of the puzzle. The PoW is an exponential function, which means a lower target value will require more attempts of hashing. The solution finding process is a probabilistic one because to find the target value, a miner has to change its hashing iteratively. This is because each input produces a unique hash and different hashing attempts are required to solve the challenge. Blockchain makes the double-spending attacks infeasible because of this attribute.

For example, the PoW function of Bitcoin can be formulated as:

```
pr(h ≤ υ) = υ / 2^256
```
(4.6)

where the probability of finding a proof (mining) `h` for a target `υ` is `pr(h ≤ υ)`. When a miner finds the target value, it broadcasts its proof in the network. The other miners then rerun this proof and validate the block. Once the block is validated and accepted by the majority of the network, it is then finally added to the blockchain.

## 4.1.3 Physical Unclonable Functions

A physical unclonable function (PUF) is a 'hardware fingerprint' that can provide semiconductor devices (such as microprocessors, integrated circuits [ICs], etc.) with unique identities. PUFs are used in place of secret keys or passwords that can be used to assign a hardware fingerprint to IoT devices [14]. They are characterised by and are based on the variations that naturally occur during the manufacturing process of semiconductor devices. This provides a way for differentiating between otherwise identical semiconductor devices. PUFs are generally used in cryptography and for applications with high-security requirements.

The PUFs provide a device with distinctive and unique hardware fingerprints determined by their responses to challenges. For example, if a challenge is input to a PUF many times, it will always produce the same output (response) with a high probability. Similarly, in a different PUF, if the same challenge is given as an input, it will always produce a different output with high probability [15]. This way, PUFs provide physical security to devices with unique fingerprints that cannot be altered or tampered with. A common example of a PUF is the subscriber identification module (SIM) card used in cellular networks.

The establishment of data provenance in this chapter is based on PUFs. A PUF is characterised by a challenge-response pair (CRP) which can be represented as:

```
R^(i) = pr(C^(i)).
```
(4.7)

where `R^i` is the response generated by a challenge `C^i`.

# 4.2 PUF-Based Blockchain Protocols for IoT in Fog and Edge Computing
