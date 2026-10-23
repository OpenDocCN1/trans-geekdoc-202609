
这个测试用例现在简洁地说明了我们未来想要对 OpPop 做什么。第一个表达式语句，即字面量 1，后面应该跟一个 OpPop 指令。一直如此。但第二个表达式语句，即 2，是隐式返回值，OpPop 指令必须被 OpReturnValue 指令替换。

现在我们有两个失败的测试用例需要修复，而测试输出实际上非常有帮助：

```
$ go test ./compiler
--- FAIL: TestFunctions (0.00s)
    compiler_test.go:693: testConstants failed: constant 2
        testInstructions failed: wrong instruction at 7.
    want="0000 OpConstant 0\n0003 OpConstant 1\n0006 OpAdd\n0007 OpReturnValue\n"
    got ="0000 OpConstant 0\n0003 OpConstant 1\n0006 OpAdd\n0007 OpPop\n"
FAIL
FAIL      monkey/compiler 0.009s
```

正如预期的那样，函数中的最后一个表达式语句并未被转换为隐式返回值，而是仍然跟随一个 OpPop 指令。

修复它的正确时机是在编译完函数体之后、在离开作用域之前。此时我们仍然可以访问刚刚发出的指令。我们可以检查最后一条指令是否为 OpPop 指令，如果需要的话将其转换为 OpReturnValue。

为了让必要的更改更容易，我们重构并将现有的 lastInstructionIsPop 方法改为更通用的 lastInstructionIs，并添加了一个防御性检查：

```go
// compiler/compiler.go

func (c *Compiler) lastInstructionIs(op code.Opcode) bool {
    if len(c.currentInstructions()) == 0 {
        return false
    }

    return c.scopes[c.scopeIndex].lastInstruction.Opcode == op
}
```

这需要更改之前调用 lastInstructionIsPop 的位置：

```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 
    case *ast.IfExpression:
        // [...] 

        if c.lastInstructionIs(code.OpPop) {
            c.removeLastPop()
        }

        // [...] 

        if node.Alternative == nil {
            // [...] 
        } else {
            // [...] 
            if c.lastInstructionIs(code.OpPop) {
                c.removeLastPop()
            }
            // [...] 
        }

        // [...] 
    }

    // [...] 
}
```

我们现在可以更改 Compile 方法中 case *ast.FunctionLiteral 分支，使用 c.lastInstructionIs：

```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 

    case *ast.FunctionLiteral:
        c.enterScope()

        err := c.Compile(node.Body)
        if err != nil {
            return err
        }

        if c.lastInstructionIs(code.OpPop) {
            c.replaceLastPopWithReturn()
        }

        instructions := c.leaveScope()

        compiledFn := &object.CompiledFunction{Instructions: instructions}
        c.emit(code.OpConstant, c.addConstant(compiledFn))

    // [...] 
    }
}
```

```go
// [...]
}

func (c *Compiler) replaceLastPopWithReturn() {
    lastPos := c.scopes[c.scopeIndex].lastInstruction.Position
    c.replaceInstruction(lastPos, code.Make(code.OpReturnValue))

    c.scopes[c.scopeIndex].lastInstruction.Opcode = code.OpReturnValue
}
```

在编译完函数体后，我们检查最后发出的指令是否为 `OpPop`，如果是，就将其替换为 `OpReturnValue`。这是一个直接的更改，两个新的测试用例现在通过了：

```text
$ go test ./compiler
ok      monkey/compiler 0.008s
```

但是为什么我们在只再次检查 `OpPop` 的情况下还要重构 `lastInstructionIsPop` 为 `lastInstructionIs` 并添加额外的安全检查呢？嗯，因为我们还没做完。仍然存在这个令人困扰的边缘情况：一个没有体的函数。我保证，不过我们已经接近终点了。

我们希望编译器将空的函数体转换为单个 `OpReturn` 指令：

```go
// compiler/compiler_test.go

func TestFunctionsWithoutReturnValue(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `fn() { }`,
            expectedConstants: []interface{}{
                []code.Instructions{
                    code.Make(code.OpReturn),
                },
            },
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

这个失败，姑且可以说，是很漂亮的：

```text
$ go test ./compiler
--- FAIL: TestFunctionsWithoutReturnValue (0.00s)
compiler_test.go:772: testConstants failed: constant 0
testInstructions failed: wrong instructions length.
want="0000 OpReturn\n"
got =""
FAIL
FAIL	monkey/compiler 0.009s
```

我们想要一个 OpReturn 指令，但什么也没得到。不能再具体了，对吧？这个问题的修复也相当漂亮，有它自己的简洁方式：

```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...]

    case *ast.FunctionLiteral:
        // [...]

        if c.lastInstructionIs(code.OpPop) {
            c.replaceLastPopWithReturn()
        }
        if !c.lastInstructionIs(code.OpReturnValue) {
            c.emit(code.OpReturn)
        }
        // [...]

        // [...]
    }

    // [...]
}
```

首先检查是否需要将 OpPop 指令替换为 OpReturnValue。我们已经有了这个。它应该将函数体中的每个最后语句转换为 OpReturnValue。要么因为它本来就是显式的 *ast.ReturnStatement，要么因为我们现在将其更改了。

但如果不是这种情况——这是新的——这意味着我们要么在函数体中没有任何语句，要么只有无法转换为 OpReturnValue 指令的语句。目前我们关注的是前者，但很快我们会谈到后者。现在，我们在两种情况下都发出 OpReturn。

而现在，这个边缘情况也修复了，我们终于准备好庆祝了：

```
$ go test ./compiler
ok	monkey/compiler 0.009s
```

酷！我们现在可以正确编译函数字面量了！

这确实是一个值得庆祝的理由：我们将函数字面量转换为 `*object.CompiledFunction`，处理函数体中的隐式和显式返回，并在 VM 中发出 `OpConstant` 指令将函数加载到栈上。为此干杯！

在编译方面，我们已经到达了中点。剩下的路是函数 *calls* 的编译。

## 编译函数调用

在打开 `compiler_test.go` 并开始敲定测试用例之前，让我们退一步思考一下。我们想要实现函数调用。换句话说，我们需要发出指令来表示 Monkey 的字节码调用约定，因为这就是在 Monkey 字节码中调用函数的方式。

在本章开始时，我们决定调用约定的开始是将要调用的函数放到栈上。我们已经知道怎么做了。要么使用 `OpConstant` 指令，如果是正在调用的函数字面量，看起来像这样：

```
fn() { 1 + 2 }()
```

或者使用 `OpGetGlobal` 指令，如果函数之前已绑定到名称：

```
let onePlusTwo = fn() { 1 + 2 };
onePlusTwo();
```

这两种选项都会使我们想要调用的 `*object.CompiledFunction` 位于栈上。为了现在执行其指令，我们需要发出一个 `OpCall` 指令。

然后 VM 执行函数的指令，完成后，它会将函数本身从栈中弹出并用返回值替换。如果有返回值的话。如果没有，它只会将函数从栈中弹出，这也没问题。

调用约定的这一整部分——VM 在执行完函数后对其做什么——是隐式的：我们不需要发出 `OpPop` 指令来将函数从栈中弹出。它是约定的一部分，我们将直接将其构建到 VM 中。

在你开始抓头之前，请记住，一旦我们引入函数调用的参数，约定就会改变。这就是为什么目前没有提到它们的原因。

不过现在，我们对需要做什么相当确定。当编译器遇到 `*ast.CallExpression` 时，它应该这样做：

```go
// compiler/compiler_test.go

func TestFunctionCalls(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `fn() { 24 }()`,
            expectedConstants: []interface{}{
                24,
                []code.Instructions{
                    code.Make(code.OpConstant, 0), // The literal "24"
                    code.Make(code.OpReturnValue),
                },
            },
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 1), // The compiled function
                code.Make(code.OpCall),
                code.Make(code.OpPop),
            },
        },
        {
            input: `
let noArg = fn() { 24 };
noArg();
`,
            expectedConstants: []interface{}{
                24,
                []code.Instructions{
                    code.Make(code.OpConstant, 0), // The literal "24"
                    code.Make(code.OpReturnValue),
                },
            },
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 1), // The compiled function
                code.Make(code.OpSetGlobal, 0),
                code.Make(code.OpGetGlobal, 0),
                code.Make(code.OpCall),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

两个测试用例中被调用的函数是有意保持简单的，因为这里的重点是 OpCall 指令，以及它前面是 OpGetGlobal 还是 OpConstant 指令。
