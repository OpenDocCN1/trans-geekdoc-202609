
- All workstations accessing the data simultaneously increase network traffic and reduce efficiency.
- If central data is corrupted or lost, the entire database will be no longer useful.
- Having all data stored in one place makes it prone and also easier for hackers to target the database.
- If any software upgradation is required to the server, then all the operations occurring on the database must be halted.
- After a certain threshold, the performance will not increase significantly even if the hardware and software capabilities of the server node are enhanced.

## Decentralized Database System

As the name itself suggests, the database is not centralized means all the data is not stored at one particular place. Here, the data is distributed and stored at multiple nodes, eliminating the need for a central server. This also means that the system does not depend on a singular and central point of control and hence does not have sole authority. Decentralization means no node has any authority over any other node. A node here refers to any workstation accessing the database. Every node makes its own decision, and the end behavior of the system is an agglomeration of the decisions of the individual nodes. This is an interconnected information system that is consolidated using a peer-to-peer network. Blockchain technologies such as Bitcoin and Ethereum are examples of decentralized systems.

### Advantages

- Having multiple storage locations, it does not have a single point of failure. As the information is shared among multiple nodes, breakdown of any one node doesn’t impede work as data can be retrieved from any other node. Higher fault tolerance and zero downtime due to redundancy.
- Does not have a sole authority, reducing the trust we put into a single third party. More autonomy of resources.
- No or less censorship as the data is openly available to all the nodes and is not manipulated by a central power.
- All operations and data have transparency.
- All the load is balanced among multiple nodes, reducing traffic and avoiding bottlenecks.
- Some nodes will always be present, increasing availability of data as compared to a single server which must be operating around the clock.
- Difficult to corrupt the data as it has multiple copies.
- Access time of data is faster as different nodes can be created in areas of high usage.

### Disadvantages

- In case of malfunction of any node, it is difficult to find it.
- Difficult to coordinate big tasks as no chain of command exists to control or direct workflow of any node.
- Maintaining a decentralized system is quite expensive for small organizations.
- Requires timely optimization, the absence of which results in inconsistent performance.
- Distribution of data increases the risk of data security and privacy as some of the nodes may have lesser security compared to a central server which increases its chances of data hacks.
- Distributed authority can also cause misuse.

From this, we can see that a decentralized system is far better than a centralized system when it comes down to the basic aspect of data access. However, the above text also explains how it may be disadvantageous in the areas of security and autonomy of power. These downsides can easily be overcome with the help of additional mechanism implementations which will establish the supremacy of the decentralized system over a general centralized one. The first can be solved using encryption and the second by putting the consensus mechanism into place, both of which will be discussed in detail later on. One major technology is the blockchain technology which is making rapid strides in the modern era [1].

## BLOCKCHAIN TECHNOLOGY

### Bitcoin

Often associated with bitcoin, blockchain was first implemented by Satoshi Nakamoto in 2008 who created the first Crypto currency, the blockchain based project called bitcoin. So, what exactly is a bitcoin? It is basically a Crypto currency that allows anonymous payment transactions of the bitcoin owners over an open and decentralized network using encryption.

Using consensus and cryptographic techniques, it builds a trust paradigm between untrusted users around the globe. It offers lower transaction fees than conventional online payment mechanisms and is operated by a decentralized authority antithetical to government issued currency. However, bitcoin is not a legal tender having no physical form but manages balances on a public ledger and uses peer-to-peer technology to facilitate payments. Moreover, crypto currencies do have their own flaws and forte. Flaws being their volatility of exchange rate making their prices unpredictable and investing in them a huge gamble. They are highly dependent on the blockchain technology making them share vulnerabilities with its very own architecture. They are also known for their use in illegal activities. Their forte is primarily in transparency, resistance to inflation and elimination of third parties in transactions. Bitcoin is not the only Crypto currency out there, but rather its success has spawned many others including Ethereum, Litecoin, Ripple, Dash, zCash, etc [2].

### What is Blockchain?

The concept was first introduced when a group of researchers wanted digital documents to be time stamped, so that they cannot be backdated or changed, in order to maintain legitimacy. Broadly, blockchain is a decentralized and distributed digital ledger of transactions that may be public or private/permissioned. Each transaction is stored as a block. Each block contains details regarding the transaction such as date, time, amount spent, product as well as information about who is participating in the transaction. After this block is created, it must be verified by the nodes present on the decentralized peer-to-peer network where the nodes either agree or disagree with each transaction which forms the basis for the consensus mechanism. Once, a majority of nodes have validated the transaction, it is time stamped and given a unique hash storing it onto the database as an immutable record. Then the ledger is updated and the block is added to the database which is the “chain” of blocks. There is no need for any administrator as the blockchain users are the administrators themselves. Each block or entry is linked to a specific user along with their previous entries to maintain a legitimacy record of each user on the network. Over the peer-to-peer network, along with all the users on it, a blockchain system can be controlled autonomously to manage information openly.

As complex as it may sound, blockchain is actually a very simple concept. It consists of a number of blocks connected or linked together with their unique hash values assigned to them. Many transactions can be housed under a single block. This huge “chain” of blocks is the database containing information that is present on each and every node of the peer-to-peer network. The identity of the users is anonymous or pseudonymous [1, 3].

### Blockchain Architecture

Basically, as described before blockchain is a chain of blocks containing information forming a database. A copy of the chain is stored in each node of the peer-to-peer network making blockchain secure and original or authentic. All these nodes are linked together instead of a centralized server system making the network decentralized. The first block of the blockchain has no parent block and is called the genesis block. This does not reference or point to any previous block and is hence a special case. It is often labeled as block 0 in modern versions of bitcoin. Its previous hash is set to 0. This genesis block has its own hash, which is added to every new block added to the blockchain creating a unique combination. The genesis block tells about the origin of that particular blockchain and forms a trust among the miners. Apart from instilling a trust for the authenticity of the blockchain the genesis block is not really necessary. Height of the blockchain refers to the total number of blocks present in the blockchain. The various components of a blockchain include [4]:

### Block

Any valid block in a blockchain consists of a block header and block body. The block header contains the following essential components:

- **Block Version:** describes the structure of any block interior as well as the validation rules to follow to enable appropriate reading of the block contents by any node on the network.

- **Merkle tree root hash:** a hash tree or Merkle tree has a cryptographic hash of the block on each of its leaf nodes. The first node’s hash is the root hash. Subsequent non-leaf nodes have hashes of their child nodes. It allows secure and efficient verification of the data in these blocks to check for unadulterated blocks sent from other nodes. It is also used to counter degradation and maintain the integrity of data. This is primitively the transaction data that is converted in the form of an alphanumeric fingerprint.

- **Previous hash:** any block contains the hash of its previous block or parent block forming a link.

- **Timestamp:** stores date and time of transaction completion which is immutable.

- **Nonce:** hashing is done using the block header along with an extra number called “number once”. It is basically an arbitrary number used for cryptographic purposes. It is used only in proof-of-work systems.

- **Target:** a value based on the difficulty of the blockchain network, which tells miners how difficult it is to add a block to the blockchain. Block difficulty is a number value that tells us the time interval between adding two successive blocks to the blockchain. Higher the difficulty, harder it is to find a hash that works and hence lower the target.

The components of the block header have been summarized in Fig. (1). Additionally, the block body consists of the transactions as well as a counter, which keeps a track of the number of transactions that are stored under the same block. The number of these transactions depends on their size as well as the size of the block [4].
