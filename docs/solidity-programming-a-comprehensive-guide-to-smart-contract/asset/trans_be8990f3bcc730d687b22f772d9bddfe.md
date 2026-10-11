
# 第 2 章：Solidity 基础

## 1. 语法与结构

### 基本语法与数据类型

Solidity 是以太坊区块链上编写智能合约的主要编程语言，其语法类似于 JavaScript 和 C++，使得熟悉这些语言的开发者能够轻松上手。Solidity 是静态类型语言，意味着数据类型在编译时指定。这确保了类型相关的错误能在开发早期被捕获，从而增强了代码的可靠性和安全性。

### 基本语法

Solidity 代码组织在合约中，合约是以太坊应用的基本构建块。合约类似于面向对象编程中的类。以下是一个简单的 Solidity 合约示例：

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleStorage {
    uint256 storedData;

    function set(uint256 x) public {
        storedData = x;
    }

    function get() public view returns (uint256) {
        return storedData;
    }
}
```

在该示例中，`pragma` 指令指定了 Solidity 编译器版本。`contract` 关键字用于定义一个名为 `SimpleStorage` 的新合约。该合约拥有一个状态变量 `storedData`，以及两个用于修改和检索 `storedData` 值的函数 `set` 和 `get`。

### 数据类型

Solidity 支持多种基本数据类型，每种类型服务于特定目的。以下是一些最常用的类型：

*   **布尔值**：用于表示 `true` 或 `false` 值。
    ```solidity
    bool isReady = true;
    ```
*   **整数**：Solidity 支持各种大小的有符号（`int`）和无符号（`uint`）整数（例如 `int8`、`uint256`）。默认情况下，`uint` 是 `uint256` 的别名。
    ```solidity
    uint256 count = 1;
    int256 balance = -10;
    ```
*   **地址**：表示以太坊地址，常用于追踪账户余额和发送交易。
    ```solidity
    address recipient = 0xAbC1234567890abcdef1234567890abcdef123456;
    ```
*   **字符串与字节**：字符串表示文本，而字节数组（`bytes`）表示字节序列。Solidity 还拥有固定大小的字节数组（`bytes1` 到 `bytes32`）。
    ```solidity
    string name = "Alice";
    bytes32 data = "0x1234567890abcdef";
    ```
*   **数组与结构体**：数组可以是固定大小或动态大小。结构体允许将变量分组。
    ```solidity
    uint256[] numbers; // 动态数组
    struct Person {
        string name;
        uint256 age;
    }
    ```
*   **映射**：类似于其他语言中的哈希表或字典，映射存储键值对。它们对于将地址与数据关联特别有用。
    ```solidity
    mapping(address => uint256) balances;
    ```

### 控制结构

Solidity 包含熟悉的控制结构，如 `if`、`else`、`while`、`for` 和 `switch`（在较新版本中）。这些结构用于控制合约内的执行流程。

```solidity
function example(uint256 x) public pure returns (uint256) {
    if (x < 10) {
        return x * 2;
    } else {
        return x / 2;
    }
}
```

理解 Solidity 的基本语法和数据类型对于编写健壮的智能合约至关重要。有了这些基础知识的坚实根基，开发者可以在以太坊区块链上创建更复杂、更安全的去中心化应用。

## 函数与修饰符

函数是 Solidity 中定义智能合约行为和逻辑的基本构建块。它们允许合约执行各种操作，包括修改状态变量、与其他合约交互以及处理用户输入。Solidity 中的函数可根据其可见性和可变性分为不同类型，为控制访问和确保安全交互提供了稳健的框架。

### 函数

Solidity 中的函数使用 `function` 关键字定义，后跟其名称、参数、可见性和函数体。以下是 Solidity 合约中简单函数的示例：

```solidity
function set(uint256 x) public {
    storedData = x;
}
```

在此示例中，`set` 函数接受单个参数 `x` 并将其赋值给状态变量 `storedData`。`public` 关键字表示该函数既可以在合约内部调用，也可以由其他合约或用户外部调用。

函数也可以指定返回类型：

```solidity
function get() public view returns (uint256) {
    return storedData;
}
```

此处的 `get` 函数标记为 `view`，表示它不修改合约状态。它返回 `storedData` 的值。Solidity 还支持 `pure` 函数，此类函数既不读取也不修改状态，因此适用于仅依赖输入参数的计算。

#### 函数可见性

Solidity 为函数提供了四种可见性类型：

*   `public`：可从合约内部、派生合约和外部访问。
*   `private`：仅可在定义该函数的合约内部访问。
*   `internal`：可在合约内部及派生合约中访问。
*   `external`：仅可从外部调用访问，不可从同一合约内部访问。

```solidity
function _internalFunction() internal {
    // 此处为逻辑
}

function _privateFunction() private {
    // 此处为逻辑
}
```

### 函数修饰符

修饰符是 Solidity 中一项强大的功能，允许你以声明方式改变函数的行为。它们常用于应用前置条件，例如确保在函数执行前满足特定条件。修饰符使用 `modifier` 关键字定义：

```solidity
modifier onlyOwner() {
    require(msg.sender == owner, "Not the contract owner");
    _;
}
```

在该示例中，`onlyOwner` 是一个修饰符，用于检查函数调用者（`msg.sender`）是否为合约所有者。`_` 符号是一个占位符，代表应用该修饰符的函数体。以下是将修饰符应用于函数的方法：

```solidity
function changeOwner(address newOwner) public onlyOwner {
    owner = newOwner;
}
```

`changeOwner` 函数只能由合约的当前所有者调用。如果 `msg.sender` 不是所有者，函数调用将回滚并显示错误消息 "Not the contract owner"。

#### 组合函数与修饰符

修饰符可以叠加使用，从而应用多个前置条件：

```solidity
modifier onlyWhileOpen() {
    require(now <= deadline, "Deadline has passed");
    _;
}

function withdraw() public onlyOwner onlyWhileOpen {
    // 提款逻辑此处
}
```

在该示例中，`withdraw` 函数只能由所有者调用，且仅在当前时间（`now`）早于截止时间时才可调用。如果任一条件失败，函数将不会执行。

函数和修饰符是编写安全高效的 Solidity 智能合约不可或缺的部分。函数封装了合约的逻辑和行为，而修饰符则强制执行前置条件并增强代码复用性。通过理解并利用这些特性，开发者可以在以太坊区块链上构建健壮的去中心化应用。

## 状态变量与局部变量
