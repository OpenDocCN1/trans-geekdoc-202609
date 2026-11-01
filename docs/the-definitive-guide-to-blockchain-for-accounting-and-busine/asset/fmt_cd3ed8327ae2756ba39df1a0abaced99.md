
An important feature of Merkle tree structure is its ability to authenticate large sets of data. It uses a “divide and conquer” strategy, by distributing large sets of data into manageable smaller parts which individually are easier to verify. Following the terminology of tree, Merkle tree comprises of a root, branches and many leaves. The root contains the fingerprint of the entire data set. Bitcoin, for example, uses an `SHA-256` algorithm. `SHA` stands for “Secure Hashing Algorithm,” and 256 denotes the fixed size of the output.

Merkle trees and hashing functions form the computing and mathematical backbone of blockchain. The distinctive features of Merkle trees and the hashing function combined gives the blockchain its valued properties. Merkle tree structure makes it feasible to store large amounts of data and easily retrieve information upon request. Additionally, the hash function provides the feature which makes it difficult to alter records or data encrypted in past blocks, giving blockchains the property of immutability.

## 3.5. TYPES OF BLOCKCHAIN

There are some variations in who can participate in the blockchain and how accessible are the records stored in the blockchain. These variations lead to two sets of blockchain: permissioned or non-permissioned; and public or private.

The distinction between permissioned and non-permissioned network is based upon who can join the network. Any individual or organization can at any time join a non-permissioned network. The entry to and the exit from the network are not monitored, hence participants have the flexibility of joining and leaving at will. In contrast, a permissioned network does not allow new participants to join without obtaining permission from the owners or creators of the network.

In a public network, transactions between members are visible to all participants in the network. In contrast, private networks allow only the parties to the transaction to be able to access and view the transaction. Thus, private networks ensure confidentiality of transactions by restricting public access to those transactions.

These two variations lead to four possible permutations of blockchain, as follows:

**1.** A public and non-permissioned network is the most open and transparent form. Any individual or organization can join and leave the network at will. Once the individual becomes a participant in the network, they will gain access to all present and historical transactions conducted in the network.

**2.** Private and non-permissioned networks allow for wide participation, enabling individuals and organization to join at will. However, the details of transaction are available only to the members who were parties to the transaction. Consequently, new participants cannot view historical transactions, as they could not have been party to those.

**3.** Public and permissioned networks restrict which individual or organization can join the network. Usually such blockchains are restricted only to the founding participants, and subsequent participants are invited to join. Most corporate blockchain, or those between organizations in a supply chain are permissioned networks. Once an individual or organization is allowed to join the blockchain they have access to the details of all transactions recorded in the network.

**4.** A private and permissioned network is the most restrictive form of blockchain. Not only does the blockchain restricts membership in the network but also restricts information to the participants in the network. Each participant is privy to the details of only those transactions that they engaged in, and not that of others.

The blockchain network property is important to regulators, as certain configurations makes it easier for regulators to monitor and control the network. From a regulatory perspective, public and non-permissioned network is the easiest to monitor due to unrestricted access to all transactions.

Bitcoin is a public and non-permissioned network; hence anyone can join the network at any time and have access to all the historical records. The Internal Revenue Service (IRS), the taxing authority in the United States, took advantage of this feature in auditing and taxing individuals who were mining and transacting in Bitcoins. IRS is becoming increasingly adept at tracing digital currency around the globe with support from international agencies and coin exchanges.[⁹](#CH003.html#fn9) IRS directly consults with blockchain companies like Chainalysis which allows IRS to be one step ahead of the participants and helps them identify money launderers, tax evaders and those engaging in nefarious transactions.

A summary of the comparison of features of permissioned and non-permissioned blockchain is presented in [Fig. 3.4](#CH003.html#fig4).

**Fig. 3.4:    A Comparison of Features between Permissioned and Non-permissioned Networks.**

![image](images/C03-FIG4.jpg)

## 3.6. ESSENTIAL FEATURES OF BLOCKCHAIN

There are some essential features of blockchain that will be presented in greater details in subsequent chapters. This section provides a brief introduction to those main features of blockchain: the consensus mechanism, smart contracts and tokenization.

The consensus mechanism is akin to the constitution or overarching rule that governs the blockchain network. It is the rules and prescribed methods by which the participants of the network can reach a collective agreement. The mechanism enables multiple participants to agree upon one version of *truth*. As the state or the truth changes with each transaction, the consensus mechanism should enable the participants to agree upon the truth continuously as new transactions occur and are appended to the blocks. This mechanism enables how and when the network decides to append new transactions into the data-ledger. There are different types of consensus mechanisms which are discussed in greater detail in the next chapter.

In most applications of blockchains there are fees to execute transactions. The fee is paid by the transacting parties and is collected by the participant or the node that appends the transaction into a block. This is also called the `gas` and it is a measure of computational power needed to execute the transaction, and the `gas cost` is the amount of fees paid.

Smart contracts are another key feature of blockchains and are simple business rules that are coded into the network. A transaction can occur only when the prescribed business logic is satisfied. For example, prior to transferring funds from the buyer to the seller, the network verifies that the buyer has sufficient fund balance. Once these types of business rules are coded into the network, these are auto-executed. When the prescribed conditions are not satisfied the transactions are blocked. Smart contracts are discussed in detail in a subsequent chapter.

Another common misnomer is with the overuse of the term “smart contract.” While the term “contract” is used, these contracts do not have any legal standing, instead these are merely simple business rules. Smart contracts are self-executory, in the sense that when the pre-conditions are satisfied the contract automatically transfers currency or assets from one participant to another. These contracts follow simple, “`if-then-else`” rules, enabling faster and error-free transactions, but have no legal bearing.

Tokenization is another key feature of blockchains. Simply put, it is digitization of any asset that can be exchanged through a blockchain. The tokenization makes the asset tradable. The underlying asset could be property, expensive painting or even a piece of music. This concept is discussed in greater detail in a subsequent chapter.

## 3.7. BLOCKCHAIN PLATFORMS
