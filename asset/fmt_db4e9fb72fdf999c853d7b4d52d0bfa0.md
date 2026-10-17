
## 第 8 章 设置开发环境

2. 点击 MetaMask 应用右上角的彩色圆圈，从下拉菜单中选择 "Import Account" 选项，如图 8-16 所示。

![](img/00118.jpg)

FIGURE 8-16: The Import Account option in MetaMask.

3. 在新出现的对话框中，粘贴 Ganache 工作区中账户的私钥，然后点击 "Import" 按钮，如图 8-17 所示。图 8-18 显示已导入的账户在 MetaMask 中。注意我们重命名了该账户。

重命名你的导入账户，以便记住它是本地 Ganache 账户。我们将导入账户重命名为 "Ganache HV 1"，因为它与原始账户名称相关。要在 MetaMask 中重命名账户，点击账户名称右侧的垂直省略号，选择 "Account Details"，然后点击账户名称旁的铅笔图标，重命名账户，最后点击复选框确认更改。 (更多详情请参见第 7 章。)

恭喜！你已成功将本地 Ganache 账户导入 MetaMask 钱包。

![](img/00133.jpg)

![](img/00129.jpg)

图 8-17：导入一个账户到你的 MetaMask 钱包。

图 8-18：在 MetaMask 中成功导入并重命名的账户。

![](img/00011.jpg)

如果你在新导入的 Ganache 账户中看到一个奇怪的余额，别慌。图 8-18 显示，即使已连接到正确的网络，我们仍然拥有 196163 ETH 的余额（！），这远超 Ganache 工作区中显示的 100 测试 ETH 余额。（参见图 8-14。）

如第 7 章所述，你必须在 MetaMask 中处于正确的网络，才能在你的每个账户中看到相应的测试 ETH 或真实 ETH。例如，图 8-19 显示，当我们切换到以太坊主网时，我们的 Ganache HV 1 账户显示 0 ETH 的余额。

图 8-19：在主网查看我们的 Ganache HV 1 账户时的 0 ETH 余额。

你现在可以像处理钱包中加载的其他账户一样，通过 MetaMask 发送交易。你尚未准备好提交一个能创建新合约账户的交易，但你可以按照以下步骤在本地 Ganache 工作区中转移资金：

![](img/00023.jpg)

1. 在“账户”选项卡中，高亮显示 Ganache 工作区中的一个不同账户，然后右键单击以复制公共账户地址，如图 8-20 所示。

图 8-20：在 Ganache 工作区中复制账户地址。

2. 按照下面列出的常规步骤，通过 MetaMask 发送交易（如图 8-21 所示）：

a. 选择合适的账户：我们这里使用 Ganache HV 1 账户。

b. 确保你处于正确的网络：我们使用名为 Handsomely-Vessel 的自定义网络。

c. 点击“发送”按钮。

3. 粘贴你在步骤 1 中从 Ganache 工作区复制的地址（如图 8-22 所示），然后选择要转移的数量。（我们选择了 5 测试 ETH。）

4. 点击“下一步”按钮，然后在随后的页面上点击“确认”按钮。正如我们在早前的警告中所述，这里显示的数字可能看起来很奇怪，这是因为 MetaMask 与本地 Ganache 环境之间存在未同步的问题。

由于交易和区块会在本地 Ganache 区块链上自动挖掘，提交的交易状态会迅速从“待处理”变为“已完成”，如图 8-23 所示。

图 8-23：MetaMask 中的交易确认。

5. 检查 Ganache 工作区中的账户余额。注意到 5 测试 ETH 已从第一个账户转移到第二个账户，如图 8-24 所示。

图 8-24：Ganache 工作区中更新后的账户余额。

![](img/00094.jpg)

### 在 Remix IDE 与 MetaMask 钱包之间同步

在本节中，你将探索 Remix，以便最终能够编译和部署智能合约——无论是在此本地环境、测试网络还是主网。

要在 Remix 中导航，请按照以下步骤：

1. 访问 [`remix.ethereum.org`](https://remix.ethereum.org/)。确保输入`http://`（不带 `s`），而不是`https://`（带 `s`），否则 Remix 无法访问 MetaMask。

2. 点击左侧工具栏上的以太坊图标，如图 8-25 所示。

图 8-25：Remix 主页。

3. 在“部署与运行交易”对话框的环境下拉菜单中选择“注入的 Web3”，如图 8-26 所示。

4. 登录你的 MetaMask 钱包。如果你已安装其他钱包浏览器扩展程序（如 Dapper），可能会出现问题。我们建议在继续本分步指南时，禁用其他扩展程序，只保留 MetaMask。

![](img/00110.jpg)

图 8-26：部署与运行交易对话框。

5. （可选）若要关闭可能导致问题的浏览器扩展程序，请执行以下操作：

a. 在浏览器工具栏上右键单击想要禁用的扩展程序图标。

b. 选择“管理扩展”。

c. 在随后的页面上，使用图 8-27 中所示的切换按钮关闭所需的浏览器扩展程序。

6. 在 MetaMask 中，选择你想用的网络和账户。图 8-28 显示我们在选择 Ropsten 测试网络以及在第 7 章中演示如何创建和资助测试账户时使用的测试账户。

图 8-29 显示我们在选择我们的 Handsomely-Vessel 自定义网络以及本章前面已导入并重命名的 Ganache HV 1 账户时的 Remix 环境。

恭喜！你现在拥有一个完全功能且自包含的解决方案栈，可以开始开发和部署智能合约。

![](img/00124.jpg)

![](img/00138.jpg)

图 8-27：禁用特定浏览器扩展。

图 8-28：在 Ropsten 测试网络上的我们的测试账户。

图 8-29：在 Handsomely-Vessel 自定义网络上的 Ganache HV 1 账户。

## 第 9 章 部署你的第一个智能合约

本章将带你逐步完成开发、编译和部署你的第一个智能合约的过程。在此之前，我们想快速介绍智能合约语言，描述智能合约的组成部分。我们还想提及智能合约库，这些在第 10 章和第 11 章中将变得更加重要。

本章代表了你在构建自己的非同质化 ERC-721 代币之前需要的最后实践准备。我们强烈建议你按顺序阅读整个章节，以便更全面地理解智能合约的基本特性以及我们在选择过程中所依据的逻辑。如果你感到急躁，也可以直接跳到最后部分“准备起飞：发射你的智能合约”。

要完成本章，你需要先安装并设置好 MetaMask 钱包。（参见第 2 章和第 4 章。）你还需要设置主网、测试网和本地账户，并需要设置本地 Ganache 环境并在此基础上在 MetaMask 中配置对应的自定义网络。（参见第 7 章和第 8 章。）最后，你需要设置 Remix-IDE 浏览器（[`remix.ethereum.org`](https://remix.ethereum.org/)）并将其与 MetaMask 钱包同步。（第 8 章可帮助你完成此任务。）

### 使用智能合约语言

要创建一个功能性的智能合约，你本质上是在向以太坊网络提交字节码的交易（不带目标地址），从而创建一个合约账户。由于[字节码](https://en.wikipedia.org/wiki/Bytecode)是以十六进制格式编写的机器级代码，学习和解释它很困难，你需要使用一种受支持且更像人类的语言——一种现有编译器可以将其翻译成字节码的语言——来编写你的智能合约源代码。

好在，你可以从几种正在积极维护的语言中进行选择。在 Remix IDE 中，我们选择它作为分步指南，其中包含的编译器设计用于轻松切换 Solidity 和 Yul 语言：

- `Solidity`: Solidity 编程语言是专门用于在以太坊虚拟机 (EVM) 上实现智能合约而设计的。它仍然是以太坊上智能合约开发者主要使用的语言，其使用已扩展到其他竞争平台。

  在编程语言的分类中，Solidity 被视为高级语言：它更易于人类理解和调试，但记忆效率较低，需要编译才能转换为执行机器可以理解的指令。

- `Yul`: 新的编程语言 Yul 需要更深入地掌握和理解操作码（低级、机器语言指令）才能有效使用。Yul 被视为中级语言。

在你选择一种语言并编写合约源代码后，你需要将代码编译，生成以下元素：

- `字节码`: 字节码是一组完全以十六进制格式指定的指令，可在 EVM 上运行。字节码是机器代码，在编程语言的分类中位于最低层，对人类直接解释最为困难。

- `操作码`: 当你更深入了解智能合约开发领域时，你会发现许多程序员引用操作码（即组装语言中的命令）。操作码指令对应于字节码所传达的内容，但提供可读的操作代码，告诉处理器应执行什么。在编程语言的分类中，组装语言被视为低级语言，它仅比机器码高一层。

- `ABI`: 编译器还会创建相应的应用二进制接口 (ABI)，这是终端应用程序与合约数据和函数进行交互所必需的。

我们选择 Solidity，因为它是使用最广泛且最易上手的语言。使用 Solidity 时，你还可以访问许多预建库，这些库提供经过精心开发和验证的代码，供你构建。我们在本章后面的“使用智能合约库：无需重新发明轮子”一节中会对预建库进行更详细说明。

#### 从源代码到字节码

考虑以下用 Solidity 编写的简单智能合约代码：

```
pragma solidity 0.8.6;

contract LittleBear {

string public msg = “Hello Little Bear (a.k.a.

Maddie)!”;

}
```

当这段 Solidity 源代码被编译时，你会得到以下机器级字节码块：

```
608060405234801561001057600080fd5b506004361061002b5760003560e01c80636b473fca14610030575b600080fd5b61003861004e565b6040516100459190610115565b60405180910390f35b6000805461005b90610186565b80601f016020809104026020016040519081016040528092919081815260200182805461008790610186565b80156100d45780601f106100a9576101008083540402835291602001916100d4565b820191906000526020600020905b8154815290600101906020018083116100b757829003601f168201915b505050505081565b60006100e782610137565b6100f18185610142565b935061010181856020860161015365b61010a816101e7565b840191505092915050565b6000602082019050818103600083015261012f81846100dc565b905092915050565b600081519050919050565b600082825260208201905092915050565b60005b838110156101715780820820151818401526020810190506101565b83811115610180576000848401525b50505050565b6000600282049050600182168061019e57607f821691505b602082108114156101b2576101b16101b8565b5b50919050565b7f4e487b7100000000000000000000000000000000000000000600052602260045260246000fd5b6000601f19601f830116905091905056fea264697066735822122067b6da38f6dde0621c9c49d1785ec9d01d5d423d6d5f4aca74e7b3f8ffa4c18f64736f6c63430008060033
```

以下是对应的操作码片段：

```
PUSH1 0x80 PUSH1 0x40 MSTORE CALLVALUE DUP1 ISZERO PUSH2 0x10 JUMPI PUSH1 0x0 DUP1 REVERT JUMPDEST POP PUSH1 0x4 CALLDATASIZE LT PUSH2 0x2B JUMPI PUSH1 0x0 CALLDATALOAD PUSH1 0xE0 SHR DUP1 PUSH4 0x6B473FCA EQ PUSH2 0x30 JUMPI JUMPDEST PUSH1 0x0 DUP1 REVERT JUMPDEST PUSH2 0x38 PUSH2 0x4E JUMP JUMPDEST PUSH1 0x40 MLOAD PUSH2 0x45 SWAP2 SWAP1 PUSH2 0x115 JUMP JUMPDEST PUSH1 0x40 MLOAD DUP1 SWAP2 SUB SWAP1 RETURN JUMPDEST PUSH1 0x0 DUP1 SLOAD PUSH2 0x5B SWAP1 PUSH2 0x186 JUMP JUMPDEST DUP1 PUSH1 0x1F ADD PUSH1 […]
```

最后，以下是对应的 ABI，为想要与该智能合约交互的终端应用程序提供路线图：

```
{
“inputs”: [],
“name”: “msg”,
“outputs”: [
{
“internalType”: “string”,
“name”: ””,
“type”: “string”
}
],
“stateMutability”: “view”,
“type”: “function”
}
```

你现在可能已经明白，为什么我们更倾向于使用高级且更像人类的语言来编写智能合约代码！

#### 智能合约的关键要素

智能合约的核心由存储在以太坊区块链上合约账户地址的函数和数据组成。此外，当执行交易以访问智能合约中的函数时，状态变更可以记录到区块链上，而无需存储在合约账户中（存储在合约账户中成本更高）。本节将解析智能合约的关键要素——即其数据、函数和事件日志。

##### 数据

Solidity 是一种静态类型编程语言，这意味着在编译前必须在源代码中明确指定变量的类型（以及通常大小）。

变量可以作为合约数据存储在存储区（storage），这些变量被称为状态变量。另一方面，你可能还会有临时变量，仅用于中间计算，在迭代之间无需保留；这些变量称为内存变量。

The information stored in `state variables` can also be accessed by other smart contracts if they’re declared as public `state variables`.

Otherwise, the information is considered private and is accessible only within the smart contract in which it is stored (though it can still be viewed by anyone because private `state variables` are stored on the public blockchain).

Whether the stored data is public or private, only the contract in which the data is stored can alter the value of its `state variables`.

##### Functions

Smart-contract functions are where the action is. For instance, functions can be used to perform calculations, set new values for state variables, retrieve data from elsewhere on the blockchain, send ETH to other addresses, or call other functions. Functions fall into these three broad categories:
