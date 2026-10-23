
```go
builtinIndex := code.ReadUint8(ins[ip+1:])
vm.currentFrame().ip += 1

definition := object.Builtins[builtinIndex]

err := vm.push(definition.Builtin)
if err != nil {
    return err
}

// [...] 
}

// [...] 
}
```

我们解码操作数，把它作为索引去访问 `object.Builtins`，获取内置函数的定义，然后把 `*object.Builtin` 压入栈中。这就是我们调用约定的第一部分：把你想调用的函数放到栈上。

现在当我们运行测试时，panic 消失了，取而代之的是更有帮助的信息：

```bash
$ go test ./vm
--- FAIL: TestBuiltinFunctions (0.00s)
    vm_test.go:847: vm error: calling non-function
FAIL
FAIL    monkey/vm    0.036s
```

虚拟机告诉我们，它只能执行用户定义的函数。要修复这个问题，我们必须修改执行 `OpCall` 指令的方式。不能再像现在这样直接调用 `callFunction` 方法，而是要先检查我们到底要调用什么东西，然后分派给相应的方法。为此，我们引入一个 `executeCall` 方法：

```go
// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 

    case code.OpCall:
        numArgs := code.ReadUint8(ins[ip+1:])
        vm.currentFrame().ip += 1

        err := vm.executeCall(int(numArgs))
        if err != nil {
            return err
        }
    }
}
```

```go
    // [...] 
    }

// [...] 
}
```

```go
func (vm *VM) executeCall(numArgs int) error {
    callee := vm.stack[vm.sp-1-numArgs]
    switch callee := callee.(type) {
    case *object.CompiledFunction:
        return vm.callFunction(callee, numArgs)
    case *object.Builtin:
        return vm.callBuiltin(callee, numArgs)
    default:
        return fmt.Errorf("calling non-function and non-built-in")
    }
}
```

```go
func (vm *VM) callFunction(fn *object.CompiledFunction, numArgs int) error {
    if numArgs != fn.NumParameters {
        return fmt.Errorf("wrong number of arguments: want=%d, got=%d",
            fn.NumParameters, numArgs)
    }

    frame := NewFrame(fn, vm.sp-numArgs)
    vm.pushFrame(frame)

    vm.sp = frame.basePointer + fn.NumLocals

    return nil
}
```

现在 `executeCall` 承担了之前由 `callFunction` 做的一些事情，即类型检查和错误生成。这反过来使 `callFunction` 变得更小，并且需要不同的接口：我们把要调用的函数以及调用的参数数量传进去。

但这主要只是代码的搬移。真正新增的是 `case *object.Builtin` 分支，以及负责执行内置函数的 `callBuiltin` 方法：

```go
// vm/vm.go

func (vm *VM) callBuiltin(builtin *object.Builtin, numArgs int) error {
    args := vm.stack[vm.sp-numArgs : vm.sp]

    result := builtin.Fn(args...)
    vm.sp = vm.sp - numArgs - 1

    if result != nil {
        vm.push(result)
    } else {
```

```
vm.push(Null)
}
    return nil
}
```

这里终于展示了执行内置函数的具体方式。

我们先从栈中取出参数（暂时不弹出），然后把它们传给包含在 `*object.Builtin` 的 `Fn` 字段中的 `object.BuiltinFunction`。这是最核心的部分——内置函数本身的执行。

之后，我们减小 `vm.sp`，把我们刚刚执行的函数以及它的参数从栈中弹出。按照我们的调用约定，这是虚拟机的职责。

栈清理完毕后，我们检查调用的结果是否为 `nil`。如果不是 `nil`，就把结果压入栈中；如果是 `nil`，就压入 `vm.Null`。这是“自带 null”策略的又一次运用。

现在，在我们低声惊叹“漂亮”的同时，可以看到每个内置函数都如预期般工作——无论是在编译器中还是在虚拟机中：

```
$ go test ./vm
ok      monkey/vm   0.045s
```

不过，尽管这个令人欣喜的 "ok" 值得庆祝，但作为最后一步，我们还需要处理 REPL。虽然我们在 `compiler.New` 函数中把每个内置函数都定义到了编译器的符号表里，但这并不会对 REPL 生效，它仍然找不到这些内置函数。

这是因为在 REPL 中我们使用的并不是 `compiler.New`，而是 `compiler.NewWithState`。`NewWithState` 允许我们在 REPL 的每一次提示符之间复用一个符号表：它用一个全局符号表覆盖掉 `New` 初始化好的符号表。由于这个全局表中没有定义任何内置函数，所以这正是我们需要修改的地方：

```
// repl/repl.go

func Start(in io.Reader, out io.Writer) {
    // [...] 

symbolTable := compiler.NewSymbolTable()

for i, v := range object.Builtins {
    symbolTable.DefineBuiltin(i, v.Name)
}

for {
    // [...] 
}
}
```

这样，即使在 REPL 中我们也能使用内置函数了：

```
$ go build -o monkey . && ./monkey
Hello monkey! This is the Monkey programming language!
Feel free to type in commands
>> let array = [1, 2, 3];
[1, 2, 3]
>> len(array)
3
>> push(array, 1)
[1, 2, 3, 1]
>> rest(array)
[2, 3]
>> first(array)
1
>> last(array)
3
>> first(rest(push(array, 4)))
2
```

完美！用这样的输出来结束一章，远比测试中那个不起眼的 "ok" 要好得多。

接下来，让我们走向函数实现的最后前沿：闭包。

## 闭包

是时候完成我们对 Monkey 的新实现了，补上最后一块缺失的拼图——闭包。到目前为止，这是字节码编译器和虚拟机领域中最珍贵、也是具有里程碑意义的特性之一。支持它的实现并不多，很快你就会明白为什么。

首先，让我们简要回顾一下什么是闭包，以及它们是如何工作的。这里有一个最典型的例子：

```
let newAdder = fn(a) {
  let adder = fn(b) { a + b; };
  return adder;
};
```

```
let addTwo = newAdder(2);
addTwo(3); // => 5
```

`newAdder` 函数返回一个名为 `adder` 的闭包。它是一个闭包，因为它不仅使用了自身参数 `b`，还访问了在 `newAdder` 中定义的参数 `a`。当 `adder` 从 `newAdder` 返回后，它仍然可以同时访问这两者。这就是为什么 `adder` 是一个闭包，也是为什么当 `addTwo` 被传入 `3` 调用时会返回 `5` 的原因——它是 `adder` 函数的一个版本，仍然能够访问 `a` 之前的值，也就是 `2`。

这就是用六行代码回答“什么是闭包？”。

我们在《用 Go 编写解释器》中的解释器也支持闭包，尽管那个实现与我们本章要构建的内容明显不同，但简单回顾一下有助于打好基础，所以这里粗略勾勒一下我们在《用 Go 编写解释器》中走向闭包的道路。

我们做的第一件事是给 `object.Function` 添加一个 `Env` 字段，用来保存一个 `*object.Environment`，我们用它来存储全局和局部绑定。当我们求值一个 `*ast.FunctionLiteral` 并将其转换为 `*object.Function` 时，会把指向当前环境的指针放入新函数的 `Env` 字段。

当函数被调用时，我们在这个环境——即放在 `Env` 字段中的那个环境——中求值它的函数体。这一切的实际效果是，函数始终能够访问其定义所在环境中的绑定，无论多晚，无论在哪里。这种能力正是闭包之所以是*闭包*的原因，也是它们与普通函数的区别所在。

我之所以要重新回顾旧实现，是因为它与我们思考闭包的方式非常吻合：它们是在定义时“捕获”其环境、将其包裹并随身携带的函数，就像 `Env` 字段中指向 `*object.Environment` 的指针一样。这是理解闭包最重要的一点。

现在我们需要再次实现闭包，只不过这一次我们没有树遍历解释器了。我们有的是编译器和虚拟机，而这带来了一个根本性问题。

## 问题所在

问题并不是我们不再*求值*函数字面量了；问题不在于*求值*本身。在我们当前的实现中，我们仍然会把 `*ast.FunctionLiteral` 转换成 `object.Object`；也就是说，我们能把它们转换成可以被传递的东西，更重要的是，可以被调用和执行的东西。从这个意义上说，语义并没有改变。

改变的是闭包被创建的时间和地点。

在我们旧的解释器中，把函数字面量转换为 `object.Function`，以及捕获环境并在该 `object.Function` 上设置 `Env` 字段，这两件事发生在*完全相同的时间*，甚至是在*同一个代码块*中。

而在我们新的 Monkey 实现中，这不仅发生在不同的时间，而且发生在两个不同的包中：我们在编译器中编译函数字面量，在虚拟机中构建环境。其结果是，我们无法在编译函数时捕获环境，因为，嗯，那时环境还不存在。

让我们在心里模拟上面那段代码在我们当前实现中的流转过程，从而让这个问题变得更具体。

首先发生的事情是编译。这两个函数——`newAdder` 和 `adder`——都被转换成一系列指令并添加到常量池中。之后，我们发出 `OpConstant` 指令，指示虚拟机把这些函数加载到栈上。此时，编译已经完成，还没有人知道 `a` 的值会是什么。

然而在虚拟机中，一旦我们执行 `newAdder`，这个值就知道了。不过到那时，`adder` 已经被编译完毕，它的指令只会被加载到栈中，包含在一个 `*object.CompiledFunction` 里，然后从 `newAdder` 返回——没有任何机会去“捕获” `a`。

你可以看到挑战在哪里了。在虚拟机中，我们需要在 `adder` 从 `newAdder` 返回之前，把 `a` 的值放入这个*已经编译好的* `adder` 函数中，而且需要以这样一种方式来完成，使得之后的 `adder` 能够访问到它。
