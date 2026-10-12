
```solidity
function addNewItem(bytes32 name, uint price) public returns (uint) {

        _items.push(Item({
            name: name,
            price: price,
            seller: msg.sender,
            status: ItemStatus.active
        }));

        // Item is pushed to the end, so the lenth is used for
        // the ID of the item
        return _items.length;
}
```

由于数组是零索引的，且我们使用数组位置作为 ID，实际上我们应该返回 `_items.length - 1`。修复此错误并再次运行：

```bash
truffle test
```

你应该会收到一条令人欣喜的消息：

```
TestHashMarket
  ✓ testAddingNewProduct (130ms)


1 passing (729ms)
```

我们已成功使用 Truffle 测试修复了代码中一个极可能存在的错误！

#### JavaScript 测试

Truffle 使我们能够使用 JavaScript 进行测试，利用 Mocha 测试框架。这使你能够编写更复杂的测试，并从测试框架中获得更多功能。

好的，让我们编写测试。首先，在 `test` 文件夹中创建一个文件，命名为 `hashmarket.js`。

我们需要做的第一件事是获取合约在 JavaScript 中的引用。为此，我们将使用 Truffle 的 `artifacts.require(...)` 函数：

```javascript
var HashMarket = artifacts.require("./HashMarket.sol");
```

现在我们有了合约的引用，让我们开始编写测试。首先，我们将使用提供给我们的 `contract` 函数：

```javascript
contract("HashMarket", function(accounts) {

});
```

这为我们的合约创建了一个测试套件。现在为了测试，我们使用 Mocha 的 `it` 语法：

```javascript
contract("HashMarket", function(accounts) {
    it("should add a new product", function() {

    });
});
```

这描述了我们将要编写的测试，并为我们呈现一条消息以了解测试的目的。现在让我们编写测试本身。最后，`hashmarket.js` 文件应如下所示。推理过程在源代码的注释中已有解释：

```javascript
var HashMarket = artifacts.require("./HashMarket.sol");

contract("HashMarket", function(accounts) {
    it("should add a new product", function() {

        // 设置测试数据的名称
        var itemName = "TestItem";
        var itemPrice = 1000;
        var itemSeller = accounts[0];

        // 由于我们所有的测试函数都是异步的，我们将合约实例
        // 存储在较高层级以便所有函数均可访问
        var hashMarketContract;

        // Item ID 将异步提供，因此我们将其提取出来
        var itemID;

        return HashMarket.deployed().then(function(instance) {
            // 将合约实例设置到变量中
            hashMarketContract = instance;

            // 订阅一个 Solidity 事件
            instance.ItemAdded({}).watch((error, result) => {
                if (error) {
                    console.log(error);
                }
                // 事件触发后，将结果存储在外部变量中
                itemID = result.args.itemID;
            });

            // 调用 addNewItem 函数并返回 Promise
            return instance.addNewItem(itemName, itemPrice, {from: itemSeller});
        }).then(function() {
            // 此函数在 addNewItem 调用交易被挖出后触发。
            // 现在使用我们从事件中接收到的 itemID 调用 getItem 函数
            return hashMarketContract.getItem.call(itemID);
        }).then(function(result) {
            // getItem 的结果是一个元组，我们可以像这样将其
            // 解构为变量
            var [name, price, seller, status] = result;

            // 开始测试。使用 web3.toAscii() 将智能合约的结果
            // 从 Solidity 字节码转换为 ASCII。之后使用 .replace()
            // 去除 bytes32 中多余的填充字节
            assert.equal(itemName, web3.toAscii(name).replace(/\u0000/g, ''), "Name wasn't properly added");
            // 使用 assert.equal() 检查所有变量
            assert.equal(itemPrice, price, "Price wasn't properly added");
            assert.equal(itemSeller, seller, "Seller wasn't properly added");
            assert.equal(status, 0, "Status wasn't properly added");
        });
    });
});
```

运行 `truffle test`，你应该会得到类似如下的结果：

```
TestHashMarket
  ✓ testAddingNewProduct (109ms)

Contract: HashMarket
  ✓ should add a new product (64ms)


2 passing (876ms)
```

你的测试已通过，你可以确信没有回归 Bug。

作为作业，为合约中的所有其他函数编写测试。

## 第 7 章：Truffle 迁移详解

### 作者：Mislav Javor

一般来说，迁移是开发者实现数据及其支持结构自动化部署的方式。它们对于管理新软件版本的部署非常有用，因此并非区块链开发所独有。

### Truffle 迁移

Truffle 迁移使我们能够将智能合约“推送”到以太坊区块链（无论是[本地、测试网还是主网](https://bitfalls.com/2018/02/08/what-is-an-ethereum-testnet-and-how-is-it-used/)），并设置将合约与其他合约链接以及用初始数据填充合约所需的步骤。

迁移真正大放异彩的地方在于对区块链上合约地址的管理。这项通常繁琐的工作在 Truffle 中几乎被完全抽象化了。

### 先决条件

请确保您已安装 [Truffle 框架](http://truffleframework.com/) 和 [Ganache CLI](https://github.com/trufflesuite/ganache-cli)。

### 入门

首先，选择一个项目文件夹，然后运行 `truffle init`。您应该会得到类似如下的输出：

```
Downloading...
Unpacking...
Setting up...
Unbox successful. Sweet!

Commands:

  Compile:        truffle compile
  Migrate:        truffle migrate
  Test contracts: truffle test
```

此命令会在您当前所在的目录中创建一个基础的 Truffle 项目。目录结构如下：

```
.
├── contracts
│   └── Migrations.sol
├── migrations
│   └── 1_initial_migration.js
├── test
├── truffle-config.js
└── truffle.js
```

首先，在 `contracts` 目录中，创建一个名为 `Storage.sol` 的新文件，内容如下：

```solidity
pragma solidity ^0.4.21;


contract Storage {

    mapping (string => string) private _store;

    function addData(string key, string value) public {
        require(bytes(_store[key]).length == 0);
        _store[key] = value;
    }

    function removeData(string key) public returns (string) {
        require(bytes(_store[key]).length != 0);
        string prev = _store[key];
        delete _store[key];
        return prev;
    }

    function changeData(string key, string newValue) public {
        require(bytes(_store[key]).length != 0);
        _store[key] = newValue;
    }

}
```

#### 初始迁移

正如您可能已经注意到的，运行 `truffle init` 时会创建两个文件。它们是 `Migrations.sol` 和 `1_initial_migration.js`。

初始迁移文件很少需要更改。它们的作用本质上是跟踪区块链上的地址。

`Migrations.sol` 文件可以是您想要的任何样子，但它必须符合一个固定的接口，该接口类似于 `truffle init` 命令创建的接口。您可以在这些文件中对迁移进行一些高级处理，但正如我所说，这很少需要。

`1_initial_migration.js` 文件也是如此。它的作用仅仅是将 `Migrations.sol` 文件推送到所需的区块链。

#### 迁移数据

为了将智能合约部署到以太坊区块链，您必须首先编写迁移脚本。为了开始，在您的 `migrations` 目录中，创建一个名为 `2_deploy_contracts.js` 的文件。您的项目结构现在应该如下所示：

```
.
├── contracts
│   ├── Migrations.sol
│   └── Storage.sol
├── migrations
│   ├── 1_initial_migration.js
│   └── 2_deploy_contracts.js
├── test
├── truffle-config.js
└── truffle.js
```

为了使用迁移部署智能合约，首先我们需要访问它们的*工件*。这些文件描述了合约地址、合约已部署的网络以及合约拥有的函数。

那么所有这些数据来自哪里？

在您的项目目录中，运行 `truffle compile`。如果一切顺利，您应该会得到类似如下的输出：

```
Compiling ./contracts/Migrations.sol...
Compiling ./contracts/Storage.sol...

Writing artifacts to ./build/contracts
```

*根据编译器版本的不同，您可能会收到一些警告，但只要没有错误，就可以继续。*

现在再次检查您的项目目录结构：

```
.
├── build
│   └── contracts
│       ├── Migrations.json
│       └── Storage.json
├── contracts
│   ├── Migrations.sol
│   └── Storage.sol
├── migrations
│   ├── 1_initial_migration.js
│   └── 2_deploy_contracts.js
├── test
├── truffle-config.js
└── truffle.js
```

请注意，现在有一个 `build` 文件夹，其中包含两个文件 —— `Migrations.json` 和 `Storage.json` —— 它们与 `contracts` 目录中的智能合约文件相对应。

这些 `*.json` 文件包含其各自智能合约的描述。描述包括：

*   合约名称
*   合约 ABI（应用程序二进制接口 —— 智能合约中所有函数及其参数和返回值的列表）
*   合约字节码（编译后的合约数据）
*   合约已部署字节码（部署到区块链的最新版本字节码）
*   最后编译合约的编译器版本
*   合约已部署的网络列表以及合约在每个网络上的地址。

此文件使 Truffle 能够创建一个 JavaScript 包装器，用于与智能合约通信。例如，当您在 JavaScript 代码中调用 `contract.address` 时，Truffle 框架会从 `*.json` 文件中读取地址，从而实现合约版本和网络之间的轻松切换。

#### 编写迁移

掌握了这些知识，让我们编写第一个迁移脚本。在 `2_deploy_contracts.js` 文件中，编写以下内容：

```javascript
// 从 Storage.json 文件获取 Storage 合约数据
var Storage = artifacts.require("./Storage.sol");

// JavaScript 导出
module.exports = function(deployer) {
    // Deployer 是用于将合约部署到网络的 Truffle 包装器

    // 将合约部署到网络
    deployer.deploy(Storage);
}
```

编写迁移就是这么简单。要运行迁移脚本，请在终端中运行以下命令：

```
truffle migrate
```

您应该会收到一个错误，内容如下：

```
Error: No network specified. Cannot determine current network.
```

这意味着 Truffle 找不到您要部署的网络。

为了使用模拟的以太坊区块链，在终端中打开一个新标签页并运行 `ganache-cli`。您应该会得到类似如下的输出：
