
```solidity
pragma solidity ^0.4.24;

contract MyContract {
    // ...
}
```

智能合约是在以太坊区块链上执行的代码片段。它的功能类似于 Web 上公开可访问的 API 微服务。智能合约的所有代码对公众可见，我们可以允许连接到网络的任何人调用智能合约上的函数。

首先，我们将编程一个简单的“存储”智能合约，它能够：

- 存储一个值
- 检索这个值

我们将通过一个名为 `value` 的变量来创建一种在智能合约中存储字符串值的方式。Solidity 是静态类型语言，因此声明变量时必须首先指定数据类型：

```solidity
pragma solidity ^0.4.24;

contract MyContract {
    string value;
}
```

现在创建一个函数从存储中读取这个值。首先用 `function` 关键字声明一个名为 `get()` 的函数：

```solidity
function get() {
    // ...
}
```

现在用 `return` 关键字从状态变量返回值。将此函数的“可见性”设为 `public`，以便任何连接到区块链的人都可以调用它。最后，为函数指定返回值类型 `string`：

```solidity
pragma solidity ^0.4.24;

contract MyContract {
    string value;

    function get() public view returns(string) {
        return value;
    }
}
```

让我们创建一种从智能合约外部设置此值的方法。我们将创建一个 `set` 函数。我们只是创建了一个接受 `_value` 参数（类型为 `string`）的函数。此函数也是公开可见的，以便任何连接到区块链的人都可以调用它。现在实际更新智能合约的值：

```solidity
function set(string _value) public {
    value = _value;
}
```

现在在智能合约的构造函数中为 `value` 状态变量设置默认值：

```solidity
constructor() public {
    value = "myValue";
}
```

请记住，以太坊区块链由称为“区块”的记录捆绑包组成，这些区块“链接在一起”构成公共账本。所有这些区块的基本单位是交易。您可以在下方看到它们的列表。您可以点击“向下”箭头查看收据的所有详细信息。

我将选择 JavaScript 虚拟机，它将在我们的浏览器中提供一个模拟区块链。

让我们更新智能合约中的代码，使其兼容撰写本文时最新版本的 Solidity。我们可以修改智能合约代码的第一行：

```solidity
pragma solidity ^0.5.1;
```

首先，修改 `get()` 和 `set()` 函数如下：

```solidity
pragma solidity ^0.5.1;

contract MyContract {
    string value;

    constructor() public {
        value = "myValue";
    }

    function get() public view returns(string memory) {
        return value;
    }

    function set(string memory _value) public {
        value = _value;
    }
}
```

我们也可以像这样给状态变量赋默认值：

## Solidity 基础数据类型与结构

### 状态变量

```solidity
string public value = "myValue";
```

我们也可以将此值设置为永不改变的常量：

```solidity
string public constant value = "myValue";
```

我们可以像这样创建布尔状态变量：

```solidity
bool public myBool = true;
```

这可以是 `true` 或 `false`。

现在我们可以像这样创建整数：

```solidity
int public myInt = 1;
```

整数可以是正数或负数，即有符号。如果你不希望数字为负数，可以像这样创建无符号整数：

```solidity
uint public myUint = 1;
```

我们可以为数字指定位数。上述示例默认为 256 位。我们可以显式指定：

```solidity
uint256 public myUint256 = 9999;
```

我们也可以将值限制为 8 位：

```solidity
uint8 public myUint8 = 8;
```

### Enums（枚举）

现在让我们了解一下 Solidity 中的一些基本数据结构。首先，让我们看看 `Enum` 数据结构，它是在 Solidity 中跟踪枚举列表的一种方式。我们可以在编写智能合约时针对该列表进行检查。让我们在智能合约中创建一个枚举：

```solidity
enum State { Waiting, Ready, Active }
```

以此为例，这将通过提供 `Waiting`、`Ready` 和 `Active` 选项帮助我们跟踪智能合约的活动状态。我们可以像这样检查智能合约的当前状态：

```solidity
State public state;
```

现在，我们可以在构造函数中设置默认状态：

```solidity
constructor() public {
    state = State.Waiting;
}
```

我们可以像这样将当前状态更新为 `Active`：

```solidity
function activate() public {
    state = State.Active;
}
```

最后，我们可以针对枚举列表进行检查，以查看状态当前是否为 `Active`：

```solidity
function isActive() public view returns(bool) {
    return state == State.Active;
}
```

现在最终的智能合约代码应如下所示：

```solidity
pragma solidity ^0.5.1;

contract MyContract {
    enum State { Waiting, Ready, Active }
    State public state;

    constructor() public {
        state = State.Waiting;
    }

    function activate() public {
        state = State.Active;
    }

    function isActive() public view returns(bool) {
        return state == State.Active;
    }
}
```

### Structs（结构体）

Solidity 允许你使用 `Structs` 定义自己的数据类型。你基本上可以使用任意数据类型的任意属性来建模任何类型的数据。让我们通过创建一个 `people` 结构体来看看这是如何工作的：

```solidity
struct Person {
    string _firstName;
    string _lastName;
}
```

我们在这里建模了一个拥有 `_firstName` 和 `_lastName` 的人。请注意，我们能够指定任意想要的数据类型！这里我们对两个属性都使用了字符串。我们最多可以在此添加 17 个不同的属性，且数据类型任意。

现在我们需要一个地方来存储这个 `Person` 结构体。让我们使用数组！我们可以像这样声明 `people` 数组：

```solidity
Person[] public people;
```

请注意，我们在数组内声明类型，即 `Person`。我们还将可见性设置为 `public` 并将其赋值给名为 `people` 的状态变量。这将为我们提供一个函数，允许我们访问该数组内部的人员。我应该提到，在智能合约外部调用 `people()` 函数不会返回整个数组。相反，`people()` 函数将接受一个索引参数，允许我们根据该索引（从零开始）引用数组内部的人员。例如，我们可以像这样访问 `people` 数组中的第一个人：`people(0)`。

现在让我们创建一种向该数组添加人员的方法。我们将创建一个 `addPerson()` 函数：

此函数将接受 `Person` 结构体属性的参数，然后实例化一个新的 `Person` 并使用 `push` 函数将其添加到 `people` 数组中。它还会将 `peopleCount` 状态变量加 1。我们可以在智能合约中像这样实现该状态变量：`uint256 public peopleCount;`

```solidity
function addPerson(string memory _firstName, string memory _lastName) public {
    people.push(Person(_firstName, _lastName));
    peopleCount += 1;
}
```

现在完成的智能合约代码应如下所示：

```solidity
pragma solidity ^0.5.1;

contract MyContract {
    Person[] public people;
    uint256 public peopleCount;

    struct Person {
        string _firstName;
        string _lastName;
    }

    function addPerson(string memory _firstName, string memory _lastName) public {
        people.push(Person(_firstName, _lastName));
        peopleCount += 1;
    }
}
```

### Mapping（映射）

Solidity 提供了一种称为 `mapping` 的数据结构，它允许我们存储键值对。此结构的作用很像其他语言中的关联数组或哈希表。我们可以在智能合约中像这样声明映射：

```solidity
mapping(uint => Person) public people;
```

这将是一个存储 `Person` 结构体的映射。它将替换我们在上一个示例中使用的 `people` 数组。键将是一个无符号整数，值将是一个 `Person` 结构体。我们将把键视为数据库 ID。我们可以更新 `Person` 结构体以跟踪该 ID：

```solidity
struct Person { uint _id; string _firstName; string _lastName; }
```

现在我们可以修改 `addPerson()` 函数以更新 `people` 映射。以下代码使用 `peopleCount` 计数器缓存为人员创建 ID。然后使用该 ID 和传入的属性实例化一个新的 `Person` 结构体。然后将其添加到 `people` 映射中。完成的智能合约代码应如下所示：

```solidity
pragma solidity ^0.5.1;

contract MyContract {
    uint256 peopleCount = 0;
    mapping(uint => Person) public people;

    struct Person {
        uint _id;
        string _firstName;
        string _lastName;
    }

    function addPerson(string memory _firstName, string memory _lastName) public {
        peopleCount += 1;
        people[peopleCount] = Person(peopleCount, _firstName, _lastName);
    }
}
```

我们可以部署合约来检查代码。如果我在 `addPerson` 字段中输入：

`"_firstName"="Hidaia"` 和 `"_lastName"="Alassouli"`

这将作为第一个元素存储在 `people` 数组中。我在 `people` 字段中输入 `1`，将获得存储在数组 `people` 中元素 `1` 的数据。

![图片](img/159551592035104727_4.jpg)

### Function Visibility（函数可见性）

让我们谈谈函数可见性。在上一节中，我们多次使用了 `public` 函数可见性，以便网络连接的账户可以在智能合约外部调用智能合约函数。如果我们想创建仅在智能合约内部使用的函数怎么办？我们可以使用 `internal` 可见性来实现。让我们将 `peopleCount` 的增加封装到其自己的 `internal` 函数中：

```solidity
function incrementCount() internal {
    peopleCount += 1;
}
```

此函数仅可在智能合约内部访问，而不能通过其他账户的公共接口访问。现在我们可以在 `addPerson()` 函数内部调用此函数：

```solidity
function addPerson(string memory _firstName, string memory _lastName) public {
    incrementCount();
    people[peopleCount] = Person(peopleCount, _firstName, _lastName);
}
```

### Modifiers（修饰符）

现在这是其他类型函数可见性的一个示例。让我们谈谈函数修饰符。这些将允许我们为函数添加特殊行为，如添加权限。让我们创建一个修饰符，仅允许管理员或“所有者”调用 `addPerson()` 函数，并限制其他所有人调用此函数。

首先，我们将创建一种存储此智能合约所有者的方法。我们可以使用状态变量来实现：

```solidity
address owner;
```

现在让我们创建一个修饰符，检查调用函数的人是否为所有者：

```solidity
modifier onlyOwner() {
    require(msg.sender == owner);
    _;
}
```

让我解释这段代码：

首先，我们使用 `modifier` 关键字声明修饰符，后跟修饰符名称 `onlyOwner`。

接下来，我们使用 `msg.sender` 访问调用该函数的当前账户。

接下来，我们使用 `require()` 来检查调用该函数的账户是否为所有者。如果传入 `require()` 的表达式计算结果为 `true`，则代码继续执行。如果不是，则抛出错误。在这种情况下，如果调用该函数的账户不是所有者，Solidity 将抛出错误。

现在我们可以将智能合约内部的所有者设置为部署该智能合约的账户，如下所示：

```solidity
constructor() public {
    owner = msg.sender;
}
```

现在我们可以将修饰符添加到 `addPerson()` 函数，以便只有所有者可以调用它。尝试运行你的代码，看看只有所有者能否成功调用该函数而不报错！此时，完整的智能合约代码应如下所示：

```solidity
pragma solidity ^0.5.1;

contract MyContract {
    uint256 public peopleCount = 0;
    mapping(uint => Person) public people;
    address owner;

    modifier onlyOwner() {
        require(msg.sender == owner);
        _;
    }

    struct Person {
        uint _id;
        string _firstName;
        string _lastName;
    }

    constructor() public {
        owner = msg.sender;
    }

    function addPerson(
        string memory _firstName,
        string memory _lastName
    )
        public
        onlyOwner
    {
        incrementCount();
        people[peopleCount] = Person(peopleCount, _firstName, _lastName);
    }

    function incrementCount() internal {
        peopleCount += 1;
    }
}
```

### 时间

我们可以创建一个使用时间的新修饰符，以演示 Solidity 中时间相关的用例。我们将创建一个名为 `onlyWhileOpen` 的新修饰符，它将检查区块链上的当前时间是否已过我们指定的时间。在创建具有“开放时间”的 ICO 众筹智能合约时，这是一种常见做法。通常，这些智能合约会拒绝在众筹开始前进行的投资者捐款。我们可以通过限制对 `addPerson()` 函数的访问，直到开放时间已过，来模拟类似的行为。首先，让我们创建一个状态变量来存储开放时间：
