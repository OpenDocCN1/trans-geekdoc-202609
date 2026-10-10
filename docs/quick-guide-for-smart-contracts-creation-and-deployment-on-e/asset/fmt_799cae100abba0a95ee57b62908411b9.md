
# Solidity 智能合约开发指南

## 构造函数与回退函数

```solidity
constructor(address payable _wallet) public {
    wallet = _wallet;
}

function() external payable {
    buyToken();
}

function buyToken() public payable {
    balances[msg.sender] += 1;
    wallet.transfer(msg.value);
    emit Purchase(msg.sender, 1);
}
```

购买代币时生成的日志：

![](images/159551592143285549_6.jpg)

## j) 智能合约交互

我将展示如何在 Solidity 中使用多个智能合约。首先，我将展示如何从一个智能合约内部调用另一个智能合约的函数。

我将按如下方式创建代币合约：

```solidity
contract ERC20Token {
    string name;
    mapping(address => uint256) public balances;

    function mint() public {
        balances[msg.sender] += 1;
    }
}
```

现在我们可以使用 `ERC20Token` 合约从 `MyContract` 中铸造代币。为此，我们需要做几件事：获取代币的地址，以及智能合约代码以便调用其 `mint()` 函数。首先，我将按如下方式将代币地址存储在状态变量中：

```solidity
contract MyContract {
    address public token;
    //...
}
```

现在我们可以在构造函数中设置代币地址的值，如下所示：

```solidity
constructor(address payable _wallet, ERC20Token _token) public {
    wallet = _wallet;
    token = _token;
}
```

既然我们有了可用的地址，就可以在 `buyToken()` 函数中访问智能合约代码，并按如下方式调用其 `mint()` 函数：

```solidity
function buyToken() public payable {
    ERC20Token _token = ERC20Token(address(token));
    _token.mint();
    wallet.transfer(msg.value);
}
```

在继续之前，我想引起你对一点的注意。如果你现在从个人账户调用 `buyToken()` 函数，你将不会为自己铸造任何代币。为什么会这样？让我们重新审视一下当前的 `mint()` 函数：

```solidity
function mint() public {
    balances[msg.sender] += 1;
}
```

之所以不会为你的账户铸造代币，是因为 `msg.sender` 实际上引用的是 `MyContract` 的地址，它正从其 `buyToken()` 函数内部调用该函数！如果我们想为自己的账户铸造代币，必须使用 `tx.origin` 来引用在区块链上发起交易的账户，如下所示：

```solidity
function mint() public {
    balances[tx.origin] += 1;
}
```

你需要先部署代币智能合约，获取其地址，然后在部署第二个智能合约时将其作为参数传入。此时，你的完整智能合约代码应如下所示：

```solidity
pragma solidity 0.5.1;

contract ERC20Token {
    string name;
    mapping(address => uint256) public balances;

    function mint() public {
        balances[tx.origin] += 1;
    }
}

contract MyContract {
    address public token;
    address payable wallet;

    constructor(address payable _wallet, address _token) public {
        wallet = _wallet;
        token = _token;
    }

    function buyToken() public payable {
        ERC20Token _token = ERC20Token(address(token));
        _token.mint();
        wallet.transfer(msg.value);
    }
}
```

### 测试代码

*   首先部署 `ERC20Token` 合约。
*   从调试菜单获取合约地址。
*   在部署字段中填入创建者钱包地址和 `ERC20Token` 智能合约地址参数后，部署 `MyContract`。
*   点击 `buyToken` 字段。
*   然后在 `ERC20Token` 合约中点击 `balance` 字段并输入购买者地址以显示余额（发起交易的人的地址）。

![](images/159551592146506453_7.jpg)

## k) 继承

现在让我们谈谈继承。Solidity 允许你创建相互继承的智能合约。让我们创建一个名为 `MyToken` 的新伪代币，它继承自我们最初的代币智能合约。我们将使用继承赋予它唯一的名称、符号和铸造函数。我们可以按如下方式继承智能合约：

```solidity
contract MyToken is ERC20Token {
    // ...
}
```

现在我们可以按如下方式在父智能合约中跟踪代币名称：

```solidity
pragma solidity 0.5.1;

contract ERC20Token {
    string public name;
    mapping(address => uint256) public balances;

    constructor(string memory _name) public {
        name = _name;
    }

    function mint() public {
        balances[tx.origin] ++;
    }
}
```

我们可以在子代币的构造函数中覆盖父代币的名称。在此同时，我们还将为子代币创建一个符号并在构造函数中设置它。我将展示如何覆盖父代币合约构造函数，同时分配新值，如下所示：

```solidity
contract MyToken is ERC20Token {
    string public symbol;

    constructor(
        string memory _name,
        string memory _symbol
    )
        ERC20Token(_name)
        public
    {
        symbol = _symbol;
    }
}
```

太棒了！现在我们已经自定义了 `MyToken`。现在让我们更新 `mint()` 函数以覆盖父代币的功能。首先，让我们创建一种存储所有代币持有者地址的方式。我们还将设置所有持有者的计数，如下所示：

```solidity
contract MyToken is ERC20Token {
    address[] public owners;
    uint256 public ownerCount;
    //...
}
```

现在让我们在自己的 `mint()` 函数中更新这些值，同时使用 `super` 关键字保留父代币智能合约的行为，如下所示：

```solidity
function mint() public {
    super.mint();
    ownerCount ++;
    owners.push(msg.sender);
}
```

太棒了！现在我们已经创建了一个继承自父代币的自定义代币。你的完整智能合约代码应如下所示：

```solidity
pragma solidity 0.5.1;

contract ERC20Token {
    string public name;
    mapping(address => uint256) public balances;

    constructor(string memory _name) public {
        name = _name;
    }

    function mint() public {
        balances[tx.origin] ++;
    }
}

contract MyToken is ERC20Token {
    string public symbol;
    address[] public owners;
    uint256 public ownerCount;

    constructor(
        string memory _name,
        string memory _symbol
    )
        ERC20Token(_name)
        public
    {
        symbol = _symbol;
    }

    function mint() public {
        super.mint();
        ownerCount ++;
        owners.push(msg.sender);
    }
}
```

### 测试代码

我使用名称参数 "Hidaia" 和符号 "HED" 部署了合约 "MyToken"。

以下数据显示了每个合约字段的内容：`balances`、`name`、`ownerCount`、`owners` 和 `symbol`。

![](images/159551592261574373_8.jpg)

## l) 库

库用于避免在每个新合约代码中重复代码。让我们声明 `Math` 库。

```solidity
pragma solidity 0.5.1;

library Math {
    function divide(uint256 a, uint256 b) internal pure returns (uint256) {
        require(b > 0);
        uint256 c = a / b;
        return c;
    }
}

contract MyContract {
    uint256 public value;

    function calaculate(uint _value1, uint _value2) public {
        value = Math.divide(_value1, _value2);
    }
}
```

`MyContract` 将使用定义的 `Math` 库来对 a 和 b 进行除法运算。

部署 `MyContract` 并在 `Calculate` 函数字段中提供 a 和 b 的值。附上结果截图：

![](images/159551592223141044_9.jpg)

## m) 在单独文件中引入库

我们可以将库放在单独的文件中，并通过引入库文件在合约中调用它。

作为示例，我们为编写的 `Math` 库打开了一个新文件。新文件为 `Library.sol`。以下是库内部的代码：

```solidity
pragma solidity 0.5.1;

library Math {
    function divide(uint256 a, uint256 b) internal pure returns (uint256) {
        require(b > 0);
        uint256 c = a / b;
        return c;
    }
}
```

然后我们可以通过 `import` 命令在 `MyContract.sol` 文件中调用库文件 `Math.sol`。以下是完整代码：

```solidity
pragma solidity 0.5.1;

import "./Math.sol";

contract MyContract {
    uint256 public value;

    function calaculate(uint _value1, uint _value2) public {
        value = Math.divide(_value1, _value2);
    }
}
```

## n) SafeMath

有一个名为 `SafeMath.sol` 的常用库，使算术运算变得更加简单。该库的链接如下：

https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/math/SafeMath.sol

*   我使用该页面上的代码创建了 `SafeMath.sol`。

```solidity
pragma solidity ^0.5.0;

/**
 * @dev Wrappers over Solidity's arithmetic operations with added overflow
 * checks.
```
