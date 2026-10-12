
# 以太坊区块链智能合约创建与部署快速指南

![cover](img/cover.jpeg)

## 2. 区块链

区块链是交易的数字记录。其名称源于其结构：单个记录（称为区块）链接在一起形成单个列表（称为链）。区块链用于记录使用加密货币（如比特币）进行的交易，并有许多其他应用。

添加到区块链的每笔交易都由互联网上的多台计算机进行验证。这些系统被配置为监控特定类型的区块链交易，形成一个点对点网络。它们协同工作，确保每笔交易在被添加到区块链之前都是有效的。这种去中心化的计算机网络确保了单个系统无法向链中添加无效区块。

当新区块被添加到区块链时，它会使用由前一个区块内容生成的加密哈希值链接到前一个区块。这确保了链永远不会断裂，并且每个区块都被永久记录。由于必须先更改所有后续区块，因此有意使区块链中的过往交易难以篡改。

### 区块链用途

虽然区块链因其在比特币、莱特币和以太币等加密货币中的应用而广为人知，但该技术还有其他多种用途。例如，它支持“智能合约”，当满足特定条件时会自动执行。这为双方之间的交易提供了一个自动化的托管系统。区块链有可能允许个人之间直接付款，而无需 ACH 和电汇所需的中央清算点。它有可能极大地提高股票交易的效率，使交易能够几乎即时结算，而不再需要每笔交易等待三天或更长时间才能清算。区块链技术也可用于非金融目的。例如，星际文件系统 (`IPFS`) 利用区块链通过在互联网上链接文件来实现文件存储的去中心化。一些数字签名平台现在使用区块链来记录签名并验证文档已被数字签名。区块链甚至可以通过将内容分发链接到原始来源来保护知识产权。

区块链是一个由记录和数据组成的去中心化数据库。所有数据分散在一堆分布式计算机中，形成一个点对点 (`p2p`) 网络。这些数据库中的记录以区块的形式存储，并以安全的方式链接在一起。

比特币区块链存储专门用于跟踪不同方之间加密货币余额的数据。

以太坊区块链可以存储比比特币区块链深得多的数据。以太坊区块链允许构建去中心化应用。这些去中心化应用由智能合约定义。因此，智能合约允许个人在不依赖银行或律师等第三方的情况下，以可信、自信、自由的方式交换信息。这些以太坊智能合约存储在以太坊区块链的特殊交易中，随后可用于构建应用程序。你可以将智能合约视为去中心化的 `API`。由于智能合约存储在以太坊区块链中，它们需要像其他交易一样被验证或挖掘。因此，部署智能合约会产生少量费用。

如何编写智能合约？我们使用 `Solidity` 来实现。`Solidity` 是一种用于编写智能合约的语言。其语法类似于 `JavaScript`，并考虑到以太坊虚拟机 (`EVM`) 进行设计。因此，我们将使用 `Solidity` 在一个名为 `Remix` 的基于 Web 的 `IDE` 中创建智能合约。

## 3. Solidity 变量与类型

*   你可以在 `https://remix.ethereum.org/` 编写和测试 `Solidity` 代码。

*   以下是 `https://remix.ethereum.org` 的截图：

![](img/159551591299085953_1.jpg)

*   创建一个新合约。我将其命名为 `Coursetro`。

*   通过编写（或粘贴）以下代码开始：

```solidity
pragma solidity ^0.4.18;

contract Coursetro {

}
```

第一行定义了你将使用的 `Solidity` 版本。接下来，定义合约及其名称，并像 `JavaScript` 类一样打开它。

*   在浏览器右侧的 **Run（运行）** 选项卡下，你将看到一个 **Deploy（部署）** 按钮。点击它。你会注意到在 Deploy 按钮下方出现了一个新部分，显示合约名称和 "at 0x..."（内存地址）：

![](img/159551591230265132_2.jpg)

*   这意味着智能合约（是的，此时它还不太“智能”）存在于一个地址上。要查看此完整地址及其他信息，请在调试器中点击 **Details（详情）** 按钮，它将提供更多信息：

*   请注意有一个 `contractAddress`；这是智能合约实际驻留的位置。不，它并不在以太坊区块链上，因为目前我们只是在 `JavaScript EVM` 中工作。

*   还请注意 `gas`。每当合约被部署和修改时，以太坊网络上的节点必须验证该合约。这被称为冗余并行，作为达成共识的一种方式。`Gas` 是发送交易者（在我们的例子中是发送智能合约交易者）为验证支付的执行费用的名称。

#### 进一步阐述

引自 `etherdocs.org`：

> “Gas 是发送交易者为在以太坊区块链上进行的每项操作支付的执行费用的名称。Gas 这一名称源于这样一种观点：该费用充当加密燃料，驱动智能合约的运行。Gas 由矿工用以太币购买并执行代码。Gas 和以太币被刻意解耦，因为 Gas 单位与具有自然成本的计算单位对齐，而以太币的价格通常因市场力量而波动。两者由自由市场调节：Gas 的价格实际上由矿工决定，他们可以拒绝处理 Gas 价格低于其最低限制的交易。要获得 Gas，你只需向账户添加以太币。以太坊客户端会自动按你指定的作为交易最大支出的金额，用你的以太币购买 Gas。”

在 `Solidity` 中，你通过首先指定其类型来定义变量。还有哪些其他类型？

1.  **bool**  

    这是布尔类型，返回 `true` 或 `false`。

2.  **int / uint**  

    `int` 和 `uint` 都代表整数或数值。`int` 和 `uint`（无符号整数）的主要区别在于 `int` 可以保存负数作为值。

3.  **address**

`address` 类型代表一个 20 字节的值，用于存储以太坊地址。类型为 `address` 的变量也拥有成员，包括 `balance` 和 `transfer`。

### 4. `bytes1` 到 `bytes32`

这是固定大小的字节数组。

### 5. `bytes`

动态大小的字节数组。

### 6. `string`

动态大小的字符串。

### 7. `mapping`

具有键类型和值类型的哈希表。我们将在课程后面更深入地探讨映射。

### 8. `struct`

结构体允许你定义新类型。我们稍后也将更深入地介绍这一点。

*   让我们在合约中定义一个字符串变量。也定义一下我的年龄。没有人会有负年龄，所以我们将使用无符号整数：

```solidity
pragma solidity ^0.4.18;

contract Coursetro {

    string fName = 'Gary';

    uint age = 34;

}
```

*   `Solidity` 对函数和变量都有四种可见性类型：

#### 1. `Public`

这允许你定义可以在内部调用或通过消息调用的函数或变量。

#### 2. `Private`

私有变量和函数仅对当前合约可用，对派生合约不可用。

#### 3. `Internal`

只能在内部访问的函数和变量（当前合约或派生合约）。

#### 4. `External`

可以从其他合约和交易调用的函数。它们不能在内部被调用，除非使用 `this.functionName()`。

*   **让我们给变量添加 `public` 可见性：**

```solidity
pragma solidity ^0.4.18;

contract Coursetro {

    string public fName = 'Gary';

    uint public age = 34;

}
```

*   点击**部署**，我们现在可以在右侧看到 2 个蓝色按钮，显示着我们变量的名称和关联的值。当你定义 `public` 状态变量时，`EVM` 会为它们创建 getter 函数。所以，你实际上可以点击这些按钮，它会返回值，就像调用函数一样。

*   每个智能合约都有一个构造函数。当合约被创建时会调用此构造函数。在其中，你可以定义变量的值。让我们调整代码以配合构造函数工作：

```solidity
pragma solidity ^0.4.18;

contract Coursetro {

    string public fName;

    uint public age;

    function Coursetro() public {

        fName = 'Gary';

        age = 34;

    }

}
```

*   变量可以声明为 `constant`。顾名思义，这些是值恒定不变的变量。让我们将 `fName` 变量转换为 `constant` 变量：

```solidity
pragma solidity ^0.4.18;

contract Coursetro {

    string constant fName = 'Gary';

    uint public age;

    function Coursetro() public {

        fName = 'Gary';

        age = 34;

    }

}
```

在你的 `IDE` 中，你会注意到第 9 行旁边有一个红色的 "X"。如果你悬停在上面，会注意到它提示 "*TypeError: cannot assign to a constant variable*"（类型错误：无法赋值给常量变量）。删除第 9 行，错误就会消失。

*   到此我们的智能合约还很无聊。让我们集成一个潜在的用户交互，手动定义 Coursetro 讲师的姓名和年龄。粘贴以下代码：

```solidity
pragma solidity ^0.4.18;

contract Coursetro {

    string fName;

    uint age;

    function setInstructor(string _fName, uint _age) public {

        fName = _fName;

        age = _age;

    }

    function getInstructor() public constant returns (string, uint) {

        return (fName, age);

    }

}
```

*   我们有两个函数，`setInstructor()` 和 `getInstructor()`。`setInstructor` 接受 2 个参数，`_fName` 和 `_age`。调用后，我们将字符串 `fName` 设置为返回的 `_fName`，`age` 同理。然后，我们的 `getInstructor()` 函数被定义为 `constant`，并返回一个 `string` 和一个 `uint`。这是调用时返回 `fName` 和 `age` 变量的地方。点击**部署**，在红色的 **set Instructor** 按钮下，输入："Gary", 34 并点击按钮。接着，点击 **getInstructor()** 按钮，你会注意到它现在返回输入的值！这就是在智能合约中通过用户输入设置变量的方法。

## 4. 如何在 Windows 上设置或安装以太坊

*   在 Windows 上安装 Chocolatey。访问 `https://chocolatey.org/install` 并复制 Windows 命令，或直接运行以下命令在 Windows 上安装 Chocolatey：

```powershell
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

*   运行以下命令安装 Node.js：

```bash
choco install nodejs.install -y
```

*   或者直接从 `https://nodejs.org/en/download/` 链接下载安装程序。

*   安装 Git。要安装，请运行以下命令：

```bash
choco install git -y
```

*   或者从 `https://gitforwindows.org/` 链接下载安装程序。

*   安装 Visual Studio Code 以及 Solidity 扩展。要安装，请运行以下命令：

```bash
choco install VisualStudioCode -y
```

*   或者从 `https://www.visualstudio.com/downloads/` 链接下载安装程序。

*   在 Windows 上安装 Python。要安装，请运行以下命令：

```bash
choco install python -y
```

*   或者从 `https://www.python.org/downloads/` 链接下载安装程序。

*   打开 Visual Studio 控制台。转到扩展页面。安装 Solidity 扩展。

*   在 Windows 上安装 Ganache。从以下链接下载安装程序：`http://truffleframework.com/ganache/`

*   或者从命令行安装：

```bash
npm install -g ganache-cli
```

*   **什么是 Ganache？** 当你开发一个应用程序时，该应用程序将托管在应用服务器上。在以太坊的情况下，以太坊区块链将持有智能合约。区块链充当应用服务器。`Ganache` 是一个在本地系统上运行的模拟区块链，为你模拟以太坊区块链。它提供 GUI 或命令行界面。

*   当你运行 Ganache 时，你将看到此图像。你会看到许多以太坊地址。每个地址上都有一些以太币。

![](img/15955159139154190_1.jpg)

*   `Remix` 是一个用于构建智能合约的 `IDE`。Remix 基于 Web 的 `IDE`：`https://remix.ethereum.org`

*   使用以下命令从 Git 或 npm 安装 `IDE`：

```bash
npm install remix-ide -g
remix-ide
git clone https://github.com/ethereum/remix-ide...
cd remix-ide
npm install
npm run setupremix
npm start
```

## 5. 如何在 JavaScript VM 上编译和部署智能合约

*   打开 Remix IDE 的 URL：`https://remix.ethereum.org`

*   当我们编译 `Solidity` 代码时，会得到可以部署在以太坊区块链上的字节码。

*   开始新合约 `student.sol`

*   以下是智能合约代码：

```solidity
pragma solidity ^0.4.18;

contract student {

    string name;

    uint age;

    function setStudentDetails(string _name, uint _age) public {

        name = _name;

        age = _age;

    }

    function getStudentDetails() public view returns(string, uint) {

        return (name, age);

    }

}
```

*   我们必须将智能合约部署到区块链上。有不同的区块链可用。其中包括：主网区块链和测试网区块链。或者我们可以将智能合约部署在我们自己的区块链环境中。我们将首先使用 Remix IDE 内置的 JavaScript VM 区块链来部署智能合约。

![](img/159551591335092675_1.jpg)

### 部署智能合约到 JavaScript VM 区块链

要在 JavaScript VM 区块链上部署智能合约，我们需要一个账户。Remix 默认提供 5 个账户。但如果我们在以太坊主网部署智能合约，则必须在那里创建一个账户。

选择任意一个账户并在 JavaScript VM 上部署智能合约，点击部署。合约部署后，将部署在某个地址上。该地址由区块链分配给该智能合约。因此我们始终可以仅通过该地址引用智能合约。

在以太坊主网部署智能合约需要以太币。因为矿工会挖掘你的交易，当交易确认时，矿工必须获得手续费。

当你给变量赋值时，你改变了变量的状态，这意味着你在区块链上进行了更改，必须支付 Gas 费。有人会挖掘该交易，随后交易才会成功。`get` 函数输出变量的值且不改变区块链状态。因此它不需要挖掘，也不需要手续费。

调试器允许你调试智能合约。

## 6. 如何在 Windows 上安装 Ganache 区块链并使用它部署智能合约

本节展示如何使用 Remix 将智能合约部署到 Ganache 区块链。

### 安装 Ganache

在 Windows 上安装 Ganache。从以下链接下载安装程序：`http://truffleframework.com/ganache/`

或通过命令行安装：

```bash
npm install -g ganache-cli
```

### 什么是 Ganache？

当你开发应用程序时，该应用程序将托管在应用服务器上。在以太坊的情况下，以太坊区块链将托管智能合约。区块链充当应用服务器。`Ganache` 是一个在本地系统上运行的模拟区块链，为你模拟以太坊区块链。它提供 GUI 和命令行两种形式。

运行 Ganache 时，你将看到如下界面。你会看到许多以太坊地址，每个地址上都有一定数量的资金。

![](img/159551591363022050_1.jpg)

默认将有 10 个账户。

“区块”选项卡将显示交易区块。

“交易”选项卡将显示交易。智能合约执行的任何交易都将显示在此窗口中。

“日志”选项卡将显示所有日志。

### 连接 Ganache 与 Remix
