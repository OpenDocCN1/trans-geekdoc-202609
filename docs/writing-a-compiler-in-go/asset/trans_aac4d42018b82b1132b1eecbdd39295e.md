

```
// [...]
"monkey/object"
// [...]
)

func Start(in io.Reader, out io.Writer) {
    scanner := bufio.NewScanner(in)

    constants := []object.Object{}
    globals := make([]object.Object, vm.GlobalsSize)
    symbolTable := compiler.NewSymbolTable()

    for {
        // [...]

        comp := compiler.NewWithState(symbolTable, constants)
        err := comp.Compile(program)
        if err != nil {
            fmt.Fprintf(out, "woops! Compilation failed:\n %s\n", err)
            continue
        }

        code := comp.Bytecode()
        constants = code.Constants

        machine := vm.NewWithGlobalsStore(code, globals)
        // [...]
    }
}
```

我们分配了一个常量切片、一个全局变量存储和一个 symbolTable。然后，在循环的每次迭代中，我们把 symbolTable 和常量传给编译器，使它能够继续之前的工作，而不是从头开始。编译器完成之后，我们会更新 constants 引用。这是必要的，因为编译器在内部使用 append，而我们之前分配的常量切片并不是最终输出的结果。由于常量已经包含在字节码中，我们不需要显式地把它们传给 VM 的构造函数，只需要传入 globals。

现在，我们已经在 REPL 中拥有了全局状态，这让我们可以把输入的每一行都当作同一个程序的一部分，尽管我们每次按回车时都会重新开始编译和执行流程。问题解决了。现在我们可以在 REPL 中尽情体验全局绑定：

```
$ go build -o monkey . && ./monkey
Hello mrnugget! This is the Monkey programming language!
Feel free to type in commands
>> let a = 1;
1
>> let b = 2;
2
>> let c = a + b;
3
>> c
3
```

是时候后仰一下，深吸一口气了，因为在接下来的章节中，我们将在目前已完成的基础上继续构建，并把所有内容组合起来。那将会非常精彩。

## 字符串、数组与哈希

就目前的形式而言，我们的编译器和 VM 只支持 Monkey 的三种数据类型：整数、布尔值和 null。但还有另外三种：字符串、数组和哈希。我们在上一本书中已经把它们全部实现了，现在是把它们也加入我们这个新的 Monkey 实现的时候了。

这并不意味着我们需要把在《用 Go 编写解释器》中做过的所有事情重做一遍。这些数据类型在对象系统中的表示仍然存在——object.String、object.Array 和 object.Hash——我们可以直接复用它们，这意味着我们能够把精力集中在实现中那些新颖的部分。

本章的目标是把字符串、数组和哈希数据类型加入编译器和 VM，这样我们最终就能执行下面这段 Monkey 代码：

```
[1, 2, 3][1]
// => 2

{"one": 1, "two": 2, "three": 3}["o" + "ne"]
// => 1
```

如你所见，除了要支持字面量和数据类型本身，我们还需要实现字符串拼接，以及数组和哈希的下标运算符，才能让这段代码正常运行。

我们将从实现对 object.String 的支持开始。

### 字符串

由于字符串字面量的值在编译期和运行期之间不会改变，我们可以把它们当作常量表达式。与整数字面量的实现类似，我们可以在编译期把它们转换成 *object.String，并添加到 compiler.Bytecode 的常量池中。

从整数字面量的实现中我们也知道，这在编译器里只需要几行代码。那么何不增加些许挑战呢？除了实现字符串字面量之外，我们还要在本节中实现字符串拼接，也就是用 + 运算符把两个字符串连接起来。

本章的第一个编译器测试期望这两者都能正常工作：

```
// compiler/compiler_test.go

func TestStringExpressions(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `"monkey"`,
            expectedConstants: []interface{}{"monkey"},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpPop),
            },
        },
        {
            input: `"mon" + "key"`,
            expectedConstants: []interface{}{"mon", "key"},
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

这两个测试用例中的第一个确保编译器知道如何把字符串字面量视为常量；第二个测试则断言可以使用 + 中缀运算符对它们进行拼接。

值得注意的是，我们不需要任何新的操作码。我们已经有了所需的操作码：我们有将常量表达式加载到栈上的 OpConstant，也有将两个值相加的 OpAdd。

这两个操作码的用法也没有变化。OpConstant 的操作数仍然是常量在常量池中的索引，OpAdd 仍然期望它的两个操作数位于栈顶——无论它们是 *object.Integers 还是 *object.Strings。

新的地方在于，我们现在期望常量池中出现字符串。这意味着我们需要测试 bytecode.Constants 是否包含正确的 *object.Strings，而要完成这一点，我们需要在 testConstants 函数中再添加一个 case 分支：

```
// compiler/compiler_test.go

func testConstants(
    t *testing.T,
    expected []interface{},
    actual []object.Object,
) error {
    // [...] 

    for i, constant := range expected {
        switch constant := constant.(type) {
        // [...] 

        case string:
            err := testStringObject(constant, actual[i])
            if err != nil {
                return fmt.Errorf("constant %d - testStringObject failed: %s",
                    i, err)
            }
        }
    }

    return nil
}

func testStringObject(expected string, actual object.Object) error {
    result, ok := actual.(*object.String)
    if !ok {
        return fmt.Errorf("object is not String. got=%T (%v)",
            actual, actual)
    }

    if result.Value != expected {
        return fmt.Errorf("object has wrong value. got=%q, want=%q",
            result.Value, expected)
    }

    return nil
}
```

testConstants 中新增的 string case 分支伴随着新的 testStringObject 函数，后者与现有的 testIntegerObject 相呼应，确保常量是我们期望的字符串。

当我们现在运行测试时，可以看到期望的常量并不是问题所在（至少目前还不是），但指令却有问题：

```
$ go test ./compiler
--- FAIL: TestStringExpressions (0.00s)
    compiler_test.go:410: testInstructions failed: wrong instructions length.
    want="0000 OpConstant 0\n0003 OpPop\n"
    got ="0000 OpPop\n"
FAIL
FAIL    monkey/compiler 0.009s
```

我们并不是没有预料到这一点。我们需要在编译字符串字面量时发出 OpConstant 指令。为此，我们必须修改编译器的 Compile 方法，让它能够处理 *ast.StringLiterals，并从中创建 *object.String：

```
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 
    case *ast.StringLiteral:
        str := &object.String{Value: node.Value}
        c.emit(code.OpConstant, c.addConstant(str))
    // [...] 
    }
    // [...] 
}
```

除了一个变量名和一个标识符之外，这个分支就是 *ast.IntegerLiterals 对应分支的复制。我们从 AST 节点中取出值，创建一个对象，然后把它加入常量池。

### 向正确方向迈出的一步：

```
$ go test ./compiler
ok      monkey/compiler 0.009s
```

太棒了，两个测试都通过了。注意，我们并没有做什么特殊的事情来生成 OpAdd 指令，以实现字符串拼接。编译器通过编译 *ast.InfixExpressions 的 Left 和 Right 节点，已经处理好了这一切。

