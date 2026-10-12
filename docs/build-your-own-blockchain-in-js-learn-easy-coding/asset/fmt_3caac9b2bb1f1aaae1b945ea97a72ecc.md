
# Build Your Own Blockchain In JS

**Author:** Sankar Srinivasan  
**Published:** May 4, 2023  
**ISBN:** 979-8223444169  
**Contact:** https://withkoji.com/@sankarsrinivasan | petra.srini@gmail.com | WhatsApp: +919042404390

> For education purpose

## Copyright

While every precaution has been taken in the preparation of this book, the publisher assumes no responsibility for errors or omissions, or for damages resulting from the use of the information contained herein.

**BUILD YOUR OWN BLOCKCHAIN IN JS**  
Copyright © 2023 Sankar Srinivasan. All rights reserved. This ebook is licensed for your personal reading only. This e-book may not be re-sold or given away to other people. If you would like to share this ebook with another person, please purchase an additional copy for each recipient. Thank you for respecting the hard work of this author. Our Print Books and E-Books are available at all leading International online book stores & E-Book stores.

Search Terms: “Sankar Srinivasan gann theory” in Google search engine.

## Table of Contents

1.  Build your own Blockchain in JS
2.  Define the Block Structure
3.  Implement Hashing
4.  Create the Blockchain
5.  Add New Blocks
6.  Implement Mining
7.  Implement Validation
8.  Summary
9.  Full Blockchain Code in JavaScript
10. Add block chain name, currency name, total supply, mining reward in above code
11. Add mining interval, halving period and halving percentage
12. Hashing Algorithm
13. Create Wallet for above new coin
14. Auto generate publickey and privatekey
15. Print publickey and privatekey after generating
16. How to send and receive coins from the wallet
17. Full code with all above addition
18. Compile the code in VPS
19. How to install nodes
20. How to create explorer for above new coin
21. What is API for above new coin
22. how to do mining for above coin
23. how to define /mine api endpoint
24. How to call /mine API endpoint as a miner

---

## Build your own Blockchain in JS

For basic understanding of Blockchain, read my eBook available at various online stores. Click **Build your own Blockchain in JavaScript**.

Building a blockchain is a complex undertaking, so it's important to have a good understanding of the underlying principles and concepts. Here are some general steps you can follow to create a basic blockchain:

### Define block structure

Each block in the blockchain should contain a set of transactions and metadata such as timestamps and unique identifiers (hashes). These properties allow you to define your block class.

### Hashing implementation

To ensure blockchain integrity, each block's hash must be based on the block's contents, so any changes to the block will invalidate that hash. A cryptographic hash function such as `SHA-256` can be used to generate the hash of each block.

### Create the Blockchain

You can create a blockchain as an array of block objects. The first block in the chain, called the genesis block, can be hard-coded as a starting point.

### Append New Blocks

To add a new transaction to the blockchain, create a new block object and append it to the end of the blockchain. The hash of a new block should be based on the contents of previous blocks in the chain to ensure the integrity of the blockchain.

### Implement Mining

To prevent spam transactions and ensure network security, you can implement proof-of-work algorithms that require miners to solve complex mathematical puzzles to add new blocks to the chain. This can be done by setting a difficulty level that miners must meet before their block is accepted.

### Implement Validation

To ensure the validity of the blockchain, you can implement a validation function that checks the integrity of each block's hash and the continuity of the chain.

### Sample Code

Here is some sample code to get you started:

```javascript
const SHA256 = require('crypto-js/sha256');

class Block {
  constructor(timestamp, transactions, previousHash = '') {
    this.timestamp = timestamp;
    this.transactions = transactions;
    this.previousHash = previousHash;
    this.hash = this.calculateHash();
  }

  calculateHash() {
    return SHA256(this.previousHash + this.timestamp + JSON.stringify(this.transactions)).toString();
  }
}

class Blockchain {
  constructor() {
    this.chain = [this.createGenesisBlock()];
    this.difficulty = 2;
  }

  createGenesisBlock() {
    return new Block('01/01/2022', 'Genesis block', '0');
  }

  getLatestBlock() {
    return this.chain[this.chain.length - 1];
  }

  addBlock(newBlock) {
    newBlock.previousHash = this.getLatestBlock().hash;
    newBlock.hash = newBlock.calculateHash();
    this.chain.push(newBlock);
  }

  isChainValid() {
    for (let i = 1; i < this.chain.length; i++) {
      const currentBlock = this.chain[i];
      const previousBlock = this.chain[i - 1];

      if (currentBlock.hash !== currentBlock.calculateHash()) {
        return false;
      }
      if (currentBlock.previousHash !== previousBlock.hash) {
        return false;
      }
    }
    return true;
  }
}

let myCoin = new Blockchain();
myCoin.addBlock(new Block('01/02/2024', { amount: 4 }));
myCoin.addBlock(new Block('01/03/2024', { amount: 8 }));
console.log(JSON.stringify(myCoin, null, 4));
console.log('Blockchain valid? ' + myCoin.isChainValid());
```

This is just a basic implementation of a blockchain in JavaScript. There are many more advanced concepts that can be added, such as a consensus algorithm, peer-to-peer networking, and smart contracts, depending on your specific requirements.
