

我们在此测试编译器上的两个新方法：enterScope 和 leaveScope。它们应当如其名称所承诺的那样，通过在新的作用域栈上压入和弹出 CompilationScopes 指令，来改变 emit 的行为。这个测试背后的主要想法是确保在一个作用域中发射的指令不会对另一个作用域中的指令产生影响。

由于这些方法尚不存在，测试会失败。我就不展示输出了。不过，让它们通过测试对我们来说很自然，因为这归结为使用某种栈，而我们现在已经非常擅长了。

首先，我们必须从 compiler 中移除 instructions、lastInstruction 和 previousInstruction 字段，并在初始化新的 *Compiler 时用一个 CompilationScope 来替换它们：

```
// compiler/compiler.go

type Compiler struct {
    constants []object.Object

    symbolTable *SymbolTable

    scopes      []CompilationScope
    scopeIndex int
}

func New() *Compiler {
    mainScope := CompilationScope{
        instructions:      code.Instructions{},
        lastInstruction:   EmittedInstruction{},
        previousInstruction: EmittedInstruction{},
    }

    return &Compiler{
        constants:  []object.Object{},
        symbolTable: NewSymbolTable(),
        scopes:     []CompilationScope{mainScope},
        scopeIndex: 0,
    }
}
```

现在我们需要更新对已移除字段的所有引用，改为使用当前作用域。为了帮助实现这一点，我们添加一个名为 currentInstructions 的新方法：

```
// compiler/compiler.go

func (c *Compiler) currentInstructions() code.Instructions {
    return c.scopes[c.scopeIndex].instructions
}
```

现在可以在 addInstruction 中使用它，emit 方法正是通过它来完成其工作：

```
// compiler/compiler.go

func (c *Compiler) addInstruction(ins []byte) int {
    posNewInstruction := len(c.currentInstructions())
    updatedInstructions := append(c.currentInstructions(), ins...)

    c.scopes[c.scopeIndex].instructions = updatedInstructions

    return posNewInstruction
}
```

这里我们首先使用 c.currentInstructions 获取当前的指令切片，然后为了修改它们，我们在栈上替换它们。

在编译器的其他辅助方法中，我们之前直接访问 instructions、lastInstruction 和 previousInstruction 字段，现在也必须通过栈来访问：

```
// compiler/compiler.go

func (c *Compiler) setLastInstruction(op code.Opcode, pos int) {
    previous := c.scopes[c.scopeIndex].lastInstruction
    last := EmittedInstruction{Opcode: op, Position: pos}

    c.scopes[c.scopeIndex].previousInstruction = previous
    c.scopes[c.scopeIndex].lastInstruction = last
}

func (c *Compiler) lastInstructionIsPop() bool {
    return c.scopes[c.scopeIndex].lastInstruction.Opcode == code.OpPop
}

func (c *Compiler) removeLastPop() {
    last := c.scopes[c.scopeIndex].lastInstruction
    previous := c.scopes[c.scopeIndex].previousInstruction

    old := c.currentInstructions()
    new := old[:last.Position]

    c.scopes[c.scopeIndex].instructions = new
    c.scopes[c.scopeIndex].lastInstruction = previous
}

func (c *Compiler) replaceInstruction(pos int, newInstruction []byte) {
    ins := c.currentInstructions()

    for i := 0; i < len(newInstruction); i++ {
        ins[pos+i] = newInstruction[i]
    }
}
```

```go
func (c *Compiler) changeOperand(opPos int, operand int) {
	op := code.OpCode(c.currentInstructions()[opPos])
	newInstruction := code.Make(op, operand)

	c.replaceInstruction(opPos, newInstruction)
}
```

然后，我们需要在 Compile 方法的核心处做一些更精细的修改：之前访问 `c.instructions` 的地方，现在需要切换为调用 `c.currentInstructions()`：

```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
	switch node := node.(type) {
	// [...]
	case *ast.IfExpression:
		// [...]

		afterConsequencePos := len(c.currentInstructions())
		c.changeOperand(jumpNotTruthyPos, afterConsequencePos)

		// [...]

		afterAlternativePos := len(c.currentInstructions())
		c.changeOperand(jumpPos, afterAlternativePos)

	// [...]
	}

	// [...]
}
```

当我们需要返回编译器产生的字节码时，也需要返回当前指令：

```go
// compiler/compiler.go

func (c *Compiler) Bytecode() *Bytecode {
	return &Bytecode{
		Instructions: c.currentInstructions(),
		Constants:    c.constants,
	}
}
```

最后，我们准备添加新的 `enterScope` 和 `leaveScope` 方法：

```go
// compiler/compiler.go

func (c *Compiler) enterScope() {
	scope := CompilationScope{
		instructions:        code.Instructions{},
		lastInstruction:     EmittedInstruction{},
```

```
c.enterScope()

err := c.Compile(node.Body)
if err != nil {
    return err
}

instructions := c.leaveScope()

compiledFn := &object.CompiledFunction{Instructions: instructions}
c.emit(code.OpConstant, c.addConstant(compiledFn))

// [...] 
}

// [...] 
}
```

这段代码片段围绕一个核心思想：在编译函数时改变所生成指令的存储位置。

因此，当我们遇到 *ast.FunctionLiteral 时，第一件事就是调用 c.enterScope 进入一个新的作用域。然后我们编译 node.Body，也就是构成函数体的 AST 节点。之后，我们通过调用 c.leaveScope 从 CompilationScopes 栈中取出刚填充的指令切片，创建一个持有这些指令的新的 *object.CompiledFunction，并将该函数添加到常量池。

## 完成，函数已编译：

```
$ go test ./compiler
--- FAIL: TestFunctions (0.00s)
compiler_test.go:654: testInstructions failed: wrong instruction at 2.
    want="0000 OpConstant 2\n0003 OpPop\n"
    got ="0000 OpConstant 0\n0003 OpPop\n"
FAIL
FAIL    monkey/compiler 0.008s
```

唉。事实证明，我们确实知道如何编译函数字面量，但不知道如何编译 *ast.ReturnStatements。而且由于测试中的函数体只不过是一个单独的 return 语句，我们并没有编译该函数的任何内容。我们只创建了一个没有指令的 *object.CompiledFunction 常量。

我们的测试基础设施还不够先进，无法用精确的错误信息指出问题的根源。不过，你可以相信我，我已经替我们俩做了深入排查。

```go
expectedConstants: []interface{}{
    5,
    10,
},
expectedInstructions: []code.Instructions{
    code.Make(code.OpConstant, 0),
    code.Make(code.OpConstant, 1),
    code.Make(code.OpAdd),
    code.Make(code.OpReturnValue),
},
},
},
expectedInstructions: []code.Instructions{
    code.Make(code.OpConstant, 2),
    code.Make(code.OpPop),
},
},
},
}

runCompilerTests(t, tests)
}
```

我们已经知道，解决这个问题涉及 OpPop 指令，因为在这个测试用例中，我们期望编译器去掉它在函数体最后一个表达式语句之后会发射的 OpPop。我们不希望任何东西将隐式返回值从栈中取出。不过，在其他情况下，我们仍然希望保留 OpPop 指令，而且在最终完全没有 OpPop 之前，让我们确保在需要它们的情况下它们能留在原处，并添加另一个测试用例：

```go
// compiler/compiler_test.go

func TestFunctions(t *testing.T) {
    tests := []compilerTestCase{
        // [...]
        {
            input: `fn() { 1; 2 }`,
            expectedConstants: []interface{}{
                1,
                2,
            },
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpPop),
                code.Make(code.OpConstant, 1),
                code.Make(code.OpReturnValue),
            },
        },
        expectedInstructions: []code.Instructions{
            code.Make(code.OpConstant, 2),
            code.Make(code.OpPop),
        },
    },
}

runCompilerTests(t, tests)
}
```

