   

# Blockchain Fundamentals

# A Gentle Intro to Blockchain Technology

Alessandro Parisi

© 2021 Alessandro Parisi 

# Introducing the Blockchain

Essentially, the *Blockchain* is a

*   **distributed** archive
    
*   based on **peer-to-peer** networks
    
*   implemented through **encryption**
    

As a **distributed and decentralized archive**, aimed at managing the transfers of digital *assets*, the Blockchain allows users to exchange digital values with each other in the form of transactions.

In this way, there is no need to resort to third parties/authorities which guarantee transactions.

Let’s now see the Blockchain goals and how they are met by the underlying technology.

## Blockchain’s Goals

Blockchain technology was originally introduced to support Bitcoin.

The main purpose was to prevent the phenomenon of **double spending** of cryptocurrencies, i.e. the possibility of spending the same currency several times.

However, the role of the Blockchain is not limited to the financial transaction sector.

In general, each transaction involving digital values can be recorded within a distributed ledger.

## Blockchain technology

Blockchain technology can take different forms and implementations.

Therefore, it represents more a concept of an architectural nature than a specific and well-defined technology.

Each different implementation can also provide specific features and functionalities, such as the execution of smart contracts.

### Blockchain transactions

The exchange of values between the counterparties within the Blockchain takes place by recurring to transactions.

The transactions are validated by the network of blockchain nodes, before being inserted into the distributed ledger.

Once appended to the ones already registered within the ledger, transactions become unalterable and unchangeable.

### Blockchain’s blocks

By its very nature, as the name itself shows, the Blockchain is nothing more than a **chain of blocks.**

Each block within the Blockchain contains one or more transactions.

The addition of new blocks to the Blockchain takes place on the basis of predetermined time elapses.

In this way, it is possible to keep the overall history of transactions, by tracing the sequence of registrations made on the blocks.

### The distributed ledger

In accounting terms, the blockchain can be considered a **distributed** and decentralized ledger, known precisely as the “distributed ledger”.

The management of the ledger takes place through the use of **consensus protocols**, which are designed to achieve the network’s consent on the transactions recorded within the ledger.

There are different types of consensus protocols, as much as there are different implementations of the blockchain.

Among the most common consensus protocols we can mention the **Proof of Work** (PoW), the **Proof of Stake** (PoS) and the **Proof of Authority** ( PoA).

# Blockchain core concepts

We’ll now introduce the concepts on which Blockchain technology is based, such as distributed archiving, decentralized peer-to-peer networks, transparency and irreversibility of transactions.

## Distributed Archiving

The ability to store data within a distributed database allows each participant to access the complete transaction history.

In addition, distributed archiving prevents a single entity from taking full control over the archived information.

Distributed archiving allows individual nodes to directly and independently verify the integrity of the information stored.

It is therefore not necessary to use third parties or intermediaries to carry out the verification of transactions.

The verification of the integrity of the information is in fact implemented through the hashing functions.

Let’s now see how peer-to-peer networks help implement distributed storaging of transactions in the Blockchain.

## Peer-to-peer networks

To implement distributed storage, the blockchain uses **Peer-to-peer** (P2P) networks.

In this type of network, no node assumes the role of central server.

On the contrary, in a P2P network each node assumes the role respectively of client and server when appropriate.

![](media/file0.png)

P2P network

## Transactions transparency

Each transaction and its associated value are publicly visible to all network participants.

The counterparties of a transaction are identified by their respective **addresses**, consisting of alphanumeric sequences.

Each transaction is subjected to a number of confirmations by the miners nodes, before being validated and inserted into the distributed ledger.

## Transactions Irreversibility

After being entered into a block and added to the blockchain, transactions are no longer modifiable.

This result is achieved by concatenating togheter the different blocks that make up the blockchain.

Any modification to the transactions already archived in the ledger would in fact lead to the alteration of the calculated previously hashes.

This alteration would be immediately evident to all the nodes in the network that would therefore prevent transaction confirmation.

# Centralized versus Decentralized networks

As we have seen, one of the basic principles of the Blockchain involves the use of a **Peer-to-peer** network communication protocol, in order to achieve **the decentralized storage** of the information.

To understand the advantages associated with decentralized networks, we will first introduce traditional centralized networks, analyzing their main characteristics, then comparing them with decentralized peer-to-peer networks.

## Centralized networks (Client-Server)

In the following image, we show a typical example of a **centralized** network:

![](media/file1.png)

Centralized network

The main feature of these types of networks is the presence of a **central node**, acting as the **server node**.

Client nodes can connect only to the central server to get the information they need.

Let’s now see some examples of centralized networks, assessing their pros & cons.

### Centralized networks: examples

A typical example of a centralized network is represented by traditional client-server web connections.

The main advantage of a centralized network is represented by the **simplicity of implementation, maintenance and updating** of this architectural model.

The necessary information is stored and updated in a single central node (the server) which makes it available to clients.

### Centralized networks: limitations

The fundamental limitation of centralized networks is represented by the fact that in the event of a malfunction or compromise of the central node (for example due to cyber attacks), the information contained therein is no longer available and accessible by the entire network.

In addition, in centralized networks the server node assumes and retains full control over information.

Due to these limitations, the Blockchain adopts a decentralized network communication protocol to achieve its own functionality.

## Decentralized (Peer-to-peer) networks

By definition, in a decentralized network there is no central node that assumes the role of control authority of information sharing.

In contrast, in a peer to peer network protocol, each individual node is able to interchangeably play the roles of client and server.

The decentralized model therefore allows each node of the network to autonomously contribute to the sharing and verification of information.

![](media/file0.png)

P2P network

This model therefore makes the presence of a central information control authority superfluous.

### Blockchain & Decentralized networks

The characteristics of decentralized networks are essential for realizing the features of the blockchain.

One of the key advantages of the blockchain is in fact the decision-making decentralization on the verification, validation and insertion of transactions within the blockchain.

These decisions are then condensed within the blocks, which constitute the building blocks of the blockchain.

# Blocks, the building elements of Blockchain

The Blockchain, as the name states, is nothing more than a **chain of blocks**.

The simplest unit of a blockchain is in fact constituted by the block.

Each block contains within it a certain number of transactions that represent the transfers of values ​​between the counterparties, carried out within the blockchain.

## Blocks and transactions

Each block contains batches of transactions with their hashes.

The number of transactions contained in a block depends on the **block size**.

The average size of a block is about 1 MB, but it can even reach larger sizes, as in the case of Ethereum.

In Bitcoin, a block contains **more than 500 transactions on average**

Let’s now see how the **block time** affects the size and the number of transactions that can be embedded inside a block.

## Blockchain block time

Each blockchain has its own **block time**, i.e. the approximate amount of time required to add a new block to the Blockchain.

The **block time** affects the **number of transactions** that are inserted within the single block.

For example, if the blockchain had a blocking time of five minutes, and there were only four transactions completed during those five minutes, the block will consequently contain only those four transactions.

### Block time and number of transactions

In the event that there are too many transactions compared to the block size, the transactions should wait for a block still open, which has enough space left to accommodate and insert them within it.

In the case of Bitcoin, the blocking time is 10 minutes.

This value derives from the limits set in the Bitcoin source code.

These limits in turn derive from the objective of issuing no more than 21 million bitcoins in the period between 2009 and 2024.

Remunerations for miners are reduced accordingly by half every four years.

## The structure of the blocks

Each block consists of a **header** and a **list of transactions.**

Each block includes the hash of the previous block, thus the blocks as a whole constitute a chain that connects all the blocks together.

The first block of the Blockchain is called “genesis block”.

### Block header

The block structure is represented by the block header.

![](media/file2.png)

Bitcoin block header

This data structure contains a series of information relating to blocks, also known as metadata.

*   Hash of the previous block: this value is required to compute the corresponding hash of the new block to be added to the blockchain;
    
*   Merkle root: it is the hash value associated with the root node of the transaction tree, which acts as a check on the validity of the block;
    
*   Timestamp: it’s the time stamp assigned to the block;
    
*   Nonce: an arbitrary value that is used in block mining.
    

The blocks are stored in a tree structure known as the Merkle tree.

# Blockchain transactions - Nature and characteristics

The Blockchain, as the name states, is nothing more than a **chain of blocks**.

The simplest unit of a blockchain is in fact constituted by the block.

Each block contains within it a certain number of transactions that represent the transfers of values ​​between the counterparties, carried out within the blockchain.

Transactions must undergo the confirmation phase by miners, which are rewarded for their work in bitcoins. Without confirmation, no transaction can be convalidated.

![](media/file3.png)

Blockchain overall process

## Transactions and Distributed Ledger

One of the characteristics of Blockchain is that it makes the intervention of intermediaries in transactions superfluous.

People can carry out transactions without third parties being involved. The shared ledger itself manages and ensures the **integrity** and **reliability** of transactions between the parties.

The ledger is maintained and updated in a distributed manner by all participants in the blockchain, and all nodes taking part of the networks can verify the reliability of transactions without resorting to trusted third parties.

Let’s now see the characteristics of the **distributed ledger** and the ways in which it is managed.

## Distributed Ledger

From the accounting point of view, the ledger is simply a cronologically held register of economic transactions.

It is analogous to the ledger commonly used by banks and other financial institutions, to reconcile the accounting balances.

All the charges and credits during an accounting period are calculated to prepare the accounting balance.

The balance sheets of banks, financial institutions and businesses, are compiled using accounting records within a ledger.

When we conduct a traditional financial transaction using fiat currency, we have a third party ledger that keeps information about each transaction.

Some of these third-party trust systems are traditionally represented by banking and financial institutions (such as VISA, MasterCard, and so on).

Blockchain has radically changed the management methods of this accounting system, making all the network operators participate in the preparation of the ledger.

This is why the ledger is also called **distributed ledger**: all those who carry out a transaction in the blockchain, also have access to the registration of other transactions that have occurred, or that are taking place in the blockchain.

The data structure employed in the implementation of the distributed ledger is known as the *merkle tree*:

![](media/file4.jpg)

Merkle tree

Basically, it traces the structure of a tree, whose leaves correspond to the different transactions recorded within the ledger; for each path, starting from the root node, the corresponding hash values ​​are calculated, the references of which are stored inside the blocks.

Since each transaction is linked to the previous ones, any subsequent changes would be immediately recognizable by anyone, simply by recalculating the corresponding hash values.

Being distributed, this decentralized ledger provides several confirmations of authenticity for each transaction that has occurred.

One of the key properties of blockchain technology is that it encourages a **global** and **shared** concept of **trust** in transactions.

# Assuring transactions integrity

How is the integrity of transactions guaranteed within the Blockchain?

This is what we will deal with now, analyzing the different cryptographic features, such as **hashing** and **hash digests**, highlighting the differences that exist with the actual encryption algorithms.

Finally, we will show a practical example of calculating a hash digest using the class of SHA algorithms used in the implementation of the Blockchain, using simple tools available online.

## Hash digests: the fingerprints of the blocks

Let’s start by showing the hash digests, considered the “fingerprints” of the blocks of the Blockchain.

As we have said, the integrity of transactions within the blockchain is achieved through the use of hash functions.

Hash functions constitute a class of algorithms that make it computationally unlikely that different alphanumeric strings will give rise to equal hash values.

Hashing algorithms are specifically designed to be sensitive to even the slightest variations in the input data.

### Encryption and Hashing: Differences

An interesting property of hashing algorithms is that they are not reversible, unlike cryptographic algorithms.

**Reversible** here means that it is possible to convert an encrypted text into its original plaintext, using the decrypting function, which is the inverse of the encrypting function:

![](media/file5.jpg)

Encrpytion and decryption

Unlike cryptography, there is no reverse function for hashing.

This means that we cannot convert the calculated hash value to its original input, as hashing is a one-way process by definition.

Now let’s see how the Blockchain exploits the irreversibility characteristics of the hashing algorithms to guarantee the integrity of transactions.

### Hashing and transaction integrity

Hashing algorithms are designed to prevent **collisions**, i.e. the possibility of obtaining the same hash value for two different input strings.

Thanks to these features, hashes can be considered a kind of **data fingerprint**: any variation, even minimal, in the original data will result in a very different calculated hashing value.

Making use of hash functions within the blockchain, anyone can verify the integrity of blocks and transactions by calculating their corresponding hash values ​​and comparing them with the values ​​stored within the blockchain.

There are several families of hashing algorithms: the bitcoin Blockchain adopts the SHA-256 hashing algorithm.

### SHA hash value: calculation example

In the example below, we see how the hash value generated by the hashing algorithm radically changes even in the case of minimal changes in the input data.

The images below show the results obtained using the hashing tool available online at www.sha1-online.com

![](media/file6.png)

SHA256 digest ex.1

![](media/file7.png)

SHA256 digest ex.2

As it is easy to notice from the output produced, even minimal variations in the input strings determine completely different output values, that are not easily attributable to the original ones.

# Achieving Trust in a Distributed environment

One of the most interesting tasks of the Blockchain concerns the goal of achieving the shared consensus of the network on the **global state** of the transactions recorded in the distributed ledger.

That of shared consensus represents one of the classic problems of computer science relating to distributed systems.

As we have seen previously, the Blockchain is nothing more than a particular implementation of a distributed storage system; as such, many of the solutions adopted by the Blockchain reproduce the solutions commonly adopted by distributed systems.

First of all, distributed systems must provide a consensus protocol that is “fault-tolerant”, meaning that it is robust and capable of tolerating any malfunctions, to ensure that a common consensus can be reached on the state of the system as a whole.

By reaching a consensus on the global status of the transactions stored in the ledger, all the players in the distributed system consequently share a common “truth” on which to place their “trust”.

Achieving consensus is fundamental in a distributed system, in order to share a common “truth”, to which to attribute “trust”.

Let’s now see the most common consensus protocols. ## Proof of Work (PoW)

In the PoW consensus protocol, the nodes of the Blockchain must employ high computational resources to solve mathematical challenges of increasing difficulty, required in order to reach the consensus on transactions.

The PoW, in fact, generates a hash value of a given length, and the goal of the nodes is to discover the input value that gave rise to this hash value.

Since, as we have seen previously, the values ​​calculated by hashing algorithms are **not reversible**, to solve these challenges it is necessary to proceed “by brute force”, that is, it is necessary to proceed **by trial and error**.

This results in a lot of computational work by the block validation nodes (hence the name “Proof of Work”).

The node that finds the solution to the math challenge sends it to the rest of the network for verification by the other nodes (in the Bitcoin blockchain, these nodes are called “miners”, and they receive a reward for their activity, which is quantified in units or fractions of bitcoins).

The logic of the PoW is to make adding a new block to the chain computationally difficult and onerous, thus reducing the possibility for anyone of being able to modify the transaction ledger.

Then, once the solution found by the node has been verified, the block created can be inserted into the blockchain.

The length of the blockchain increases accordingly, reflecting the computational effort (PoW) it took to reach the current size.

Therefore, the consensus on which of the local copies of the blockchain should be considered the updated one, is reached simply by selecting the longest chain, which is consequently attributed the trust of the network.

Given the characteristics of the PoW, it is very difficult to modify a block (thus altering the transactions within it) once it has been inserted into the blockchain, and this difficulty increases as the length of the chain increases.

The advantages of PoW are not without costs, both in terms of the time required to validate the blocks, and the electricity required to meet the required computational load.

To try to address these disadvantages, the alternative consensus mechanism known as Proof of Stake (PoS) has been proposed.

## Proof of Stake (PoS)

In the case of the PoS protocol, digital signatures are used instead of hash values, and the node that was authorized to create the next block to be included in the blockchain is selected, based on the amount of investment made by that node in the network.

Block validation is rewarded by attributing financial commissions to the nodes that contributed to the validation.

## Proof of Authority (PoA)

Unlike previous mechanisms, the Proof of Authority (PoA) protocol is a consensus mechanism that works in the presence of a limited number of transaction validation nodes.

Its use is therefore considered more appropriate in permissioned blockchains, rather than in public blockchains.

In the case of PoA, consensus is reached on the basis of the greater trust (authority) recognized in these nodes.

# The problem of the Byzantine Generals

One of the classical coordination problems, most studied in the field of computer science and distributed systems, is known as the “Byzantine Generals” problem.

The problem concerns the achievement of consensus by the Generals who surrounded the enemy, on the moment in which to launch the attack all together, to guarantee the success of the military operation.

The problem lies in the fact that Generals can communicate with each other remotely, through the reciprocal exchange of messages.

Each General decides whether to attack or retreat, communicating their decision to the others by sending messengers.

Among these, however, there may be “traitors”, who prevent with their behavior to reach shared and unanimous consent, by sending contradictory messages to others.

The final aim, in fact, is to reach a shared consensus on the action to be undertaken all together, to attack or withdraw, avoiding a disordered behavior, which would determine a sure failure.

### Byzantine Generals problem in the context of the Blockchain

The problem of the Byzantine Generals arises in the context of the Blockchain in relation to the need to choose the correct version of the ledger, which preserves the real history of transactions.

In the blockchain, this choice occurs in the presence of nodes that cannot communicate correctly with others, or of dishonest nodes that intend to cheat on the correct version of the transaction history, thus making it difficult to reach consensus within the network.

## What solution to the problem of the Byzantine generals?

The problem of the Byzantine Generals therefore represents a problem of coordination on how to reach shared consensus in the presence of possible errors (represented by the conflicting messages sent by the “infidel” Generals).

This coordination problem also arises in achieving consensus on Blockchain transactions.

Therefore, it is necessary to implement a consensus protocol capable of maintaining its reliability even in the presence of “unfaithful” nodes.

It has been shown that the Byzantine Generals problem does not admit a solution in the event that the number of infidel generals is equal to or greater than one third of the total.

A consensus protocol capable of resisting the problem of the Byzantine Generals is called Byzantine Fault Tolerant (BFT).

The Proof of Work consensus protocol demonstrates this capability.

In the case of the PoW, the problem of the Byzantine Generals is solved by the fact that the protocol does not require the participation of all the nodes of the network to reach consensus.

# The Purpose of Mining

The ways in which consensus is obtained within the network varies according to the different types of blockchains.

Consequently, not all consensus mechanisms are suitable for all blockchains.

In the case of the Bitcoin’s blockchain, the mechanism for achieving consensus is based on the economic incentive.

Nodes are encouraged to help reach consensus on transactions through their mining activity, which is rewarded in the form of bitcoin (as we saw when talking about PoW).

This system of economic incentives is particularly important for public blockchains, as it allows them to achieve and maintain the sustainability of the architecture itself.

# The different types of Blockchain

There are different implementations of Blockchain technology, which offer different features and functionalities.

In fact, blockchains can be differentiated not only based on the consensus protocol adopted, but also for other features, such as the ability to execute smart contracts.

So let’s see the main types of blockchains currently existing.

### Public blockchain

A public blockchain is a blockchain in which anyone can join, without the need to obtain permissions based on the role played within the network.

Therefore, public blockchains are also called **permissionless** blockchains.

Among the examples of public blockchains we can mention Bitcoin, Ethereum, Litecoin and so on.

### Private blockchain

In private blockchains, read and write permissions within the network are assigned to different groups of users.

Read permissions are usually public or assigned to an indefinite number of users, while write permissions are reserved for a predetermined group of users or organizations.

Consequently, the validation of the transactions is entrusted to a predetermined number of nodes.

Some examples of private blockchain include the Gem Health network, Corda, and so on.

### Consortium Blockchain

In this type of blockchain, consensus management is limited to a predefined group of subjects.

Consequently, there are no incentives or economic rewards for the validation of transactions.

Transaction validation times are reduced compared to public blockchains.

Among the examples of blockchain consortium we can mention Deutsche Boerse and R3.

# About the Author

Alessandro Parisi has been an IT professional for over 20 years, acquiring significant experience as a Security Data Scientist, and as an Artificial Intelligence Cybersecurity and Blockchain specialist.

He has experience of operating within organizational and decisional contexts characterized by high complexity.

Over the years, he has helped companies to adopt Artificial Intelligence and Blockchain DLT technologies as strategic tools in protecting sensitive corporate assets.

He holds a Master Degree in Economics and Statistics.

Please find further info on the professional profile of the Author at the following link:  
[https://www.linkedin.com/in/parisialessandro/](https://www.linkedin.com/in/parisialessandro/)

# Image Credits

Unless otherwise expressly indicated, the images appearing in the text are available under public domain license and can be found on the Wikipedia commons website (https://commons.wikimedia.org)