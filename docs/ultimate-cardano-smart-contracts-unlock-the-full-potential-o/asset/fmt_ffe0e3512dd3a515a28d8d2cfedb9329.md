
The first commonly used digital signature was Rivest-Shamir-Asleman (RSA), created in 1977, which uses the property that factoring two large primes is difficult. In 1991, the Digital Signature Algorithm (DSA) was created, leveraging the fact that solving the discrete log problem (`x ^ y = z`) is difficult. Given `x` and `z`, solving for `y` is difficult when `y` is a large enough number. An elliptic curve signature algorithm was added to DSA, creating the Elliptic Curve Digital Signature Algorithm (ECDSA), which has a smaller key size and faster operations.[^(10)](#c02.xhtml#ftn10) Cardano uses the Edwards-curve Digital Signature Algorithm (EdDSA), which has the following benefits[^(11)](#c02.xhtml#ftn11):

*   Fast signing and verification
*   High level of security
*   Small signatures
*   Small keys

*[Table 2.1](#c02.xhtml#tab2_1)* summarizes the different signature algorithms used in Bitcoin, Ethereum, and Cardano:

| **Blockchain** | **Signing Algorithm** | **Elliptic Curve** | **Hash Function** |
| --- | --- | --- | --- |
| Bitcoin | ECDSA | Secp256k1 | SHA-256 |
| Ethereum | ECDSA | Secp256k1 | Keccak-256 |
| Cardano | EdDSA | Curve25519 | BLAKE2b |

**Table 2.1:** Digital signatures[^(12)](#c02.xhtml#ftn12)

## [Chain of Ownership](#toc.xhtml#s32a)

An electronic coin, as defined in the Bitcoin whitepaper, is a chain of digital signatures.[^(13)](#c02.xhtml#ftn13) A Bitcoin is transferred digitally by signing the previous transaction’s hash and the next owner’s public key. A transaction will only be approved if the signature matches the public key included in the previous transaction. By linking these together, the **chain of ownership** can be verified, as shown in *[Figure 2.3](#c02.xhtml#fig2_3)*.

![](images/Figure-2.3.jpg)

**Figure 2.3:** Chain of Ownership[^(14)](#c02.xhtml#ftn14)

## [Proof-of-Work (PoW)](#toc.xhtml#s33a)

In the Bitcoin whitepaper, the double-spend problem is where Bob tries to create two transactions to spend the same amount twice. To solve this issue, a timestamp or timeline is introduced. Each block hash is linked to the previous block hash, creating a chain of blocks and ordering transactions, as shown in *[Figure 2.4](#c02.xhtml#fig2_4)*. The ledger can now confirm if a transaction is trying to double-spend outputs that have already been spent and reject it accordingly.

To help regulate the frequency of block production, a nonce is used and incremented to find a block hash with a required number of zero bits. The Bitcoin network monitors the pace of block production, and if blocks are produced too fast, the number of required zero bits increases. Conversely, if the number of blocks being produced takes too long, the number of required zero bits decreases. The adjustment of the required number of zero bits is also known as **difficulty**.[^(15)](#c02.xhtml#ftn15) The level of CPU effort increases exponentially as the **difficulty** increases. Because the blocks are chained together, undoing a previous transaction requires changing all the previous blocks, which becomes practically impossible as more blocks are confirmed by the network.

![](images/Figure-2.4.jpg)

**Figure 2.4:** Proof-of-Work

## [Mining](#toc.xhtml#s34a)

The last issue to solve is to provide an incentive for creating new blocks called mining and encourage miners to be honest and not attack the network. This is accomplished by distributing new Bitcoins in the first transaction in each block to the miner who created the block. The number of new Bitcoins created decreases exponentially over time, which controls Bitcoin’s inflation rate. Additionally, if the output value of the transaction is less than the input value, this is considered a transaction fee and awarded to the miner.[^(16)](#c02.xhtml#ftn16) The new Bitcoins plus the transaction fee will make it more profitable for the miner to act honestly rather than try to subvert the network with an invalid block.

## [Proof-of-Stake (PoS)](#toc.xhtml#s35a)

With the growing popularity of Bitcoin, the difficulty has increased exponentially. As a result, the **PoW** consensus protocol requires a lot of energy for miners to produce a block. **PoS**, on the other hand, is significantly more energy efficient by selecting block producers randomly and proportionally to the amount of Ada they have staked on the network. Stakeholders can delegate their stake to a Stake Pool Operator (**SPO**) to aggregate Stake together and increase the chances for block production. In a PoS protocol, there is no need to generate computationally intensive puzzles; meanwhile, the security and permissionless properties are still comparable to **PoW**.[^(17)](#c02.xhtml#ftn17)

**PoS**, however, introduces a different threat vector for determining the block (slot) leader. To achieve a fair randomized election among stakeholders, **entropy** must be introduced into the system and may be prone to manipulation by an adversary.[^(18)](#c02.xhtml#ftn18) Ouroboros **PoS** protocol mitigates this risk by using an entropy parameter that represents something unpredictable outside the Cardano ecosystem.[^(19)](#c02.xhtml#ftn19) “*The value of this parameter is calculated based on events that could not have been known in advance, or that anyone could have had insider information about*.”[^(20)](#c02.xhtml#ftn20)

We will look into the Ouroboros protocol in more detail in the next section and will complete the **PoS** overview by examining the two major categories of **PoS** protocols:[^(21)](#c02.xhtml#ftn21)

*   **Probabilistic Finality** (Chain-based)
*   **Absolute Finality** (PBFT)

## [Probabilistic Finality (Chain-based)](#toc.xhtml#s36a)

**Probabilistic** or chain-based finality attempts to simulate the **PoW** Nakamoto consensus protocol used in Bitcoin. As more blocks are linked together, they form the longest chain and become probabilistically final.[^(22)](#c02.xhtml#ftn22) Typically, waiting until 6 blocks have been linked together is sufficient for probabilistic finality, with a high likelihood that a transaction will not be reverted or rolled back. One of the key advantages of a probabilistic finality mechanism is that it prioritizes network **availability** for continuous and permissionless access.

## [Absolute Finality (PBFT)](#toc.xhtml#s37a)

In an **Absolute Finality** or Practical Byzantine Fault Tolerant (**PBFT**) protocol, a validator is randomly chosen to propose a new block. The validators then vote on the inclusion of this new block, and consensus is achieved when the required number of validators agree on accepting a new block.[^(23)](#c02.xhtml#ftn23) Additionally, **PoS** blockchains like Ethereum implement an economic penalty that makes it prohibitively expensive for validators who are unavailable or act maliciously against the network. By using **Absolute** and **Economic Finality**, the protocol prioritizes the **consistency** of the network and would halt the network rather than accept an invalid transaction for any length of time.[^(24)](#c02.xhtml#ftn24)

## [Ouroboros Protocol](#toc.xhtml#s38a)

Ouroboros is the first provably secure **PoS** protocol and the first blockchain protocol based on peer-reviewed research.[^(25)](#c02.xhtml#ftn25) It consists of a family of PoS protocols, including:

*   Ouroboros Classic
*   Ouroboros BFT
*   Ouroboros Praos
*   Ouroboros Genesis
*   Ouroboros Crypsinous
*   Ouroboros Chronos

## [Ouroboros Classic](#toc.xhtml#s39a)
