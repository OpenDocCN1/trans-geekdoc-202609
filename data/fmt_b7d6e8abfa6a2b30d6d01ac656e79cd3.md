
`CIP-0040` 引入了一种名为 `Collateral Outputs`（抵押输出）的新输出类型。正如我们在*第 4 章，Plutus*中所回想的，`Collateral`（抵押）作为押金是要求的，如果 `Plutus` 脚本第二阶段评估失败则将使用它。虽然这有助于保护网络免受垃圾信息或恶意攻击，但它为提交交易增加了额外的 `Ada` 要求。通过使用抵押输出，可以构建交易使我们可以使用任何 `UTXO` 作为抵押，但仅在需要时消耗押金金额，并将找零作为抵押返回输出返回。在 `CIP-0040` 之前，仅包含 `Ada` 的纯 `UTXO` 只能作为抵押输入。

## CIP-0068 Datum 元数据标准

`CIP-0068` 是一种定义使用 `datum` 存储代币元数据的标准。这与使用交易元数据存储代币元数据的 `CIP-0025` 不同。使用 `Datum` 的优势是它可以被智能合约直接更新和读取。该标准适用于非同质化令牌 (`NFT`s）或同质化令牌 (`FT`s）。`CIP-0068` 涉及创建一个与铸造的原始代币（s）关联的引用令牌，如图 9.5 所示。这种设计允许 `NFT`s 或 `FT`s 在区块链上移动，但引用令牌保留在一个位置。

![](img/Figure-9.5.jpg)

**图 9.5：** CIP-0068

代币命名规范是为十六编码标签添加前缀，例如 `NFT`s 使用 `222`，引用令牌使用 `100`。常用的前缀标签列在表 9.1 中。

| Label | Class | Description | Hex Label |
| :--- | :--- | :--- | :--- |
| 100 | NFT | Reference Token | `100` |
| 222 | NFT | Non-Fungible Token | `222` |
| 333 | FT | Fungible Token | `333` |
| 444 | NFT | Non-Fungible Token | `444` |

## 更新交换单 (Updating Swap)

如果满足以下两个条件，用户可以随时更新交换单位置：

*   钱包的质押 `PKH` 与交换单合约参数中的质押 `PKH` 匹配。
*   交换单合约参数中指定的灯标代币（Beacon Token）始终返回到脚本地址。

如果这两个条件均满足，则智能合约将允许更新价格，如图 9.11 所示。然而，正在交换的资产类型无法更改，因为它是被硬编码为合约参数的。

![](img/Figure-9.11.jpg)

**图 9.11：** 更新交换交易

## 执行交换 (Executing Swap)

只要满足 `askedAsset`（请求资产）的价格，任何人都可以执行交换。可购买的 `offeredAsset`（提供资产，票务令牌）数量将是在交换 UTXO 中的票务令牌数量，如图 9.12 所示。交换验证器还将确保灯标代币始终发送回验证者脚本地址，卖者收到正确数量的 `askedAsset`，买家收到正确数量的 `offeredAsset`（票务令牌）。

![](img/Figure-9.12.jpg)

**图 9.12：** 执行交换交易

在交换执行交易期间，我们还必须将票务令牌转换为唯一的票务令牌，进入场场时可以标记为 `used`（已使用）。我们通过在同一笔交易内销毁原始票务令牌并铸造新令牌来实现这一点，如图 9.13 所示。引用令牌数据值（Reference Token Datum value）初始设置为为空字符串，但在用户打印票务时将填充为支付的 PKH。

![](img/Figure-9.13.jpg)

**图 9.13：** 转换票务交易

## 关闭交换 (Closing Swap)

卖家可以随时关闭交换，如图 9.14 所示。

![](img/Figure-9.14.jpg)

**图 9.14：** 关闭交换交易

票务令牌必须返回到代币持有脚本地址，该地址定义为交换脚本参数。图 9.15 中详细的销毁灯标（Burn Beacon）交易也必须包含在关闭交换交易中。

![](img/Figure-9.15.jpg)

**图 9.15：** 销毁灯标代币交易

## 打印票务 (Print Ticket)

为了访问活动，用户必须证明他们确实拥有该票务令牌。这是通过使用打印票务（Print Ticket）交易实现的，该交易将使用作为交易一部分签名的支出 PKH 更新引用令牌数据，如图 9.16 所示。应用程序将创建一个稍后显示的 QR ，其中包含交易的数字签名。

![](img/Figure-9.16.jpg)

**图 9.16：** 打印票务

## 线下序列图 (Off-Chain Sequence Diagrams)

下一节将回顾描述应用程序内不同组件如何交互的高层理想路径（happy path）序列图。交易用 `[]` 表示，组件之间传递的任何值（如果显示）都用 `()` 表示。

## 铸造票务 (Minting Tickets)

使用应用程序铸造活动门票如图 9.17 所示。第一步是从钱包获取 UTXO 列表，然后构建铸造票务交易。用户将同时使用他们的支出密钥（用于支付交易费用）和质押密钥（证明他们确实拥有该质押密钥）对交易签名。一旦交易成功提交，应用程序数据库将进行更新，将质押密钥与之关联。

![](img/Figure-9.17.jpg)

**图 9.17：** 铸造票务

## 连接钱包 (Connected Wallet)

当用户连接钱包时，他们可以看到他们创建的事件列表，如图 9.18 所示。可以实施额外的安全措施，例如要求用户使用质押密钥进行签名。

![](img/Figure-9.18.jpg)

**图 9.18：** 连接钱包

## 开启交换 (Opening Swap)

票务铸造完成后，用户可以决定开启交换位置并出售票务，如图 9.19 所示。第一步是确定哪些铸造策略哈希（MPH）属于该用户。接下来，重建票务持有验证器以获取脚本地址和 UTXO。然后我们使用 UTXO 构建转移票务和铸造灯标交易。

![](img/Figure-9.19.jpg)

**图 9.19：** 开启交换

## 查看交换 (Viewing Swaps)

应用程序创建的所有开启交换均可用如图 9.20。灯标资产用于获取构建交换交易所需的 UTXO。

![](img/Figure-9.20.jpg)

**图 9.20：** 查看交换

## 区块链更新 (Blockchain Updates)

在使用本地数据库数据时，我们需要确保接收来自区块链的更新，如图 9.21 所示。

![](img/Figure-9.21.jpg)

**图 9.21：** 区块链更新

## 更新交换单 (Updating Swap)

用户可以随时更新交换位置以更改价格。他们将从自己的交换列表中选择一个，并用新价格更新它（参见图 9.22）。交换的灯标令牌用于查找 UTXO。使用钱包 UTXO、交换 UTXO、交换元数据和交换脚本可以构建并提交交易。

![](img/Figure-9.22.jpg)

**图 9.22：** 更新交换

## 执行交换 (Executing Swap)

买家现在可以去票务应用程序查看所有出售的票务。如果支付的价格符合要求，且数量充足，则交换将执行，如图 9.23 所示。使用钱包 UTXO 和交换 UTXO，支付票务的价值将直接发送到卖者地址，买家收到票务令牌。在票务转换期间，为每个唯一的票务令牌创建一个引用令牌。该引用令牌只能由应用程序更新，并包含一个指示令牌是否已使用的标记。

![](img/Figure-9.23.jpg)

**图 9.23：** 执行交换

## 关闭交换 (Closing Swap)

当交换中的票务数量为零，或者卖家不再希望出售这些票务时，卖家将想要关闭交换（参见图 9.24）。灯标资产用于获取构建交换交易所需的 UTXO，并将票务令牌（如有）返回到票务持有地址。灯标令牌还作为关闭交易的一部分被销毁，因此该交换将不再出现在可用交换列表中。

![](img/Figure-9.24.jpg)

**图 9.24:** 关闭交换 (Close Swap)

## 打印票据

票据应用程序也用于兑换活动票以进入活动。用户将显示 `QR code` 来验证所有权，这可以在活动开始之前的（或期间）任何时候进行。`QR code` 是一种数字签名，当他们使用持有票据令牌的钱包签名交易时生成。在 `Print Ticket` 交易期间，引用令牌数据（datum）会使用钱包花费的 `PKH` 进行更新。随后在活动现场，通过显示的 `QR code` 验证花费的 `PKH`。在活动现场验证 `QR code` 后，票据将在应用程序数据库中标记为已使用，如图 [9.25] 所示。

![](img/Figure-9.25.jpg)

**图 9.25:** 显示票据 (Show Ticket)

## 验证票据

`QR code` 的生成可以提前完成。这避免了用户将钱包带到活动现场并在入口时提交区块链交易。由于如果打印，引用令牌数据可能会用支付 `PKH` 更新，因此在进行任何二次传输之前验证票据是非常关重要的。应用程序拥有一个 API，允许查询区块链以确认票据是否已显示或已用于进入活动，如图 [9.26] 所示。

![](img/Figure-9.26.jpg)

**图 9.26:** 验证票据 (Verify Ticket)

## 结论

在本章中，我们理解了 `Thread Token`、`Beacon Token` 和 `Order Book` 设计模式，以及它们如何利用 EUTXO 架构的优势。我们查看了诸如池（pools）和批处理器（batchers）等反模式，这些模式通常会在 Cardano 等 UTXO 区块链上导致次优的方案。我们探索了若干 Cardano 改进提案 (`CIPs`）以及它们如何与我们的应用程序设计相关。特别是审查了 `CIP-0068`，了解了它如何提供了一种使用数据（datums）存储令牌元数据的不同方法。然后，我们开始根据本章中审查的设计模式和标准进行票据应用程序的设计。接下来，我们为每个用例创建了带有输入和输出的状态转换图。然后，我们创建了显示系统组件交互的序列图。我们准备好在下一章中实现票据应用程序，[第 10 章，票据应用程序实现]。

## 记忆要点

*   账户模型设计模式通常不适用于 EUTXO 架构。
*   `Thread Token` 设计模式使用唯一令牌来帮助隔离锁定在脚本地址上的特定 UTXO。
*   `Beacon Token` 设计模式使用唯一令牌来在链外轻松识别特定的 UTXO。
*   `Beacon Token` 可以同时用于 `Thread Token` 和 `Beacon Token` 设计模式。
*   `Order Book` 设计模式非常适用于 EUTXO 架构，因为 UTXO 是不可变的、唯一的且互不相关的。
*   可以使用链下计算完成原子交换对的识别。
*   交换 (`Swap`）在链上执行，不涉及任何第三方中间人。
*   原子交换保留了完全的自托管，并可以随时取消。
*   `Order Book` 设计模式可以应用于许多不同的用例。
*   `Liquidity Pools`（流动性池）和 `Batches`（批次）是性能和可扩展性次优的反模式示例。
*   `CIP-0068` 元数据标准使用 `Datums` 来存储 `NFTs` 或 `FTs` 的元数据，这些数据是可以更新的。
*   `Mint Ticket` 交易使用 `CIP-0025` 交易元数据发布铸造脚本参数。
*   `Open Swap` 交易需要在同一笔交易中包含 `Transfer Ticket` (`ticket.hl`) 和 `Mint Beacon` (`beacon.hl`)。
*   `Execute Swap` 交易需要在同一笔交易中包含 `Execute Swap` (`swap.hl`) 和 `Convert Token` (`ticket.hl`)。
*   `Convert Ticket` 使用带有支付 `PKH` 值的 `CIP-0068`。
*   `Update Swap` 和 `Close Swap` 只能由创建交换的钱包执行，并可以随时进行。
*   为活动打印票据时，用户……

## 单选题

1.  `QR code` 的生成可以提前完成……
2.  `UTXO` 架构非常适用于……
3.  `CIP-0068` 允许……
4.  如何识别 `Order Book`……
5.  为什么 `QR code` 签名……

## 答案

1.  c
2.  b
3.  a
4.  c

## 问答

1.  `Plutus` 如何确保……
2.  什么 `CIP` 允许……
3.  用于……的 `CIP`
4.  什么时候使用……
5.  `UTXO` 会发生什么

## 术语

*   `Anti-Patterns`: 反模式。
*   `FT`: 同质化令牌。
*   `KYC`: 了解您的客户。
*   `MPH`: 元数据。
*   `NFT`: 非同质化令牌。
*   `PKH`: 公钥哈希值。
*   `P2P`: 点对点。
*   `State`: 状态。
*   `State Machine`: 状态机。
*   `UTXO`: 未花费的交易输出。
*   `UTXO Contention`: UTXO 竞争。
*   `Zero Knowledge`: 零知识。

¹³ [`github.com/cardano-foundation/CIPs/tree/master/CIP-0068`](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0068)
¹⁴ [`developers.cardano.org/docs/governance/cardano-improvement-proposals/cip-0068/`](https://developers.cardano.org/docs/governance/cardano-improvement-proposals/cip-0068/)
¹⁵ [`github.com/cardano-foundation/CIPs/tree/master/CIP-0068`](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0068)
¹⁶ [`github.com/inimrod/cip68-fungible-token-demo/blob/main/src/lib/init-vars.ts`](https://github.com/inimrod/cip68-fungible-token-demo/blob/main/src/lib/init-vars.ts)
¹⁷ [`www.rapidtables.com/convert/number/decimal-to-hex.html`](https://www.rapidtables.com/convert/number/decimal-to-hex.html)
¹⁸ [`crccalc.com/`](https://crccalc.com/)

# 第 10 章

# 票务应用实现

## 引言

在本章中，我们将介绍票务应用的实现过程，包括区块链集成。我们将首先概述系统组件和应用栈，这些组件包括 CharkraUI、Next.js、Redis 数据库和 Blockfrost。接下来，我们将查看前端和离链代码，这些代码用于构建我们在`第 9 章，票务应用设计`中定义的交易。然后，我们将检查相应的链上智能合约代码、业务逻辑和验证规则。我们还将查看后端组件，例如用于缓存和查询相关区块链数据的 Redis 数据库架构。此外，我们将查看在区块链事件发生时调用的应用 API 和 Blockfrost Webhooks。最后，我们将运行应用程序的端到端演示。

## 结构

在本章中，我们将讨论以下主题：

*   应用栈
*   应用资源
*   前端组件
*   智能合约
*   后端组件
*   应用演示
*   区块链优势

## 应用栈

在我们的票务应用中，我们需要能够对任意数量包含待售票务的交换（swaps）进行搜索和过滤。如果将交换详情存储在带有索引的应用程序数据库中以便快速访问，就可以高效地实现这一目标。然而，事实来源始终是区块链，数据库仅仅是区块链数据的缓存副本。通过引入数据复制，我们必须确保当交易提交到区块链时，数据库能够进行相应的更新。`图 10.1`显示了如何针对本地应用程序数据库进行交换查询，该数据库会随着新的相关区块链数据通过 Blockfrost webhook 传入而持续更新。

![](img/Figure-10.1.jpg)

**图 10.1：** 系统组件

Next.js 将用作应用程序服务器框架，用于构建 HTML 和 JavaScript 组件。应用程序还将使用 Redis 数据库，带有 `full stack JSON` 和搜索模块，以实现快速的内存数据库存储和检索。为了改进错误处理和故障排除，所有交易将通过 Blockfrost API 提交。这种方法允许我们在区块链事件发生时调用应用 API 和 Blockfrost webhooks。

## 应用资源

应用程序使用 Next.js 目录结构，见`图 10.2`。

注：`图 10.1`显示了如何针对本地应用程序数据库进行交换查询，该数据库会随着新的相关区块链数据通过 Blockfrost webhook 传入而持续更新。

![](img/Figure-10.2)

**图 10.2:** Next.js 目录结构

## 通用

`common` 文件夹包含客户端 JavaScript 代码。该目录包含以下文件：

*   `metadata.ts`: 用于创建元数据
*   `network.ts`: 用于与网络交互
*   `orders.ts`: 用于订单计算
*   `types.ts`: 定义数据类型
*   `utils.ts`: 工具函数

## 组件

所有的 React 函数组件都位于此文件夹中，用于构建应用程序的弹出窗口。

## 配置

`config` 文件夹定义了设置、主题和标记。

## 初始化
