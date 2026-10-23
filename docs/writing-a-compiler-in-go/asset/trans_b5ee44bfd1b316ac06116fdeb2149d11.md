
```
$ go test ./vm
--- FAIL: TestCallingFunctionsWithArgumentsAndBindings (0.00s)
    vm_test.go:357: testIntegerObject failed:\
        object is not Integer. got=<nil> (<nil>)
panic: runtime error: \
    invalid memory address or nil pointer dereference [recovered]
panic: runtime error: invalid memory address or nil pointer dereference
[signal SIGSEGV: segmentation violation code=0x1 addr=0x20 pc=0x10f7841]

goroutine 13 [running]:
testing.tRunner.func1(0xc420a80f0)
/usr/local/go/src/testing/testing.go:742 +0x29d
panic(0x11215e0, 0x11fffa0)
/usr/local/go/src/runtime/panic.go:502 +0x229
monkey/vm.(*VM).executeBinaryOperation(0xc4204b3eb8, 0x1, 0x0, 0x0)
/Users/mrnugget/code/07/src/monkey/vm/vm.go:270 +0xa1
monkey/vm.(*VM).Run(0xc4204b3eb8, 0x10000, 0x10000)
/Users/mrnugget/code/07/src/monkey/vm/vm.go:87 +0x155
monkey/vm.runVmTests(0xc420a80f0, 0xc4204b3f58, 0x2, 0x2)
/Users/mrnugget/code/07/src/monkey/vm/vm_test.go:276 +0x5de
monkey/vm.TestCallingFunctionsWithArgumentsAndBindings(0xc420a80f0)
/Users/mrnugget/code/07/src/monkey/vm/vm_test.go:357 +0x93
testing.tRunner(0xc420a80f0, 0x11540e8)
/usr/local/go/src/testing/testing.go:777 +0xd0
created by testing.(*T).Run
/usr/local/go/src/testing/testing.go:824 +0x2e0
FAIL    monkey/vm    0.049s
```

第一个测试用例告诉我们，最后从栈中弹出的值不是预期的 4，而是 nil。好吧。显然 VM 找不到栈上的参数。

第二个测试用例没有提供任何信息就崩溃了。为什么会这样并不立刻显而易见，需要沿着堆栈跟踪向上追溯。一旦到达 vm.go，我们就找到了 panic 的原因：VM 试图对两个为相加而从栈中弹出的 nil 指针调用 object.Object.Type 方法。

两种失败归根结底是同一个问题：VM 试图在栈上找到参数，但得到的是 nil。

至少有些东西不工作，这有点是我们预期的。但话说回来，也不是真的。参数位于栈顶，正好在被调用的函数之上。那里本应存储局部绑定。而且由于我们把参数当作局部变量处理，并希望用 OpGetLocal 指令检索它们，它们本就应该在那里。这就是把参数当作局部变量处理的整个想法的精妙之处。那么为什么 VM 找不到它们呢？

简短回答：因为我们的栈指针太高了。我们初始化它的方式

![](img/ab2ef57dcaaed64759b089e71bfdb58d_277_0.png)

这样就能工作。有了这个，如果我们计算 `basePointer` 加上参数的局部绑定索引，就能得到正确的槽位。而且（双关语！）`vm.sp` 仍然会指向栈上的下一个空槽。完美！

以下是这个想法的代码实现：

```
```go
// vm/vm.go

func (vm *VM) Run() error {
    // […]
    switch op {
    // […]

    case code.OpCall:
        numArgs := code.ReadUInt8(ins[ip+1:])
        vm.currentFrame().ip += 1

        err := vm.callFunction(int(numArgs))
        if err != nil {
            return err
        }

    // […]
    }
    // […]
}

func (vm *VM) callFunction(numArgs int) error {
    fn, ok := vm.stack[vm.sp-1-numArgs].(*object.CompiledFunction)
    if !ok {
        return fmt.Errorf("calling non-function")
    }

    frame := NewFrame(fn, vm.sp-numArgs)
    vm.pushFrame(frame)

    vm.sp = frame.basePointer + fn.NumLocals

    return nil
}
```
```

在为时已晚之前，我们将 OpCall 实现的主要部分移到了一个新方法中，名为 callFunction。不过不要被骗了，实现本身几乎没有变化。唯一的区别是调用 NewFrame 时的第二个参数。我们不再直接传入 vm.sp 作为帧的未来 basePointer，而是先减去 numArgs。这就得到了如前图所示的 basePointer。

现在看一下：

```
$ go test ./vm
ok      monkey/vm   0.047s
```

我们的所有测试都通过了！让我们再大胆一点，给 VM 扔更多测试：

```
// vm/vm_test.go

func TestCallingFunctionsWithArgumentsAndBindings(t *testing.T) {
    tests := []vmTestCase {
        // [...] 
        {
            input: `
let sum = fn(a, b) {
    let c = a + b;
    c;
};
sum(1, 2);
`,
            expected: 3,
        },
        {
            input: `
let sum = fn(a, b) {
    let c = a + b;
    c;
};
sum(1, 2) + sum(3, 4);`,
            expected: 10,
        },
        {
            input: `
let sum = fn(a, b) {
    let c = a + b;
    c;
};
let outer = fn() {
    sum(1, 2) + sum(3, 4);
};
outer();
`,
            expected: 10,
        },
    }
}
```

```
runVmTests(t, tests)
}
```

这些测试用例确保我们可以混合手动创建的局部绑定和参数：在一个函数中，或在同一个函数被多次调用时，或在一个函数中多次调用另一个函数。它们全部通过：

```
$ go test ./vm
ok      monkey/vm  0.041s
```

现在，让我们看看是否已经达到了目标：

```
// vm/vm_test.go

func TestCallingFunctionsWithArgumentsAndBindings(t *testing.T) {
    tests := []vmTestCase {
        // [...] 
        {
            input: `
let globalNum = 10;

let sum = fn(a, b) {
    let c = a + b;
    c + globalNum;
};

let outer = fn() {
    sum(1, 2) + sum(3, 4) + globalNum;
};

outer() + globalNum;
`,
            expected: 50,
        },
    }

    runVmTests(t, tests)
}
```

运行此测试会告诉我们：

```
$ go test ./vm
ok      monkey/vm  0.035s
```

是的，我们做到了！我们已成功将函数调用参数添加到编译器和 VM 中！

现在我们只需要确保在调用参数数量错误时栈不会崩塌，因为我们的很多实现都依赖于这个数字：

```
// vm/vm_test.go

func TestCallingFunctionsWithWrongArguments(t *testing.T) {
	tests := []VMTestCase{
		{
			input:    `fn() { 1; }();`,
			expected: `wrong number of arguments: want=0, got=1`,
		},
		{
			input:    `fn(a) { a; }();`,
			expected: `wrong number of arguments: want=1, got=0`,
		},
		{
			input:    `fn(a, b) { a + b; }();`,
			expected: `wrong number of arguments: want=2, got=1`,
		}
	}

	for _, tt := range tests {
		program := parse(tt.input)

		comp := compiler.New()
		err := comp.Compile(program)
		if err != nil {
			t.Fatal("compiler error: %s", err)
		}

		vm := New(comp.Bytecode())
		err = vm.Run()
		if err == nil {
			t.Fatal("expected VM error but resulted in none.")
		}

		if err.Error() != tt.expected {
			t.Fatalf("wrong VM error: want=%q, got=%q", tt.expected, err)
		}
	}
}
```

我们希望确保在参数数量错误时调用函数会得到 VM 错误。是的，这次我们 *想要* 一个错误，但却没有得到：

```
$ go test ./vm
--- FAIL: TestCallingFunctionsWithWrongArguments (0.00s)
vm_test.go:801: expected VM error but resulted in none.
FAIL
FAIL	monkey/vm	0.053s
```

为了解决这个问题，我们需要快速前往 object 包，并在 object.CompiledFunction 的定义中添加一个新字段：

```
// object/object.go
```

```
type CompiledFunction struct {
    Instructions code.Instructions
    NumLocals    int
    NumParameters int
}
```

我们现在将在编译器中填充这个新的 NumParameters 字段，在那里我们手头有函数字面量的参数数量：

```
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 

    case *ast.FunctionLiteral:
    // [...] 

        compiledFn := &object.CompiledFunction{
            Instructions: instructions,
            NumLocals:    numLocals,
            NumParameters: len(node.Parameters),
        }
        c.emit(code.OpConstant, c.addConstant(compiledFn))

    // [...] 
    }

    // [...] 
}
```

在 VM 中，我们可以使用该字段来确保栈上存在正确数量的参数：

```
// vm/vm.go

func (vm *VM) callFunction(numArgs int) error {
    fn, ok := vm.stack[vm.sp-1-numArgs].(*object.CompiledFunction)
    if !ok {
        return fmt.Errorf("calling non-function")
    }

    if numArgs != fn.NumParameters {
        return fmt.Errorf("wrong number of arguments: want=%d, got=%d", fn.NumParameters, numArgs)
    }

    // [...] 
}
```

有了它，我们就处于安全地带：
