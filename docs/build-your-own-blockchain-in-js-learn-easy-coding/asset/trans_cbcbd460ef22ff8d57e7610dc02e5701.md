
# 添加挖矿间隔、减半周期和减半百分比

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

# 哈希算法

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

# 为上述新币种创建钱包

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

# 自动生成公钥和私钥

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
