
- 10. Allison, I.: “微软将以太坊语言 Solidity 添加到 Visual Studio。” *国际商业时报.* https://www.ibtimes.co.uk/microsoft-adds-ethereum-language-solidity-visual-studio-1552171. 最后访问于 2020 年 9 月 1 日。 2016 年 3 月 30 日。
- 11. Waters, R.: ‘以太币’因 5000 万美元加密货币被盗而坠落。 *金融时报*, 2016 年 6 月 18 日。
- 12. Gatteschi, V., Lamberti, F., Demartini, C., Pranteda, C., Santamaría, V.: 区块链与保险中的智能合约：该技术是否足够成熟？ *未来互联网* 10, 20, 2018。
- 13. Tapscott, D., Tapscott, A.: *区块链革命：比特币背后的技术如何改变金钱、商业和世界。* Penguin Publishing Group: London, pp. 72, 83, 101, 127. 2016。
- 14. Luu, L., Chu, D.H., Olickel, H., Saxena, P., Hobor, A.: 使智能合约更智能。 In: ACM Conference on Computer and Communications Security 2016, 254–269. 2016。
- 15. Buterin, V.: 以太坊：下一代智能合约和去中心化应用平台。 https://github.com/ethereum/wiki/wiki/White-Paper, 最后访问于 2020 年 12 月 1 日。 2013。
- 16. 即将进行硬分叉以更改 EIP150 Gas 成本的公告。 https://blog.ethereum.org/2016/10/13/announcement-imminent-hardfork-eip150-gas-cost-changes/ 2016。

## 9 在以太坊平台中安装框架、部署和测试智能合约

*Tushar Sharma*  
高等教育 ICFAI 基金会  
（被视为大学）

### 目录

| Section | Title | Page |
|---|---:|---:|
| 9.1 | 引言 | 138 |
| 9.2 | Gas 和交易 | 138 |
| 9.2.1 | 交易共识 | 138 |
| 9.3 | 智能合约账户 | 139 |
| 9.3.1 | 智能合约结构 | 139 |
| 9.4 | 在以太坊 Rinkeby 测试网络中部署合约 | 140 |
| 9.5 | Web3 库 | 142 |
| 9.5.1 | Ganache 模块 | 143 |
| 9.5.2 | 从 Ganache 获取账户 | 144 |
| 9.5.3 | 获取账户的异步方法 | 145 |
| 9.6 | Metamask 扩展 | 146 |
| 9.6.1 | Infura | 147 |
| 9.7 | 使用 Mocha 框架进行测试 | 149 |
| 9.8 | 设计智能合约 | 151 |
| 9.8.1 | 为智能合约确定变量和函数 | 152 |
| 9.8.2 | 进入彩票合约 | 152 |
| 9.8.3 | 使用 “require” 语句进行验证 | 153 |
| 9.9 | 伪随机数生成器 | 154 |
| 9.9.1 | 伪随机数生成器使用的方法 | 154 |
| 9.9.2 | 选择获胜者 | 155 |
| 9.9.3 | 从合约发送以太币 | 155 |
| 9.9.4 | 重置合约状态 | 156 |
| 9.10 | 需要管理员 | 157 |
| 9.11 | 智能合约文件 | 157 |
| 9.11.1 | package.json 文件 | 157 |
| 9.11.2 | Raffle.sol 文件 | 158 |
| 9.11.3 | Raffle.test.js 文件 | 159 |

**表 9.1**  
**以太坊平台中交易的属性**

| Property | Description |
|---|---|
| Nonce | 发送方已发送交易的次数 |
| To | 资金正在转移到的账户地址 |
| Value | 发送到目标地址的以太币数量 |
| gasPrice | 发送方愿意为处理特定交易每单位 Gas 支付的以太币数量 |
| startGas/gasLimit | 交易可以消耗的 Gas 单位 |

以太坊平台中可以执行三种类型的交易：

- 1. 从一个账户向其他账户转账以太币。
- 2. 部署智能合约。
- 3. 在合约内调用函数。

交易与其相关有一些重要属性，如表 9.1 所示。v、r 和 s 是与密码学 [1] 数据片段相关的账户属性，可用于生成发送方的账户地址。

### 9.3 智能合约账户

智能合约可以被视为自动化合约中描述的某些条件和义务的一种方式。每个智能合约都有自己的地址，在发送或接收以太币时很有用。智能合约可以识别调用它的人，通过此我们可以对合约施加特权访问。

每个智能合约账户都有四个相关属性。这些是字段、余额、存储和代码。表 9.2 给出了这些属性的描述。

### 9.3.1 智能合约结构

图 9.1 所示的代码描述了智能合约的基本结构。

以下是上述编写的智能合约的特性：

- 1. 第一行 simply specifies that the source code is written for Solidity version 0.5.2. This is to make sure that the contract does not behave abnormally with a new compiler version. The keyword pragma can be used.

**表 9.2**  
**智能合约账户的属性**

| Field | Description |
|---|---|
| Balance | 任何特定账户拥有的以太币数量 |
| Storage | 合约的数据存储 |
| Code | 合约的原始机器代码 |

![](img/115a7d47166d21dfa1d1dc5986da244b_159_0.png)

**图 9.2** sol 文件的编译。

使用合约地址部署智能合约。如果任何账户想要调用智能合约的函数，它会利用 ABI 来哈希函数并构建 EVM 字节码以调用该函数。它是一个 JavaScript 格式的对象（JSON），描述了合约的各种功能，如输入/输出参数、函数名称、可支付性（是否可以发送以太币）、函数的状态可变性。它使用户能够为合约创建适当的消息。

只有字节码会被输入到 Rinkeby 测试网络中用于智能合约的部署和测试目的。

Remix 是一个基于浏览器的 Solidity 集成开发环境（IDE），用于编码、部署和测试智能合约。Remix 中列出了各种执行环境，如 JavaScript VM、Injected web3 [13] 和 Web3 Provider。

Remix 不仅仅是一个代码编辑器，它还包含一个微型的假以太坊网络，可用于部署和与合约交互。图 9.3 说明了如何使用 Remix IDE 进行测试。

在 Remix 中编译合约后，点击 Remix IDE 中的“run”选项卡以部署合约。如上所述，Remix IDE 中列出了各种执行环境，如 JavaScript VM、Injected web3 [13] 和 Web3 Provider。

**JavaScript VM—** 该环境允许开发者使用 JavaScript 实现的 EVM 直接运行合约。此外，该环境不允许其他人与合约交互。因此，该环境适用于简单的测试目的。

**Injected Web3—** web3 库可从应用程序连接以太坊网络。通过使用 MetaMask，这是一个 Chrome 浏览器扩展，我们可以与以太坊网络互连。此选项将允许开发者使用注入的执行将合约部署到测试网络或主以太坊网络。

**Web3 Provider—** 它通过超文本传输协议（HTTP）直接连接到以太坊节点。因此，此环境可用于与 Ganache 模块账户连接。

![](img/115a7d47166d21dfa1d1dc5986da244b_160_0.png)

**图 9.3** 使用 Remix 进行测试。

对于合约的初始开发和测试，JavaScript VM 是最佳选择。但另一方面，如果我们希望其他人与我们的合约交互，我们需要使用另一种可用的环境。

### 9.5 Web3 库

为在以太坊网络上创建和部署合约，使用 Node.js 及其模块。为在 Node.js 中编译 Solidity 文件，必须在机器上安装 node 模块 “solc”。使用此模块，Node.js 将编译 Solidity 文件，从而生成字节码和 ABI。要与区块链上的合约交互，使用 web3 [13, 14] 库。

如第 9.4 节所述，web3 库用于从应用程序连接以太坊网络。因此，web3 被用作 JavaScript 应用程序与以太坊网络之间通信的完美解决方案。ABI 被提供给 web3 库，后者使用它来提供对部署在以太坊网络上的合约的编程访问 [13]。

要使用 Web3，必须实例化 Web3 类的对象。

```javascript
const Web3=require('web3');
    const web3=new Web3();//Instance
```

可以创建多个 web3 库的实例，每个实例用于连接到不同的以太坊网络。要连接或与以太坊网络通信，web3 的实例需要一个称为
