
¹⁶ [`preprod.cexplorer.io/datum/a5b09d918a1fd954e14ca4609ae4216ec3cad02fda81b70a9eb87c5ab9a71854`](https://preprod.cexplorer.io/datum/a5b09d918a1fd954e14ca4609ae4216ec3cad02fda81b70a9eb87c5ab9a71854)

¹⁷ [`plutus-apps.readthedocs.io/en/latest/reference/cost-model-parameters.html`](https://plutus-apps.readthedocs.io/en/latest/reference/cost-model-parameters.html)

¹⁸ Andre Knispel, et al., “A Formal Specification of the Cardano Ledger integrating Plutus Core,” 6.

# 第 5 章

## 交易构建器

### 简介

本章将结合我们对链上 Plutus 脚本的知识，以及如何使用链下代码将 Ada 锁定到智能合约中。我们将了解 Cardano 钱包，它是与区块链和智能合约交互的入口。接下来，我们将介绍一些有助于构建和提交交易的工具，例如 `Demeter.run`。然后，我们将使用两种流行的方法构建一个简单的归属智能合约：Helios 和 Lucid + Aiken。

### 结构

在本章中，我们将讨论以下主题：

*   交易生命周期
*   钱包
    *   助记词
    *   测试网水龙头
    *   地址派生
    *   质押
    *   CIP-30
*   Demeter.run
*   链下代码示例
    *   Helios
    *   Lucid + Aiken

### 交易生命周期

在上一章中，我们了解了 Cardano 节点和账本如何评估 Plutus 脚本。本章将重点介绍如何构建并提交包含 Plutus 脚本的交易。构建交易的过程包括组装 UTXO 输入和输出、附加要运行的脚本，以及在必要时添加兑换凭证、数据和元数据。交易组装完成后，必须对其进行签名，并将签名作为见证包含在内。图 5.1 展示了构建、签名、序列化交易并将其提交到网络的链下步骤。

![](img/Figure-5.1.jpg)

**图 5.1：** 交易生命周期

### 钱包

在加密货币中，钱包是与区块链交互的用户界面。钱包通常允许用户创建账户，账户是锁定在公钥地址上的 UTXO 集合。这种**账户抽象**有助于用户直观地理解账户余额和交易历史等熟悉概念。许多钱包还允许用户选择质押池并注册其质押密钥以收集质押奖励。表 5.1 按字母顺序列出了 Cardano 网络上的部分钱包提供商。

| **名称** | **全节点** | **硬件钱包支持** | **移动端应用** | **开源** |
| --- | --- | --- | --- | --- |
| `Daedalus` | ✔ | ✔ | ✖ | ✔ |
| `Eternl` | ✖ | ✔ | ✔ | ✖ |
| `Flint` | ✖ | ✔ | ✔ | ✔ |
| `GameChanger` | ✖ | ✖ | ✖ | ✔ |
| `GeroWallet` | ✖ | ✔ | ✖ | ✖ |
| `Lace` | ✖ | ✔ | ✖ | ✔ |
| `Ledger` | ✖ | ✔ | ✖ | ✔ |
| `Nami` | ✖ | ✖ | ✖ | ✔ |
| `NuFi` | ✖ | ✔ | ✖ | ✖ |
| `Typhon` | ✖ | ✔ | ✖ | ✔ |
| `VESPR` | ✖ | ✖ | ✔ | ✔ |

**表 5.1：** Cardano 钱包¹

**全节点：** 包含完整 Cardano 节点的钱包，不使用任何第三方服务在区块链上查找交易。

**硬件钱包支持：** 支持使用硬件设备对交易进行签名的钱包。

**移动端应用：** 在 iOS 或 Android 设备上拥有原生移动应用的钱包。

**开源：** 钱包的开源代码可在 GitHub 上获取。

### 助记词

要使用钱包创建账户，必须创建新的助记词或导入现有助记词。如果回顾第 3 章，交易，签名交易需要私钥。为了创建这个私钥，钱包通常使用**助记词**来生成随机私钥。这是一个两步过程：首先，使用一组助记词或单词组来创建随机种子²；然后，使用该随机种子派生公钥和私钥对³。

### 测试网水龙头

Cardano 通常有两个测试网，用于在主网上线前进行端到端测试⁴。发送和接收资金时，请注意你连接的是哪个网络。

*   **预览测试网：** 纪元缩短为 1 天，且比主网分叉领先至少 4 周。
*   **预生产测试网：** 该网络用于主网发布的候选版本测试。它尽可能模拟生产环境，是更稳定的测试网网络。

我们将使用测试网水龙头获取测试 Ada 并发送到我们的钱包地址。本书中我们将使用 `Eternl` 钱包，图 5.2 展示了如何获取地址以接收资金。

![](img/Figure-5.2.jpg)

**图 5.2：** Eternl 钱包接收资金

复制地址并粘贴到 [`docs.cardano.org/cardano-testnet/tools/faucet/`](https://docs.cardano.org/cardano-testnet/tools/faucet/) 的测试网水龙头表单中，如图 5.3 所示。

![](img/Figure-5.3.jpg)

**图 5.3：** 测试网水龙头请求

选择“`Request Funds`”，你应该会看到包含交易哈希的“`Success`”消息，可使用该哈希在 [`preprod.cexplorer.io/`](https://preprod.cexplorer.io/) 上验证状态。

![](img/Figure-5.4.jpg)

**图 5.4：** 测试网水龙头已提交

10–60 秒后，你应该会在 `Eternl` 钱包中看到 10,000 测试 Ada（`tAda`）。

![](img/Figure-5.5.jpg)

**图 5.5：** Eternl 钱包账户摘要

### 地址派生

确定性分层（HD）钱包（如 `Eternl`）遵循 CIP-1852⁵ 规范中的派生路径：

`m / purpose' / coin_type' / account' / role / index`

在图 5.5 中，我们可以看到接收地址的派生路径为：

`m/1852'/1815'/0'/0/0`

表 5.2 解释了派生路径的每个元素：

| **名称** | **值** | **备注** |
| --- | --- | --- |
| Purpose | 1852 | 规范名称（例如 CIP-1852） |
| Coin Type | 1815 | 每种加密货币不同的值（例如 Ada Lovelace 诞辰年份） |
| Account | 0 | 允许创建独立的钱包账户 |
| Role | 0 | 0 = 外部链（接收付款）<br>1 = 内部链（找零地址）<br>2 = 质押密钥 |
| Index | 0 | 从 0 开始的地址索引 |

**表 5.2：** 派生路径

你可以使用 HD 钱包为同一个私钥创建不同的地址来接收付款（和找零）。然而在实践中，通常首选“`single address mode`”（单地址模式），即重复使用同一个地址。为每笔交易创建新地址有助于匿名化，使其无法关联到钱包账户。但在 Cardano 中，一旦为钱包地址注册了质押密钥，该地址的所有交易都可以通过质押密钥关联。为接收和找零地址使用多个地址会增加 dApp 的复杂性，这就是为什么一些钱包仅支持单地址模式。图 5.6 展示了如何将 `Eternl` 切换（或保持）为单地址模式。

![](img/Figure-5.6.jpg)

**图 5.6：** Eternl 单地址模式

### 质押

Cardano 网络最重要的功能之一是能够轻松地从钱包进行质押。这被称为流动性非托管质押，这也是 Cardano 网络拥有高质押率的原因，这有助于其安全性和去中心化。要进行质押，用户进入质押标签页，选择一个质押池，并选择“`Delegate`”，如图 5.7 所示。

![](img/Figure-5.7.jpg)

**图 5.7：** 质押池委托

接下来，用户必须签署一笔交易，将质押密钥注册和质押池委托证书提交到网络，如图 5.8 所示。

![](img/Figure-5.8.jpg)

**图 5.8：** 质押池注册

当包含质押密钥注册证书和质押池委托证书的交易被确认后，用户将根据第 2 章，密码学和共识算法概述中讨论的 Ouroboros 生命周期接收质押奖励。

### CIP-30

为了让 dApp 能够连接到浏览器扩展钱包（如 `Eternl`），dApp 应遵循 CIP-30 标准⁶。该标准描述了一种基于网页的通信桥接，允许网页与浏览器扩展钱包交互。这是通过将 JavaScript 代码注入到正在渲染的网页中来实现的。然后，网页或 dApp 可以调用具有预定义公共方法的 JavaScript 代码，以从钱包检索和提交数据。在本章后面的链下代码示例中，我们将看到如何使用 CIP-30 与钱包交互。

## Demeter.run

### 环境搭建

在深入第一个链下智能合约示例之前，我们必须快速启动并运行一个环境。`Demeter.run` 可以提供帮助。它是一个完全托管的解决方案，可以启动各种 Cardano 环境。Cardano 完全开源，因此你可以在本地或云环境中安装并运行 Cardano 组件。在本书中，我们将使用 `Demeter.run`，以便更多地关注概念和应用逻辑，减少在环境搭建和配置上花费的时间。

要为本书中的示例设置环境，请遵循以下步骤：

1. 访问 [`demeter.run/`](https://demeter.run/)
2. 开始免费试用。
3. 注册/登录。
4. 创建组织。
5. 创建一个新项目，如图 5.9 所示。

   ![](img/Figure-5.9.jpg)

   **图 5.9：** Demeter.run 新建项目

6. 你可以从免费层级开始，但根据使用情况，你可能需要升级到付费层级或购买额外的 DCU。每个购买的计划都与特定项目关联。

   ![](img/Figure-5.10.jpg)

   **图 5.10：** Demeter.run 项目视图

7. 选择 `ADD APIS` `&` `SERVICES`，如图 5.10 所示。
8. 向下滚动并创建一个新工作区。
9. 选择“`Clone an existing repository`”。
10. 在文本框中粘贴 GitHub URL：`https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts.git`
11. 保持分支默认为 main。
12. 选择 Node.js 作为工具链。
13. 选择工作区 `small` 规格。
14. 选择 `Pre-prod` 网络。
15. 选择页面底部的 `Create`。
16. 如果向上滚动到页面顶部，你将看到工作区正在被配置并最终完成，如图 5.11 所示。

    ![](img/Figure-5.11.jpg)

    **图 5.11：** Demeter.run 项目配置

17. 向下滚动页面并 `EDIT` Exposed Ports。
18. 名称输入 `Next.js`。
19. 端口号输入 `3000`。
20. 选择 `Expose`。
21. 滚动回页面顶部并选择 VS Code 图标以启动 VS Code 编辑器。
22. 授权受信任访问，以便你可以使用 VS Code Web 编辑代码。
23. 选择 `Terminal` -> `New` `Terminal` 创建一个终端窗口以在命令行执行命令，如图 5.12 所示。

    ![](img/Figure-5.12.jpg)

    **图 5.12：** Visual Studio Code Web

### 链下示例

本节将展示构建简单归属智能合约链下代码的两种方法。每种方法都将使用 Next.js 作为应用框架。有关 Next.js 的更多信息，建议读者查阅 Next.js 文档：[`nextjs.org/docs`](https://nextjs.org/docs)。

#### Helios

Helios 既是一个链下 JavaScript/TypeScript SDK，也是一个链上函数式、强类型编程语言。它优先考虑可读性和易用性，以提供最佳的开发者体验。Helios 的主要优势之一是它是一个没有第三方库的单个 JavaScript 文件，这提高了正在执行的智能合约的可审计性和透明度。

### 初始化

我们将参考 GitHub 代码示例，通过一个功能完整的端到端示例来执行你的第一个链下代码。在上一节使用 Demeter.run 工作区设置的 Visual Studio Web 中，选择一个新的终端窗口并执行以下步骤：

```
$ cd chapter_05/helios/vesting
$ nvm install 18.17.0
$ npm install
$ npm run dev
```

这将启动 Next.js 并在默认端口 3000 上运行。忽略 Visual Studio 关于端口转发的任何提示，因为我们将使用暴露的端口 URL 进行访问。你可以进入 `Demeter.run` 上的工作区并选择暴露端口的 URL 来访问 Next.js Web 应用程序。在浏览器中，你应该会看到类似图 5.13 的内容。

![](img/Figure-5.13.jpg)

**图 5.13：** Helios 交易构建器

请确保在选择钱包之前，你的 Chrome 浏览器上已安装 `Eternl`（或 Nami）浏览器钱包扩展。如果你刚安装或启用了浏览器钱包扩展，可能需要刷新页面。在 `Helios Tx Builder` 页面上，当选择钱包时，如果钱包之前未连接到该站点，钱包将提示用户确认是否允许连接到该站点。确认后，你将看到所选钱包的钱包余额，如图 5.14 所示。

![](img/Figure-5.14.jpg)

**图 5.14：** Helios 钱包选择器

### 锁定

在图 5.14 中，你会注意到屏幕底部有一个“`Lock UTXO`”按钮。该按钮将创建一个链下交易，在脚本地址锁定 2 Ada 和一个 Datum。让我们通过以下步骤查看提交链上交易所需的代码。

#### 步骤 1

要连接到浏览器钱包 API，我们将在 Next.js 应用程序中创建一个 `WalletConnector.tsx` 组件。在图 5.15 的第 52 行和第 53 行，代码首先确认浏览器插件是否存在。如果存在，则在第 56 行更新 `walletAPI` 状态变量，以便应用程序的其余部分可以访问它。

![](img/Figure-5.15.jpg)

**图 5.15：** 钱包 API⁷

#### 步骤 2

一旦我们有了 `walletAPI` 的访问权限，就可以查询钱包以获取可用的 UTXO 和找零地址，如图 5.16 第 89 行和第 92 行所示。Helios 使用一个 `walletHelper` 类来包装 `walletAPI` 对象，以提供便利函数和到 Helios 数据类型的自动转换。

![](img/Figure-5.16.jpg)

**图 5.16：** Helios WalletHelper⁸

接下来，我们必须编译 Plutus 脚本以确认脚本地址。这可以通过客户端 JavaScript 完成，如图 5.17 第 104 行所示。在第 107 行，我们可以看到从链上代码导入 Datum 结构并在链下创建适当 Datum 是多么容易。接下来，我们在第 113 行到第 117 行使用脚本地址和 Lovelace 数量（2 Ada）构建 UTXO 输出，并将 Datum 作为内联 Datum 附加。

![](img/Figure-5.17.jpg)

**图 5.17：** Helios Program⁹

#### 步骤 3

在签署交易之前的最后一步是获取当前网络参数，包括当前纪元、成本模型、最大 `tx` 大小等。这对于在构建脚本时进行内部验证是必需的。在本示例中，我们只是在脚本地址发送（锁定）Ada，因此不需要评估 Plutus 脚本。然而，我们将在下一章“验证器”中评估 Plutus 脚本。在图 5.18 第 124 行，交易被最终确定，这会平衡交易输入和输出，并在需要时将找零返回给钱包。一旦交易被最终确定，我们会请求钱包提示用户签署交易。完全签名的交易在第 131 行提交到网络。

![](img/Figure-5.18.jpg)

**图 5.18：** Helios 提交交易¹⁰

用户将被提示使用 `Eternl` 钱包签署交易，如图 5.19 所示。

![](img/Figure-5.19.jpg)

**图 5.19：** Eternl 钱包签署交易

成功使用浏览器钱包签署交易后，将显示交易哈希（`TxId`）及区块链浏览器链接，如图 5.20 所示。

![](img/Figure-5.20.jpg)

**图 5.20：** 交易成功

如果我们选择区块链浏览器链接，可以看到包含附加内联 Datum 的交易，如*图 5.21*所示。

![](img/Figure-5.21.jpg)

**图 5.21：** 区块链浏览器¹¹

#### Lucid + Aiken

Lucid + Aiken 组合的优势在于在 Cardano 社区中拥有更广泛的采用和使用。Aiken 团队也专注于卓越的开发者体验，并创建了多个实用工具来帮助智能合约开发者的生命周期。本节将重点介绍如何使用 Lucid 构建链下交易，以便在 Aiken 脚本地址锁定 UTXO。

与 Helios 不同，后者可以选择在运行时编译 Plutus 脚本，Aiken 遵循更典型的两阶段部署流程：
