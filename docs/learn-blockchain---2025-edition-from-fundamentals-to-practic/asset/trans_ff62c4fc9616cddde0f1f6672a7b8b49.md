

# 区块链 3.0 与 Web3

## 可互操作的区块链

区块链之间的互操作性允许不同网络连接并无缝交换数据和资产。

1.  **Polkadot 协议**：  
    促进平行链之间的通信。
2.  **Cosmos 网络**：  
    利用跨链通信（IBC）协议创建“区块链互联网”。

## 资产代币化

1.  **房地产**：  
    允许将房地产划分为代币化份额，便于投资。
2.  **无形资产**：  
    从专利到版权，区块链使创建交易市场变得容易。

## 区块链 3.0

区块链 3.0 指的是技术的下一次进化，解决了限制前几代发展的可扩展性、能源效率和互操作性问题。

### 主要特性

1.  **速度与可扩展性**：  
    Solana 和 Avalanche 等网络以低成本提供每秒数千笔交易。
2.  **可持续性**：  
    第三代区块链采用节能共识机制，如权益证明。
3.  **去中心化治理**：  
    实施先进系统，使参与者在网络决策中拥有积极发言权。

### 区块链 3.0 示例

1.  **Cardano**：  
    专注于安全性、可扩展性和科学治理。
2.  **Tezos**：  
    链上升级允许在不分裂网络（硬分叉）的情况下演进。
3.  **Avalanche**：  
    为可扩展性和效率优化的共识协议。

```solidity
pragma solidity ^0.8.0;

contract ScalableApp {
    uint256 public transactionCount;

    function processTransaction() public {
        transactionCount++;
    }

    function getTransactionCount() public view returns (uint256) {
        return transactionCount;
    }
}
```

该合约展示了在高可扩展性网络上的基础应用，可不间断处理数千笔交易。

## Web3：互联网的未来

Web3 是去中心化互联网的愿景，用户借助区块链和互补技术，完全掌控自己的数据、身份和数字资产。

### 基本要素

1.  **去中心化**：  
    消除大型科技公司等中心化中介。
2.  **数据所有权**：  
    用户控制其数据如何被使用和货币化。
3.  **数字身份**：  
    使用去中心化标识符（DIDs）实现安全访问和隐私保护。
4.  **DApps**：  
    运行在区块链网络上的去中心化应用。

### 实际应用

1.  **金融**：  
    DeFi 实现全球借贷、投资和支付。
2.  **社交媒体**：  
    奖励用户创建和策划内容的平台。
3.  **游戏**：  
    基于区块链的游戏，其中资产（如角色和物品）归玩家真实所有。

```solidity
pragma solidity ^0.8.0;

contract DecentralizedIdentity {
    struct Identity {
        string name;
        uint256 age;
        address wallet;
    }

    mapping(address => Identity) public identities;

    function createIdentity(string memory name, uint256 age) public {
        identities[msg.sender] = Identity(name, age, msg.sender);
    }

    function getIdentity(address user) public view returns (Identity memory) {
        return identities[user];
    }
}
```

该合约创建了一个可跨多个 Web3 应用使用的去中心化身份。

## 挑战与展望

### 挑战

1.  **可扩展性**：  
    尽管取得进展，区块链网络在高交易量下仍面临限制。
2.  **大规模采用**：  
    让技术变得普罗大众易用且易懂是一个持续的挑战。
3.  **监管**：  
    协调全球规则以促进采用并避免碎片化。

### 展望

1.  **通用集成**：  
    区块链将成为物联网、人工智能和 5G 等多元技术的底层基础设施。
2.  **社会影响**：  
    去中心化应用可普及金融、教育和医疗服务的获取。
3.  **持续演进**：  
    随着持续创新，区块链和 Web3 有潜力改变数字经济和整个社会。

区块链的未来光明，创新将推动其边界并重塑整个行业。区块链 3.0 和 Web3 正引领这场演进，为每个人铺平通往去中心化、高效且可及生态系统的道路。

# 第 25 章 实战项目示例

---

## 去中心化应用（DApp）开发

去中心化应用结合了智能合约、用户界面和区块链连接。本项目将演示如何创建一个用于管理待办事项列表的 DApp。

### 初始设置

**所需工具安装：**

*   `Node.js`：管理包并运行 DApp 开发脚本。
*   `Truffle`：用于开发、测试和部署智能合约的框架。
*   `Ganache`：用于开发和测试的本地区块链。

```bash
npm install -g truffle ganache-cli
```

**创建 Truffle 项目：**  
在终端中启动一个新项目：

```bash
mkdir ToDoList && cd ToDoList
truffle init
```

**安装依赖：**  
在项目目录中，安装 `Web3.js` 以与区块链交互。

```bash
npm install web3
```

### 智能合约

智能合约管理列表中的任务。

```solidity
pragma solidity ^0.8.0;

contract ToDoList {
    struct Task {
        uint256 id;
        string content;
        bool completed;
    }

    uint256 public taskCount;
    mapping(uint256 => Task) public tasks;

    event TaskCreated(uint256 id, string content, bool completed);
    event TaskCompleted(uint256 id, bool completed);

    function createTask(string memory content) public {
        taskCount++;
        tasks[taskCount] = Task(taskCount, content, false);
        emit TaskCreated(taskCount, content, false);
    }

    function toggleComplete(uint256 id) public {
        Task storage task = tasks[id];
        task.completed = !task.completed;
        emit TaskCompleted(id, task.completed);
    }
}
```

1.  **函数 `createTask`**：  
    创建新任务并发出事件以通知创建。
2.  **函数 `toggleComplete`**：  
    在完成和未完成之间切换任务状态。

### 合约部署

编辑迁移文件 `2_deploy_contracts.js` 以部署合约：

```javascript
const ToDoList = artifacts.require("ToDoList");

module.exports = function (deployer) {
    deployer.deploy(ToDoList);
};
```

**启动 Ganache：**

```bash
ganache-cli
```

**编译并部署合约：**

```bash
truffle compile
truffle migrate
```

### 用户界面

使用 HTML、CSS 和 JavaScript 创建界面以与合约交互。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
</head>
<body>
    <h1>To-Do List</h1>
    <form id="taskForm">
        <input type="text" id="taskContent" placeholder="New task" required />
        <button type="submit">Add Task</button>
    </form>
    <ul id="taskList"></ul>
    <script src="app.js"></script>
</body>
</html>
```

```javascript
const Web3 = require("web3");
const contractABI = /* ABI given to the contract */;
```

