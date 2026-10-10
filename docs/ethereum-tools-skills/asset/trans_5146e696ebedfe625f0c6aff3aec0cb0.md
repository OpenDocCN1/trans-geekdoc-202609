
正在下载...
正在解包...
正在设置...
解包成功。太棒了！

命令：

*   编译合约：`truffle compile`
*   迁移合约：`truffle migrate`
*   测试合约：`truffle test`

如果你遇到一些错误，可能是因为你使用的 Truffle 版本不同。本教程编写时使用的版本是 `Truffle v4.1.5`，但这些说明至少在未来几个版本中仍应保持相关性。

## Truffle 项目结构

你的 Truffle 文件夹看起来应该有点像这样：

```
.
├── contracts
│   ├── ConvertLib.sol
│   ├── MetaCoin.sol
│   └── Migrations.sol
├── migrations
│   ├── 1_initial_migration.js
│   └── 2_deploy_contracts.js
├── test
│   ├── TestMetacoin.sol
│   └── metacoin.js
├── truffle-config.js
└── truffle.js
```

### Contracts 文件夹

这是你存放所有智能合约的文件夹。

在你的 contracts 文件夹中，还有一个 `Migrations.sol` 文件，这是一个特殊文件——关于这一点我们将在下一节详细介绍。

当 Truffle 编译项目时，它会遍历 `contracts` 文件夹并编译所有兼容的文件。目前，最常用的文件是扩展名为 `.sol` 的 Solidity 文件。

未来，这可能会过渡到 Vyper 或 SolidityX（两者都更适合智能合约开发，但目前使用较少）。

## Migrations 文件夹

什么是 Truffle 迁移？从本质上讲，它是一个定义合约*如何*部署到区块链的脚本。

### 为什么我们需要迁移？

随着你的项目变得越来越复杂，你的部署复杂度也会随之相应增加。

让我们举个例子：

*   你有智能合约 `One`、`Two` 和 `Three`
*   智能合约 `Three` 包含对智能合约 `One` 的引用，*并且* 在其构造函数中需要合约 `Two` 的地址。

这个例子要求合约不仅要按顺序部署，还要相互引用。简而言之，迁移使我们能够自动化这个过程。

你大致会这样做：

```
var One = artifacts.require("One");
var Two = artifacts.require("Two");
var Three = artifacts.require("Three");

module.exports = function(deployer) {
  deployer.deploy(One).then(function() {
    deployer.deploy(Two).then(function() {
      deployer.deploy(Three, One.address);
    })
  });
};
```

除此之外，迁移还允许你做很多其他很酷的事情，比如：

*   设置部署的最大 Gas 限制
*   更改部署的 `from` 地址
*   部署库
*   调用任意合约函数

### 初始迁移

正如你在 `MetaCoin` 项目中注意到的，你有一个名为 `1_initial_migration.js` 的文件。该文件的作用是将 `Migrations.sol` 合约部署到区块链。

通常一旦初始化完成，你不需要对该文件做任何操作，所以我们不会过多关注这一点。

## Test 文件夹

正如我所说：你！必！须！测！试！智！能！合！约！没有借口，没有假设，没有也许：你必须这么做。

但如果你要做，拥有一个自动化工具来让你无缝地完成它会很酷。

Truffle 通过内置测试框架实现了这一点。它允许你用 Solidity 或 JavaScript 编写测试。

MetaCoin 项目中的示例基本上不言自明，所以我们不会深入探讨。

关键在于，如果你编写 Solidity 测试，你可以使用 Solidity `import` 指令将合约导入测试中：

```
import "../contracts/MetaCoin.sol";
```

如果你用 JavaScript 编写测试，则使用 `artifacts.require()` 辅助函数导入它们：

```
var MetaCoin = artifacts.require("./MetaCoin.sol");
```

## 配置文件

配置文件名为 `truffle.js` 或 `truffle-config.js`。在大多数情况下它叫 `truffle.js`，但之所以有备选名称，是因为 Windows 机器上奇怪的命令优先级规则。

只需知道，当你看到 `truffle.js` 或 `truffle-config.js` 时，它们基本上是同一个东西。（另外，不要在 Windows 上用 CMD；PowerShell 好得多。）

配置文件定义了以下几个方面，详见下文。

**环境** 开发环境、测试网、主网（生产环境）。你可以定义 Geth 节点的地址、`network_id`、部署的最大 Gas 限制、你愿意支付的 Gas 价格。

**项目结构** 你可以更改文件构建和存放的位置，但这既非必要也不推荐。

**编译器版本和设置** 固定 `solc` 版本并设置 `-O`（优化）参数。

**包管理**

*   Truffle 可以配合 EthPM（以太坊包管理器）工作，但目前仍不太稳定。
*   你可以为 Truffle 项目设置 EthPM 依赖。

**项目描述** 项目作者、项目名称、联系地址等。

**许可证** 使用 [GPLv3](https://pbs.twimg.com/profile_images/561116211258220544/FlICmGnj_400x400.jpeg)。

## 运行代码

要编译你的合约，请运行：

```
truffle compile
```

要运行迁移，你可以直接使用：

```
truffle migrate
```

或者你可以通过指定环境来运行：

```
truffle migrate --network live
```

要测试你的合约，请运行：

```
truffle test
```

或者你可以通过运行以下命令来运行*特定*测试：

```
truffle test ./path/to/FileTest.sol
```

## 结论

Truffle 是一个非常实用的工具，它让这个全新生态系统中的开发变得更容易一些。它旨在将开发世界其他领域的标准和通用实践带入区块链实验的一个小角落。

# 第 5 章：使用 OpenZeppelin 等编写高质量 Solidity 代码

### 作者：Tonino Jankov

**鉴于 [Ethereum](https://bitfalls.com/2017/09/19/what-ethereum-compare-to-bitcoin/) 的所有计算都需要在网络中的所有 [节点](https://bitfalls.com/2017/11/26/whats-bitcoin-node-mining-vs-validation/) 上重现，Ethereum 的计算本质上是昂贵且低效的。（事实上，GitHub 上的 Ethereum 开发者文档指出，我们不应期望 Ethereum 提供的计算能力超过 1999 年的手机。）**

因此，Ethereum 虚拟机上的安全性——即部署在 Ethereum 区块链上的智能合约的安全性——至关重要。所有错误都会造成真金白银的损失——无论是编写糟糕的合约抛出的错误，还是黑客利用合约中的漏洞，就像著名的 DAO 黑客事件那样，导致社区分裂并催生了 Ethereum Classic 区块链。

*图灵完备性*——以及一系列其他使 Ethereum 变得更强大、更复杂的设计决策——都是有代价的。Ethereum 的丰富性使其更容易受到错误和黑客的攻击。

更糟糕的是，部署在 Ethereum 上的智能合约无法修改。[区块链](https://www.sitepoint.com/blockchain-what-it-is-how-it-works-why-its-so-popular) 是一种不可变的数据结构。

[这篇](https://medium.com/loom-network/how-to-secure-your-smart-contracts-6-solidity-vulnerabilities-and-how-to-avoid-them-part-1-c33048d4d17d) 和 [这篇](https://medium.com/loom-network/how-to-secure-your-smart-contracts-6-solidity-vulnerabilities-and-how-to-avoid-them-part-2-730db0aa4834) 文章更深入地探讨了智能合约的安全性，以及帮助我们保障智能合约安全的工具和库生态系统。

让我们看看今天可以用来利用 Solidity 环境提供的最佳实践的一些令人惊叹的工具集升级。

## 辅助工具
