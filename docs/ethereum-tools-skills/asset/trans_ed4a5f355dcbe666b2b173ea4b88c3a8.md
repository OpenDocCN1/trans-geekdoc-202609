

# 以太坊：工具与技能

版权所有 © 2018 SitePoint Pty. Ltd.

电子书 ISBN：978-1-925836-02-8

- **封面设计：** Alex Walker
- **项目编辑：** Bruno Škvorc

## 权利声明

保留所有权利。未经出版方事先书面许可，本书任何部分不得以任何形式或任何方式复制、存储于检索系统或传播，除非是在评论文章或书评中引用简短片段。

## 责任声明

作者和出版方已竭尽全力确保书中信息的准确性。然而，本书所含信息不提供任何担保，无论明示或暗示。因本书包含的说明，或书中描述的软硬件产品而直接或间接造成的任何损害，作者和 SitePoint Pty. Ltd. 及其经销商或分销商概不负责。

## 商标声明

本书并未在每次出现商标名称时都加以标注，而是仅以编辑方式使用这些名称，旨在造福商标所有者，绝无侵犯商标之意。

![SitePoint logo](images/00001.gif)

由 SitePoint Pty. Ltd. 出版

48 Cambridge Street Collingwood  
VIC Australia 3066  

网址：www.sitepoint.com  
邮箱：books@sitepoint.com

## 关于 SitePoint

SitePoint 专注于为 Web 专业人士发布有趣、实用且通俗易懂的内容。访问 [http://www.sitepoint.com/](http://www.sitepoint.com/) 可获取我们的博客、书籍、时事通讯、文章和社区论坛。您将找到大量关于 JavaScript、PHP、设计等方面的信息。

# 前言

随着以太坊平台的发展，支持它的工具生态系统也随之壮大。在本书中，我们将探讨一些最流行的以太坊工具，并指导您在构建自己的以太坊应用时如何使用它们。

## 谁应该阅读本书？

本书适合任何有兴趣使用以太坊平台进行开发的人阅读。如果您不熟悉区块链技术，建议在阅读本书前先阅读《以太坊开发者指南》。

## 约定说明

### 代码示例

本书中的代码使用等宽字体显示，如下所示：

```
<h1>A Perfect Summer's Day</h1>
<p>It was a lovely day for a walk in the park.
The birds were singing and the kids were all back at school.</p>
```

当需要现有代码作为上下文时，为了避免重复所有代码，将显示 `⋮`：

```
function animate() {
    ⋮
    new_variable = "Hello";
}
```

某些代码行本应在一行内输入，但因页面宽度限制不得不换行。`➥` 表示仅为排版目的而存在的换行，输入时应忽略：

```
URL.open("http://www.sitepoint.com/responsive-web-
➥design-real-user-testing/?responsive1");
```

您会注意到，我们在全书中使用了特定的排版风格来表示不同类型的信息。请留意以下项目。

### 提示、注释与警告

#### 嘿，您！

提示提供有用的小建议。

#### 嗯，打扰一下……

注释是相关但非关键的补充说明。可将其视为额外的信息片段。

#### 请务必……

……关注这些重要要点。

#### 当心！

警告会强调那些可能让您在过程中绊倒的陷阱。

# 第 1 章：Remix：为以太坊区块链开发智能合约

### 作者：Ahmed Bouchefra

**Remix 是一款 Solidity IDE，用于编写、编译和调试 Solidity 代码。[Solidity](https://solidity.readthedocs.io) 是一种高级的、面向合约的编程语言，用于编写智能合约。它受 C++、Python 和 JavaScript 等流行语言的影响。**

`IDE` 代表集成开发环境，是一款包含一组工具的应用程序，旨在帮助程序员执行与软件开发相关的各种任务，如编写、编译、执行和调试代码。

在开始使用 Remix 开发智能合约之前，请确保您熟悉一些基本概念。特别是，请阅读这些关于[区块链](https://www.sitepoint.com/blockchain-what-it-is-how-it-works-why-its-so-popular)和[以太坊](https://bitfalls.com/2017/09/19/what-ethereum-compare-to-bitcoin/)的文章。

### 什么是智能合约/Dapp？

智能合约是双方之间利用区块链技术达成的无需信任的协议，它强制双方遵守条款，而不依赖传统方式，如信任中间人或利用法律解决纠纷。

使用以太坊区块链，您可以用 Solidity 语言（以及其他语言）创建智能合约。以太坊并非唯一可用于创建智能合约的平台，但它是最受欢迎的选择，因为它从一开始就设计为支持构建智能合约。

[Dapp](http://ethdocs.org/en/latest/contracts-and-transactions/developer-tools.html#dapps) 代表**去中心化应用程序**，是一种 Web3 应用程序，其前端可用 JavaScript、HTML、CSS 等传统语言编写，智能合约（作为后端代码）则运行在区块链上。因此，您可以简单地将 Dapp 视为前端加上相关的区块链智能合约。

与部署在区块链上的智能合约不同，Dapp 的前端既可以托管在 CDN 等中心化服务器上，也可以托管在 [Swarm](http://ethdocs.org/en/latest/contracts-and-transactions/developer-tools.html#swarm) 等去中心化存储上。

## 访问 Remix IDE

您可以通过不同方式访问 Remix IDE：在线访问、通过 Chrome 等 Web 浏览器、从本地安装的副本，或从 Mist（以太坊 Dapp 浏览器）启动。

### 使用浏览器版 Remix IDE

您无需任何特殊安装，即可从 Web 浏览器访问 Remix IDE。访问 [https://remix.ethereum.org/](https://remix.ethereum.org/)，您将看到一个完整的 IDE，包含代码编辑器和各种面板，用于编译、运行和调试智能合约。您将获得一个默认的示例 *Ballot*（投票）合约供您练习。

![Remix IDE](images/00002.jpeg)

### 从 Mist 启动 Remix IDE

您可以通过点击 *Develop*（开发），然后选择 *Open Remix IDE*（打开 Remix IDE）从 Mist 启动 Remix IDE。Remix 将在新窗口中打开。如果这是您首次运行该 IDE，将会看到一个简单的示例 *Ballot* 合约。

要熟悉 Mist，请参阅[这篇文章](https://bitfalls.com/2018/02/12/explaining-ethereum-tools-geth-mist/)。

### 运行您自己的 Remix IDE 副本

您也可以通过执行以下命令运行自己的 Remix IDE 副本：

```
npm install remix-ide -g
remix-ide
```

您需要安装 Node.js 和 npm。更多信息请查看此 [GitHub 仓库](https://github.com/ethereum/remix-ide)。

## Remix 面板

了解如何打开 Remix IDE 后，现在让我们看看构成该 IDE 的各个面板。

### 文件浏览器

文件浏览器提供了一个视图，显示存储在浏览器存储中的已创建文件。您可以通过右键点击文件，然后从上下文菜单中选择相应操作来重命名或删除文件。

![上下文菜单选项](images/00003.jpeg)

请注意，文件浏览器默认使用浏览器的本地存储，这意味着如果您清除存储或操作系统自动清除存储，可能会丢失所有文件。对于高级工作，建议使用 [Remixd](https://github.com/ethereum/remixd) —— 一个 Node.js 工具（可通过 npm `npm install -g remixd` 获取），它允许 Remix IDE 访问您计算机的文件系统。

现在让我们看看浏览器顶部按钮可以执行的不同操作。

![Remix 按钮](images/00004.jpeg)

#### 在 Remix 中创建/打开文件

