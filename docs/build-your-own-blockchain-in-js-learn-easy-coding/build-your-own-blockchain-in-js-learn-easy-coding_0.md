# 区块链构建指南：轻松学习 JS 编码












---

## 用 JavaScript 构建你自己的区块链

要基本了解区块链，请阅读我的电子书，可在各大在线商店购买。点击 **用 JavaScript 构建你自己的区块链**。

构建区块链是一项复杂的工程，因此深入理解其底层原理和概念至关重要。以下是创建基础区块链的一些通用步骤：

## 定义区块结构

区块链中的每个区块都应包含一组交易以及元数据，例如时间戳和唯一标识符（哈希值）。这些属性使你能够定义你的区块类。

### 哈希实现

为确保区块链的完整性，每个区块的哈希值必须基于该区块的内容，因此对区块的任何更改都会使该哈希值失效。可以使用加密哈希函数（如 `SHA-256`）来生成每个区块的哈希值。

## 创建区块链

你可以将区块链创建为区块对象的数组。链中的第一个区块称为创世区块，可以将其硬编码作为起点。

### 追加新区块

要向区块链添加新交易，请创建一个新的区块对象并将其追加到区块链的末尾。新区块的哈希值应基于链中前序区块的内容，以确保区块链的完整性。

## 实现挖矿

为防止垃圾交易并确保网络安全，你可以实现工作量证明算法，要求矿工解决复杂的数学难题以将新区块添加到链中。这可以通过设置难度级别来实现，矿工必须满足该级别，其区块才会被接受。

## 实现验证

为确保区块链的有效性，你可以实现一个验证函数，用于检查每个区块哈希值的完整性以及链的连续性。

## 示例代码

以下是一些入门示例代码：

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

这只是 JavaScript 中区块链的基本实现。根据你的具体需求，还可以添加许多更高级的概念，例如共识算法、点对点网络和智能合约。





## 定义区块结构

区块结构是区块链中的基本数据单元。它包含一组交易和元数据，如时间戳和称为哈希的唯一标识符。以下是区块组件的更详细细分：

- **索引**：区块链中的每个区块都有一个唯一的索引或编号，用于跟踪其在链中的位置。
- **时间戳**：时间戳表示区块创建的日期和时间。
- **数据**：数据字段包含自上一个区块创建以来记录的交易序列。这些交易可以代表从金融交易到智能合约数据的任何内容。
- **哈希**：哈希是通过将加密哈希函数应用于区块内容而创建的唯一数字指纹。哈希值对于每个区块都是唯一的，用于标识区块并确保其完整性。
- **前一个哈希**：前一个哈希字段包含区块链中前一个区块的哈希值。这用于将每个区块链接在一起，确保区块链的连续性和完整性。

以下是区块结构在 JavaScript 中可能的样子示例：

```javascript
class Block {
  constructor(index, timestamp, data, previousHash) {
    this.index = index;
    this.timestamp = timestamp;
    this.data = data;
    this.previousHash = previousHash;
    this.hash = this.calculateHash();
  }

  calculateHash() {
    return SHA256(this.index + this.timestamp + JSON.stringify(this.data) + this.previousHash).toString();
  }
}
```

在此示例中，我们定义了一个具有以下属性的 `Block` 类：

- **索引**：一个数字，表示区块在链中的位置。
- **时间戳**：一个时间戳，表示区块创建的时间。
- **数据**：包含在区块中的交易数组。
- **前一个哈希**：链中前一个区块的哈希值。
- **哈希**：当前区块的哈希值，使用加密哈希函数 (`SHA256`) 计算得出。

## 实现哈希

在区块链中，哈希用于为每个区块创建唯一的数字指纹或哈希值。然后使用此哈希将区块链接在一起，确保其完整性和不可篡改性。

哈希是一个将任意大小的数据转换为称为哈希的固定大小输出的过程。在 JavaScript 中，SHA-256 算法常用于哈希。以下是在 JavaScript 中使用 SHA-256 算法实现哈希的示例：

```javascript
const SHA256 = require('crypto-js/sha256');

class Block {
  constructor(data, previousHash) {
    this.timestamp = new Date();
    this.data = data;
    this.previousHash = previousHash;
    this.hash = this.calculateHash();
  }

  calculateHash() {
    return SHA256(this.timestamp + this.previousHash + JSON.stringify(this.data)).toString();
  }
}
```

在此示例中，我们创建了一个 `Block` 类，它接受一些数据和链中前一个区块的哈希值作为参数。

`calculateHash()` 方法随后使用 `crypto-js` 库中的 `SHA256` 算法为区块生成唯一的哈希值。`SHA256` 函数的输入是区块的时间戳、前一个哈希和当前数据的连接字符串。

重要的是要注意，SHA-256 算法是单向函数，这意味着从数据生成哈希很容易，但从哈希生成原始数据是不可能的。这一特性使得哈希对于创建安全且防篡改的区块链非常有用。

## 创建区块链

创建区块链涉及创建一个区块的链表，其中每个区块包含一组交易和一个将其链接到链中前一个区块的哈希值。以下是在 JavaScript 中创建基本区块链的示例：

```javascript
const SHA256 = require('crypto-js/sha256');

class Block {
  constructor(timestamp, data, previousHash = '') {
    this.timestamp = timestamp;
    this.data = data;
    this.previousHash = previousHash;
    this.hash = this.calculateHash();
    this.nonce = 0;
  }

  calculateHash() {
    return SHA256(this.previousHash + this.timestamp + JSON.stringify(this.data) + this.nonce).toString();
  }

  mineBlock(difficulty) {
    while (this.hash.substring(0, difficulty) !== Array(difficulty + 1).join('0')) {
      this.nonce++;
      this.hash = this.calculateHash();
    }
    console.log('Block mined: ' + this.hash);
  }
}

class Blockchain {
  constructor() {
    this.chain = [this.createGenesisBlock()];
    this.difficulty = 4;
  }

  createGenesisBlock() {
    return new Block(Date.now(), 'Genesis Block', '0');
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

let myBlockchain = new Blockchain();
console.log('Mining Block 1...');
myBlockchain.addBlock(new Block(Date.now(), { amount: 50 }));
console.log('Mining Block 2...');
myBlockchain.addBlock(new Block(Date.now(), { amount: 100 }));
```

在此示例中，我们定义了一个代表区块链中每个区块的 `Block` 类。每个区块都有一个时间戳、一组数据、链中前一个区块的哈希值、其自身内容的哈希值和一个 nonce 值。

我们还定义了一个包含区块链的 `Blockchain` 类，从创世区块开始。`Blockchain` 类包含向链中添加新区块、获取链中最新区块以及检查链有效性的方法。

要向链中添加新区块，我们调用 `Blockchain` 类的 `addBlock` 方法，传入一个包含当前时间戳和我们想要存储在区块中的数据的 `Block` 类的新实例。然后调用 `Block` 类的 `mineBlock` 方法来计算区块的哈希值，通过增加 nonce 直到哈希值满足指定的难度级别。

最后，我们实例化了一个新的 `Blockchain` 对象并向链中添加了两个区块，每个区块都包含一些数据。当我们运行脚本时，可以看到显示每个区块挖掘过程的控制台输出。




## 添加新区块

向区块链添加新区块涉及创建一个包含数据的 `Block` 类新实例，然后调用 `Blockchain` 类的 `addBlock` 方法将其添加到链中。示例如下：

```javascript
// create a new instance of Blockchain
let myBlockchain = new Blockchain();
// add a new Block to the chain
let newBlock = new Block(Date.now(), { amount: 50 });
myBlockchain.addBlock(newBlock);
// add another Block to the chain
let anotherBlock = new Block(Date.now(), { amount: 100 });
myBlockchain.addBlock(anotherBlock);
```

在该示例中，我们首先创建一个名为 `myBlockchain` 的 `Blockchain` 类实例。然后，我们使用当前时间戳和一些数据创建一个 `Block` 类的新实例，并将其赋值给 `newBlock` 变量。

接着，我们调用 `myBlockchain` 对象的 `addBlock` 方法，将 `newBlock` 对象作为参数传入。这会将 `newBlock` 添加到链中。

随后，我们创建另一个名为 `anotherBlock` 的 `Block` 类实例，并再次调用 `myBlockchain` 对象的 `addBlock` 方法将其添加到链中。

值得注意的是，向链中添加新区块时，必须确保链中前一个区块的哈希值包含在新区块的数据中。这确保了区块按正确顺序链接在一起，且链无法被篡改。

在上述示例代码中，`Blockchain` 类的 `addBlock` 方法会自动处理此过程，将前一个区块的哈希值赋给新区块的 `previousHash` 属性。

## 实现挖矿

挖矿是通过解决复杂的加密难题将新区块添加到区块链的过程。为在区块链中实现挖矿，我们需要引入**工作量证明**的概念。

工作量证明是一种协议，要求在新区块添加到区块链之前付出一定的计算工作量。这是通过向区块数据添加一个称为“nonce”的随机字符串并对结果进行哈希来完成的。矿工不断更改 nonce，直到区块的哈希值满足特定条件（例如具有特定数量的前导零）。

以下是区块链中实现挖矿的示例：

```javascript
class Blockchain {
  constructor() {
    this.chain = [this.createGenesisBlock()];
    this.difficulty = 4; // number of leading zeros required in the Block's hash
  }
  createGenesisBlock() {
    return new Block(0, "01/01/2024", "Genesis Block", "0");
  }
  getLatestBlock() {
    return this.chain[this.chain.length - 1];
  }
  addBlock(newBlock) {
    newBlock.previousHash = this.getLatestBlock().hash;
    newBlock.mineBlock(this.difficulty);
    this.chain.push(newBlock);
  }
}

class Block {
  constructor(index, timestamp, data, previousHash = "") {
    this.index = index;
    this.timestamp = timestamp;
    this.data = data;
    this.previousHash = previousHash;
    this.hash = this.calculateHash();
    this.nonce = 0;
  }
  calculateHash() {
    return sha256(
      this.index +
      this.previousHash +
      this.timestamp +
      JSON.stringify(this.data) +
      this.nonce
    ).toString();
  }
  mineBlock(difficulty) {
    while (
      this.hash.substring(0, difficulty) !== Array(difficulty + 1).join("0")
    ) {
      this.nonce++;
      this.hash = this.calculateHash();
    }
    console.log("Block mined: " + this.hash);
  }
}
```

在该示例中，我们向 `Blockchain` 类添加了 `difficulty` 属性，用于指定区块哈希值所需的前导零数量。我们还向 `Block` 类添加了接受 `difficulty` 参数的 `mineBlock` 方法。

在 `mineBlock` 方法内部，我们使用 `while` 循环不断增加 nonce 并重新计算哈希，直到区块的哈希值满足难度要求。我们通过将哈希值的前 `difficulty` 个字符与由 `difficulty` 个零组成的字符串进行比较来实现这一点。一旦找到满足此要求的哈希值，我们会向控制台记录一条消息并返回该哈希值。

向链中添加新区块时，我们使用 `Blockchain` 类中指定的难度调用新区块的 `mineBlock` 方法。这确保了仅在完成一定量的计算工作后才将区块添加到链中。

值得注意的是，增加难度级别会使挖矿更难并需要更多计算能力，但也会使区块链更安全。不过，这也会增加挖掘新区块所需的时间。

> `01/01/2024` 可替换为唯一字符串。

## 实现验证

为确保区块链的完整性，我们需要实现一个验证机制，检查链是否有效且未被篡改。这对于防止对区块链中存储的数据进行未经授权的更改非常重要。

以下是区块链中实现验证的示例：

```javascript
class Blockchain {
  // constructor and other methods omitted for brevity
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

在该示例中，我们向 `Blockchain` 类添加了 `isChainValid` 方法来检查链是否有效。该方法遍历链中的每个区块，从第二个区块开始（因为第一个区块是创世区块，没有前一个区块可供验证）。

对于每个区块，我们首先检查区块的 `hash` 属性是否与使用 `calculateHash` 方法计算的哈希值匹配。如果哈希值不匹配，说明区块中的数据已被篡改，我们返回 `false`。

接着，我们检查当前区块的 `previousHash` 属性是否与前一个区块的 `hash` 属性匹配。如果前一个区块的哈希值与当前区块的 `previousHash` 不匹配，说明前一个区块已被篡改，我们返回 `false`。

如果所有区块都通过这些检查，说明链有效且未被篡改。我们返回 `true` 以表明链有效。

值得注意的是，此验证机制仅检查区块链的完整性，不检查区块链中存储的数据是否正确或准确。确保存储和检索的数据正确准确是使用区块链的应用程序的责任。

# 总结

使用 JavaScript 创建区块链可以是一个有趣且富有教育意义的项目，有助于理解区块链技术的核心概念。通过实现区块结构、哈希、挖矿和验证等基本构建模块，可以创建一个简单的区块链，演示去中心化、不可变数据存储的威力。

但必须注意，此实现非常简单，缺乏真实区块链中使用的许多高级功能和安全措施。例如，真实区块链拥有更复杂的共识算法，以确保网络中所有节点就链的状态达成一致，并提供安全性以防止攻击。

若想深入了解区块链技术，网上有许多资源可帮助你更好地理解这一令人兴奋的领域。从学术论文到在线课程和教程，有许多途径可探索区块链的内部运作，并发现利用该技术解决现实问题的新方法。




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




## 添加挖矿间隔、减半周期和减半百分比

要向区块链添加挖矿减半周期和减半百分比，可以按如下方式修改 `Blockchain` 类和 `mineBlock` 方法：

```javascript
class Blockchain {
  constructor(name, currency, totalSupply, miningReward, miningInterval, halvingPeriod, halvingPercentage) {
    this.name = name;
    this.currency = currency;
    this.totalSupply = totalSupply;
    this.miningReward = miningReward;
    this.chain = [this.createGenesisBlock()];
    this.difficulty = 4;
    this.miningInterval = miningInterval; // 单位：秒
    this.halvingPeriod = halvingPeriod; // 单位：区块
    this.halvingPercentage = halvingPercentage; // 以小数表示（例如：0.5 代表 50%）
  }

  createGenesisBlock() {
    return new Block(0, "01/01/2024", {name: this.name, currency: this.currency, totalSupply: this.totalSupply}, "0");
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

  mineBlock(minerAddress) {
    const latestBlock = this.getLatestBlock();
    const now = new Date().getTime() / 1000;
    // 检查挖矿间隔是否已过
    if ((now - latestBlock.timestamp) < this.miningInterval) {
      console.log(`挖矿间隔尚未经过。请等待 ${(this.miningInterval - (now - latestBlock.timestamp)).toFixed(2)} 秒后再挖掘下一个区块。`);
      return;
    }
    const newBlock = new Block(
      latestBlock.index + 1,
      now,
      [],
      latestBlock.hash
    );
    // 计算挖矿奖励
    const currentReward = this.miningReward * (1 - Math.floor((latestBlock.index + 1) / this.halvingPeriod) * this.halvingPercentage);
    // 将挖矿奖励添加到矿工地址
    console.log(`正在挖掘区块 ${newBlock.index}...`);
    console.log(`挖矿奖励：${currentReward} ${this.currency}`);
    console.log(`正在向矿工地址 ${minerAddress} 添加 ${currentReward} ${this.currency}...`);
    // 在此处，您需要在您的区块链实现中将挖矿奖励添加到指定的矿工地址。
    newBlock.data.push(`挖矿奖励：${currentReward} ${this.currency}`);
    this.addBlock(newBlock);
  }
}
```

在更新后的 `Blockchain` 类中，构造函数接受三个额外参数：`miningInterval`、`halvingPeriod` 和 `halvingPercentage`。`mineBlock` 方法已修改为在允许挖掘下一个区块前检查挖矿间隔是否已过。然后，它根据构造函数中指定的当前区块索引、减半周期和减半百分比计算当前的挖矿奖励。挖矿奖励会添加到指定的矿工地址（您需要在您的区块链实现中实现此功能），同时挖矿奖励也会添加到新区块的数据中。

请注意，在 `mineBlock` 方法中，挖矿奖励被添加到控制台输出和新区块的数据中。在您的实现中，您需要修改此部分，以将挖矿奖励添加到您区块链网络中矿工的地址里。

## 哈希算法

在上述区块链实现中，使用的哈希算法是 SHA-256（安全哈希算法 256 位）。这是许多区块链网络（包括比特币）常用的哈希算法。

在 `Block` 类中，`calculateHash` 方法使用 SHA-256 算法创建区块内容的哈希值。以下代码片段展示了 JavaScript 中 SHA-256 哈希的实现：

```javascript
const SHA256 = require("crypto-js/sha256");

class Block {
  constructor(index, timestamp, data, previousHash = "") {
    this.index = index;
    this.timestamp = timestamp;
    this.data = data;
    this.previousHash = previousHash;
    this.hash = this.calculateHash();
    this.nonce = 0;
  }

  calculateHash() {
    return SHA256(
      this.index +
      this.previousHash +
      this.timestamp +
      JSON.stringify(this.data) +
      this.nonce
    ).toString();
  }

  mineBlock(difficulty) {
    while (
      this.hash.substring(0, difficulty) !== Array(difficulty + 1).join("0")
    ) {
      this.nonce++;
      this.hash = this.calculateHash();
    }
  }
}
```

此处，`SHA256` 从 `crypto-js` 库导入，并用于在 `calculateHash` 方法中计算区块内容的哈希值。

## 为上述新币种创建钱包

要为新币种创建钱包，您需要生成一个由公钥和私钥组成的密钥对。公钥是其他用户发送币种的地址，私钥用于签署交易并证明对与该地址关联的币种的所有权。以下是使用 JavaScript 中的 `elliptic` 库创建密钥对的示例：

```javascript
const EC = require('elliptic').ec;
const ec = new EC('secp256k1');

class Wallet {
  constructor() {
    this.keyPair = ec.genKeyPair();
    this.publicKey = this.keyPair.getPublic('hex');
    this.privateKey = this.keyPair.getPrivate('hex');
  }
}
```

此处，使用 `secp256k1` 曲线创建 `EC` 类的实例，该曲线与比特币使用的曲线相同。然后，在 `Wallet` 类构造函数中，使用 `genKeyPair` 方法生成新的密钥对，并提取公钥和私钥，将它们作为钱包对象的属性存储。

使用此代码，您可以通过调用 `new Wallet()` 创建一个新的钱包对象，这将生成一个新的密钥对，并返回包含公钥和私钥属性的相应钱包对象。然后，您可以使用公钥接收币种，使用私钥签署交易并花费币种。

## 自动生成公钥和私钥

要为每个钱包自动生成公钥和私钥，可以修改 `Wallet` 构造函数，使其在未提供密钥作为参数时生成新的密钥对，如下所示：

```javascript
const EC = require('elliptic').ec;
const ec = new EC('secp256k1');

class Wallet {
  constructor(publicKey = null, privateKey = null) {
    if (!publicKey || !privateKey) {
      const keyPair = ec.genKeyPair();
      this.publicKey = keyPair.getPublic('hex');
      this.privateKey = keyPair.getPrivate('hex');
    } else {
      this.publicKey = publicKey;
      this.privateKey = privateKey;
    }
  }
}
```

此处，`publicKey` 和 `privateKey` 参数是可选的，如果未提供，则使用 `EC` 类的 `genKeyPair` 方法生成新的密钥对。否则，如果提供了密钥，则将它们用作钱包的公钥和私钥。

通过此修改，您可以在不提供任何密钥的情况下创建新的钱包对象，如下所示：`new Wallet()`。这将生成一个新的密钥对，并返回包含公钥和私钥属性的相应钱包对象。或者，您可以使用特定密钥创建钱包对象，如下所示：`new Wallet('public key', 'private key')`。




## 生成后打印公钥和私钥

使用 `Wallet` 类生成新钱包后，您可以作为钱包对象的属性访问公钥和私钥。以下是生成新钱包后打印公钥和私钥的示例：

```
const myWallet = new Wallet();
console.log('Public key: ' + myWallet.publicKey);
console.log('Private key: ' + myWallet.privateKey);
```

此代码使用 `Wallet` 类创建一个新的钱包对象并将其赋值给 `myWallet` 变量。然后，它使用 `console.log()` 将公钥和私钥记录到控制台。您可以将 `myWallet` 替换为您自己的变量名，并使用 `publicKey` 和 `privateKey` 属性来访问您钱包对应的密钥。

## 如何从钱包发送和接收币

要从钱包发送和接收币，您需要使用私钥创建并签名交易，然后将交易广播到网络以进行验证并打包入区块链。

以下是如何创建交易对象并使用 JavaScript 中的 elliptic 库通过钱包私钥对其进行签名的示例：

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

在这里，`Transaction` 类构造函数接受三个参数：交易的发送方、接收方和金额。时间戳使用 `Date.now()` 自动设置为当前时间。`calculateHash` 方法计算交易数据的 SHA-256 哈希值，`signTransaction` 方法使用 `EC` 类的 `keyFromPrivate` 方法通过给定的 `privateKey` 对交易进行签名，并将生成的签名作为交易对象的属性存储。`isValid` 方法通过使用 `keyFromPublic` 方法验证签名并返回布尔值来检查交易是否有效。

要从钱包发送币，您可以使用发送方、接收方和金额字段创建一个新的交易对象，然后使用交易对象的 `signTransaction` 方法通过您的私钥对其进行签名。示例如下：

```
const myWallet = new Wallet();
const recipientAddress = 'recipient public key';
const amountToSend = 10;
const transaction = new Transaction(myWallet.publicKey, recipientAddress, amountToSend);
transaction.signTransaction(myWallet.privateKey);
```

在该代码中，使用 `Wallet` 类创建一个新的钱包对象并将其赋值给 `myWallet` 变量。然后，指定接收地址和发送金额。接下来，使用 `Transaction` 类创建一个新的交易对象，发送方设为 `myWallet.publicKey`，接收方设为 `recipientAddress`，金额设为 `amountToSend`。最后，调用 `signTransaction` 方法并传入 `myWallet.privateKey` 作为参数来对交易进行签名。

要接收币到钱包，您只需将您的公钥（即钱包地址）分享给其他用户，他们即可向该地址发送币。您可以通过遍历区块链并累加所有以该地址为接收方的交易金额来查询该地址的余额。

## 包含上述所有添加功能的完整代码

以下是一个完整的 JavaScript 程序示例，包含区块链实现及新增功能，如自定义币种名称、总供应量、挖矿奖励、挖矿间隔、减半周期，以及带有公私钥生成和交易功能的钱包功能：

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





## 在 VPS 上编译代码

要在 VPS（虚拟专用服务器）上运行此代码，请遵循以下步骤：

### 安装 Node.js

根据您的特定操作系统，按照安装说明在 VPS 上安装 `Node.js`。

### 安装所需包

安装完 `Node.js` 后，导航至项目目录并运行以下命令以安装所需包：

```
npm install
```

### 启动服务器

安装完所需包后，运行以下命令启动服务器：

```
node index.js
```

这将默认在端口 `3000` 上启动服务器。如果您想使用其他端口，可以通过修改 `index.js` 文件中 `port` 变量的值来指定。

### 访问区块链

服务器运行后，您可以在 Web 浏览器中访问 `http://your_vps_ip_address:3000` 来访问区块链。您应该能看到区块链信息以及挖矿和交易表单。

> **注意：** 请确保在 VPS 的防火墙中开放了端口 `3000`，以便从互联网访问区块链。

---

## 如何安装 Node.js

在 VPS 上安装 `Node.js` 的步骤取决于您使用的操作系统。以下是一些流行操作系统的通用步骤：

### Ubuntu/Debian

更新软件包索引并安装 `Node.js` 的依赖项：

```
sudo apt-get update
sudo apt-get install curl git-core build-essential openssl libssl-dev
```

使用包管理器安装 `Node.js`：

```
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### CentOS/RHEL

安装 EPEL 仓库和 `Node.js` 的依赖项：

```
sudo yum install epel-release
sudo yum install curl git-core openssl-devel
```

使用包管理器安装 `Node.js`：

```
curl -sL https://rpm.nodesource.com/setup_14.x | sudo bash -
sudo yum install -y nodejs
```

### Windows

从官方网站下载 `Node.js` 安装程序。运行安装程序并按照安装向导操作。

安装完 `Node.js` 后，可以通过在终端运行以下命令来验证安装：

```
node -v
```

如果安装正确，这应该会输出 `Node.js` 的版本号。

安装完 `Node.js` 后，您可以继续为区块链项目安装所需包。

使用终端导航至项目目录：

```
cd /path/to/your/project
```

通过运行以下命令初始化项目：

```
npm init -y
```

通过运行以下命令安装所需包：

```
npm install express body-parser crypto-js ejs nodemon --save
```

这将安装以下包：

- `express`：用于构建 Web 应用程序的 Node.js Web 框架。
- `body-parser`：用于以可读格式解析请求体的中间件。
- `crypto-js`：用于实现加密算法的库。
- `ejs`：用于通过 JavaScript 生成 HTML 标记的模板引擎。
- `nodemon`：当代码发生更改时自动重启服务器的工具。

包安装完成后，可以使用以下命令启动服务器：

```
nodemon index.js
```

---

## 如何为上述新币创建浏览器

要为您的区块链创建浏览器，可以遵循以下通用步骤：

为浏览器创建一个新目录并导航至其中：

```
mkdir blockchain-explorer
cd blockchain-explorer
```

使用 `npm` 初始化项目：

```
npm init -y
```

安装以下依赖项：

```
npm install express body-parser ejs request-promise --save
```

以下是每个包的简要说明：

- `express`：用于构建 Web 应用程序的 Node.js Web 框架。
- `body-parser`：用于以可读格式解析请求体的中间件。
- `ejs`：用于通过 JavaScript 生成 HTML 标记的模板引擎。
- `request-promise`：用于基于 Promise 发起 HTTP 请求的库。

创建服务器的 `index.js` 文件并添加以下代码：

```javascript
const express = require('express');
const bodyParser = require('body-parser');
const ejs = require('ejs');
const rp = require('request-promise');
const app = express();

app.set('view engine', 'ejs');
app.use(bodyParser.urlencoded({ extended: true }));

// 定义您的路由
app.listen(3000, () => console.log('Blockchain explorer running on port 3000'));
```

为浏览器定义路由。以下是一些示例：

```javascript
// 显示区块链的路由
app.get('/blockchain', async (req, res) => {
  const blockchain = await rp('http://localhost:3001/blockchain');
  res.render('blockchain', { blockchain: JSON.parse(blockchain) });
});

// 显示特定区块的路由
app.get('/block/:blockHash', async (req, res) => {
  const block = await rp(`http://localhost:3001/block/${req.params.blockHash}`);
  res.render('block', { block: JSON.parse(block) });
});

// 显示特定交易的路由
app.get('/transaction/:transactionId', async (req, res) => {
  const transaction = await rp(`http://localhost:3001/transaction/${req.params.transactionId}`);
  res.render('transaction', { transaction: JSON.parse(transaction) });
});
```

在 `views` 目录中为路由创建相应的视图。以下是区块链路由的示例：

```html
<!DOCTYPE html>
<html>
<head>
  <title>Blockchain Explorer</title>
</head>
<body>
  <h1>Blockchain Explorer</h1>
  <h2>Blockchain</h2>
  <% blockchain.forEach((block) => { %>
    <ul>
      <li><a href="/block/<%= block.hash %>">Block <%= block.index %></a></li>
    </ul>
  <% }); %>
</body>
</html>
```

使用 `node index.js` 启动服务器，如果已安装 `nodemon`，也可使用 `nodemon index.js`。

这是为您的区块链创建浏览器的基本示例。您可以根据需要进行自定义并添加更多功能。

---

## 上述新币的 API 是什么

**API**（应用程序编程接口）是一组用于构建与区块链网络交互的软件和应用程序的规则、协议和工具。对于一种新币，您需要为各种操作定义并实现 API 端点，例如创建新钱包、发送和接收币、获取钱包余额以及检索交易详情。

API 可以使用任何支持 HTTP 请求和响应的编程语言或框架构建，例如 `Node.js` 或 `Django`。API 端点可以通过 Web 服务器或云平台（如 `AWS` 或 `Google Cloud`）暴露。

一些流行的区块链 API 包括 `Ethereum` 的 `JSON-RPC API` 和 `Bitcoin` 的 `RESTful API`。然而，对于一种新币，您需要根据币的特性和功能定义并实现自己的 API 端点。




## 如何为上述币种进行挖矿

要挖掘一种新币种，你需要执行一系列计算密集型的数学计算，以便在区块链网络中生成新区块。使用我们之前讨论的示例代码来挖掘新币种的步骤如下：

1.  使用命令 `node index.js` 在你的系统或 VPS 上运行节点应用程序。
2.  使用 `/wallet/new` API 端点创建一个新钱包，并将公钥和私钥存储在安全的位置。
3.  使用 `/mine` API 端点开始挖矿。这将在区块链中生成一个新区块并将其添加到现有链中。挖矿过程涉及反复计算区块的哈希值，直到该哈希值满足所需的难度级别。
4.  一旦挖矿过程完成，新生成的区块将被添加到区块链中，挖矿奖励将发送到矿工的钱包地址。

在我们之前讨论的示例代码中，可以通过调用 `/mine` API 端点来启动挖矿。该端点将执行生成新区块并将其添加到区块链所需的计算。挖矿过程涉及反复计算区块的哈希值，直到该哈希值满足所需的难度级别。

请记住，挖矿可能是一个资源密集型过程，并且随着更多矿工加入网络，难度级别可能会随时间增加。

## 如何定义 `/mine` API 端点

要为你的新币种定义 `/mine` API 端点，你需要修改我们之前讨论的代码，以包含一个启动挖矿过程的新 API 路由。以下是定义 `/mine` API 端点的步骤：

### 在 `index.js` 文件中，添加一个新的 API 路由以启动挖矿：

```javascript
// 启动挖矿的 API 端点
app.get('/mine', (req, res) => {
    const lastBlock = blockchain.getLastBlock();
    const previousBlockHash = lastBlock.hash;
    const currentBlockData = {
        transactions: pendingTransactions,
        index: lastBlock.index + 1
    };
    const nonce = blockchain.proofOfWork(previousBlockHash, currentBlockData);
    const blockHash = blockchain.hashBlock(previousBlockHash, currentBlockData, nonce);
    const newBlock = blockchain.createNewBlock(nonce, previousBlockHash, blockHash);
    // 向矿工地址发送挖矿奖励
    blockchain.createNewTransaction(0, miningReward, nodeAddress);
    res.json({
        message: "New block mined successfully",
        block: newBlock
    });
});
```

此路由通过执行必要的计算来计算满足所需难度级别的区块哈希值，从而生成一个新区块。它还会创建一笔新交易，将挖矿奖励发送到矿工的钱包地址。

### 在 `Block.js` 文件中，添加执行必要计算以计算满足所需难度级别的区块哈希值的 `proofOfWork` 函数：

```javascript
Block.prototype.proofOfWork = function(previousBlockHash, currentBlockData) {
    let nonce = 0;
    let hash = this.hashBlock(previousBlockHash, currentBlockData, nonce);
    while (hash.substring(0, difficulty) !== Array(difficulty + 1).join("0")) {
        nonce++;
        hash = this.hashBlock(previousBlockHash, currentBlockData, nonce);
    }
    return nonce;
};
```

此函数执行工作量证明算法，以计算满足所需难度级别的区块哈希值。它使用不同的 nonce 反复计算区块的哈希值，直到该哈希值满足所需的难度级别。

### 在 `Block.js` 文件中，添加计算区块哈希值的 `hashBlock` 函数：

```javascript
Block.prototype.hashBlock = function(previousBlockHash, currentBlockData, nonce) {
    const dataAsString = previousBlockHash + nonce.toString() + JSON.stringify(currentBlockData);
    const hash = sha256(dataAsString);
    return hash;
};
```

此函数通过将上一个区块的哈希值、nonce 和当前区块的数据连接成一个字符串，然后对该字符串应用 SHA-256 哈希算法来计算区块的哈希值。

进行这些更改后，你可以使用命令 `node index.js` 运行节点应用程序，`/mine` API 端点将可用于启动挖矿过程。

## 如何作为矿工调用 `/mine` API 端点

要作为矿工调用 `/mine` API 端点，你可以使用你编程语言中可用的任何 HTTP 客户端库。以下是使用 Python 中的 `requests` 库调用 `/mine` API 端点的示例：

```python
import requests

## 定义 API 端点 URL
api_url = "http://localhost:5000/mine"

## 定义挖矿参数
params = {
    "miner_address": "your_miner_address_here",
    "difficulty": 4
}

## 发送 POST 请求到带有挖矿参数的 API 端点
response = requests.post(api_url, json=params)

## 检查请求是否成功
if response.status_code == 200:
    print("Block mined successfully!")
    print("Block hash:", response.json()["block_hash"])
else:
    print("Error:", response.text)
```

在此示例中，我们首先定义 API 端点 URL 和挖矿参数（在本例中为矿工地址和难度级别）。然后我们使用 `requests.post()` 函数向 API 端点发送 POST 请求，请求体中包含挖矿参数。最后，我们检查响应状态码以查看挖矿是否成功，如果成功则打印出区块哈希值。

你可以单独开发挖矿软件。要向矿工提供单独的挖矿代码，你可以创建一个独立的程序或应用程序，该程序实现挖矿算法并使用适当的 API 端点连接到网络。该程序可以分发给矿工，他们可以在自己的计算机上运行它以参与挖矿过程。

重要的是要注意，挖矿代码必须设计为安全可靠，以防止对网络的攻击或其他可能损害区块链完整性的问题。

重要的是要注意，创建单独的挖矿代码可能是一个复杂的过程，建议你与经验丰富的开发人员或安全专业人员合作，以确保你的挖矿代码安全可靠。本书仅用于教育目的。

谢谢

Sankar Srinivasan
印度国家证券交易所认证市场专业人士

*   https://withkoji.com/@sankarsrinivasan
*   petra.srini@gmail.com
*   WhatsApp: +919042404390

![](img/image-d1uh5s4z.png)

---

不要错过！

点击下面的按钮，你可以注册以在 Sankar Srinivasan 出版新书时接收邮件。无需付费，无任何义务。

https://books2read.com/r/B-I-BYHC-JBUIC

![](img/image-7233j8fo.png) https://books2read.com/r/B-I-BYHC-JBUIC

![](img/image-o20b4lb0.png) 连接独立读者与独立作家。

---

Sankar Srinivasan 的其他作品

*   Fibonacci Retracement : Simplified
*   Gann Mid Point Theory : Simplified
*   Gann Square of 9 : Simplified
*   Gann Angle Theory : Simplified
*   William D. Gann's Simplified Stock Market Theories
*   Retração de Fibonacci : Simplificado
*   Retroceso de Fibonacci : simplificado
*   What is Divergence?
*   What is Candlestick Pattern?
*   Technical Analysis : An Introduction
*   Elliott Wave Theory : An Introduction
*   Dow Theory : An Introduction
*   The concise history of Patrice Lumumba
*   Basics of Option Trading
*   Basics of Stock Market
*   Fundamental Analysis : An Introduction
*   Understanding Blockchain
*   Build Your Own Blockchain In JS
*   Basics of Forex Trading
*   Become an Entrepreneur Without Money
*   Crude Trading Guide
*   Beware of Trading Scams
*   Advanced Option Trading

关注 Sankar Srinivasan 的更多作品





![](img/image-fca6wvea.jpg)

## 关于作者

Sankar Srinivasan 在技术分析和在线交易领域拥有超过 10 年的经验。他为在线交易开设技术分析和 GANN 理论课程。

他负责全球外汇和印度股票交易的分仓业务。他为南印度的众多股票、商品和外汇交易者提供技术指导。此外，他是印度国家证券交易所认证的市场

在 Sankar Srinivasan 的

