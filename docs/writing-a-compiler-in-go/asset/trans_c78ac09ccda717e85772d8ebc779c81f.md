

`false` 也不是 `null`。它的唯一操作数是一条指令的偏移量，VM 应跳转到该指令。`OpJump` 会告诉 VM“跳到那里”，而“那里”就是它的操作数，同样也是一条指令的偏移量。

这两个操作码的操作数都是 16 位宽。这与 `OpConstant` 的操作数宽度相同，这意味着我们无需扩展 `code` 包中的工具来支持它。

现在我们准备编写第一个测试。我们会从简单开始，只尝试处理没有 `else` 部分的条件语句。下面是我们希望编译器在输入一个单分支条件语句时生成的指令：

```
// compiler/compiler_test.go

func TestConditionals(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `
                if (true) { 10 }; 3333;
                `,
            expectedConstants: []interface{}{10, 3333},
            expectedInstructions: []code.Instructions{
                // 0000
                code.Make(code.OpTrue),
                // 0001
                code.Make(code.OpJumpNotTruthy, 7),
                // 0004
                code.Make(code.OpConstant, 0),
                // 0007
                code.Make(code.OpPop),
                // 0008
                code.Make(code.OpConstant, 1),
                // 0011
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

解析后，输入会变成一个 `*ast.IfExpression`，包含 `Condition` 和 `Consequence`。`Condition` 是布尔字面量 `true`，`Consequence` 是整数字面量 `10`。这两个都是特意选择的简单 Monkey 表达式，因为在这个测试用例中，我们并不关心表达式本身。我们关心的是编译器生成的跳转指令，以及这些指令是否带有正确的操作数。

这就是为什么我在 `expectedInstructions` 上添加了注释，这些注释显示了 `code.Make` 生成的指令的偏移量。我们以后不需要这些注释，但现在，它们帮助我们写出预期的跳转指令，尤其是因为我们要跳转到的指令的偏移量是基于每条指令占用的字节数。例如，一条 `opPop` 指令宽度为 1 字节，而一条 `opConstant` 指令占 3 字节。

我们期望编译器生成的第一条指令是 `opTrue`，告诉 VM 将 `vm.True` 压入栈。这就是 `Condition`。然后它应该生成一条 `opJumpNotTruthy` 指令，使 VM 跳过错 `Consequence`，而 `Consequence` 是将整数 `10` 加载到栈上的 `opConstant` 指令。

但是，第一条 `opPop` 指令（偏移量 `0007`）是从哪里来的？它不是 `Consequence` 的一部分，不是。它之所以存在，是因为 Monkey 中的条件语句是表达式——`if (true) { 10 }` 求值为 `10`——而值为未使用的独立表达式会被包装在 `*ast.ExpressionStatement` 中。我们编译这些表达式时会附加一条 `opPop` 指令来清理 VM 的栈。因此，第一个 `opPop` 是整个条件语句*之后*的第一条指令，这使得它的偏移量成为 `opJumpNotTruthy` 为了跳过 `Consequence` 而需要跳转到的位置。

所以现在你可能想知道 Monkey 代码中的 `3333;` 是干什么的。它作为一个参照点。并不是严格必需的，但为了确保跳转偏移量正确，在代码中有一个表达式能让我们轻松地在生成的指令中找到它，并作为路标告诉我们*不*应该跳转到哪里。当然，加载 `3333` 的 `opConstant 1` 指令后面也跟随着一条 `opPop` 指令，因为它是一个表达式语句。

对一个测试来说，这个解释已经相当长了。下面是编译器对其理解程度：

```
$ go test ./compiler
--- FAIL: TestConditionals (0.00s)
    compiler_test.go:195: testInstructions failed: wrong instructions length.
    want="0000 opTrue\n0001 opJumpNotTruthy 7\n0004 opConstant 0\n0007 opPop\
    \n0008 opConstant 1\n0011 opPop\n"
    got  ="0000 opPop\n0001 opConstant 0\n0004 opPop\n"
FAIL
FAIL    monkey/compiler 0.008s
```

条件的条件部分和结果部分都没有被编译。实际上，整个 `*ast.IfExpression` 都被编译器跳过了。我们可以通过扩展编译器的 `Compile` 方法来解决第一个问题（条件未被编译）：

```
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 

    case *ast.IfExpression:
        err := c.Compile(node.Condition)
        if err != nil {
            return err
        }

    // [...] 
    }

    // [...] 
}
```

经过这一改动，编译器现在认识了 `*ast.IfExpression`，并生成表示 `node.Condition` 的指令。尽管 `Consequence` 和跳过它的条件跳转指令仍然缺失，但我们已经正确生成了六个指令中的四个：

```
$ go test ./compiler
--- FAIL: TestConditionals (0.00s)
    compiler_test.go:195: testInstructions failed: wrong instructions length.
    want="0000 OpTrue\n0001 OpJumpNotTruthy 7\n0004 OpConstant 0\n0007 OpPop\n\n0008 OpConstant 1\n0011 OpPop\n"
    got ="0000 OpTrue\n0001 OpPop\n0002 OpConstant 0\n0005 OpPop\n"
FAIL
FAIL    monkey/compiler 0.009s
```

`OpTrue` 指令在那里，最后三条也在：`*ast.IfExpression` 后面的 `OpPop`、加载 `3333` 的 `OpConstant`，以及它后面的 `OpPop`，顺序都正确。现在剩下的就是生成 `OpJumpNotTruthy` 指令以及表示 `node.Consequence` 的指令。

当然，我说的“现在剩下的”意思是：“这里开始变得棘手了”。现在的挑战是生成一条 `OpJumpNotTruthy` 指令，其偏移量指向 `node.Consequence` 的指令之后——但在编译 `node.Consequence` 之前。

当我们还不知道需要跳多远时，该使用哪个偏移量？答案是一种相当务实的做法：“先随便放个值，之后再来修”。你可能会笑，但我是认真的。让我们用一个假偏移量，稍后再修复它：

```
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 
    
    case *ast.IfExpression:
        err := c.Compile(node.Condition)
        if err != nil {
            return err
        }
        
        // Emit an `OpJumpNotTruthy` with a bogus value
        c.emit(code.OpJumpNotTruthy, 9999)
        
        err = c.Compile(node.Consequence)
        if err != nil {
            return err
        }
        
        // [...] 
    }
    
    // [...] 
}
```

尽管大多数程序员看到代码中的 `9999` 时已经会眯起眼睛，本能地感觉到有什么不对劲，但此处的一行内联注释有助于明确意图。因为在这里，我们确实想要生成一条带垃圾偏移量的 `OpJumpNotTruthy` 指令，然后再编译 `node.Consequence`。同样，`9999` 不是最终会进入 VM 的内容，我们稍后会处理它。但目前，它应该能让我们的测试获得更多正确的指令。

但是，不，我们只多了一条正确的指令，那就是 `OpJumpNotTruthy` 本身：

```
$ go test ./compiler
--- FAIL: TestConditionals (0.00s)
compiler_test.go:195: testInstructions failed: wrong instructions length.
want="0000 OpTrue\n0001 OpJumpNotTruthy 7\n0004 OpConstant 0\n0007 OpPop\n\
0008 OpConstant 1\n0011 OpPop\n"
got ="0000 OpTrue\n0001 OpJumpNotTruthy 9999\n0004 OpPop\n\
0005 OpConstant 0\n0008 OpPop\n"
FAIL
```

```
FAIL    monkey/compiler 0.008s
```

虽然我们有了 `OpJumpNotTruthy 9999` 指令，但显然还没有编译 `Consequence`。

那是因为它是一个 `*ast.BlockStatement`，而我们的编译器还不知道它。为了编译它，我们需要给 `Compile` 方法再增加一个 case 分支：

```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...]

    case *ast.BlockStatement:
        for _, s := range node.Statements {
            err := c.Compile(s)
            if err != nil {
                return err
            }
        }

    // [...]
    }

    // [...]
}
```

这与我们在 `*ast.Program` 分支中已有的代码完全相同。而且它能工作：

```
$ go test ./compiler
--- FAIL: TestConditionals (0.00s)
compiler_test.go:195: testInstructions failed: wrong instructions length.
want="0000 OpTrue\n0001 OpJumpNotTruthy 7\n0004 OpConstant 0\n\
  0007 OpPop\n0008 OpConstant 1\n0011 OpPop\n"
got ="0000 OpTrue\n0001 OpJumpNotTruthy 9999\n0004 OpConstant 0\n\
  0007 OpPop\n0008 OpPop\n0009 OpConstant 1\n0012 OpPop\n"
FAIL
FAIL    monkey/compiler 0.010s
```

我们越来越接近了。但是，除了那个我们并不指望它会神奇消失的虚假 `9999` 偏移量之外，输出中还出现了一个新的问题，一个更微妙的问题。你可能已经忽略了它，所以让我指出来：编译器在位置 `0007` 生成了额外的 `OpPop` 指令。它的来源是 `node.Consequence` 的编译——它是一个表达式语句。

我们需要去掉这个 `OpPop`，因为我们希望 `Consequence` 和

