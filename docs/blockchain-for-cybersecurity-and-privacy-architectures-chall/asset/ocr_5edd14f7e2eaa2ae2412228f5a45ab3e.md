# Blockchain for Internet of Vehicles Security

# 8.4.3.1 Public Blockchain

Public blockchain or permissionless blockchain is open and decentralized. Any peer that joins the network can read, send, or receive transactions. Moreover, the peer can participate in the consensus process. There is no central authority to manage membership. Bitcoin is an example of a public blockchain.

# 8.4.3.2 Private Blockchain

Private blockchain or permissioned blockchain has restrictions on joining the network, reading or writing transactions, and participating to create blocks (mining). In this system, a central authority manages the membership and attributes the rights to the peers. This management ensures the trustworthiness of the participant peers. Hyperledger is the most known permitted blockchain.

# 8.4.3.3 Consortium Blockchain

Another type is the consortium blockchain, which is a hybrid blockchain (i.e., the network includes public and private blockchains). This type is required when different companies operate a blockchain together; these companies are equally involved in the consensus protocol. Quorum is a solution to develop consortium blockchains.

# 8.4.4 ARCHITECTURE

# 8.4.4.1 Transaction

Transactions are the fundamental units of a blockchain (Antonopoulos 2014). Transactions are data structures that can represent various actions. In cryptocurrency, it represents the transfer of value between participants. The transaction lifecycle is introduced as follows (Bashir 2018; Bikaditya, Gautam, and Priyansu Shekhar 2018):

+   - A transaction's lifecycle starts with the transaction's creation.
- The transaction is then broadcasted to the blockchain network.
- Each node validates and broadcasts the transaction, until it reaches almost every node in the network.
- The transaction is verified and included in a block of transactions.
- The block is recorded on the blockchain.

Once a transaction is confirmed and recorded in the blockchain, it cannot be edited or removed. The structure of a transaction is dependent on the application, but at minimum, it requires a value, a hash, identity information, and timestamp information.

# 8.4.4.2 Block

A block is a container data structure that groups valid transactions for inclusion in the blockchain. The block is made of a header, containing metadata, followed by a body that contains a long list of transactions (Antonopoulos 2014). The block header of the Bitcoin contains the following information:

+   - Block version: The version of the block that describes the structure of the data and indicates which set of block validation rules to follow.