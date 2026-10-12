
Ouroboros Classic was the first Ouroboros protocol published in July 2017.[^(26)](#c02.xhtml#ftn26) The paper defined the protocol as an energy-efficient rival to `PoW`, introduced the mathematical framework to analyze `PoS`, and introduced a novel incentive mechanism to reward participants in a `PoS` setting.[^(27)](#c02.xhtml#ftn27) What distinguishes Ouroboros from other blockchain protocols is its ability to generate unbiased randomness in its leader selection algorithm with security assurances.[^(28)](#c02.xhtml#ftn28) Let’s examine this in more detail.

> Ouroboros divides time on Cardano into epochs, where each epoch is divided into slots. A slot is a short period of time in which a block can be created, and grouping slots into epochs is central to adjusting the leader election process to the dynamically changing stake distribution. A slot leader is elected for each slot, responsible for adding a block to the chain and passing it to the next slot leader. To protect against adversarial attempts to subvert the protocol, each new slot leader must consider the last few blocks of the received chain as transient: only the chain that precedes the prespecified number of transient blocks is considered settled.[^(29)](#c02.xhtml#ftn29)

# Ouroboros BFT

The Ouroboros Byzantine Fault Tolerance (`BFT`) was a simplified protocol[^(30)](#c02.xhtml#ftn30) based on Ouroboros Classic and was used primarily to help with one of the most significant milestones in Cardano known as the Shelly release. It transitioned the network to a federated model to avoid requiring all nodes to be online all the time.[^(31)](#c02.xhtml#ftn31)

# Ouroboros Praos

Praos introduces a verifiable random function (`VRF`) on the current timestamp and a nonce for a specific epoch.[^(32)](#c02.xhtml#ftn32) Given a private key and an input, a `VRF` outputs a pseudo-random number and a proof.[^(33)](#c02.xhtml#ftn33) The corresponding public key can verify the proof and random number. Additionally, this approach prevents anyone except the proposed slot leader from knowing the slot leader for a specific slot in advance. This is important to avoid `DDoS` or targeted attacks, where a slot leader is publicly known in advance.[^(34)](#c02.xhtml#ftn34)

# Ouroboros Genesis

The Bitcoin `PoW` consensus protocol has the advantage that any participant can join the network and participate using only the Genesis block. This is a very important feature of any blockchain, as it does not rely on any trusted notion or checkpoints of the correct state of the network. Ouroboros Genesis addresses this limitation with the Ouroboros `PoS` protocols by using a novel chain selection rule that allows new or offline participants to join the network using only the genesis block.[^(35)](#c02.xhtml#ftn35) This approach is called "bootstrapping from genesis," and the Ouroboros Genesis paper proves that it can still retain the prior security assurances while using this approach. The paper also provides proof of the protocol’s Universal Composability, showing that it retains its security properties even when used in different protocol configurations.[^(36)](#c02.xhtml#ftn36)

# Ouroboros Crypsinous

Ouroboros Crypsinous is the first formally analyzed privacy-preserving `PoS` blockchain protocol.[^(37)](#c02.xhtml#ftn37) Using SNARKs and key-private forward secure encryption, the paper uses a novel coin evolution technique to prove the network is secure against adaptive attacks.[^(38)](#c02.xhtml#ftn38) This protocol is not intended to be implemented on the main Cardano settlement layer but may be used in a side chain such as Midnight, a privacy-preserving blockchain.

# Ouroboros Chronos

Ouroboros Chronos demonstrates how blockchain protocols can synchronize clocks securely via a novel time synchronization mechanism, thereby becoming independent of external time services.[^(39)](#c02.xhtml#ftn39) The paper aims to make the ledger more resistant to attacks that target time information.[^(40)](#c02.xhtml#ftn40)

# Ouroboros Protocol Lifecycle

Let’s walk through the Ouroboros protocol lifecycle to provide a step-by-step example of how everything fits together.

## Time

The first block in the Cardano blockchain is the genesis block, which is the beginning of time from a blockchain perspective. Cardano uses the concept of slots, which occur approximately every second, where at most one block can be created. The expected block production frequency is 0.05, meaning that, on average, a block will be produced every 20 seconds.[^(41)](#c02.xhtml#ftn41) Only a slot leader can create a block for a given slot. There are precisely 432,000 slots in every epoch, equivalent to every 5 days.

## Register

The first step in participating in the Cardano network is registering the stake key associated with the Ada to be staked. This typically refers to the registration of Ada to a specific Stake Pool Operator (`SPO`). The amount staked is used to calculate rewards and distribute proportionally back to the staking addresses. The `SPO` will handle (among other things) the stake pool registration process, as shown in *[Figure 2.5](#c02.xhtml#fig2_5)*:

1. Synchronize with the network ledger.
2. Obtain the current slot.
3. Obtain the global random oracle.

## Staking

1. At the start of each epoch, each stake pool operator queries the blockchain to obtain the stake distribution of a previous block, which was two epochs ago.
2. Using a `VRF` generated from the first ⅔ slots in the previous epoch, the stakeholder with their private key can produce an output in the current epoch to determine if they can be a slot leader.[^(42)](#c02.xhtml#ftn42)
3. If the `VRF` output value is below a certain threshold, they can become the slot leader for that block.
4. Slot Leader Responsibilities:[^(43)](#c02.xhtml#ftn43)
    1. Assemble the transactions that should be included in the block.
    2. Include in the block the random value (v) and proof (π) obtained from the VRF output.
    3. Generate a new private key and delete the old one so it is impossible to forge signatures with the old private key.
    4. Broadcast the new block to the network.
5. The rewards are calculated at the end of the epoch and then distributed to the reward addresses in the next block.

![](images/Figure-2.5.jpg)

**Figure 2.5:** Ouroboros Protocol Lifecycle

# Conclusion

This chapter introduced cryptography with a focus on public key hash algorithms. We saw how this extended to a concept called digital signatures, which underpins cryptocurrencies today. By linking digital signatures, a blockchain can create proof-of-ownership for the movement of a digital coin like Bitcoin. We looked deeper at Proof-of-Work and how mining a block incentivizes miners to be honest and prevent network attacks. We then looked at the energy-efficient Proof-of-Stake and how to mitigate the risk associated with predicting random number generation, along with the differences and tradeoffs between Probabilistic and Absolute Finality. Finally, we reviewed the Ouroboros family of protocols and the current protocol lifecycle on the Cardano Mainnet today. Using our knowledge of cryptography and how `PoS` blockchains work, we will explore how to transfer value using transactions in the next chapter.

# Points to Remember

* Using public key encryption requires generating a pair of public and private keys.
* If a transaction is signed by a private key, anyone on the blockchain can verify it using the corresponding public key.
* Bitcoin is transferred digitally by signing the previous transaction’s hash and including the next owner’s public key.
