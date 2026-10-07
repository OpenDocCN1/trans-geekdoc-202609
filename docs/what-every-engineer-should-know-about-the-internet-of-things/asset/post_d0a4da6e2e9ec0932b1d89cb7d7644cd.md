
# 11 Blockchain Technologies and IoT¹

## 11.1 INTRODUCTION

According to Hileman and Rauchs (2017) "A blockchain is a special data structure that is composed of transactions, batched into blocks, that are cryptographically linked to each other to form a sequential, tamper-evident chain that determines the ordering of transactions in the system. In this context, a transaction represents any change or modification to the database". More broadly, a blockchain is a peer-to-peer (P2P) distributed network of independent participants that generally broadcast all data to each other, each of whom have different motivations and objectives. They may not necessarily trust one another but reach a consensus (a consistent agreement about the state of the shared database) on a linear history of operations of that shared database. A high-level workflow of blockchain is presented in Figure 11.1.

The key advantages of blockchain (compared to existing distributed systems and database technologies) are the use of a specialized data structure that bundles transactions into blocks and the broadcast of all data to all participants. Some of the main components of a blockchain are cryptography, P2P networks, consensus mechanisms, the ledger, validity rules, and access or permission types.

![](img/41fdf2aa71adfa568d36836737f447e6_187_0.png)

FIGURE 11.1 Blockchain technology.

¹This chapter was contributed by Giuseppe Defesani, Ludovica Marchesi, Michele Marchesi, Marco Ortu, Roberto Tonelli.

DOI: 10.1201/9781003027799-11

# What Every Engineer Should Know About IoT

There are general permission type distinctions for current blockchain architectures:

- Permissionless, public or open refers to blockchains where access is not restricted to a specific set of vetted participants. In these types of blockchain, participants do not know and trust each other.
- "Permissioned", "private" or "closed" refers to blockchains where access is restricted to a specific set of vetted participants (Hileman & Rauchs, 2017). These blockchains operate in an environment where participants are already known, and there is a level of trust among them; this removes the need for a native token to incentivize good behavior. Participants are held liable through off-chain legal contracts and agreements and are incentivized to behave honestly by the threat of legal prosecution in the case of misbehavior (Hileman & Rauchs, 2017).
- "Consortium" refers to a blockchain where the architecture could be private or hybrid (public and private). This type of blockchain uses features such as permission restriction, multiple controlling authorities; they allow easy, yet controlled information sharing between various stakeholders and more.

## 11.2 THE IDEA OF CRYPTURRENCIES

The first application on a blockchain is Bitcoin, the most famous cryptocurrency. The basic ideas on which Bitcoin (and the other cryptocurrencies) are based on the following:

- The coin is a registration in a public register (the blockchain), shared on the Internet by thousands of nodes which create a P2P network, without any centralized controller.
- Each record has a public address (derived from a public cryptographic key).
- The owner of the coin owns the associated private key.
- The currency can be transferred only using this private key to another address.
- This transfer (transaction) is validated and registered in the blockchain.

Verifying transactions and creating blocks is a computational cost which must be remunerated. For each transaction, it is necessary to verify that (1) the entity which activates it is really the owner, (2) the relative currency has already been spent, and (3) there are no other errors.

The network is democratic and anonymous, and the nodes do not get information about their identity; anyone able to access the network can validate blocks. An attacker could create many nodes (thousands or millions) seemingly independent nodes and take control of the network. This attack is called “Sibling Attack”, and a fundamental constraint is that the system must be able to work even in the presence of attacks and fraud attempts. Trusting all the participants in the network is not a requirement for the system to work.

# Blockchain Technologies and IoT

The Sibling Attack problem is solved by making block validation computationally expensive. This concept is called "Proof of Work" (PoW). To translate the actions, and therefore the blocks, it is necessary to have high-speed and therefore energy-consuming hardware. The network self-adjusts to the available computing power so that the time required for validating transactions is approximately constant. In this scenario, a Sibling Attack would be costly and therefore impractical.

Validation of transactions and blocks through PoW is also used for creating currency. The first node which validates the current block, stores it in the blockchain and earns a fixed amount of cryptocurrency. All nodes concurring for solving the computational challenge accept the validated block, solving it, and move on to the next block. In this, two problems are solved:

- The remuneration of mining;
- The gradual introduction of new currency in the system.

Existing cryptocurrencies typically have a limited amount of currency, or one that grows by a fixed amount each year, so that the growth percentage decreases over time. Bitcoin is an example of the first approach: the reward for validating a block is halved every 4 years, until it reaches zero in 2040. Ethereum is an example of the second approach.

## 11.3 BITCOIN

Bitcoin is the cryptocurrency par excellence, the mother of all other cryptocurrencies. It was introduced in 2009 by Satoshi Nakamoto (Nakamoto & Bitcoin, 2008), the pseudonym of a still unknown person or group. Bitcoin is used with three different meanings:

- The architecture/platform of the Bitcoin network;
- The protocols to make this platform work;
- The "currency" traded on the platform (the acronym is BTC).

One Bitcoin is composed of 100 million Satoshi (the current minimum transfer unit of the cryptocurrency).

### 11.3.1 THE BITCOIN ADDRESS

A Bitcoin address is a number associated with a private–public key pair, and it is the public part of all Bitcoin transfers.
An address is generated from the public key so that:

- An address corresponds to a single public key;
- Given the address, it is not possible to know the public key; this is because the explicit knowledge of this key could in the future make the system more vulnerable;
- An address contains checks in order to recognize any typing errors (as with the tax code).

# 174 What Every Engineer Should Know About IoT

When transferring the Bitcoins associated with one address to another, the public key of the first must be revealed.

The procedure for generating a new Bitcoin address is as follows:

1. A random number d (private key) of 256 bits is generated;
2. The public key B is generated from d and from the standard elliptic curve sec56k1;
3. Starting from b, the Bitcoin address A is generated with a procedure;
4. A Bitcoin address has about 195 bits, and it is represented with 30-34 alphanumeric characters (BASE5 representation) always starting with “1”.

Given an address, only the owner of the key d can generate B from it, and from B generate A.

The steps to generate a Bitcoin address from the public key are the following:

1. Calculation of the RIPEMD160 hash of the SHA256 hash of B:
hash:= RIPEMD160 (SHA256 (B))
2. Add a byte (address version) in the hash of:
ha:=b with equal:
0x05(0000101) for the main key (Bitcoin)
0xc4(1100100) for the net test
3. Calculation of the SHA256 hash of the SHA256 hash of ha:
hh:=SHA256 (SHA256 (ha))
4. Extract the first 4 bytes of hh, to be used as checksum (cs):cs=First4Bytes(hh)
5. Concatenation of b, hash and cs (8+60+32=200 bits):
a:=BASE58(b.hash.cs)

A BASE58 string is generated by encoding a number (a sequence of bits) in base 58, using the following 58 alphanumeric characters as digits from 0 to 57:
123456789ABCDEFJKLQRSTUVWXYZabcdefghijkmnopqrstqrstuvwxyz

Without the “ambiguous” characters: 0, O, 1
Examples of Bitcoin addresses:

NdNaNG1K9eDW5jFDmTIbih5micPsGE1yQ3Kkhf9QABRKK...

The procedure of calculating A starting from B, with four successive hashing is to:

- Prevent B from being made public (because it could be attacked with quantum computers in the future);
- Insert a “checksum” that verifies whether the address has been entered incorrectly: in this case, the software does not make payments to this address.
