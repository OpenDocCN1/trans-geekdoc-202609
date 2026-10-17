
还有其他全局变量列表，例如`blockhash`、`block.chainid`、`block.number`等，可以在官方文档查看：[`docs.soliditylang.org/en/v0.8.28/units-and-global-variables.html#special-variables-and-functions`](https://docs.soliditylang.org/en/v0.8.28/units-and-global-variables.html#special-variables-and-functions)

### 构造函数

构造函数是用于初始化合约的特殊函数。它们在合约部署时仅执行一次。

示例：

```solidity
contract MyContract {
    uint public value;

    constructor(uint _value) {
        value = _value;
    }
}
```

上述构造函数在合约部署时设置状态变量`value`的初始值。

### Fallback 函数和 Receive 函数

**Receive 函数**：合约最多可以有一个`receive`函数，当向合约发送 Ether 且不带 calldata 时，该函数会被触发。

**Fallback 函数**：当没有其他函数匹配调用，或者在发送 Ether 时没有匹配的`receive`函数时，会调用`fallback`函数。

示例：

```solidity
receive() external payable {
    // 处理发送到合约的 Ether 的逻辑
}

fallback() external payable {
    // fallback 情况的逻辑
}
```

### 函数可见性

函数的可见性标识符包括`public`、`private`、`internal`和`external`。这些决定了函数可以在何时以及如何被调用（在本章前面介绍）。

### View 函数与 Pure 函数

`view`函数用于函数从区块链读取数据但不修改数据的情况。

`pure`函数用于函数不读取或修改区块链上任何数据的情况。

示例：

```solidity
uint public x = 10;

function getX() public view returns (uint) {
    return x; // 读取状态变量 x
}

function add(uint a, uint b) public pure returns (uint) {
    return a + b; // 不读取或修改状态
}
```

### return 关键字

`return`关键字用于从函数返回值。它通常用于执行计算或从合约获取数据的函数。

示例：

```solidity
function multiply(uint a, uint b) public pure returns (uint) {
    return a * b;
}
```

# 向函数传递参数

*   **按值传递 (By Value)**：基本数据类型（如`uint`或`bool`）按值传递，这意味着该值的副本会被发送到函数。

*   **按引用传递 (By Reference)**：复杂类型（如数组和结构体）可以按引用传递，允许函数修改原始数据。

# Memory, Calldata 和 Storage 关键字

`memory`：用于声明临时数据结构，这些结构在函数执行后会被删除。适用于函数参数和局部变量。

```solidity
function setData(string memory _data) public {
    // _data 存储在内存中，执行后将丢弃
}
```

`calldata`：与`memory`类似，但`calldata`是只读的，用于外部传递的函数参数。它更节省 Gas（燃料费）。

```solidity
function processData(uint[] calldata _data) external {
    // _data 是只读的
}
```

`storage`：指区块链上的持久化存储。状态变量存储在`storage`中。

### 局部变量

局部变量定义在函数内部，仅在其执行期间存在。

```solidity
function calculateSum(uint a, uint b) pure returns (uint) {
    uint sum = a + b;
    return sum;
}
```

# 函数修饰器 (Modifiers)

修饰器用于为函数执行添加前提条件。它们使用`modifier`关键字定义。

示例：

```solidity
contract MyContract {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Not the owner");
        _;
    }

    function setValue(uint _value) public onlyOwner {
        // 此函数只能由所有者调用
    }
}
```

### require 语句

`require`语句经常用于修饰器中以确保满足某些条件。

示例：

```solidity
function transferOwnership(address newOwner) public {
    require(msg.sender == owner, "Not the owner");
    owner = newOwner;
}
```

### 事件与日志

事件（Events）和日志在 Solidity 中起着至关重要的作用，它们为智能合约与外部世界的通信提供了机制。事件允许开发者创建日志，日志可以用于跟踪合约活动或触发外部应用程序中的操作。

# 创建和触发事件

**定义事件**：事件定义在智能合约内部，类似于函数或状态变量。

示例：

```solidity
event ValueChanged(address indexed author, uint256 oldValue, uint256 newValue);
```

**触发事件**：当满足某些条件或函数执行时，触发事件以记录数据。

示例：

```solidity
function setValue(uint256 newValue) public {
    uint256 oldValue = value;
    value = newValue;
    emit ValueChanged(msg.sender, oldValue, newValue);
}
```

在`setValue`函数中，每当值发生变化时都会触发`ValueChanged`事件。该日志随后存储在交易收据中，允许外部应用程序监控该事件。

# 使用 Revert 和错误事件进行错误处理

## Revert (回滚):

`revert`语句用于终止函数的执行并回滚任何状态更改。它通常用于在不满足某些条件时的错误处理。

示例：

```solidity
function withdraw(uint256 amount) public {
    if (amount > address(this).balance) {
        revert("Insufficient balance");
    }
    payable(msg.sender).transfer(amount);
}
```

在此示例中，如果要提取的`amount`超过了合约余额，`revert`语句将终止函数并提供一条错误消息。

## 错误事件 (Error Events):

当合约出现问题时，可以触发错误事件以提供额外的上下文。

示例：

```solidity
event ErrorOccurred(string message);

function safeDivide(uint a, uint b) public returns (uint) {
    if (b == 0) {
        emit ErrorOccurred("Division by zero");
        revert("Cannot divide by zero");
    }
    return a / b;
}
```

在`safeDivide`函数中，如果`b`为零，在回滚交易之前会触发`ErrorOccurred`事件，以指示尝试进行除零操作。

# 事件的使用场景

*   **跟踪交易**：事件被用于跟踪重要的变化，例如价值转账或状态更新。

*   **与 DApps 通信**：前端应用程序使用事件来获何时更新界面或执行某些操作。事件帮助 DApps 实时响应区块链上的变化。

*   **调试**：事件可以用于记录数据，使得在开发过程中更容易对合约调试。

# 使用事件的完整合约示例

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ⁰.8.0;

contract EventExample {
    uint256 public value;
    address public owner;

    event ValueSet(address indexed author, uint256 newValue);
    event ErrorOccurred(string message);

    modifier onlyOwner() {
        require(msg.sender == owner, "Not the contract owner");
        _;
    }

    constructor() {
        owner = msg.sender;
    }

    function setValue(uint256 newValue) public onlyOwner {
        if (newValue == 0) {
            emit ErrorOccurred("Value cannot be zero");
            revert("Value must be non-zero");
        }
        value = newValue;
        emit ValueSet(msg.sender, newValue);
    }
}
```

在此示例中，合约定义了两个事件（`ValueSet`和`ErrorOccurred`），并使用它们在修改状态时记录操作。`onlyOwner`修饰器确保只有合约所有者可以赋值，如果提供了无效值，合约将触发错误事件并回滚。

事件和日志是 Solidity 编程不可或缺的一部分，提供了透明以及外部应用程序与区块链数据交互的方法。通过触发事件，合约可以有效地通信重要情况，帮助跟踪变化并简化与去中心化应用的交互。在下一节中，我们将探索 Solidity 中的控制结构，例如条件语句和循环，这些对于控制合约执行流至关重要。

# 控制结构：条件语句和循环

Solidity 中的控制结构用于管理智能合约内的执行流。本节涵盖了条件语句和循环，它们在智能合约中实现复杂逻辑至关重要。

# 条件语句：If 和 Switch 语句

## If 语句:

`if`语句用于在满足条件时执行代码块。

示例：

```solidity
function checkValue(uint value) public returns (string memory) {
    if (value > 100) {
        return "Value is greater than 100";
    } else {
        return "Value is 100 or less";
    }
}
```

在上述示例中，如果条件满足，`checkValue`函数将返回相应的字符串。

## Switch 语句 (Solidity 不直接支持):

Solidity 没有内置的`switch`语句。开发者使用一系列`if-else`语句来实现类似的功能。

示例：

```solidity
function categorizeNumber(uint value) pure returns (string memory) {
    if (value == 1) {
        return "Category One";
    } else if (value == 2) {
        return "Category Two";
    } else {
        return "Other Category";
    }
}
```

在此示例中，使用`if-else`语句来创建分支。

# 循环：For 和 While

### For 循环:

当循环次数已知时，使用`for`循环。

示例：

```solidity
function sumNumbers(uint n) public returns (uint) {
    uint sum = 0;
    for (uint i = 1; i <= n; i++) {
        sum += i;
    }
    return sum;
}
```

在此示例中，`for`循环从 1 迭代到`n`，并将值加加`sum`。

### While 循环:

当无法预知循环次数时，使用`while`循环。

示例：

```solidity
function countDown(uint start) public returns (uint) {
    uint counter = start;
    while (counter > 0) {
        counter--;
    }
    return counter;
}
```

在此示例中，`while`循环递减`counter`直到零。

## Do-While 循环 (Solidity 中不常用):

Solidity 也支持`do-while`循环，但由于复杂性很少使用。

# Solidity 中循环的使用实践

*   **Gas 限制考虑**：Solidity 中的循环在 Gas 方面可能昂贵，特别是当迭代次数很高时。避免无限循环至关重要。

*   **避免无边界循环**：始终确保循环有定义且有限的次数，以防止 Gas 耗尽错误。

# 使用条件语句和循环的示例

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ⁰.8.0;

contract ControlStructures {
    uint[] public numbers;

    // 将 1 到 n 的数字添加到数组中
    function addNumbers(uint n) public {
        for (uint i = 1; i <= n; i++) {
            numbers.push(i);
        }
    }

    // 检查数组中是否存在数字
    function checkNumber(uint num) public view returns (bool) {
        for (uint i = 0; i < numbers.length; i++) {
            if (numbers[i] == num) {
                return true;
            }
        }
        return false;
    }
}
```

在此示例中，`addNumbers`函数使用`for`循环将 1 到`n`的数字添加到数组，而`checkNumber`函数则遍历数组以检查特定数字是否存在。

Solidity 中的错误处理对于确保智能合约能够可预测且安全运行至关重要，特别是在出现意外情况时。Solidity 提供了多种错误处理机制，包括`require`、`revert`、`assert`和自定义错误消息。这些工具帮助开发者管理意外场景，并防止执行无效或不的操作。

## 错误处理机制

### Require 语句

`require`语句用于在执行函数之前验证条件。如果条件评估为`false`，交易将回滚，剩余的 gas 将退还给调用者。

示例：

```solidity
function transfer(uint amount) public {
    require(amount <= balance, "Insufficient balance");
    balance -= amount;
}
```

在此示例中，`require`语句确保转账金额不超过余额。如果不满足条件，交易将带有错误消息并进行回滚。

### Revert 语句

`revert`语句显式地用于终止函数并撤销执行期间发生的所有更改。它适用于在执行某些逻辑后可能需要回滚交易的条件检查。

示例：
