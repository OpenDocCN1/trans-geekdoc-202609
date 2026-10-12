
# Print publickey and privatekey after generating

After generating a new wallet with the `Wallet` class, you can access the public and private keys as properties of the wallet object. Here's an example of how to print the public and private keys after generating a new wallet:

```
const myWallet = new Wallet();
console.log('Public key: ' + myWallet.publicKey);
console.log('Private key: ' + myWallet.privateKey);
```

This code creates a new wallet object using the `Wallet` class and assigns it to the `myWallet` variable. Then, it logs the public and private keys to the console using `console.log()`. You can replace `myWallet` with the name of your own variable, and use the `publicKey` and `privateKey` properties to access the corresponding keys for your wallet.

# How to send and receive coins from the wallet

To send and receive coins from the wallet, you need to create and sign transactions with your private key, and then broadcast the transactions to the network for validation and inclusion in the blockchain.

Here's an example of how to create a transaction object and sign it with the wallet's private key using the elliptic library in JavaScript:

```
const EC = require('elliptic').ec;
const ec = new EC('secp256k1');

class Transaction {
  constructor(sender, recipient, amount) {
    this.sender = sender;
    this.recipient = recipient;
    this.amount = amount;
    this.timestamp = Date.now();
  }

  calculateHash() {
    return crypto.createHash('sha256').update(this.sender + this.recipient + this.amount + this.timestamp).digest('hex');
  }

  signTransaction(privateKey) {
    const key = ec.keyFromPrivate(privateKey);
    const signature = key.sign(this.calculateHash(), 'base64');
    this.signature = signature.toDER('hex');
  }

  isValid() {
    if (!this.signature || this.signature.length === 0) {
      return false;
    }
    const key = ec.keyFromPublic(this.sender, 'hex');
    return key.verify(this.calculateHash(), this.signature);
  }
}
```

Here, the `Transaction` class constructor takes three arguments: the sender, recipient, and amount of the transaction. The timestamp is automatically set to the current time using `Date.now()`. The `calculateHash` method calculates the SHA-256 hash of the transaction data, and the `signTransaction` method signs the transaction with the given `privateKey` using the `keyFromPrivate` method of the `EC` class and stores the resulting signature as a property of the transaction object. The `isValid` method checks whether the transaction is valid by verifying the signature with the `keyFromPublic` method and returning a Boolean value.

To send coins from the wallet, you can create a new transaction object with the sender, recipient, and amount fields, and then sign it with your private key using the `signTransaction` method of the transaction object. Here's an example:

```
const myWallet = new Wallet();
const recipientAddress = 'recipient public key';
const amountToSend = 10;
const transaction = new Transaction(myWallet.publicKey, recipientAddress, amountToSend);
transaction.signTransaction(myWallet.privateKey);
```

In this code, a new wallet object is created using the `Wallet` class and assigned to the `myWallet` variable. Then, a recipient address and an amount to send are specified. Next, a new transaction object is created using the `Transaction` class with the sender set to `myWallet.publicKey`, the recipient set to `recipientAddress`, and the amount set to `amountToSend`. Finally, the `signTransaction` method is called with `myWallet.privateKey` as the argument to sign the transaction.

To receive coins to the wallet, you simply need to share your public key (i.e., the wallet address) with other users, and they can send coins to that address. You can then check the balance of the address by iterating over the blockchain and summing the amounts of all transactions that have the address as the recipient.

# Full code with all above addition

Here's an example of a full JavaScript program that includes the blockchain implementation with added features such as a custom coin name, total supply, mining reward, mining interval, halving period, and wallet functionality with public and private key generation and transactions:

```
const SHA256 = require('crypto-js/sha256');
const EC = require('elliptic').ec;
const ec = new EC('secp256k1');

class Transaction {
  constructor(sender, recipient, amount) {
    this.sender = sender;
    this.recipient = recipient;
    this.amount = amount;
  }

  calculateHash() {
    return SHA256(this.sender + this.recipient + this.amount).toString();
  }

  signTransaction(signingKey) {
    if (signingKey.getPublic('hex') !== this.sender) {
      throw new Error('You cannot sign transactions for other wallets!');
    }
    const hashTx = this.calculateHash();
    const sig = signingKey.sign(hashTx, 'base64');
    this.signature = sig.toDER('hex');
  }

  isValid() {
    if (this.sender === null) return true;
    if (!this.signature || this.signature.length === 0) {
      throw new Error('No signature in this transaction');
    }
    const publicKey = ec.keyFromPublic(this.sender, 'hex');
    return publicKey.verify(this.calculateHash(), this.signature);
  }
}

class Block {
  constructor(timestamp, transactions, previousHash = '') {
    this.timestamp = timestamp;
    this.transactions = transactions;
    this.previousHash = previousHash;
    this.hash = this.calculateHash();
    this.nonce = 0;
  }

  calculateHash() {
    return SHA256(
      this.previousHash +
      this.timestamp +
      JSON.stringify(this.transactions) +
      this.nonce
    ).toString();
  }

  mineBlock(difficulty) {
    while (
      this.hash.substring(0, difficulty) !== Array(difficulty + 1).join('0')
    ) {
      this.nonce++;
      this.hash = this.calculateHash();
    }
    console.log('Block mined: ' + this.hash);
  }

  hasValidTransactions() {
    for (const tx of this.transactions) {
      if (!tx.isValid()) {
        return false;
      }
    }
    return true;
  }
}

class Blockchain {
  constructor(coinName, totalSupply, miningReward, miningInterval, halvingPeriod, halvingPercentage) {
    this.chain = [this.createGenesisBlock()];
    this.difficulty = 2;
    this.pendingTransactions = [];
    this.miningReward = miningReward;
    this.coinName = coinName;
    this.totalSupply = totalSupply;
    this.miningInterval = miningInterval;
    this.halvingPeriod = halvingPeriod;
    this.halvingPercentage = halvingPercentage;
  }

  createGenesisBlock() {
    return new Block('01/01/2021', 'Genesis block', '0');
  }

  getLatestBlock() {
    return this.chain[this.chain.length - 1];
  }

  minePendingTransactions(miningRewardAddress) {
    const rewardTx = new Transaction(
      null,
      miningRewardAddress,
      this.miningReward
    );
    this.pendingTransactions.push(rewardTx);
    let block = new Block(
      Date.now(),
      this.pendingTransactions,
      this.getLatestBlock().hash
    );
    block.mineBlock(this.difficulty);
    console.log('Block successfully mined!');
    this.chain.push(block);
    this.pendingTransactions = [];
  }

  addTransaction(transaction) {
    if (!transaction.sender || !transaction.recipient) {
      throw new Error('Transaction must include sender and recipient addresses');
    }
    Find this code in GitHub and Fork the repository.
  }
}
```
