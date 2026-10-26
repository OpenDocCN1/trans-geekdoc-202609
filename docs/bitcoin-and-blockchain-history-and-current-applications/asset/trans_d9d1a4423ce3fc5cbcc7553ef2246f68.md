
### 8.7.6 函数类型

在 Solidity 中，几种函数类型会影响函数的行为和执行。让我们逐一讨论它们。

- **A. 公共：** 公共函数可以直接从外部访问。它们作为智能合约接口的成员而存在。它们可以从内部调用，甚至可以从外部调用。
- **B. 私有：** 私有函数只能在合约内部调用。它们无法被其他合约访问，甚至在派生合约中也无法访问。与公共不同，这些函数不是智能合约接口的成员。
- **C. 内部：** 内部函数与私有类似，不能从外部访问。它们只能在定义它们的合约内部或继承自它的合约中使用，而不使用 “this” 关键字。这些函数也不是智能合约接口的成员。
- **D. 外部：** 外部函数可以直接从外部访问，但不能在内部访问。它们可以被其他合约或通过交易 [10] 轻松访问。这些函数是智能合约接口的成员。
- **E. 视图：** 视图函数是指那些保持不变的函数。因此，我们可以将术语 “view” 和 “constant” 互换使用。视图函数返回数据但不修改合约数据。
- **F. 纯：** 纯函数不能修改或读取合约的数据。它们无权读取状态或交易变量 [11]。
- **G. 可支付：** 可支付函数用于接受以 ether 形式支付的款项。每当某个外部实体使用可支付函数时，它会尝试随之发送一些资金。如果未发送所需的 ether [11]，此函数调用将失败。

### 8.7.7 回退函数

回退函数是一个无名函数。它既不接受参数也不返回任何数据。当合约收到匿名 ether 或给定的函数标识符未定义时，它会被调用。智能合约只能维护一个回退函数。如果合约预期接收一些 ether，则其回退函数必须包含 “payable” 关键字。

通过图 8.17 中的示例来理解这一点。

在上面的示例中，我们定义了一个合约 “Test”。它包含一个回退函数，该函数在每次无效函数调用时递增 x 值。合约 “Caller” 展示了如何调用一个不存在的函数，每次调用时递增 x 的值。

### 8.7.8 函数重载

Solidity 支持函数重载。函数重载是一种支持两个或多个具有相同名称但功能不同的函数的特性。当具有相同名称的函数具有不同的返回类型或参数数量时就会发生这种情况 [5]。

请参考图 8.18 中的示例以了解 Solidity 中的函数重载。

**表 8.8**  
**加密函数**

| 函数 | 返回类型 | 描述 |
|---|---|---|
| keccak256 (bytes memory) | bytes32 | 接收输入，计算 keccak256 哈希。 |
| sha256 (bytes memory) | bytes32 | 接收输入，计算 sha256 哈希。 |
| ripemd160 (bytes memory) | bytes20 | 接收输入，计算 ripemd160 哈希。 |

```solidity
pragma solidity ^0.5.0;

contract Encrypt {
    function encryption() public pure returns(bytes32 result){
        return keccak256("XYZ");
    }
}
```

**图 8.19**  加密函数。

也称为基合约。继承用于减少合约内部的重复逻辑和重复代码，从而提高代码的可重用性。

例如，参见图 8.20 中的程序。合约具有以下属性。

### 8.8.1  构造函数

它是一个使用 “constructor” 关键字声明的特殊函数。在合约中，构造函数用于初始化状态变量。每当创建新合约时就会调用它。每个合约只允许一个构造函数。

```solidity
pragma solidity ^0.4.0;

contract Storage {
    uint Data;

    function setData(uint x) public {
        Data = x;
    }

    function getData() public view returns (uint) {
        return Data;
    }
}
```

**图 8.20**  Solidity 中的合约。

### 8.8.2 **状态变量**

这些用于存储变量的状态。我们已在本章前面的章节中讨论过状态变量。

### 8.8.3 **函数**

函数通过修改状态变量来改变合约的状态。我们也在本章前面的章节中讨论过函数。

### 8.9 **事件**

正如我们所知，区块链交易存储在区块中。每笔交易都有一些相关的日志。日志记录事件发生的详细信息。Solidity 中的事件保存合约的当前状态。它以日志的形式存储。事件在合约中全局声明，并将在其函数内部触发。要声明一个事件，请使用关键字 “event” 后跟标识符和参数列表。要发出事件，请使用 “emit” 关键字后跟事件名称和括号中的参数。

让我们通过图 8.21 中的示例来理解这一点。

```solidity
pragma solidity ^0.5.0;

contract TestEvent {
    event Deposit(address indexed _from, bytes32 indexed _id, uint _value);
    function deposit(bytes32 _id) public payable {
        emit Deposit(msg.sender, _id, msg.value);
    }
}
```

**图 8.21**  Solidity 中的事件。

### 8.10 **错误处理**

Solidity 中的合约被编译为字节码。在编写合约时，我们会遇到各种错误。异常错误可能在运行时或设计时发生。设计级别在编译时会检查任何语法错误。但运行时错误更难检测，因为它们在合约执行期间发生。因此，检查合约是否存在可能的运行时错误至关重要。因此，为了减少运行时和设计时错误，合约应遵循清晰且健壮的方式。

Solidity 支持多种错误处理方法。其中一些列在表 8.9 中。

**表 8.9**  
**错误处理方法**

| 方法 | 描述 |
|---|---|
| assert (bool condition) | 如果条件不满足，方法调用会引发无效操作码，并且对状态的任何更改都会被回滚。 |
| require (bool condition) | 如果条件不满足，此方法调用将回滚到原始状态。 |
| require (bool condition, string memory message) | 对于输入或外部组件中的错误，使用此方法。如果条件不满足，此方法将回滚到原始状态。 |
| revert () | 此方法回滚对状态所做的更改并中止执行。 |
| revert (string memory reason) | 此方法回滚对状态所做的更改，中止执行，并提供自定义消息的选项。 |

## 结论

Solidity 语言是为在以太坊网络上部署智能合约而开发的。Solidity 是一种面向合约的高级语言，用于轻松高效地编写智能合约。它生成在 EVM 上执行的机器级代码。Solidity 与 C、Python 和 JavaScript 等其他高级编程语言具有相似之处。其大部分值和运算符类型与 C 相似，并有一些额外的内容。其控制语句和函数像 JavaScript 一样编写。它支持 enum、array、struct、string 和 mapping 等数据结构。面向对象概念如继承也存在，这对代码可重用性很有用。最后，它还支持各种库、复杂用户定义数据类型和许多其他功能。在 Solidity 中，合约发挥着非常关键的作用。当用 Solidity 编写的代码部署到特定地址时，它会作为智能合约运行。合约类似于其他面向对象语言中的类。至此，本章结束。

## 参考文献

1. Dannen, C.: Solidity 编程。收录于 Chris Dannen (编) *介绍以太坊和 Solidity*。Springer: Berlin, Germany, pp. 69–88, 2017.
2. Clack, C.D., Bakshi, V.A., Braine, L.: 智能合约模板：基础、设计格局和研究方向。 *CoRR* abs/1608.00771. 2016.
3. Szabo, N.: 形式化并保护公共网络上的关系。 *First Monday* 2(9), 1–28, 1997.
4. Dannen, C.: *介绍以太坊和 Solidity：加密货币和区块链编程基础入门*。Apress, New York. p. 30.
5. Solidity 官方文档。 https://solidity.readthedocs.io/. 2017.
6. Tschorsch, F., Scheuermann, B.: Bitcoin 及以后：关于去中心化数字货币的技术调查。Cryptology ePrint Archive, Report 2015/464, 2015.
7. Bonneau, J., Miller, A., Clark, J., Narayanan, A., Kroll, J. A., and Felten, E. W.: Bitcoin 和加密货币的研究视角和挑战。Cryptology ePrint Archive, Report 2015/261, 2015.
8. Tikhomirov, S., Voskresenskaya, E., Ivanitskiy, I., Takhaviev, R., Marchenko, E., Alexandrov, Y.: SmartCheck：以太坊智能合约的静态分析。收录于 Sergei Tikhomirov, Ekaterina Voskresenskaya, Ivan Ivanitskiy, Ramil Takhaviev, Evgeny Marchenko, and Yaroslav Alexandrov (编) *软件工程区块链新兴趋势国际研讨会第一届*。ACM, Gothenburg, Sweden, pp. 9–16, 2018.
9. Wood, G.: Ethereum：一个安全的去中心化通用交易账本。www.gavwood.com/paper.pdf. 2014.
