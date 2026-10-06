
# Chapter 6 Ethereum — A Distributed World Computer? | 209

**Table 6.2 Some useful ETH units and their naming conventions.** As of this writing (October 2020), average transaction size is 5 ETH, block mining reward is 2 ETH; cost of basic transaction is about 2,000 szabo; cost of gas is 100 Gwei.

| Unit | Number per ETH | Usage |
|---|---|---||
| ETH (ether) | 1 | Transaction amounts and block rewards |
| finney | 1,000 | |
| szabo | 1,000,000 | Cost of a basic transaction |
| Gwei | 1,000,000,000 | Gas price |
| wei | 1,000,000,000,000 | The base indivisible unit |

early contributors and investors to the project (see Table 6.2 on units and naming conventions). This is frequently cited by Bitcoin purists, who do not view Ethereum as a truly distributed protocol. On a related matter, Satoshi Nakamoto, the creator of Bitcoin, is as elusive as ever, while one of the founders of Ethereum, Vitalik Buterin, keeps a high profile and exerts a significant influence on the Ethereum ecosystem. A typical example of why the decision is to execute a hard fork to counter the decentralized autonomous organization (DAO) hack is see Chapter 2 and Section 6.9.6. The importance, or lack thereof, of this additional source of centralization, remains to be seen.

Surprisingly, Ethereum's payment-operation structure is archaic — this is how people used to charge their customers on a per-minute basis for phone calls in the 20th century. By now, it became subscription-based payments are the only way to pay for large-volume services. Recently, paying for Ethereum transactions became prohibitively expensive for all speculative purposes. However, there is a good reason why Ethereum relies on the payment-operation model. Ethereum provides anti-denial of service protection. By paying per canonical operation relative to its computational weight, no attacker can pollute the network by exploiting expensive but financially cheap operations. In the future, more flexible alternatives may augment the existing per-operation payment model.

The Ethereum protocol development was funded by an online sale that took place between July and August 2014. The protocol went live on July 30, 2015 with the genesis supply of approximately 72,010,000 pre-minined eth. As of September 15, 2020, the total supply of ether is about 112,600,000. Thus — the fact often cited by Bitcoin purists.

## 6.4 Ethereum account types

An Ethereum address can refer to two types of entities: (a) Externally Owned Accounts (EOAs) and (b) smart contracts (SCs). Both EOAs and SCs have public addresses, only EOAs have associated secret keys. EOAs are comparable to Bitcoin addresses in principle but rely on a very different paradigm: whereas Bitcoin maintains the accounting of its system by tracking immutable UTXOs. Ethereum is more akin to traditional bank accounts: it stores an explicit balance for each address, mutated by transactions and out. As a result, the state of an Ethereum account is more complicated than Bitcoin. An EOA contains the following fields:

- (1) nonce, incremented for every outgoing transaction and acting as an anti-replay protection;
- (2) ETH balance;
- (3) empty contract code;
- (4) storage (which is initially empty by default).³

Unlike Bitcoin's UTXO paradigm, Ethereum's account model requires picking and choosing UTXOs to satisfy various criteria, such as fee minimization, privacy optimization, etc. Thereby the account model significantly simplifies the process of building transactions. However, the consequence of making accounts mutable is that one transaction signed by the wallet owner can be re-executed a second time. This is trivially guaranteed by the UTXO model given that a UTXO no longer is "spent" as soon as it is consumed for a transaction. However under account model, the balance is mutated for each transaction but nothing inherently prevents a transaction from being replayed multiple times.

In order to prevent replays, Ethereum maintains a nonce as part of the account state on the blockchain. This nonce is incremented for every outgoing transaction and Ethereum guarantees that it processes an outgoing transaction if the nonce — which is signed by the transaction — is precisely one than current nonce registered on the on-chain. If a replay attack is attempted, the nonce has already been consumed, and the transaction can immediately be disregarded. The nonce, as an outgoing counter, is critically important in deciding the transaction's validity.

To summarize, an EOA with no associated code can only send and receive ETH transactions and trigger contract code, and is controlled by a secret key.

The truly original feature of Ethereum is its support for SCs. A smart contract is an immutable piece of software. Once deployed on the blockchain, it maintains its own state and can receive requests from EOAs or other SCs.

In theory, the code of a smart contract is Turing-complete and perform arbitrary complex operations. In particular, it has a permanent state, it can operate arbitrary rules on this state and it, if necessary, it can call other contracts. In practice, the fees associated with the consumption of memory and the execution of the contract, as well as the archaic performance of the EVM, limit the reach of possible applications to small programs focused on security-critical code. For this restricted class of applications, Turing completeness is achieved precisely because such contracts rarely need to reach the limits of Ethereum.

³ storage is populated with transaction information.

# Chapter 6 Ethereum — A Distributed World Computer? | 21

We describe how Ethereum operates based on the white paper, Buterin (2013), yellow paper, Wood (2015), and a recent book, Antonopoulos and Wood (2018). As before, we distinguish between the Ethereum protocol and the new cryptocurrency (ETH).

## 6.5 The Ethereum Virtual Machine

The Ethereum Virtual Machine, or EVM is a sandboxed execution environment running on every node. It is responsible for the execution of transactions and their related smart contracts and provides a Turing-complete set of operations. It runs in a segregated container from the rest of the node logic and the network. In essence, it is the common standard Ethereum nodes share for the execution of contracts and which makes the Ethereum “language” interpretable on each node of the network.

Importantly, we like to emphasize the distinction between Ethereum “distributed computing” and previous kinds of distributed computing networks that have existed for a long time. Originally, distributed computing meant horizontal scaling, i.e., the sharding of the computational effort across distributed nodes, each processing a tiny part of the all problem; see for instance, Folding@home*. For networks, more nodes means increased performance; but the corollary is that trust in the result is low because there is no duplication of the work. There are no trivial means to identify data tampering or processes on the distributed system. These distributed computations accelerate rather than trust.

Ethereum’s goal is entirely different. It aims at having each execute the same computation. Ethereum provides no horizontal scaling, at least in its current version of its network — although, it is slower than a single machine due to network latencies and the limitations of the EVM. However, such a redundancy enables one to achieve a high level of trust.

Like everything in life, reality does not have to be one of the two extremes. One obvious, albeit non-trivial, way of scaling distributed ledger technologies is to “shard” the execution of transactions and contracts, i.e., to position the D between the two options mentioned above. Instead of all machines executing all computations, it is sufficient for a subset of nodes duplicate each other so that the result is trustworthy.

Thus, the EVM is a massively replicated, redundant, distributed computer whose aim is to ensure proper execution of transactions and contracts at the cost of efficiency.

## 6.6 Transfers and smart contract calls

Ethereum is a state transition protocol, similar to the Bitcoin protocol, described by Eqs (5.37) and (5.38). One particular here is that it relies on a single abstraction for both

> *See https://foldingathome.org/.
