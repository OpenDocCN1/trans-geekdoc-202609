
# 使用 Truffle 和 OpenZeppelin 创建自定义 Token

本文介绍如何使用 Truffle 和 OpenZeppelin 创建一个扩展自 OpenZeppelin 标准 Token 的简单自定义 Token。

## 环境要求

本教程需要具备 Truffle、Ethereum 和 Solidity 的基础知识。您可以阅读 [区块链简介](https://www.sitepoint.com/blockchain-what-it-is-how-it-works-why-its-so-popular/) 和 [Ethereum 简介](https://www.sitepoint.com/ethereum-introduction/)。

您还需要在系统上安装 Node.js `5.0+` 和 npm。请参考其 [下载页面](https://nodejs.org/en/download/) 获取安装说明。

## 安装 Truffle

在终端中运行以下命令安装 Truffle：

```
npm install -g truffle
```

## 创建新的 Truffle 项目

首先创建一个新的项目目录，命名为 `simpletoken` 并进入该目录：

```
mkdir simpletoken
cd simpletoken
```

接下来，使用以下命令创建实际的项目文件：

```
truffle init
```

该命令将创建多个文件夹（如 `contracts/` 和 `migrations/`）以及部署合约到区块链时所需的文件。

接着，安装 OpenZeppelin：

```
npm install openzeppelin-solidity
```

## 创建简单的 Token 合约

在 `contracts/` 文件夹内，创建一个名为 `SimpleToken.sol` 的文件并添加以下内容：

```
pragma solidity ^0.4.23;

import 'openzeppelin-solidity/contracts/token/ERC20/StandardToken.sol';

contract SimpleToken is StandardToken {
    address public owner;

    string public name = 'SimpleToken';
    string public symbol = 'STt';
    uint8 public decimals = 2;
    uint public INITIAL_SUPPLY = 10000;

    constructor() public {
      totalSupply_ = INITIAL_SUPPLY;
      balances[owner] = INITIAL_SUPPLY;
    }

}
```

这是我们将要扁平化和调试的合约。我们导入了 OpenZeppelin 的 `StandardToken.sol` 合约，并使用 `is` 操作符声明了继承自 `StandardToken.sol` 的 `SimpleToken` 合约。

我们的合约将继承一系列变量和函数，这些需要被重写以实现自定义。

为了完成 Truffle 项目，在项目的 `migrations/` 文件夹内创建一个名为 `2_deploy_contract.js` 的文件并添加以下内容：

```
var SimpleToken = artifacts.require("SimpleToken");
module.exports = function(deployer) {
    deployer.deploy(SimpleToken);
};
```

使用该文件，我们可以将智能合约部署/迁移到区块链，但本例中并不需要此步骤，因为我们将在扁平化后使用 Remix IDE 部署智能合约。

## 使用 Truffle Flattener 扁平化合约

[Truffle Flattener](https://www.npmjs.com/package/truffle-flattener) 是一个 npm 工具，用于将 Truffle 下开发的 Solidity 文件及其所有依赖按正确顺序扁平化或合并。

首先，全局安装 `truffle-flattener`：

```
npm install -g truffle-flattener
```

接下来，在 Truffle 项目中运行以下命令扁平化 `SimpleToken.sol` 文件：

```
truffle-flattener contracts/SimpleToken.sol > FlattenedSimpleToken.sol
```

`truffle-flattener` 将扁平化后的合约输出到标准输出（终端）。使用 `>` 操作符将输出保存到当前文件夹下的 `FlattenedSimpleToken.sol` 文件中。

## 使用 Remix IDE 编译和部署合约

您可以从 `FlattenedSimpleToken.sol` 文件获取扁平化后的智能合约。打开文件并复制其内容。

接着，打开 Remix IDE（[https://remix.ethereum.org](https://remix.ethereum.org)），将扁平化后的智能合约粘贴到 IDE 中的新文件里。

如果出现 *Mock compiler : Source not found* 错误，请确保在 *Settings tab > Solidity version pane > select new compiler version dropdown* 中选择了更新的编译器版本。

如果 *Auto compile* 被禁用，请在 *Compile* 面板点击 *Start to compile* 按钮。

接下来，激活 *Run* 面板。首先确保 *Environment* 选择了 *JavaScript VM*。在第二个下拉框中选择 *SimpleToken* 合约，然后点击下拉框下方的红色 *Deploy* 按钮。

您的合约已部署并在 JavaScript VM 上运行，该虚拟机模拟了区块链环境。现在我们可以开始以不同方式对其进行调试。

# 调试自定义 Token 合约

为了演示如何调试合约，我们将首先引入一些错误。

在 Remix IDE 中，根据用例不同，有两种方式开始调试智能合约。

当您首次部署智能合约或随后执行任何交易时，终端会记录一些信息，您可以点击日志旁边的白色 *Debug* 按钮开始调试。让我们看看实际操作。

## 使用 assert()

SafeMath 是 OpenZeppelin 用于带安全检查的数学运算的库，检查失败会抛出错误。`sub(a,b)` 函数用于两数相减并返回无符号数。第一个参数必须大于第二个参数以保证结果为正数。该函数使用 `assert()` 函数强制执行此规则。以下是 `sub` 函数的代码：

```
function sub(uint256 a, uint256 b) internal pure returns (uint256) {
    assert(b <= a);
    return a - b;
}
```

只要您提供的 `a` 和 `b` 值满足条件 `b <= a`，执行就会继续而不会出现问题；但一旦您提供的 `b` 值大于 `a`，`assert()` 函数将抛出如下错误：

```
VM error: invalid opcode. invalid opcode The execution might have thrown. Debug the transaction to get more information.
```

因此，让我们在 `SimpleToken` 合约的构造函数中添加一个带有错误参数的 `sub()` 调用：

```
constructor() public {
    totalSupply_ = INITIAL_SUPPLY;
    balances[owner] = INITIAL_SUPPLY;
    SafeMath.sub(10, 1000);
}
```

如果您重新部署合约，终端将显示 invalid opcode 错误：

![Invalid opcode error](images/00038.jpeg)

点击 *Debug* 按钮后，您将进入 *Debugger* 面板，可以开始调试代码。

![The debugger panel](images/00039.jpeg)

在代码编辑器中，第一行/指令会被高亮显示，标记当前所在位置。

![First line/instruction highlighted](images/00040.jpeg)

点击 *Step over forward* 按钮逐步执行代码。

![Step over forward button](images/00041.jpeg)

您也可以使用 *Jump to exception* 按钮直接跳转到异常处。

![Jump to exception button](images/00042.jpeg)

无论使用哪种方式，调试器都会定位到导致问题的代码并停下。

![Stopping on the problem](images/00043.jpeg)

您可以在当前步骤检查局部变量的状态。

![local variables at the current step](images/00044.jpeg)

*Solidity Locals* 面板显示与当前上下文关联的局部变量。

通过源代码和 *Solidity Locals*，您可以得出结论：问题源于 `assert()` 方法以及 `b` 的值大于 `a` 的值。

您可以使用 *stop debugging* 按钮停止调试。

![Stop debugging button](images/00045.jpeg)

查看调试器的其他面板也很有价值。

### Instructions（指令）

![Instructions panel](images/00046.jpeg)

*Instructions* 面板显示被调试合约的字节码。当前步骤的字节码会被高亮显示。

### Solidity State（Solidity 状态）

![Solidity state](images/00047.jpeg)

*Solidity State* 面板显示当前被调试合约的状态变量。

### Low Level Panels（底层面板）

![Low level panels](images/00048.jpeg)

这些面板显示执行的底层信息，如步骤详情、内存、堆栈和函数返回值。

## 结论
