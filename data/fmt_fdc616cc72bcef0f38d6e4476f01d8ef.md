
Vyper 在逻辑上与 Solidity 相似，与 Python 也有一些相似之处。在本文编写时，Vyper 仍处于测试阶段，因此我不会对其进行详细介绍。

## WEB3-ETH

`Web3-eth` 用于以太坊的区块链和智能合约开发。该库是 `Web3`，我倾向于将其视为进入以太坊开发和去中心化应用世界的“快速通道”。

例如，你可以将 `Web3-eth` 与 `Ganache` 使用，创建测试账户来测试你的智能合约。你可以指定 `ether` 在你的账户之间进行转账。`Web3-eth` 还有许多其他功能，支持去中心化应用的快速开发。

使用 `Web3` 的主要挑战在于，如果你在开发时不小心，你可能正在使用的版本在与库交互的方式上存在某些差异。

下载 `Web3` 库后，你只需使用以下命令初始化你的应用程序节点：

```
npm install web3
```

在进行任何操作之前，请参考 `https://web3js.readthedocs.io/en/1.0/getting-started.html` 中的 web3 文档。

## 以太坊测试

软件开发通常有一个被广泛接受的流程，区块链开发领域也是如此。主要区别在于区块链的步骤不同，相比之下它多了一个额外的步骤。

`表 10.3` 比较了传统软件开发中广泛接受的步骤与区块链开发。

**表 10.3**: 传统开发 vs. 区块链开发

| 传统软件开发阶段 | 区块链软件开发阶段 |
| --- | --- |
| 原型 | 原型 |
| Alpha/Beta | 框架测试 |
| 生产环境 | 私有链测试 |
| 更新发布 | 测试网 |
|  | 主网 |

需要理解的主要点是区块链中存在软件开发阶段，我们必须以不同的方式对待它们。区块链部署智能合约，因此开发可能比典型的企业级应用更简单。然而，需要注意的主要区别是智能合约一旦部署到某些区块链上，就是不可变的。

## 以太坊测试网

在主网上部署应用程序之前，你可能希望在以太坊测试网上对其进行测试。可以直接从 MetaMask 访问以下测试网：

* `Rikeby`
* `Ropsten`
* `Kovan`

测试网虽然用于测试，但仍需要 `ether`（尽管是测试 `ether`），它用于维护节点。你可以通过多种方式获得测试 ether，例如通过挖掘测试网或使用水龙头（f）。

## TRUFFLE SUITE

`Truffle Suite` 本质上是一套 dapp 解决方案。以下解决方案是 `Truffle Suite` 的组成部分：

* `Truffle`，即 IDE
* `Ganache`，允许开发者部署个人区块链
* `Drizzle`，包含了所有需要的前端库

## TRUFFLE

`Truffle` 是一个用于区块链的开发者环境、测试框架和资产流水线。`Truffle` 本质上是一个基于 `NodeJS` 的 JavaScript 库。`Truffle` 非常受欢迎，使用量每月都在增长。`Truffle` 由 Consensus 开发。

`Truffle` 允许开发者只需点击即可启动智能合约项目，并为你提供项目结构、文件和目录，使得部署和测试变得简单得多（否则你必须手动配置这些内容）。

要安装和运行 `Truffle`，你首先需要安装 `Node` 和 Node 包管理器 (`NPM`)。可以在 `https://nodejs.org/en/40T` 找到。安装 `Node` 后，你可以进入任何命令行界面（Mac/Linux 上的 `Terminal` 或 Windows 上的 `PowerShell`）与 `npm` 交互。

`Truffle` 框架的一个有趣项目是 `Truffle Box`。这些预配置的“微脚手架项目”让启动新的分布式应用程序变得更加高效。`truffle boxes` 列表可以在 `http://truffleframework.com/boxes/40T` 找到。

使用基础 JavaScript，`Truffle Box`。

`truffle framework` 可以在 `truffleframework.com/` 或 `https://truffleframework.com/` 找到。

`图 10.3` 显示了 `Truffle Suite`。

## GANACHE

`Ganache` 是一个命令行工具，允许你部署 ` `` 并且 `Transactions` 会即时区块。

`Ganache` 是 `blockchain` 的最新版本。

`Ganache` 是 `Truffle` 的一部分，允许你在没有运行以太坊节点开销的情况下对 `blockchain` 进行调用。

`Ganache` 支持 `Windows`、`Mac` 和 `Linux`。

`Ganache` 本质上模拟了一个真实的 `blockchain`。

`Ganache` 以桌面应用程序和命令行工具的形式提供。

`图 10.15` 显示了 `Truffle Suite`。

`图 10.15` 显示了 `Truffle`。

## DRIZZLE

`Drizzle` 是一组前端库，使得编写 dapp 变得简单、高效且可预测。`Drizzle` 的核心基于 `Redux` 存储，你可以访问 `Redux`。

## TRUFFLE 还是 GANACHE？

决定使用 `Truffle` 还是 `Ganache` 可能会有些困惑，因为这些解决方案之间存在重叠。以下是一些帮助你做建议：

* `Truffle` 允许你开发、测试和部署 dapp，并集成了 `Ganache`。
* `Ganache` 是 `Truffle` 生态系统的一部分，你可以使用它来开发 dapp。它模拟了真实的区块链。你也可以放弃使用 `Ganache` 而使用 `Truffle` 连接到公共测试网或进行本地部署。
* 一旦开发并测试了 dapp，就可以使用 `Geth` 或 `Parity` 在以太坊客户端上部署它们。

## OPEN ZEPPELIN

`Open Zeppelin` 是一个规范且流行的可重用智能合约框架，适用于以太坊和其他基于 `EVM` 的区块链。`Open Zeppelin` 是一个用于安全智能合约开发的库。

它提供了 `ERC-20` 和 `ERC-721` 等标准的实现，你可以直接部署它们或根据需要进行扩展，这些 Solidity 组件用于构建自定义合约和更复杂的去中心化系统。

这些可重用的智能合约非常有用，因为它们经过了同行评审。

有关 `Open Zeppelin` 的更多信息，请访问 `https://openzeppelin.org/`。

## 私有区块链测试

开发者的一个感兴趣领域是在本地部署、测试和验证应用程序，而无需连接 VPN。或者你可能正在开发应用程序，并希望确保特定的网络变量可用。你会希望使用 `Ganache` 进行私有部署。

## 以太坊代币

代币根据以太坊中的特定标准 `ERC-20` 标准创建的。以太坊生态系统中的代币可以代表任何同质的可交易物品，如忠诚积分、金属证书、IOU、硬币等。

在大多数情况下，代币（Tokens）以标准方式实现了一些基本功能，这意味着你的代币可能兼容以太坊钱包或其他使用相同标准的客户端或合约。

这些代币需要遵循特定的标准，也称为 `constants`（常量）。示例包括：

* `Symbol`，你的代币符号或行情代码（ticker）
* `Name`，你给它起的名称
* `Total supply`，总总量，指定发行的代币数量
* `Decimals`，使用的小位数数量

这些标准列在 `Ethereum.org/token`。

## 以太坊意见请求 (ETHEREUM REQUEST FOR COMMENTS)

以太坊意见请求（ERC）是一个增强版的 GitHub 问题跟踪器。这是主要的联系点，开发者可以在这里对合约以及与以太坊提案的其他问题寻求意见。一个 `ERC` 以 `#1` 开始，每当开启新问题时，编号就会递增。

你可以在 `https://eips.ethereum.org/erc` 找到 ERC。

## 以太坊 ERC 代币 (ERC-20)

`ERC-20` 代币合约是在以太坊区块链上作为智能合约部署同质化代币的“标准”模板。`ERC` 代币标准基本上是一个标准接口，也是创建和操作 `ERC-20` 代币所需函数的示例实现。

以太坊开发者需要非常意识到他们如何开发应用程序。一种方法是遵循 `ERC-20` 标准。`ERC-20` 标准有多个用途，但主要目的集中于合约的可移植性。

## 以太坊改进提案 (ETHEREUM IMPROVEMENT PROPOSALS)

以太坊改进提案（EIPs）的格式与 ERC 相同，但用于提议以太坊协议的更改。`EIPs` 的作用与比特币改进提案（BIPs）相同。`BIPs` 用于引入对比特币重要的新功能或信息。`EIPs` 以 `EIP #1` 开始，每当开启新问题时，编号就会递增。

要了解更多信息，请访问 `https://github.com/ethereum/EIPs`。

## Hyperledger 开发

在 Hyperledger Fabric 中开发应用程序具有许多巨大的优势。对于一个开源项目来说，Hyperledger 生态系统非常健壮且维护良好。Hyperledger 项目在开发选项上几乎没有遗漏，显然是管理最良好的区块链项目。

本节提供了 Hyperledger Fabric 开发者需要处理和围绕之开发内容的大致概念。

### 链码 (Chaincode)

链码是 Hyperledger Fabric 中的一种智能合约，由区块链外部客户端应用程序调用，该程序管理对世界状态中一组键值对的访问和修改。世界状态是当前区块链交易的实际状态，以不可篡改的方式记录。

链码服务是安全且轻量级的，因为环境被部署在一个受限制、安全的容器中。该容器包含一组签名的基础镜像，其中包含了安全的操作系统以及链码语言、运行时以及针对 `Golang`、`Java` 和 `Node.js` 的 SDK 镜像。

每个链码必须实现链码接口，该接口用于提供类似于云计算中端点（endpoint）的连接。链码接口使得客户端应用程序能够调用响应收到的交易提案而调用的函数。链码实现了链码接口，特别是 `Init` 和 `Invoke` 函数。

#### 安装链码

在安装链码时，你应该确保先已经安装了 Go 编程语言，然后根据你的部署类型设置正确的配置要求。

你可能需要为链码应用程序创建一个目录，并作为 `$GOPATH/src/.` 的子目录。

以下命令将创建一个名为 `wiley:code:` 的目录：

```
mkdir -p $GOPATH/src/wiley:code own
```

要进入该目录，可以使用以下命令：

```
cd $GOPATH/src/wiley:code
```

要为链码创建源文件，请使用以下命令：

```
touch wiley:code.go
```

#### 编写链码的注意事项

在安装 Go 并设置好环境后，你就可以开始开发你的链码了。

注意，本书将不会教授链码，但其组织目的是为开发者在 Hyperledger 开发中可能需要考虑的任务提供见解。其中某些任务与以太坊不同，值得招聘经理关注并赏识这一点。

接下来你可以做的下一件事是实现 `init` 函数。`init` 在链码实例化期间被调用，并将初始化作为链码一部分的任何数据。链码应用程序将实现两个通过 `invoke` 函数调用的函数。

在设置平台时，一个容易困惑的地方是关于数据库选项。如果复杂的查询基于预期的调用序列，你可能需要注意链码的设计。

这种困惑可能会发生，因为如果你不了解状态数据的数据库选项，无效的交易很可能会发生。状态数据库可以写在 `LevelDB` 或 `CouchDB` 中。

关于开始学习链码的教程信息，请参考以下网站：

`https://hyperledger-fabric.readthedocs.io/en/release-1.4/chaincode.html`

#### 区块链平台扩展

针对 VSCode 的 IBM Blockchain 平台扩展有助于 Hyperledger Fabric 开发者快速开发、配置和测试他们的链码。这也可以用于在他们的本地机器上测试客户端应用程序。该扩展目前支持 Windows 10、Linux 和 macOS。

该扩展的工作原理是创建一个基础智能合约，在你自己选择的开发语言中本地管理一个示例资产。

真正有用的一点是，扩展提供了将你的智能合约部署到 Hyperledger Fabric 实例所需的所有依赖。这些功能允许直接在 IBM Blockchain 上对链码进行高效开发。

要了解更多关于 VSCode 扩展的信息，请参考以下网站：

`https://cloud.ibm.com/docs/services/blockchain?topic=blockchain-develop-vscode`

### Hyperledger Fabric 共识选项

Hyperledger Fabric 有两种共识选项，从开发角度来看理解它们的区别是非常重要的。一旦你部署了区块链，就无法回滚。

* `Solo` 用于开发，是一个没有高可用性的单节点。
* `Kafka` 是部署在区块链上的版本。`Kafka` 是 Hyperledger 中接近投票共识的形式。

正如第 2 章所述的，共识方法有不同的优缺点。例如，节点越多，达成共识的时间越长。开发者应该意识到扩展性与性能之间的权衡。Hyperledger Fabric 关于共识的白皮书是主要的起点。要了解更多，请查看以下网站：

`https://www.hyperledger.org/wp-content/uploads/2017/08/Hyperledger_Arch_WG_Paper_1_Consensus.pdf`

### Hyperledger Fabric 数据库选项

考虑的重要事项之一是 Hyperledger Fabric 状态数据库的力量。Hyperledger Fabric 的账本系统使用 `LevelDB`，它通过内部同步允许并发写入器安全地向数据库插入数据。

状态数据库选项包括 `LevelDB` 和 `CouchDB`。`LevelDB` 是嵌入在 peer 进程中的默认键值状态数据库。`CouchDB` 是支持二进制数据的替代外部状态数据库。

表 10.4 显示了交易日志和状态数据库的选项。

| 操作 | 创建、检索 | 所有增删改 (CRUD) |
| :--- | :--- | :--- |
| DC | LevelDB | LevelDB/CouchDB |
| Attitude | 嵌入同级节点中 | 键值对 (JSON, 二进制) |
| Query | 简单 | 复杂查询（二进制）使用 CouchDB |

需要注意的是，当资产以 JSON 文档的形式存储时，`CouchDB` 允许你根据资产状态等对资产执行复杂的查询。由于查询的格式与 CouchDB 的声明式 JSON 查询语法格式完全一致，因此实际上没有学习曲线。

### 客户端应用程序

在为区块链（特别是 `Hyperledger Fabric`）开发客户端应用程序时，根据具体的用例需要设计一些重要的考虑因素。这些客户端前端的考虑因素包括：

* 通过安全协议（`HTTPS`）保护 REST 服务器。
* 使用身份验证选项，例如通过 `Oath` 或支持的平台使用令牌。
* 为 `REST API` 服务使用多用户模式。
* 理解区块链应用程序的完整用例考虑因素。
* 使用当前的企业级密钥管理系统 (`KMS`）。
* 使用当前的软件开发包 (`SDKs`) 以确保运行的是支持组件的最新版本。

图 10.16 显示了 Hyperledger 区块链开发的不同层次。从开发的角度来看，如果你正在开发面向最终用户的区块链应用程序，这被认为是前端开发。在前端开发中将开发应用程序、钱包、移动应用程序和监控工具。

![图 10.16 前端应用程序工作流](img/c10f016.png)

图 10.16 前端应用程序工作流

`Hyperledger Fabric` 的业务网络存档（包）由模型文件、链码（chaincode）、访问控制文件和静态查询文件组成。

原生查询语言可以使用定义的标准来过滤返回的结果。原生查询语言也可以在事务中调用以执行更新等操作。

区块链查询定义在业务网络定义父目录下的查询文件 (`.qry`) 中。

发生的事件将创建区块链上重大操作（例如新区块）的通知，以及在处理智能合约/链码时实现里程碑的相关通知。客户端应用可以订阅这些事件并采取适当的业务操作。

### Fabric REST 服务

`REST` 服务器使用启动期间指定的业务网络卡来连接并发现已部署业务网络中的资产、参与者和交易。这种信息的可见性是生成 `REST API` 所必需的。该业务网络卡被称为发现业务网络卡。默认情况下，发现业务网络卡也用于处理所有对 `REST API` 的请求。

`Chaincode Services` 使用 `Docker` 来托管（部署）链码，而不依赖于任何虚拟机或计算机语言。`Docker` 提供了一种安全、轻量的方法来对链码执行进行沙箱处理。环境是一个“锁定”且安全的容器，以及一组包含签名的基础镜像，其中包含安全的操作系统、链码语言、运行时以及 `Golang` 的 SDK 镜像。

`Hyperledger` 包含了 `REST` 和 `JSON RPC APIs`、事件以及用于应用程序与网络通信的 `SDK`。

### 服务发现

为了在同级节点上执行链码、向排序器提交事务并获取事务状态的更新，应用程序连接到由 `SDK` 暴露的 API。发现服务通过让同级节点动态计算所需信息并以可消费的方式呈现给 `SDK` 改进了这一过程。

应用程序在启动时已已知一组被应用程序开发者/管理员信任的同级节点，这些节点可以对发现查询提供真实的响应。

客户端应用程序需要使用的理想候选同级节点应当是处于同一组织中的节点。

### Hyperledger Composer
