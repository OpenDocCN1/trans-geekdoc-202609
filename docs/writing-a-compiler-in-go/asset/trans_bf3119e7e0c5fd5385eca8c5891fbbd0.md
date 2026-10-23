
这再次让我们的测试从红色变为绿色：

```
$ go test ./code
ok      monkey/code 0.006s
```

而且由于 OpAdd 没有任何操作数，我们不需要更改 ReadOperands，这意味着我们已经完成了工具的更新。OpAdd 现在已完全定义，可以在编译器中使用了。

现在，回想一下我们第一个编译器测试 TestIntegerArithmetic。我们断言 Monkey 表达式 1 + 2 应该产生两个 OpConstant 指令。当时这是错误的，现在仍然是错误的。但我们最初的目标是构建一个尽可能小的编译器，只做一件事——将整数压入栈，所以那样是可以的。现在我们想要对这些数字进行加法运算，这意味着是时候通过添加缺失的 OpAdd 指令来修复测试了：

```go
// compiler/compiler_test.go

func TestIntegerArithmetic(t *testing.T) {
    tests := []compilerTestCase{
        {
            input:                "1 + 2",
            expectedConstants:    []interface{}{1, 2},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpConstant, 1),
                code.Make(code.OpAdd),
            },
        },
    }
    // [...]
}
```

expectedInstructions 现在是正确的。两个 OpConstant 指令用于将两个常量压入栈，然后是一个 OpAdd 指令，应该会导致 VM 将它们相加。

由于我们只更新了工具而尚未更新编译器，测试现在告诉我们我们没有发出哪条指令：

```
$ go test ./compiler
--- FAIL: TestIntegerArithmetic (0.00s)
    compiler_test.go:26: testInstructions failed: wrong instructions length.
        want="0000 OpConstant 0\n0003 OpConstant 1\n0006 OpAdd\n"
        got ="0000 OpConstant 0\n0003 OpConstant 1\n"
FAIL
FAIL    monkey/compiler 0.007s
```

我坚定地认为 `Instructions.String` 方法物有所值，价值千金。

这个失败的测试现在清晰地、易读地告诉我们——我们需要发出一条 `OpAdd` 指令。而且由于我们在编译器的 `Compile` 方法中已经遇到了 `*ast.InfixExpression`，我们知道该在哪里实现：

```go
// compiler/compiler.go

import (
    "fmt"
    // [...]
)

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...]

    case *ast.InfixExpression:
        err := c.Compile(node.Left)
        if err != nil {
            return err
        }

        err = c.Compile(node.Right)
        if err != nil {
            return err
        }

        switch node.Operator {
        case "+":
            c.emit(code.OpAdd)
        default:
            return fmt.Errorf("unknown operator %s", node.Operator)
        }

    // [...]
    }

    // [...]
}
```

就这样了。我们的编译器现在能够发出 OpAdd 指令：

```
$ go test ./compiler
ok      monkey/compiler 0.006s
```

这开始感觉像是一波连胜。现在，我们不走任何弯路，直接进入 VM 并在那里也实现 OpAdd。

最好的部分是，我们不需要编写新的测试——只需要修复旧的测试。因为在 vm 包中，我们之前也写了一个“错误”的测试。还记得我们关于 1 + 2 留下 2 在栈上的断言吗？我们需要更改它：

```go
// vm/vm_test.go

func TestIntegerArithmetic(t *testing.T) {
    tests := []vmTestCase{
        // [...]
        {"1 + 2", 3},
    }

    runVmTests(t, tests)
}
```

现在我们期望得到 3 而不是 2。但仅此一项就导致测试失败：

```
$ go test ./vm
--- FAIL: TestIntegerArithmetic (0.00s)
    vm_test.go:20: testIntegerObject failed: object has wrong value. got=2, want=3
FAIL
FAIL    monkey/vm    0.007s
```

我们现在必须对压入栈的整数做点什么，这意味着我们终于进入了栈算术。那么，要把两个数字相加，第一步需要做什么？没错，从栈中弹出操作数。为此，我们在 vm 中添加另一个辅助函数：

```go
// vm/vm.go

func (vm *VM) pop() object.Object {
    o := vm.stack[vm.sp-1]
    vm.sp--
    return o
}
```

我们首先取出位于 vm.sp-1 的栈顶元素并暂时保存。然后递减 vm.sp，使得刚刚弹出的元素位置最终可以被覆盖。

为了使用这个新的 pop 方法，我们首先需要为新的 OpAdd 指令添加“解码”部分。但这单独提及并不值得，所以这里连同“执行”的第一部分一起给出：

```go
// vm/vm.go

func (vm *VM) Run() error {
    // [...]
    switch op {
    // [...]

    case code.OpAdd:
        right := vm.pop()
        left := vm.pop()
        leftValue := left.(*object.Integer).Value
        rightValue := right.(*object.Integer).Value

    }
    // [...]
}
```

看起来足够无害，但这里正是细微 bug 可能潜入的地方。我们隐式假设中缀运算符的右操作数是最后压入栈的。对于 + 来说，操作数的顺序无关紧要，所以这种隐式性不是立即的问题。但还有其他运算符，操作数顺序错误会导致错误结果。而且我说的不是什么冷门运算符——减法也需要操作数按正确顺序排列。

这只是 OpAdd 实现的开始，VM 测试仍然失败，所以让我们用一个优雅的加法来完成它：

```go
// vm/vm.go

func (vm *VM) Run() error {
    // [...]
    switch op {
    // [...]

    case code.OpAdd:
```

## 连接 REPL

在继续之前，我们可以将编译器和 VM 连接到我们的 REPL。这样在我们想尝试 Monkey 时就能获得即时反馈。只需从 REPL 的 Start 函数中移除求值器和环境设置，并用我们测试中已知的编译器和 VM 调用替换即可：

```go
// repl/repl.go

import (
    "bufio"
    "fmt"
    "io"
    "monkey/compiler"
    "monkey/lexer"
    "monkey/parser"
    "monkey/vm"
)

func Start(in io.Reader, out io.Writer) {
    scanner := bufio.NewScanner(in)

    for {
        fmt.Printf(PROMPT)
        scanned := scanner.Scan()
        if !scanned {
            return
        }

        line := scanner.Text()
        l := lexer.New(line)
        p := parser.New(l)

        program := p.ParseProgram()
        if len(p.Errors()) != 0 {
            printParserErrors(out, p.Errors())
            continue
        }

        comp := compiler.New()
        err := comp.Compile(program)
        if err != nil {
            fmt.Fprintf(out, "Woops! Compilation failed:\n %s\n", err)
            continue
        }

        machine := vm.New(comp.Bytecode())
        err = machine.Run()
        if err != nil {
            fmt.Fprintf(out, "Woops! Executing bytecode failed:\n %s\n", err)
            continue
        }

        stackTop := machine.StackTop()
        io.WriteString(out, stackTop.Inspect())
        io.WriteString(out, "\n")
    }
}
```

首先我们对输入进行词法分析，然后解析它，然后编译并执行程序。我们还用打印 VM 栈顶的对象替换了之前打印 Eval 返回值的操作。

现在我们可以启动 REPL，看到编译器和 VM 在幕后工作：

```
$ go build -o monkey . && ./monkey
Hello mrnugget! This is the Monkey programming language!
Feel free to type in commands
>> 1
1
>> 1 + 2
3
>> 1 + 2 + 3
6
>> 1000 + 555
1555
```

很漂亮。但当然，一旦我们想要做的不止是加两个数字，情况就会崩溃：

```
>> 99 - 1
Woops! Compilation failed:
  unknown operator -
>> 80 / 2
Woops! Compilation failed:
  unknown operator /
```

我们还有工作要做。让我们开始吧。
