

# JavaScript 完整区块链代码

## Block 类

```javascript
class Block {
  constructor(index, timestamp, data, previousHash) {
    this.index = index;
    this.timestamp = timestamp;
    this.data = data;
    this.previousHash = previousHash;
    this.nonce = 0;
    this.hash = this.calculateHash();
  }

  calculateHash() {
    return sha256(this.index + this.previousHash + this.timestamp + JSON.stringify(this.data) + this.nonce).toString();
  }

  mineBlock(difficulty) {
    while (this.hash.substring(0, difficulty) !== Array(difficulty + 1).join("0")) {
      this.nonce++;
      this.hash = this.calculateHash();
    }
    console.log("Block mined: " + this.hash);
  }
}
```

## Blockchain 类（基础版）

```javascript
class Blockchain {
  constructor() {
    this.chain = [this.createGenesisBlock()];
    this.difficulty = 4;
  }

  createGenesisBlock() {
    return new Block(0, "01/01/2022", "Genesis block", "0");
  }

  getLatestBlock() {
    return this.chain[this.chain.length - 1];
  }

  addBlock(newBlock) {
    newBlock.previousHash = this.getLatestBlock().hash;
    newBlock.mineBlock(this.difficulty);
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
```

这段代码提供了一个包含 `Block` 结构、哈希、挖矿和验证的区块链基础实现。你可以将其作为起点，并添加自己的自定义功能，使区块链满足你的需求。

---

## 添加区块链名称、货币名称、总供应量、挖矿奖励

你可以将区块链名称、货币名称、总供应量和挖矿奖励作为 `Blockchain` 类的属性添加进去。以下是添加了这些属性的更新版代码：

### Block 类（未变更）

```javascript
class Block {
  constructor(index, timestamp, data, previousHash) {
    this.index = index;
    this.timestamp = timestamp;
    this.data = data;
    this.previousHash = previousHash;
    this.nonce = 0;
    this.hash = this.calculateHash();
  }

  calculateHash() {
    return sha256(this.index + this.previousHash + this.timestamp + JSON.stringify(this.data) + this.nonce).toString();
  }

  mineBlock(difficulty) {
    while (this.hash.substring(0, difficulty) !== Array(difficulty + 1).join("0")) {
      this.nonce++;
      this.hash = this.calculateHash();
    }
    console.log("Block mined: " + this.hash);
  }
}
```

### Blockchain 类（扩展版）

```javascript
class Blockchain {
  constructor(name, currency, totalSupply, miningReward) {
    this.name = name;
    this.currency = currency;
    this.totalSupply = totalSupply;
    this.miningReward = miningReward;
    this.chain = [this.createGenesisBlock()];
    this.difficulty = 4;
  }

  createGenesisBlock() {
    return new Block(0, "01/01/2022", {name: this.name, currency: this.currency, totalSupply: this.totalSupply}, "0");
  }

  getLatestBlock() {
    return this.chain[this.chain.length - 1];
  }

  addBlock(newBlock) {
    newBlock.previousHash = this.getLatestBlock().hash;
    newBlock.mineBlock(this.difficulty);
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
```

在更新后的代码中，`Blockchain` 构造函数现在接受四个参数：`name`、`currency`、`totalSupply` 和 `miningReward`。`createGenesisBlock` 方法已更新，以在数据对象中包含 `name`、`currency` 和 `totalSupply` 属性，并且 `miningReward` 属性已添加到 `Blockchain` 类中。创建新的 `Blockchain` 实例时，你可以设置这些属性，如下所示：

```javascript
const OkavangoBlockchain = new Blockchain("Okavango Blockchain", "OKA", 1000000, 50);
```

这将创建一个名为“Okavango Blockchain”、货币符号为“OKA”、总供应量为 1,000,000、挖矿奖励为 50 的新区块链。然后你可以使用 `addBlock` 方法向链中添加新区块。

