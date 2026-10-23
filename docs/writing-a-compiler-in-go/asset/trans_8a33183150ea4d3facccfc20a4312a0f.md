
将这些信息传递给 VM 对我们来说是微不足道的。

我们首先需要做的是为 `object.CompiledFunction` 扩展一个字段：

```go
// object/object.go

type CompiledFunction struct {
    Instructions code.Instructions
    NumLocals    int
}
```

`NumLocals` 稍后会告诉我们这个函数将要创建多少个局部绑定。在编译器中，我们现在可以询问符号表在编译函数时定义了多少个符号，并将该数字放入 `NumLocals` 中：

```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...]

    case *ast.FunctionLiteral:
        // [...]

        numLocals := c.symbolTable.numDefinitions
        instructions := c.leaveScope()

        compiledFn := &object.CompiledFunction{
            Instructions: instructions,
            NumLocals:    numLocals,
        }
        c.emit(code.OpConstant, c.addConstant(compiledFn))
    // [...]
    }
    // [...]
}
```

在调用 `c.leaveScope` 之前，我们取出当前符号表的 `numDefinitions`，将其暂存，并在离开作用域后将其保存到 `*object.CompiledFunction` 中。这就给了我们函数将在 VM 中创建和使用的局部绑定的数量。第一个迷你挑战完成！太棒了！

现在，根据我们的计划，我们需要做的另一件事是跟踪栈指针在 *执行函数之前* 的值，然后在 *执行之后* 将其恢复到该值。换句话说，我们需要一个在函数调用期间存在的临时存储。猜猜看？我们已经有了它，称之为 Frame。我们只需要再添加一个字段，即所谓的 basePointer：

```
// vm/frame.go

type Frame struct {
    fn          *object.CompiledFunction
    ip          int
    basePointer int
}

func NewFrame(fn *object.CompiledFunction, basePointer int) *Frame {
    f := &Frame{
        fn:          fn,
        ip:          -1,
        basePointer: basePointer,
    }

    return f
}
```

“base pointer” 这个名字不是我编造的。相反，给指向当前调用帧栈底部的指针起这个名字是常见做法。它是在执行函数时许多引用的基准。有时它也被称为“frame pointer”。在本书接下来的章节中我们会更多地使用它。现在，我们只需要 在推送新帧之前对其进行初始化：

```
// vm/vm.go

func New(bytecode *compiler.Bytecode) *VM {
    // [...] 

    mainFrame := NewFrame(mainFn, 0)

    // [...] 
}

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 

    case code.OpCall:
        fn, ok := vm.stack[vm.sp-1].(*object.CompiledFunction)
        if !ok {
            return fmt.Errorf("calling non-function")
        }
        frame := NewFrame(fn, vm.sp)
        vm.pushFrame(frame)

    // [...] 
}
```

```
		}
		// [ ... ]
	}
```

在 vm.New 函数中，我们传入 0 作为栈指针的当前值，以便让我们的 mainFrame 正常工作，即使这个特定的帧永远不会从栈中弹出并且没有局部绑定。我们真正想要的是在 case code.OpCall 分支中新帧的设置。现在是调用 NewFrame 时的第二个参数，即 vm.sp 的当前值，它将作为新帧的 basePointer。

好了！我们现在有了 basePointer，并且知道函数将使用多少个局部变量。这给我们留下了两个任务：在执行函数之前为局部绑定在栈上分配空间。意思是：创建“空洞”。而且我们还需要实现 VM 中的 opSetLocal 和 opGetLocal 指令来使用它。

“在栈上分配空间”听起来很高级，但归结起来就是在不推送任何东西的情况下增加 vm.sp 的值。而且由于我们在执行函数之前已经将其值保存到一边，我们已经有一个完美的位置可以这样做：

```
// vm/vm.go

func (vm *VM) Run() error {
    // [ ... ]
    switch op {
        // [ ... ]

        case code.OpCall:
            fn, ok := vm.stack[vm.sp-1].(*object.CompiledFunction)
            if !ok {
                return fmt.Errorf("calling non-function")
            }
            frame := NewFrame(fn, vm.sp)
            vm.pushFrame(frame)
            vm.sp = frame.basePointer + fn.NumLocals

            // [ ... ]
        }
    // [ ... ]
}
```

我们将 vm.sp 设置为 frame.basePointer + fn.NumLocals，以明确起点是 basePointer，并且我们在栈上为 fn.NumLocals 预留槽位。这些槽位可能不包含值或包含旧值，在任何情况下我们都不关心。我们现在可以使用这个栈区域用于局部绑定，并且正常

```go
frame := vm.currentFrame()

err := vm.push(vm.stack[frame.basePointer+int(localIndex)])
if err != nil {
    return err
}

// [...] 
}
// [...] 
}
```

完成！让我们看看我们的测试会说什么：

```
$ go test ./vm
--- FAIL: TestCallingFunctionsWithBindings (0.00s)
    vm_test.go:444: vm error: unsupported types for binary operation:\
    COMPILED_FUNCTION_OBJ INTEGER
FAIL
FAIL    monkey/vm    0.031s
```

什么？在我们的任何测试用例中我们都没有尝试将函数加到整数上。只有在我们让函数留在栈上的情况下才会发生这种情况。啊！我们忘了清理栈！我们已经有了 basePointer，但我们在执行完函数后并没有用它来重置 vm.sp。

不过我们知道在哪里可以做到这一点：当我们遇到 OpReturnValue 或 OpReturn 指令时。目前，我们只将返回值和刚刚执行的函数从栈中取出。现在我们也需要摆脱局部绑定。最简单的方法是将栈指针设置为包含刚刚执行函数的帧的 basePointer：

// vm/vm.go

```go
func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 

    case code.OpReturnValue:
        returnValue := vm.pop()

        frame := vm.popFrame()
        vm.sp = frame.basePointer - 1

        err := vm.push(returnValue)
        if err != nil {
            return err
        }
    case code.OpReturn:
```

```
frame := vm.popFrame()
vm.sp = frame.basePointer - 1

err := vm.push(Null)
if err != nil {
    return err
}

// [...] 
}
// [...] 
}
```

当我们从函数返回时，我们首先将帧从帧栈中弹出。之前我们也这样做了，但没有保存弹出的帧。现在我们还将 vm.sp 设置为 frame.basePointer - 1。额外的 -1 从何而来？这是一个优化：将 vm.sp 设置为 frame.basePointer 会去掉局部绑定，但仍会将刚刚执行的函数留在栈上。因此，我们用进一步递减 vm.sp 来代替之前放置在那里的 vm.pop()。

这样就完成了。是的，真的。我们来到了一个旅程的终点，这个旅程始于 OpSetLocal 和 OpGetLocal 操作码的定义，带领我们从编译器测试经过符号表回到编译器，最后经过 object.CompiledFunction 的小小绕路来到了 VM。局部绑定可以工作了：

```
$ go test ./vm
ok      monkey/vm   0.039s
```

我们现在可以编译并执行这段 Monkey 代码：

```
let globalSeed = 50;
let minusOne = fn() {
    let num = 1;
    globalSeed - num;
}
let minusTwo = fn() {
    let num = 2;
    globalSeed - num;
}
minusOne() + minusOne()
```

而且还有更多。我们在没有明确打算这样做的情况下，又获得了对一等函数的升级。我们现在可以获取函数并将其分配给名称——在其他函数中：

// vm/vm_test.go

```go
func TestFirstClassFunctions(t *testing.T) {
	tests := []vmTestCase{
		// [...] 
		{
			input: `
			let returnsOneReturner = fn() {
			let returnsOne = fn() { 1; };
			returnsOne;
			};
			returnsOneReturner()();
			`,
			expected: 1,
		},
	}

	runVmTests(t, tests)
}
```

是的，这通过了：

```bash
$ go test ./vm
ok      monkey/vm    0.037s
```

现在我们已经达到了目标，下一步去哪里？函数调用的参数——它们比你想象的更接近我们现在的位置。
