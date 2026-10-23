
## 中缀表达式

Monkey 支持八个中缀运算符，其中四个用于算术运算：+、-、* 和 /。我们已经使用 OpAdd 操作码添加了对 + 的支持。现在我们需要再添加三个。并且由于这三个运算符在操作数和使用栈方面的工作方式相同，我们将一起添加它们。

第一步是在 code 包中添加 Opcode 定义：

```go
// code/code.go

const (
    // [...] 
    OpSub
    OpMul
    OpDiv
)

var definitions = map[Opcode]*Definition{
    // [...] 
    OpSub: {"OpSub", []int{}},
    OpMul: {"OpMul", []int{}},
    OpDiv: {"OpDiv", []int{}},
}
```

OpSub 代表 -，OpMul 代表 *，OpDiv 代表 / 中缀运算符。定义了这些操作码后，我们可以在编译器测试中使用它们，以确保编译器知道如何输出它们：

```go
// compiler/compiler_test.go

func TestIntegerArithmetic(t *testing.T) {
    tests := []compilerTestCase{
        // [...] 
        {
            input:          "1 - 2",
            expectedConstants: []interface{}{1, 2},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpConstant, 1),
                code.Make(code.OpSub),
                code.Make(code.OpPop),
            },
        },
        {
            input:          "1 * 2",
            expectedConstants: []interface{}{1, 2},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpConstant, 1),
                code.Make(code.OpMul),
                code.Make(code.OpPop),
            },
        },
        {
            input:              "2 / 1",
            expectedConstants: []interface{}{2, 1},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpConstant, 1),
                code.Make(code.OpDiv),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

希望这里唯一让你犹豫的是最后一个测试用例，我在其中更改了操作数的顺序。除此之外，这些与我们之前对 1 + 2 的测试用例相比乏味地相似，除了运算符本身和预期的操作码之外。但是，唉，相似性并不是编译器天生就理解的东西：

```text
$ go test ./compiler
--- FAIL: TestIntegerArithmetic (0.00s)
compiler_test.go:67: compiler error: unknown operator -
FAIL
FAIL    monkey/compiler  0.006s
```

我们需要更改的是编译器 Compile 方法中检查 node.operator 的 switch 语句：

```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
        // [...]

    case *ast.InfixExpression:
        // [...]

        switch node.Operator {
        case "+":
            c.emit(code.OpAdd)
        case "-":
            c.emit(code.OpSub)
        case "*":
            c.emit(code.OpMul)
        case "/":
            c.emit(code.OpDiv)
        default:
            return fmt.Errorf("unknown operator %s", node.Operator)
        }

        // [...] 
    }

    // [...] 
}
```

这段代码中只有六行是新的：针对 "-"、"*" 和 "/" 的 case 分支。它们使测试通过：

```text
$ go test ./compiler
ok      monkey/compiler 0.006s
```

好吧，编译器现在输出了另外三个操作码。我们的 VM 现在必须迎接这一挑战。在这里，同样首先要做的是添加测试用例：

```go
// vm/vm_test.go

func TestIntegerArithmetic(t *testing.T) {
    tests := []vmTestCase{
        // [...] 
        {"1 - 2", -1},
        {"1 * 2", 2},
        {"4 / 2", 2},
        {"50 / 2 * 2 + 10 - 5", 55},
        {"5 * (2 + 10)", 60},
        {"5 + 5 + 5 + 5 - 10", 10},
        {"2 * 2 * 2 * 2 * 2", 32},
        {"5 * 2 + 10", 20},
        {"5 + 2 * 10", 25},
        {"5 * (2 + 10)", 60},
    }

    runVmTests(t, tests)
}
```

有人可能会说这太过分了，过了头。但我想在这里展示的是栈算术的威力。我们不仅有三个必要的测试用例来确保 VM 能识别 OpSub、OpMul 和 OpDiv 操作码，还有一系列混合中缀运算符的测试用例，玩弄它们不同的优先级并通过手动添加括号来操作它们。目前，它们全部失败，这并不是我想表达的重点：

```text
$ go test ./vm
--- FAIL: TestIntegerArithmetic (0.00s)
vm_test.go:30: testIntegerObject failed: object has wrong value.
got=2, want=-1
vm_test.go:30: testIntegerObject failed: object has wrong value.
got=5, want=55
vm_test.go:30: testIntegerObject failed: object has wrong value.
got=12, want=60
vm_test.go:30: testIntegerObject failed: object has wrong value.
got=2, want=32
vm_test.go:30: testIntegerObject failed: object has wrong value.
got=12, want=20
vm_test.go:30: testIntegerObject failed: object has wrong value.
got=12, want=25
vm_test.go:30: testIntegerObject failed: object has wrong value.
got=12, want=60
FAIL
FAIL    monkey/vm    0.007s
```

我的观点是使它们全部通过所需的更改有多么最小化。首先，我们用以下内容替换 VM 中现有的 case code.OpAdd：

```go
// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 

    case code.OpAdd, code.OpSub, code.OpMul, code.OpDiv:
        err := vm.executeBinaryOperation(op)
        if err != nil {
            return err
        }

    }
    // [...] 
}
```

所有与二元操作相关的内容现在都整齐地隐藏在 executeBinaryOperation 方法之后：

```go
// vm/vm.go

func (vm *VM) executeBinaryOperation(op code.Opcode) error {
    right := vm.pop()
    left := vm.pop()

    leftType := left.Type()
    rightType := right.Type()

    if leftType == object.INTEGER_OBJ && rightType == object.INTEGER_OBJ {
        return vm.executeBinaryIntegerOperation(op, left, right)
    }

    return fmt.Errorf("unsupported types for binary operation: %s %s",
        leftType, rightType)
}
```

## 布尔值

我们添加的这四个运算符只是 Monkey 中可用运算符的一个子集。还有比较运算符 ==、!=、>、< 以及两个前缀运算符 ! 和 -。我们的下一个目标是实现所有这些运算符，这包括向我们的 Monkey VM 教授另一种 Monkey 数据类型：布尔值。如果没有布尔值，我们就无法表示这些运算符的结果（好吧，除了 - 前缀），但布尔值在 Monkey 中也作为字面量表达式存在：

```
true;
false;
```

我们将从为这两个字面量添加支持开始。这样在添加运算符时，我们的布尔数据类型已经就位。

那么布尔字面量有什么作用呢？好吧，在我们的求值器中，布尔字面量求值为它指定的布尔值：true 或 false。现在我们正在使用编译器和 VM，所以我们必须稍微调整一下期望。不是让布尔字面量求值为布尔值，我们现在希望它们导致 VM 将布尔值加载到栈上。

这与整数字面量的做法非常接近，而整数字面量被编译为 OpConstant 指令。我们也可以将 true 和 false 视为常量，但那样会浪费，不仅浪费字节码，还浪费编译器和 VM 资源。相反，我们现在将定义两个新的操作码，直接告诉 VM 将 *object.Boolean 推到栈上：

```go
// code/code.go

const (
    // [...] 
    
    OpTrue
    OpFalse
)

var definitions = map[Opcode]*Definition{
    // [...] 
    
    OpTrue:  {"OpTrue", []int{}},
    OpFalse: {"OpFalse", []int{}},
}
```

Granted，我在这两个名称上并没有浪费太多创造力。但它们的作用应该仍然很清楚。两个操作码都没有操作数，只是简单地告诉 VM“将 true 或 false 推到栈上”。

我们现在可以用它来创建一个编译器测试，确保布尔字面量 true 和 false 被翻译为 OpTrue 和 OpFalse 指令：

```go
// compiler/compiler_test.go

func TestBooleanExpressions(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: "true",
            expectedConstants: []interface{}{},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpTrue),
                code.Make(code.OpPop),
            },
        },
        {
            input: "false",
            expectedConstants: []interface{}{},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpFalse),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

这是我们的第二个编译器测试，其结构与第一个相同。tests 切片将在实现比较运算符后被扩展。

两个测试用例都失败，因为编译器只知道在表达式语句后应该发出 OpPop：

```text
$ go test ./compiler
--- FAIL: TestBooleanExpressions (0.00s)
    compiler_test.go:90: testInstructions failed: wrong instructions length.
        want="0000 OpTrue\n0001 OpPop\n"
        got ="0000 OpPop\n"
FAIL
FAIL    monkey/compiler 0.009s
```

为了发出 OpTrue 或 OpFalse 指令，我们需要在编译器的 Compile 方法中为 *ast.Boolean 添加一个新的 case 分支：
