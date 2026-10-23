
## 编译表达式

在之前的两章中，我们学习了很多新奇且奇怪的东西，构建了一个微型编译器、一个虚拟机并定义了字节码指令。在这一章中，我们将利用我们对字节码编译和执行的全新认识，并结合第一本书中的知识，为 Monkey 支持的所有中缀和前缀运算符添加支持。

这不仅使我们能够熟悉代码库并进一步扩展其基础设施，还能让我们喘口气。况且，在继续之前我们还有一些清理工作要做。最需要打扫的东西？我们的栈。

### 清理栈

在当前状态下，我们的编译器和 VM 唯一能做的就是加两个数字。给它们表达式 1 + 2，我们的 VM 会正确地将 3 放在其栈上。这正是我们想要的，但暗中潜伏着一个问题：3 会一直留在栈上，如果我们不采取措施，它将永远留在那里。

问题不在于表达式 1 + 2 本身，而在于它出现的位置。它是表达式语句的一部分。快速回顾一下，Monkey 中有三种语句类型：let 语句、return 语句和表达式语句。前两种显式地重用其子表达式节点产生的值，而表达式语句只是包装表达式，使其可以独立出现。根据定义，它们产生的值不会被重用。但现在我们的問題是我們確實重用了它，因為我們無意中把它保留在栈上。

看看下面的 Monkey 程序：

```
1;
2;
3;
```

那是三个独立的表达式语句。你知道栈上最终会有什么吗？不仅仅是最后产生的值 3，而是全部：1、2 和 3。如果我们有一个由大量表达式语句组成的 Monkey 程序，我们可能会不小心填满栈。这不好。

为了修复这个问题，我们需要做两件事。首先，我们需要定义一个新的操作码，告诉 VM 从栈顶弹出元素。其次，我们需要在每个表达式语句之后发出这个操作码。

我们从操作码的定义开始，恰如其名 OpPop：

// code/code.go
const (
    // [ ... ]

    OpPop
)
```
```
var definitions = map[Opcode]*Definition{
    // [...] 
    OpPop:    {"OpPop", []int{}},
}
```

OpPop 没有任何操作数，就像 OpAdd 一样。它的唯一工作是告诉 VM 弹出栈顶元素，为此它不需要操作数。

现在我们需要使用这个新的操作码在每个表达式语句之后清理栈。幸运的是，在我们的测试套件中断言这种新行为很容易，因为我们目前还没有很多编译器测试，这也是我认为现在引入 OpPop 而不是两章之后引入是明智的原因。我们只需要更改 TestIntegerArithmetic 中的单个测试用例：

// compiler/compiler_test.go

func TestIntegerArithmetic(t *testing.T) {
    tests := []compilerTestCase{
        {
            input:            "1 + 2",
            expectedConstants: []interface{}{1, 2},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpConstant, 1),
                code.Make(code.OpAdd),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

这里唯一的更改是包含 code.Make(code.OpPop) 调用的新行。我们断言编译后的表达式语句后面应该跟随一个 OpPop 指令。可以通过添加另一个包含多个表达式语句的测试使期望的行为更加清晰：

// compiler/compiler_test.go

func TestIntegerArithmetic(t *testing.T) {
    tests := []compilerTestCase{
        // [...] 
        {
            input:            "1; 2",
            expectedConstants: []interface{}{1, 2},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpPop),
                code.Make(code.OpConstant, 1),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

请注意分隔 `1` 和 `2` 的 `;`。这两个整数字面量是独立的表达式语句，在每个语句之后都应发出 `OpPop` 指令。这不是当前发生的情况。相反，我们告诉 VM 通过将常量加载到栈上来填满其栈：

```text
$ go test ./compiler
        --- FAIL: TestIntegerArithmetic (0.00s)
compiler_test.go:37: testInstructions failed: wrong instructions length.
  want="0000 OpConstant 0\n0003 OpConstant 1\n0006 OpAdd\n0007 OpPop\n"
  got ="0000 OpConstant 0\n0003 OpConstant 1\n0006 OpAdd\n"
FAIL
FAIL    monkey/compiler  0.007s
```

但好消息来了。为了修复这个问题并正确清理栈，我们所需要做的只是在编译器中添加一次对 `c.emit` 的调用：

```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...]

    case *ast.ExpressionStatement:
        err := c.Compile(node.Expression)
        if err != nil {
            return err
        }
        c.emit(code.OpPop)

    // [...]
    }

    // [...]
}
```

在编译 `*ast.ExpressionStatement` 的 `node.Expression` 之后，我们发出一个 `OpPop`。就这么简单：

```text
$ go test ./compiler
ok      monkey/compiler  0.006s
```

好吧，这并不 *全部* 是它所需要的。我们仍然有一些工作要做，因为现在我们需要告诉我们的 VM 如何处理这个 `OpPop` 指令，如果不是因为我们的测试，这也只是一个微小的补充。

在我们的 VM 测试中，我们使用 `vm.StackTop` 来确保我们的 VM 将正确的内容放到其栈上，但有了 `OpPop` 之后我们就不能再这样做了。现在，我们想要断言的是“在你弹出它之前，亲爱的 VM，栈上应该是这个”。为了做到这一点，我们向我们的 VM 添加一个仅用于测试的方法，并去掉 `StackTop`：

```go
// vm/vm.go

func (vm *VM) LastPoppedStackElem() object.Object {
    return vm.stack[vm.sp]
}
```

根据我们的约定，`vm.sp` 总是指向 `vm.stack` 中 *下一个空闲* 槽。这是一个新元素将被推送的位置。但由于我们只通过递减 `vm.sp`（而不显式地将其设置为 `nil`）来弹出栈元素，这也是我们可以在其中找到之前栈顶元素的位置。有了 `LastPoppedStackElem`，我们可以更改我们的 VM 测试以确保 `OpPop` 确实被正确处理：

```go
// vm/vm_test.go

func runVmTests(t *testing.T, tests []vmTestCase) {
    t.Helper()

    for _, tt := range tests {
        // [...]

        stackElem := vm.LastPoppedStackElem()

        testExpectedObject(t, tt.expected, stackElem)
    }
}
```

我们将调用从 `vm.StackTop` 改为 `vm.LastPoppedStackElem`。这足以破坏我们的测试：

```text
$ go test ./vm
--- FAIL: TestIntegerArithmetic (0.00s)
vm_test.go:20: testIntegerObject failed:\
    object is not Integer. got=<nil> (<nil>)
vm_test.go:20: testIntegerObject failed:\
    object is not Integer. got=<nil> (<nil>)
vm_test.go:20: testIntegerObject failed:\
    object has wrong value. got=2, want=3
FAIL
FAIL    monkey/vm    0.007s
```

为了让它们再次通过，我们需要告诉我们的 VM 保持其栈干净整洁：

// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 
    case code.OpPop:
        vm.pop()
    }
    // [...] 
}
```

这样，栈的卫生就恢复了：

```
$ go test ./vm
ok      monkey/vm   0.006s
```

但我们也需要修复我们的 REPL，在那里我们仍然使用 StackTop，通过将其替换为 LastPoppedStackElem：

// repl/repl.go

func Start(in io.Reader, out io.Writer) {
    // [...] 
    for {
        // [...] 
        lastPopped := machine.LastPoppedStackElem()
        io.WriteString(out, lastPopped.Inspect())
        io.WriteString(out, "\n")
    }
}
```

完美！这意味着我们可以继续前进，并在栈上安全地进行更多算术运算，而不必担心栈在我们面前慢慢爆炸。
