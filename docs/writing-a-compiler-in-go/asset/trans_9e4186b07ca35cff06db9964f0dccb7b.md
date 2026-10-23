
```
Make(OpAdd),
Make(OpGetLocal, 1),
Make(OpConstant, 2),
Make(OpConstant, 65535),
Make(OpClosure, 65535, 255),
}

expected := `0000 OpAdd
0001 OpGetLocal 1
0003 OpConstant 2
0006 OpConstant 65535
0009 OpClosure 65535 255
`

// [...] 
}
```

```
func TestReadOperands(t *testing.T) {
    tests := []struct {
        op Opcode
        operands []int
        bytesRead int
    }{
        // [...] 
        {OpClosure, []int{65535, 255}, 3},
    }

    // [...] 
}
```

当我们现在运行 code 包的测试时，会看到以下内容：

```
$ go test ./code
--- FAIL: TestInstructionsString (0.00s)
code_test.go:56: instructions wrongly formatted.
    want="0000 OpAdd\n0001 OpGetLocal 1\n0003 OpConstant 2\n\
0006 OpConstant 65535\n0009 OpClosure 65535 255\n"
    got="0000 OpAdd\n0001 OpGetLocal 1\n0003 OpConstant 2\n\
0006 OpConstant 65535\n\
0009 ERROR: unhandled operandCount for OpClosure\n\n"
FAIL
FAIL    monkey/code 0.007s
```

看起来我们只需要修复 Instructions 上的 fmtInstruction 方法：

```
// code/code.go

func (ins Instructions) fmtInstruction(def *Definition, operands []int) string {
    // [...] 

    switch operandCount {
    case 0:
        return def.Name
    case 1:
        return fmt.Sprintf("%s %d", def.Name, operands[0])
    case 2:
```

```
return fmt.Sprintf("%s %d %d", def.Name, operands[0], operands[1])
}
// [...]
}
```

再添加一个 case 分支，我们就恢复正常了，因为 code.Make 和 code.ReadOperands 已经可以处理每个操作码的两个操作数：

```
$ go test ./code
ok      monkey/code 0.008s
```

我们已经铺平了道路，可以开始将函数视为闭包了。

在编译器的术语中，这意味着我们现在将发出 OpClosure 指令而不是 OpConstant 指令来将函数压入栈。目前其他一切保持不变。我们将函数编译为 *object.CompiledFunctions 并将其添加到常量池中。但我们不再取常量池的索引并将其用作 OpConstant 的操作数，而是将其传递给 OpClosure 指令。作为 OpClosure 的第二个操作数，表示栈上自由变量的数量，我们目前使用 0。

如果我们现在直接进入 compiler.go 并将 OpConstant 指令替换为 OpClosure 指令，我们将得到大量失败的编译器测试。意外的失败测试总是件坏事，所以让我们先主动解决问题并先调整测试。我们需要做的就是在我们期望函数被加载到栈上的任何地方，将 OpConstant 改为 OpClosure：

```
// compiler/compiler_test.go

func TestFunctions(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `fn() { return 5 + 10 }`,
            expectedConstants: []interface{}{
                // [...]
            },
            expectedInstructions: []code.Instructions{
                code.Make(code.OpClosure, 2, 0),
                code.Make(code.OpPop),
            },
        },
        {
            input: `fn() { 5 + 10 }`,
            expectedConstants: []interface{}{
                // [...]
            },
            expectedInstructions: []code.Instructions{
                code.Make(code.OpClosure, 2, 0),
```

```
    code.Make(code.OpPop),
},
{
    input: `fn() { 1; 2 }`,
    expectedConstants: []interface{}{
        // [...] 
    },
    expectedInstructions: []code.Instructions{
        code.Make(code.OpClosure, 2, 0),
        code.Make(code.OpPop),
    },
},
}

runCompilerTests(t, tests)
}
```

这看起来比实际要多，但那只是因为我想为这些更改提供一些上下文。在每个测试用例的 expectedInstructions 中，我们将之前的 OpConstant 改为 OpClosure 并添加第二个操作数 0。就这样。现在我们需要在加载函数的其他测试中做同样的事情：

```
// compiler/compiler_test.go

func TestFunctionsWithoutReturnValue(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `fn() { }`,
            expectedConstants: []interface{}{
                // [...] 
            },
            expectedInstructions: []code.Instructions{
                code.Make(code.OpClosure, 0, 0),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

```
func TestFunctionCalls(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `fn() { 24 }();`,
            expectedConstants: []interface{}{
                // [...] 
            },
            expectedInstructions: []code.Instructions{
                code.Make(code.OpClosure, 1, 0),
                code.Make(code.OpCall, 0),
                code.Make(code.OpPop),
            },
        },
```

```
},
{
    input: `
    let noArg = fn() { 24 };
    noArg();
    `
    expectedConstants: []interface{}{
        // [...] 
    },
    expectedInstructions: []code.Instructions{
        code.Make(code.OpClosure, 1, 0),
        code.Make(code.OpSetGlobal, 0),
        code.Make(code.OpGetGlobal, 0),
        code.Make(code.OpCall, 0),
        code.Make(code.OpPop),
    },
},
{
    input: `
    let oneArg = fn(a) { a };
    oneArg(1);
    `
    expectedConstants: []interface{}{
        // [...] 
    },
    expectedInstructions: []code.Instructions{
        code.Make(code.OpClosure, 0, 0),
        code.Make(code.OpSetGlobal, 0),
        code.Make(code.OpGetGlobal, 0),
        code.Make(code.OpConstant, 1),
        code.Make(code.OpCall, 1),
        code.Make(code.OpPop),
    },
},
{
    input: `
    let manyArg = fn(a, b, c) { a; b; c };
    manyArg(1, 2, 3);
    `
    expectedConstants: []interface{}{
        // [...] 
    },
    expectedInstructions: []code.Instructions{
        code.Make(code.OpClosure, 0, 0),
        code.Make(code.OpSetGlobal, 0),
        code.Make(code.OpGetGlobal, 0),
        code.Make(code.OpConstant, 1),
        code.Make(code.OpConstant, 2),
        code.Make(code.OpConstant, 3),
        code.Make(code.OpCall, 3),
        code.Make(code.OpPop),
    },
},
}

runCompilerTests(t, tests)
}

func TestLetStatementScopes(t *testing.T) {
```

```
tests := []compilerTestCase{
    {
        input: `
        let num = 55;
        fn() { num }`,
        expectedConstants: []interface{}{
            // [...] 
        },
        expectedInstructions: []code.Instructions{
            code.Make(code.OpConstant, 0),
            code.Make(code.OpSetGlobal, 0),
            code.Make(code.OpClosure, 1, 0),
            code.Make(code.OpPop),
        },
    },
    {
        input: `
        fn() {
            let num = 55;
            num
        }`,
        expectedConstants: []interface{}{
            // [...] 
        },
        expectedInstructions: []code.Instructions{
            code.Make(code.OpClosure, 1, 0),
            code.Make(code.OpPop),
        },
    },
    {
        input: `
        fn() {
            let a = 55;
            let b = 77;
            a + b
        }`,
        expectedConstants: []interface{}{
            // [...] 
        },
        expectedInstructions: []code.Instructions{
            code.Make(code.OpClosure, 2, 0),
            code.Make(code.OpPop),
        },
    },
}

    runCompilerTests(t, tests)
}

func TestBuiltins(t *testing.T) {
    tests := []compilerTestCase{
        // [...] 
        {
            input: `fn() { len([]) }`,
            expectedConstants: []interface{}{
                // [...] 
            },
        },
```

```
expectedInstructions: []code.Instructions{
    code.Make(code.OpClosure, 0, 0),
    code.Make(code.OpPop),
},
},
}
    runCompilerTests(t, tests)
}
```

在更新了期望但编译器仍然旧的情况下，我们现在有失败的测试：

```
$ go test ./compiler
--- FAIL: TestFunctions (0.00s)
compiler_test.go:688: testInstructions failed: wrong instructions length.
    want="0000 OpClosure 2 0\n0004 OpPop\n"
    got ="0000 OpConstant 2\n0003 OpPop\n"
--- FAIL: TestFunctionsWithoutReturnValue (0.00s)
compiler_test.go:779: testInstructions failed: wrong instructions length.
    want="0000 OpClosure 0 0\n0004 OpPop\n"
    got ="0000 OpConstant 0\n0003 OpPop\n"
--- FAIL: TestFunctionCalls (0.00s)
compiler_test.go:895: testInstructions failed: wrong instructions length.
    want="0000 OpClosure 1 0\n0004 OpCall 0\n0006 OpPop\n"
    got ="0000 OpConstant 1\n0003 OpCall 0\n0005 OpPop\n"
--- FAIL: TestLetStatementScopes (0.00s)
compiler_test.go:992: testInstructions failed: wrong instructions length.
    want="0000 OpConstant 0\n0003 OpSetGlobal 0\n\
    0006 OpClosure 1 0\n0010 OpPop\n"
    got ="0000 OpConstant 0\n0003 OpSetGlobal 0\n\
    0006 OpConstant 1\n0009 OpPop\n"
--- FAIL: TestBuiltins (0.00s)
compiler_test.go:1056: testInstructions failed: wrong instructions length.
    want="0000 OpClosure 0 0\n0004 OpPop\n"
    got ="0000 OpConstant 0\n0003 OpPop\n"
FAIL
FAIL    monkey/compiler 0.010s
```

正如预期的那样：我们想要 OpClosure 而不是 OpConstant。完美。现在我们可以更改编译器，这是一个多大的改动：

```
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 
    case *ast.FunctionLiteral:
        // [...] 
        fnIndex := c.addConstant(compiledFn)
        c.emit(code.OpClosure, fnIndex, 0)
    // [...] 
    }
}
```
