
Selvakumarasamy
SRM Institute of Science and Technology
Chennai, India

Susee S K
SRM Madurai College for Engineering and Technology
Madurai, India

Shenbagavadivu
SRM Valliammai Engineering College
Chennai, India

Sahunthala S
Rajalakshmi Institute of Technology
Chennai, India

Anusoya S
B.S. Abdur Rahman Crescent Institute of Science Technology
Chennai, India

Subramaniyam
SRM Institute of Technology
Nagar, India

Karthik S
SRM Institute of Technology
Chennai, India

VijayAnanth Suyambajan
nVels Institute of Science and Advanced Studies
Chennai, India

Mubeena S
B.S. Abdur Rahman Crescent Institute of Technology
Chennai, India

Manikandan T
Rajalakshmi Engineering College
Chennai, India

Sandhya S
SRM Valliammai Engineering College
Kattankulur, India

Jean Shilpa V
B.S. Abdur Rahman Crescent Institute of Technology
Chennai, India

![](img/7237166d0c6f79ea99cc6e305e5ec1f5_12.png)

## Foundations in Blockchain

## Architecture, Security, and Privacy for Blockchain Using Enabling Technologies

Priyadarsini K, Karthik S, Anitha, Jean Shilpa V, Anusooya S, Jeba Sonia J, Charanjeet K

### INTRODUCTION

In 2009 Nakamoto Satoshi developed blockchain to make Bitcoins more secure. As of January 2018, the capital of Bitcoin was $80 billion. Blockchain is a multi-disciplinary topic that involves mathematics, big data, IoT, and cloud computing. Blockchain isn't always proved, however, it is also used as the primary software of Bitcoin. A block is part of the blockchain that consists of a block header, which is divided into fundamental hash, block model, timestamp, nonce value, simple records, and Merkle root. The block also includes series of information with cryptography and shared ledger. It performs unusual operations by consensus, smart contracts, preferred ledger, and cross-chain generation. Each block is connected to different blocks (nodes) and knows the previous and subsequent hashes in peer-to-peer network. Blocks are not deleted or changed by blockchain users. It has verification facility by which individual blocks have to be completely verified. Blocks have the traits of decentralization, anonymity, independence, openness, immutability, safety and agreement, collective renovation, programmability, transparency, unforgeability, and auditability [5] (Figure 1).

A transaction is deleted from public ledger in a list of instructions or information recorded in blocks as Bitcoins are exchanged among users. Customers in transactions participate through blockchain addresses [16] and are controlled by using wallets. A user is not limited to one address; they can access several Bitcoin addresses in their wallets. These addresses are mapped to unique public/private key pairs through transformation characteristics [18]. A transaction among addresses, say, a and b, is expressed as:

## Blockchain

| Hash of current block | Hash of previous block | Timestamp | Nonce | Other information |
| :--- | :--- | :--- | :--- | :--- |
| | | | Merkle Root | |
| | | | Main data l | |
| | | | Main data N | |

FIGURE 1 Block structure.

(ab) = {source, BTC, b, Sig ska (source, BTC, b)}

Where Sig ska is the signature with the aid of a private key and BTC is the Bitcoin amount to be transferred. There are a few shadow addresses that are mechanically created when transactions change values. A transaction (P, C, d, t, s) among P and C is carried out and there may be CS, Devote, Open, and Nice stages denoting execution, starting, and aborting the transaction. If the transaction is completed successfully by secret key s, the Bitcoin price d is assigned to the receiver. There are several types of metadata: text, which uses many textual messages; hash, a code that specifies the possession of files in the blockchain; financial document, a file of virtual payments or property; copyright, which allows manufacturers to promote and display the file; script; the many languages used for blockchain; photo, photos are sometimes also present in a blockchain; and archive, records saved in the compact form (Figure 1.2).

The authority is the centralized authority in a centralized device who has all the rights to update the database without third-party permission. In a blockchain, the advantage is that the consent of anybody might be required to perform an operation. It minimizes the monopoly of the relevant authority [24, 28, 46]. There are numerous varieties of blockchain: private for a private enterprise of small range; public or all, which have a wider range; and consortium for a group of organizations. They may be analyzed on the basis of the following parameters:

- 1. Only a few private nodes can perform the validation process of consensus determination.

| Block representing transaction | Participants in Block chain | Miners to validate transaction |
| :--- | :--- | :--- |
| Block1 | Block2 | Block3 | Blockn |

FIGURE 1.2 Chain of blocks.

## Architecture, Security, and Privacy for Blockchain

- 1. Only a consortium or organization has the power to decide whether information will be public or private.
- 2. Immutability: Blockchains are difficult for outsiders to tamper, while the consortium or organization is authorized to alter the blocks.
- 3. Efficiency: The fewer the number of operations, the better.
- 4. Centralized: By one organization.
- 5. Consensus process: Only certified nodes are able to join.

## ARCHITECTURE OF BLOCKCHAIN

The blockchain architecture is a collection of layers showing the functions [1, 32]:

- i. **Data layer**: It is used to store accurate information by nodes in the shared ledger. It exhibits a higher satisfaction level in consensus efficiency.
- ii. **Network layer**: It creates a network with no fixed topology. Nodes can verify, transmit, route.
- iii. **Consensus layer**: It is used to reach agreement among nodes. In a peer-to-peer network, all nodes work together to reach a consensus by Byzantine consensus. There could also be an oral or written consensus. After a block miner signs the blocks and broadcasts them, the receiver signs a new block after verification.

### TABLE 1. Different Cryptocurrencies

| Cryptocurrency | Year of Launch | Hashing | Mining |
| :--- | :--- | :--- | :--- |
| Bitcoin | 2008 | SHA-256 | PoW |
| Litecoin | 2011 | S crypt | Same as Bitcoin PoW |
| Peercoin | 2012 | SHA-256 | PoW and proof of stake |
| Primecoin | 2012 | Cunningham Chain | PoW |
| Ripple | 2014 | Digital Signature | Consensus based |
| Ethereum | 2014 | Ethash | PoW |
| Permcoin | 2014 | Floating Digital Signature | PoW |
| BlackCoin | 2014 | S crypt | Proof of stake |
| Aurorcoin | 2014 | S crypt | PoW |
| Darkcoin | 2014 | X11 | PoW |
| Namecoin | 2015 | SHA-256d | PoW |

![](img/7237166d0c6f79ea99cc6e305e5ec1f5_18.png)

FIGURE 1.3 Year-wise paper selection.

- **Contract layer**: It is the lowest layer to make a blockchain operational via sophisticated programming. Examples are Ethereum and Definition. There are vulnerabilities in contracts, errors in encoding, cryptography, aligned incentives, transaction ordering, timestamp dependence, mishled exceptions, reentrancy, and data feed.
