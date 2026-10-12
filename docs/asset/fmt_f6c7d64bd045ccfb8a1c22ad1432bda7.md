
1. 使用基于 Rust 的 Aiken 编译器编译 Aiken 脚本，生成编译后的 Plutus 脚本和脚本哈希等构件，存入称为 `blueprint` 的文件中。

2. Lucid 链下代码读取 `blueprint` 文件中的编译脚本以及可能需要的任何合约参数。

## Blockfrost API

在我们的示例中，我们将使用 Blockfrost API 与 Cardano Preprod 网络交互。因此，您必须获取 API 密钥并将其设置为环境变量。

1. 访问 [`blockfrost.io/`](https://blockfrost.io/)

2. 创建免费账户并为 Cardano Preprod 网络创建 API 密钥。

## 初始化

对于 Lucid 链下代码示例，我们将参考可通过以下步骤运行的 GitHub 代码：

```
$ cd chapter_05/aiken/vesting
$ nvm install 18.17.0
$ npm install
$ echo export NEXT_PUBLIC_BLOCKFROST_API=https://cardano-preprod.blockfrost.io/api/v0 >> ~/.bashrc
$ echo export NEXT_PUBLIC_BLOCKFROST_KEY=your-blockfrost-API-key >> ~/.bashrc
$ source ~/.bashrc
$ npm run dev
```

这将启动 Next.js 并提供与使用 Helios Transaction Builder 相同的体验。对于本章，Aiken 合约已经预编译，我们将在第 6 章“Validators”中讨论 Aiken 的安装和构建步骤。

*图 5.22、5.23* 和 *5.24* 展示了 blueprint 文件的内容。它描述了 Aiken Validator 以及 Datum 和 Redeemer 数据类型。

![](img/Figure-5.22.jpg)

**图 5.22：** Aiken Blueprint Validator

![](img/Figure-5.23.jpg)

**图 5.23：** Aiken Blueprint Datum 定义

![](img/Figure-5.24.jpg)

**图 5.24：** Aiken Blueprint Redeemer 定义

## Lucid 链下代码

`WalletConnect.tsx` 组件将以与 Helios 链下代码示例相同的方式获取 `walletAPI`。不同之处在于 Lucid 还需要使用区块链 API 提供者，例如 `Blockfrost`。一旦在 *图 5.25* 的第 32-35 行创建了提供者，`walletAPI` 就会在第 118 行传递给它（见 *图 5.26*）。

![](img/Figure-5.25.jpg)

**图 5.25：** Lucid Blockfrost 提供者¹²

Datum 手动构建，Plutus 验证器脚本分别从 blueprint 文件的第 126 行和第 129 行读取（见 *图 5.26*）。最后，交易在第 133 行构建、第 139 行签名、第 142 行提交。

![](img/Figure-5.26.jpg)

**图 5.26：** Lucid 提交交易¹³

> **提示：** 如果您的钱包中只有 1 个 UTXO，余额可能显示为 0 lovelace，因为您的钱包已将其排除并保留作为抵押品。对于 Lucid，您必须在钱包中显式设置抵押品。对于 Eternl，您可以通过进入钱包设置选项卡，选择抵押品下拉菜单，然后按下“设置抵押品”按钮来设置抵押品。

## 结论

我们从交易生命周期和 Cardano 中常用钱包的演示开始本章。然后我们使用两种不同的方法进行链下交易构建：Helios 和 Lucid + Aiken。为每种方法创建了相同的用户体验，以突出它们之间的代码差异。我们还演示了 `Demeter.run` 等实用工具如何用于搭建开发环境，以及如何使用钱包将您的权益注册到权益池。展望未来，我们已准备好审查链上代码并将其作为交易的一部分执行。

## 要点回顾

*   交易生命周期涉及构建、签名和提交。
*   交易在提交到网络时使用 CBOR 格式进行序列化。
*   钱包是通往区块链和智能合约的网关。
*   助记词用于帮助生成私钥。
*   测试网水龙头用于获取用于预览和预生产网络的测试 Ada (`tAda`)。
*   地址派生用于使用相同的私钥派生多个地址。
*   从钱包质押将提交权益注册和权益池委托证书。
*   CIP-30 是连接浏览器扩展钱包的 Cardano 标准。
*   Demeter Run 是用于 Cardano 环境的按需托管平台。
*   Helios 既是链下库也是链上库。
*   Helios 和 Lucid 可在客户端浏览器中使用。
*   Blueprints 在 Aiken 构建过程中创建，包含编译后的脚本、元数据以及 Datum 和 Redeemer 的类型定义。

## 多项选择题

1. 委托给权益池需要什么？

    1. 权益池委托证书
    2. 提款证书
    3. 使用钱包
    4. 权益注册证书

2. 关于接收地址和找零地址，以下哪项陈述是正确的？

    1. 两者都是内部地址
    2. 一个是内部地址，另一个是变量
    3. 一个是外部地址，另一个是内部地址
    4. 两者都是外部地址

3. 以下哪个 CIP 是 Cardano 浏览器钱包连接标准？

    1. CIP-22
    2. CIP-42
    3. CIP-30
    4. CIP-32

4. 生成私钥时使用什么？

    1. 网络
    2. 助记词
    3. 密码
    4. 以上都不是

5. Aiken blueprint 在 Lucid 中用于什么？

    1. 锁定在脚本地址的 UTXOs
    2. 当前 Epoch
    3. 编译后的 Plutus 脚本和参数
    4. ADA 价格

## 答案

1. a
2. c
3. c
4. b
5. c

## 问题

1. 单地址模式钱包的优缺点是什么？
2. Helios 或 Lucid + Aiken 能否用于服务端模型？
3. 还可以使用哪些其他语言和框架来编写 Cardano 链下代码？
4. 为什么 Aiken blueprints 有帮助？
5. 生成私钥是否需要助记词？

## 关键术语

*   **组装交易**：创建包含输入、输出、Datum 和 Redeemer 的交易。
*   **账户抽象**：创建一个具有余额和交易历史的账户视图或模型。
*   **全节点**：Cardano 节点，不使用任何第三方服务在区块链上查找交易。
*   **助记词**：用于帮助生成私钥。
*   **确定性钱包层级**：用于从同一私钥派生多个地址。
*   **单地址模式**：复用相同的网络地址。
*   **可审计性**：确认智能合约已被审计的能力。
*   **透明度**：如何确保正在执行的智能合约是正确的。
*   **WalletAPI**：用于与符合 CIP-30 标准的浏览器钱包交互的 JavaScript 对象。
*   **Blockfrost**：用于查询 Cardano 区块链的 API 服务。

____________________________________

## 第 6 章：验证器

### 简介

本章将探讨什么是验证器以及它们为何如此重要。我们将展示如何花费锁定在验证器脚本地址上的 UTXO，以及如何访问兑换数据和数据中提供的数据。接下来将深入了解 `ScriptContext` 以及它如何用于访问与交易相关的输入和输出。本章还将回顾使用两种不同方法的代码示例：Helios 和 Lucid + Aiken。

### 结构

在本章中，我们将讨论以下主题：

*   验证器
*   Helios
    *   Helios 链上验证器
    *   Helios 链下解锁
    *   Helios 链下取消
*   Lucid + Aiken
    *   Aiken 链上验证器
    *   Lucid 链下解锁
    *   Lucid 链下取消

### 验证器

验证器是 Cardano 智能合约的基础，因为它们指定了花费锁定在验证器脚本地址上的 UTXO 所需的链上条件。一旦验证器部署到链上，它就是不可变的，代码即“法律”。验证器的一个典型用例是归属合约，资金被锁定在合约中，直到满足特定条件。我们将在后续章节中进一步构建我们的归属示例，并查看链上和链下代码。验证器由两个部分组成：定义规则和逻辑的链上代码，以及创建和提交交易的链下代码。

#### Helios

我们首先在第 5 章，交易构建器中看到了如何使用 Helios 构建链下交易。在本章中，我们将首先查看构建链上验证器的代码，然后是花费锁定在脚本地址上的 UTXO 所需的链下代码。用于链上代码的 Helios 语言是一种强类型函数式编程语言，具有类似 Haskell 或 Aiken 等语言的代码质量优势。然而，Helios 编译器是用 JavaScript 编写的，并具有仅使用 JavaScript 在运行时编译的独特优势。这使得设置和安装变得微不足道，因为您只需要一个广泛可用于许多操作系统的最新版 Node.js。

### Helios 链上验证器

Helios 链上验证器的第一行指定了 Plutus 脚本的用途。在本例中，它是一个 `spending`（花费）脚本，脚本的名称称为 `vesting`（归属）。在图 6.1 的第 7 行，定义了一个数据作为 `struct`，包含一个使用 `PubKeyHash` 数据类型的 `owner` 变量。这将存储在锁定在脚本地址上的 UTXO 中的链上。我们之前在第 4 章，Plutus 的图 4.5 中看到了这种类型数据的示例。在图 6.1 的第 15 行，有一个带有 `enum` 数据类型的兑换数据，包含两个元素：`Cancel`（取消）和 `Claim`（领取）。`Claim` 元素有一个 `msg` 变量，用于在运行时向验证器传递消息。

![](img/Figure-6.1.jpg)

**图 6.1：** Helios 链上验证器声明¹

**注意**：本地运行时，可用 Helios Visual Studio Code 扩展 (`ext:hl`) 进行语法高亮。对于 Visual Studio Web，您必须将 `.hl` 扩展与 C # 关联。

在图 6.2 的第 23 行，声明了一个**合约参数** `MESSAGE`，它将被硬编码到 Plutus 脚本中。**合约参数** 是一个位于主验证器函数之前的 UPLC 值，如果需要，可以在编译时或运行时动态更新。

![](img/Figure-6.2.jpg)

**图 6.2：** Helios 链上验证器主体²

主验证器函数在图 6.2 的第 26 行定义。我们可以看到，三个参数 `Datum`、`Redeemer` 和 `ScriptContext` 被传递给主函数。验证器可能根据验证器逻辑使用这些参数中的无、任意或所有参数。我们已经在第 4 章，Plutus 中讨论过 `Datum` 和 `Redeemer`，因此我们将更详细地研究 `ScriptContext`。`ScriptContext` 包括脚本用途以及与提交的交易相关的所有信息，**辅助数据（元数据）**除外。

正如我们从第 3 章，交易中回忆的那样，脚本用途是在锁定在脚本地址上的每个 UTXO 的兑换数据中指定的。因此，可在 `ScriptContext` 中使用的四种脚本用途如下：

*   `Spending`：用于验证花费锁定在脚本地址上的 UTXO。
*   `Minting`：用于铸造或销毁原生代币。
*   `Certifying`：用于质押密钥注册和将质押委托给质押池。
*   `Rewarding`：用于提取质押奖励。

## 参考文献

[¹] [`www.cardanocube.com/cardano-ecosystem-interactive-map`](https://www.cardanocube.com/cardano-ecosystem-interactive-map)

[²] [`github.com/bitcoin/bips/blob/master/bip-0039.mediawiki`](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)

[³] [`github.com/bitcoin/bips/blob/master/bip-0032.mediawiki`](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki)

[⁴] [`book.world.dev.cardano.org/environments.html`](https://book.world.dev.cardano.org/environments.html)

[⁵] [`github.com/cardano-foundation/CIPs/tree/master/CIP-1852`](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1852)

[⁶] [`cips.cardano.org/cips/cip30/`](https://cips.cardano.org/cips/cip30/)

[⁷] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/components/WalletConnector.tsx`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/components/WalletConnector.tsx)

[⁸] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/pages/index.tsx`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/pages/index.tsx)

[⁹] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/pages/index.tsx`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/pages/index.tsx)

[¹⁰] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/pages/index.tsx`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/pages/index.tsx)

[¹¹] [`preprod.cexplorer.io/tx/32a447855aa33edd50454eb897054a5c89b8cea1019e958a340c3f03302daf3f`](https://preprod.cexplorer.io/tx/32a447855aa33edd50454eb897054a5c89b8cea1019e958a340c3f03302daf3f)

[¹²] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/aiken/vesting/pages/index.tsx`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/aiken/vesting/pages/index.tsx)

[¹³] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/aiken/vesting/pages/index.tsx`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/aiken/vesting/pages/index.tsx)

在 *Figure 6.2* 第 27 行，我们定义了一个局部变量 `tx`，它从当前正在执行的交易中获取所有交易信息。随后将用于提取该交易所需的签名者。接下来，我们对 `Redeemer` 使用 `switch` 语句，根据 `Redeemer` 的值执行不同的代码。
