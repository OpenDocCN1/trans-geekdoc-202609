
# Blockchain Fundamentals

## The Growing Chain

The length of the chain increases as time goes on. As soon as a new block is formed, all participating computers on the network collaborate to validate the transactions contained within the block and protect the block's position within the chain.

## The Ledger: Core Component

It is the ledger that serves as the most fundamental component of the `blockchain`. In this location, information about the accounts on the network is kept safe and secure. The ledger included within the `blockchain` is what takes the place of the ledger found in a bank or other financial institution. This ledger is often comprised of account numbers, transactions, and balances in the case of a `cryptocurrency`. Every time you submit a transaction to the `blockchain`, you're adding information to the ledger regarding where the money is coming from and where it's going.

A `blockchain` ledger is a digital record that is disseminated throughout the network. Everyone on the network maintains their own copy of the ledger, which is updated whenever a new transaction is sent to the network. `Blockchain` promises to replace banks and other financial institutions through the use of a "shared ledger." Instead of having the bank maintain a single official copy of the ledger, everyone will maintain their own copy of the ledger, and we will then validate transactions by reaching an agreement on the final version.

Each `blockchain` system has its own ledger, and the various ledgers operate in a variety of ways (as we'll see in a moment). However, in order to put a transaction on the `Bitcoin` ledger, which was the first `blockchain` ledger, three pieces of information are required:

## How Transactions Work on the Bitcoin Ledger

### Required Information

1. **Transaction input**: If John wishes to transfer David a bitcoin, he must first inform the network of how and where he obtained that particular bitcoin. Because the initial section of the ledger entry indicates that John received the Bitcoin from Sarah yesterday, it is possible that John received the Bitcoin yesterday.
2. **Amount**: A dollar amount: this is the amount of money that John wishes to transfer to David.
3. **Transaction output**: A result: this is David's Bitcoin address, as well as the location where the bitcoin should be placed.
4. **Change output** (implied): The remainder returned to the sender.

## The Nature of Bitcoin

The next concept is one that is tough to grasp: there is no such thing as a `Bitcoin` in the real world. Of course, there are no actual Bitcoins to be found. That's something you were probably already aware of. However, there are no Bitcoins stored on a computer's hard disk or anywhere else. To identify a Bitcoin, you cannot point to a physical thing, digital file, or piece of code and say, "This is what it looks like." As opposed to this, the whole `Bitcoin` network is nothing more than a collection of transaction records. Every transaction in the history of Bitcoin is recorded on the `Bitcoin Blockchain`, which serves as a distributed ledger for all transactions. If you wish to demonstrate that you have 20 bitcoins, the only way to do so is to provide links to the transactions in which you obtained those 20 bitcoins.

This is a trait shared by nearly all `blockchain` technologies. The currency is represented by the transaction history. There isn't any distinction between the two. To enable better anonymity and privacy in transactions, some new cryptocurrencies are modifying the way their ledgers are maintained. When sending and receiving transactions, they use identity masking techniques to conceal who sent and who received the transaction while still maintaining the functionality of the distributed ledger.

## Block Structure

### Ledger, Header, and Footer

A block's ledger is its central component. However, it is not the only component that goes into a newly generated block. Every block must have a header and a footer, which are both essential. Additionally, the transactions included in the block are subjected to a compression, encoding, and standardization process before being included in the block. When a verifier creates a new block, the ledger on which it is based looks radically different from the ledger on which it was based. The underlying ledger, on the other hand, remains intact and can be accessed in the future if new transactions require knowledge about previously completed blocks of data.

## Adding Transactions

### Transaction Verification Process

To begin establishing a block, gather all of the existing transactions and enter them into the block's ledger as a first step. Each time a user initiates a new transaction, the transaction is broadcast to the whole network. The transaction will then be reviewed by a computer connected to a verifier to ensure that it is genuine.

As a result, because `blockchain` currencies are nothing more than a series of transactions, the first step in verifying a transaction is to look at where the sender claims they received their money from in the first place. The verifier will then go back through the history of the `blockchain` in order to locate the block and transaction in which the money was received by the sender. As long as the input transaction is confirmed on the `blockchain`, the transaction is valid, and they will just need to confirm the address of the recipient party after that point. If the input transaction has not been confirmed, the present transaction is deemed illegitimate and will not be placed in the ledger, and it will be deleted.

### Ledger Creation and Hashing

The ledger is created once all of the transactions in a block have been validated and approved. Here's a simple example in which the transactions are listed one after the other in chronological order:

A cryptographic technique known as `hashing` will be applied to each of the transactions by the verifier after that. When reduced to its most fundamental definition, `hashing` is the process of taking one string of characters and generating another string of characters. As a result, when you feed a hashing algorithm the input, amount, and output address, the algorithm will convert the transaction into a string of characters that is unique to that transaction, such as this:

```
a1075db55d416d3ca199f55b6084e2115b9345e16c5cf302fc80e9d5fbf5d48d
```

* The hash shown here is a real transaction hash from the `Bitcoin Blockchain`.

Consequently, `hashing` is used to standardize data while also ensuring that it has not been tampered with in any way. If someone attempted to modify a transaction in the `blockchain`, they would have to rehash the transaction, which would result in the transaction looking completely different. It would be clear if it had been tampered with in some way.

### Merkle Trees

Most blockchains hash transactions more than once in order to make it even more difficult to tamper with the `blockchain` and to lower the amount of memory required to keep the transaction ledger. The hash of a transaction is combined with the hash of another transaction, and the result is re-hashed into a new smaller hash, which is what they are doing. When transactions are combined in this manner, the result is known as a "`merkle tree`," and the root hash of all transactions is included at the beginning of each block of a transaction. It is beyond the scope of this book to explain why we need a Merkle Tree, but at its most basic level, the `merkle tree` confirms that all of the transactions in a block are valid while consuming less memory in the long term.

## Block Identification

### Timestamp and Block ID

A block's time stamp and block ID are the last elements to be added. This makes looking up previous blocks in the future a breeze. To minimize double spending, future transactions can refer to this block ID as the block containing the input transaction (also known as the "`coinbase`").

## Chaining Blocks Together

The final step in generating a block is connecting it to the blocks that came before it in the chain. Several approaches can be used to accomplish this, but practically all of them include hashing the content of the previous block in some way in order to make it a part of the current block.
