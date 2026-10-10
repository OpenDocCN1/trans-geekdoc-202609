

# Remix IDE 指南

## 文件浏览器

您可以使用左上角带有 `+` 图标的第一个按钮，在浏览器本地存储中创建一个新文件。随后，您可以在弹出的对话框中提供名称并按下 `OK`。

使用左上角的第二个按钮，您可以将计算机文件系统中现有的 Solidity 文件打开到 Remix IDE 中。该文件也将存储在浏览器的本地存储中。

### 将浏览器文件发布为 GitHub Gist

使用左上角的第三个和第四个按钮，您可以将 IDE 中的文件发布为公开的 GitHub Gist。

### 将文件复制到另一个 Remix IDE 实例

使用左上角的第五个按钮，您可以通过提供目标实例的 URL，将文件从本地存储复制到另一个 Remix 实例中。

### 连接到本地文件系统

如果您正在运行 `Remixd` 工具，可以使用最后一个按钮将 Remix IDE 连接到您的本地文件系统。

## Solidity 代码编辑器

Solidity 代码编辑器提供了一个编写代码的界面，具有语法高亮、自动重新编译、自动保存等众多功能。您可以打开多个标签页，也可以使用左上角的 `+/-` 按钮增加或减小字体大小。

![Solidity Code Editor](images/00005.jpeg)

## 终端

编辑器下方的终端窗口集成了一个 JavaScript 解释器和 `web3` 对象。您可以在当前上下文中执行 JavaScript 代码，可视化 IDE 执行的操作，可视化所有网络交易或从 Remix IDE 创建的交易等。您还可以在终端中搜索数据并清除日志。

![Remix terminal](images/00006.jpeg)

## 标签页面板

`Tabs` 面板提供了许多用于操作 IDE 的标签页：

*   `Compile` 标签页：用于编译智能合约并发布到 Swarm。
*   `Run` 标签页：用于向配置的环境发送交易。
*   `Settings` 标签页：用于更新设置，如编译器版本和编辑器的许多通用设置。
*   `Debugger` 标签页：用于调试交易。
*   `Analysis` 标签页：用于获取关于最新编译的信息。
*   `Support` 标签页：用于与 Remix 社区联系。

![Remix tabs](images/00007.jpeg)

# Remix 执行环境

Remix IDE 提供了多种用于执行交易的环境：

*   **JavaScript VM**：一种在浏览器中用 JavaScript 实现的沙盒区块链，用于模拟真实的区块链。
*   **Injected Web3**：一种注入 web3 的提供者，例如 `Mist` 和 `Metamask`，[将您连接到您的私有区块链](https://bitfalls.com/2018/03/26/connecting-myetherwallet-mist-metamask-private-blockchain/)。
*   **Web3 Provider**：一个运行 geth、parity 或任何以太坊客户端的远程节点。可用于连接到真实网络，或直接连接到您的私有区块链，而无需 MetaMask 作为中介。

![Remix Execution Environments](images/00008.jpeg)

# 使用 Remix IDE 编译和部署智能合约

为了演示使用 Remix IDE 可以实现的功能，我们将使用一个示例合约，并了解如何：

*   在 Remix IDE 中编译合约。
*   查看编译器在未遵循最佳实践时发出的一些警告。
*   在 JavaScript EVM（以太坊虚拟机）上部署合约。
*   对已部署的合约进行交易。
*   在终端 IDE 中查看示例读写操作。

我们将使用以下示例合约 [来自本教程](https://bitfalls.com/2018/03/31/solidity-development-crash-course-building-blockchain-raffle/)，它实现了一个区块链抽奖：

```
pragma solidity ^0.4.20;

contract Blocksplit {

    address[] public players;
    mapping (address => bool) public uniquePlayers;
    address[] public winners;

    address public charity = 0xc39eA9DB33F510407D2C77b06157c3Ae57247c2A;

    function() external payable {
        play(msg.sender);
    }

    function play(address _participant) payable public {
        require (msg.value >= 1000000000000000 && msg.value <= 100000000000000000);
        require (uniquePlayers[_participant] == false);

        players.push(_participant);
        uniquePlayers[_participant] = true;
    }

}
```

该合约声明了一些变量，例如：

*   `players` 数组变量，用于存储抽奖参与者的地址。
*   `uniquePlayers` 映射，用于保存唯一参与者，防止参与者从同一地址多次参与。（一个地址将映射到一个布尔值，true 或 false，表示该参与者是否已参与。）
*   `winners` 数组变量，将存储获奖者的地址。
*   `charity` 变量，存储一个硬编码的慈善机构地址，利润将流向该地址。

它还声明了：

*   一个标记为 `payable` 的回调函数，使智能合约能够接收付款。
*   一个 `play()` 函数，允许参与者通过提供地址来参加抽奖。

您可以从这个 [教程](https://bitfalls.com/2018/03/31/solidity-development-crash-course-building-blockchain-raffle/) 阅读关于该合约的更多详细信息，其中详细解释了所有代码。

现在，请前往 [remix.ethereum.org](https://remix.ethereum.org/) 打开 Remix IDE。

接下来，点击带有 `+` 图标的按钮创建一个新文件。

![Creating a new file](images/00009.jpeg)

一个新的对话框将弹出。输入您的文件名（`blocksplit.sol`），然后按下 `OK`：

![Naming the file](images/00010.jpeg)

代码编辑器中将打开一个新标签页，您可以在其中开始编写合约。因此，只需将之前的合约代码复制粘贴进去即可。

首先，开始编译合约。从 `Compile` 标签页，点击 `Start to compile` 按钮。

我们收到一个包含两个由静态代码分析提出的警告的消息框。

![Two warnings](images/00011.jpeg)

如果您点击该消息框，将被带到 `Analysis` 标签页，该标签页提供关于警告的更多信息：

![warning info](images/00012.gif)

第一个警告在函数的 Gas 需求过高时触发，第二个警告在 `require()` 或 `assert()` 函数使用不当的时候触发。

您还可以使用 `Analysis` 标签页中的复选框来确定何时希望编译器发出警告。

![determine when you want the compiler to emit warnings](images/00013.jpeg)

接下来，让我们使用 JavaScript VM 部署合约。切换到 `Run` 标签页，并从下拉菜单中选择 `JavaScript VM`。

![Selecting the JavaScript VM](images/00014.jpeg)

接下来，点击合约名称下方的 `Deploy` 按钮。

![The Deploy button](images/00015.jpeg)

一旦合约在 JavaScript VM 上成功部署，`Run` 标签页底部将打开一个框。

![Run tab box](images/00016.jpeg)

在已部署合约的名称和地址下方，我们有一些红色和蓝色的按钮。红色按钮代表会导致区块链写入的操作（在本例中为回调函数和 `play()` 函数），需要一笔交易；蓝色按钮代表从区块链读取数据（我们在合约代码中定义的 `charity`、`players`、`uniquePlayers` 和 `winners` 公共变量）。

您还将在 IDE 终端中看到类似于下面截图的消息。

![Terminal message](images/00017.gif)

目前，唯一持有值的变量是 `charity` 变量，因为地址在代码中是硬编码的，所以如果您点击相应的按钮，将获得该地址的值。

![address value](images/00018.gif)

该合约的构建允许参与者通过向地址发送以太币（使用可支付的回调函数）或调用带有参与者地址的 `play()` 函数来参加抽奖。

