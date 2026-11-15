

- 1. If the central authority fails, our whole system is not working.
- 2. It is also possible that central authority is biased to some participants in the system.

Unlike the centralized system, a decentralized system doesn't have a single authority. In fact, all the participants in the system have a copy of the data. It means if anyone can change the database, others can also see their reflection.

To overcome the drawbacks of centralized systems, blockchain was developed. It was first introduced by researchers in 1991. But it was mainly used in bitcoin in 2009. Nowadays, bitcoin application has a very high demand in cryptocurrencies.

## 12.1.1 WHAT IS BLOCKCHAIN?

It is a platform for exchanging digital assets peer to peer, from me to you. That’s why we call it an internet of value.

Blockchain is defined as a decentralized distributed ledger that records the provenance of exchanging a digital asset. Ledger refers to the immutable database [1].

In other words, it has a chain of blocks connected to each other with the help of previous block hash. Each block contain three things: hash, data, previous block hash (Figure 12.1).

The above figure says that each block is connected to previous block hash and a new hash for that particular block hash is calculated by combining data and previous block hash.

## 12.1.2 BLOCKCHAIN IS TRUSTWORTHY

Suppose we change the data of second block (Figure 12.2).

Then it will change the hash of that particular block. Then ultimately it will change every block hash afterwards (Figure 12.3).

Then the hash of the particular block mismatch with the next block. As a result it will inform that data is change in the system (Figures 12.4 and 12.5).

Now, the next block hash also changes accordingly (Figures 12.6 and 12.7). Hence, we will see that if we change the data in our system, it will change the subsequent blocks afterwards. Hence, it is trustworthy.

- Linked list
  - 1. Replicated
  - 2. Distributed

![](img/c5c79333a43e0e9a69d1119635e3c244_190_0.png)

- 3. Consistency maintained by consensus
- 4. Cryptographically linked
- 5. Cryptographically assured integrity of data

- Used as:
  - 1. Immutable ledger of events, transactions, or time-stamped data
  - 2. Tamper-resistant log
  - 3. Platform to create and transact in cryptocurrencies
  - 4. Log of events/transactions unrelated to currency.

![](img/c5c79333a43e0e9a69d1119635e3c244_191_0.png)

![](img/c5c79333a43e0e9a69d1119635e3c244_191_1.png)

![](img/c5c79333a43e0e9a69d1119635e3c244_191_2.png)

![](img/c5c79333a43e0e9a69d1119635e3c244_191_3.png)

![](img/c5c79333a43e0e9a69d1119635e3c244_192_0.png)

### FIGURE 12.6 Third block hash changes.

![](img/c5c79333a43e0e9a69d1119635e3c244_192_1.png)

### FIGURE 12.7 Similarly with fourth block.

We all know that a linked list is a set of blocks which are connected to each other by some kind of a link. In case of a data structure linked list, you have the nodes, and nodes are connected by pointers and pointers are basically memory addresses. But, in case of a blockchain technology, the blockchain is a distributed data structure, that is replicated at various nodes or various computers and therefore, the linking is not based on memory addresses. So we have a different notion of linking between nodes and each of these nodes are called blocks. So therefore, we can imagine a blockchain as a series of blocks and each block is connected to its previous block and later block by some kind of a link.

And so it is replicated all over because replication gives you a number of different advantages like if one of the replica gets corrupted, the other replicas are there to make sure that the integrity of the information contained in the in the data structure is maintained. And also replication gives you some kind of guarantee of integrity of data. Therefore, blockchain is a data structure that is maintained distributedly and that is replicated and main aim of blockchain is to maintain the full integrity of the data.

And what is the integrity? Integrity means that the data once it has been agreed by all the relevant parties to put in the data structure, it has not been tampered with.

Nobody has come and changed the data and claimed that this is the data that was put in. The blockchain is designed in such a way, so that it is an immutable ledger of events, which means it is a log that cannot be changed by a malicious party or by mistake. And therefore, all the data that you put in there could be event logs, it could be transactions, it could be various kinds of accesses and modifications you do to some other thing like a data or you do a property transaction.

When you make a banking transaction, the bank keeps logs of when you interacted with its banking servers and what you did, what transactions you made; all this is logged. The main problem with keeping logs without any notion of protection of the integrity is that somebody can tamper with the logs and somebody can delete some of the accesses. And therefore, later on when you check the log, you would know some part of its history. All these things logs are has to be kept in an immutable ledger. And that is what blockchain provides.

![](img/c5c79333a43e0e9a69d1119635e3c244_193_0.png)

### FIGURE 12.8 Decentralized consensus between participants.

The internet of things on the other hand also play a main role in a network of connected devices. The goal of IoT is to provide a reliable and protected exchange of things, but the security challenges will be solved by cryptographic techniques. These techniques include user authentication and knowledge privacy [2].

## 12.2 THE NAKAMOTO CONSENSUS MECHANISM

### Consensus as an emergent phenomenon

The main invention by the creator of bitcoin Satoshi Nakamoto, is a decentralized consensus mechanism. It gives us provision for the participants to agree on the contents of the database (Figure 12.8).

If we want to change our data then there is a majority of voting in favor of changing the data. Only then can we change the data [3].

There is no single point of failure in the blockchain as it is decentralized and replicated.

## 12.3 PEER-TO-PEER NETWORKS

The data in the blockchain is connected peer to peer. It means the data in one system has the same data in other system also. Each node in the system is connected with other nodes in the system. It means if we want to change the data in one computer

![](img/c5c79333a43e0e9a69d1119635e3c244_194_0.png)

### FIGURE 12.9 Peer-to-peer network.

then we should also change the data in other computer in system connected in the peer-to-peer manner (Figure 12.9).

## 12.4 HOW WE ADD A NEW BLOCK IN OUR SYSTEM

The process given by Satoshi Nakamoto in 2008 is explained in following steps:

- 1. When a new transaction comes, it will first be broadcast to all nodes.
- 2. In the second step, each and every node collects this new transaction into a particular block.
- 3. In the next step, each node is working on finding a consensus for this block.
- 4. In the next step, when a node gets a consensus it will broadcasts the block to all available nodes.
- 5. Now, if all the transactions in the block are marked as valid and not behave malicious, then only nodes will accept the block.
- 6. Lastly, nodes express their acceptance of the block by working on creation of the next block in the chain, by joining the hash of the accepted block as the previous hash [3].

Now, we come to the point that the data in our system is transparent and immutable.

## 12.5 APPLICATIONS

Now we come to say that we can use blockchain in such a case where a constant amount of data is required, so that no one can change it.

- 1. In real estate for storing information related to house owner.
- 2. Online voting
- 3. Digital Identity card for storing information such as birth certificate, unique voter ID card, passport, pan card, Aadhar card, driving license, medical records, insurance, etc.
- 4. In banking and finance
- 5. In medicine and healthcare
- 6. In Internet of Things
- 7. In travel and transportation
- 8. In cryptocurrencies like bitcoin, etc.

Now we will discuss blockchain in medicine and healthcare in detail. One of the best uses of blockchain is in healthcare.

Developed and even developing countries invest a large amount of their gross domestic product (GDP) on the healthcare domain. In the meantime, hospital costs are too expensive, along with unfit ways and health data losses are poised to continue.

This is one such area in which we can use blockchain. It can do for us many things such as storing guarded patient information to handling the epidemics.

Main concerns related with blockchain applications in healthcare include:

- 1. A large network infrastructure at different levels.
- 2. There should be Identity verification and authorization of all participants.
- 3. There should be constant patterns of verification process to access electronic health data or information.

There should be a distributed data of patients that will be shared between different hospitals but there must be a power given to patients to share their data.

## 12.6 HOW BLOCKCHAIN WILL CHANGE THE HEALTHCARE SYSTEM

- a) Health records:

We know very well that electronic medical records (EMR) are the pillar or foundation of our modern healthcare system. Each time we visit the doctor, these medical records grow. And as every hospital and every doctor's office has its own way of storing the patient information, it is always difficult for healthcare providers to obtain them. The basic purpose of many companies like Patientory, Medibloc, and Medicalchain is to solve this problem. The purpose of this is to give patients authentication over their entire medical

