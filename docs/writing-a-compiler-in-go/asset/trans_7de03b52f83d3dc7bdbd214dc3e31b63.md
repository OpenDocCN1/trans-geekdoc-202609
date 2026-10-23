
```
freeSymbols := c.symbolTable.FreeSymbols
numLocals := c.symbolTable.numDefinitions
instructions := c.leaveScope()

for _, s := range freeSymbols {
    c.loadSymbol(s)
}

compiledFn := &object.CompiledFunction{
    Instructions: instructions,
    NumLocals:    numLocals,
    NumParameters: len(node.Parameters),
}

fnIndex := c.addConstant(compiledFn)
c.emit(code.OpClosure, fnIndex, len(freeSymbols))

// [...] 
}

// [...] 
}
```

这里展示这些内容，主要是为了让你理解改动背景——这些改动其实只有五行代码。

第一行新代码是 `freeSymbols` 的赋值。关键点在于，这必须在我们调用 `c.leaveScope()` 之前完成。然后，在离开作用域之后，我们遍历 `freeSymbols`，对每个符号调用 `c.loadSymbol`。

随后，`len(freeSymbols)` 被用作 `OpClosure` 指令的第二个操作数。在 `c.loadSymbol` 调用之后，自由变量位于栈顶，等待着与 `*object.CompiledFunction` 合并成一个 `*object.Closure`。

这五行代码带来了巨大的成果：

```
$ go test ./compiler
ok      monkey/compiler 0.008s
```

看看！我们成功编译了闭包！编译期搞定。现在我们需要处理运行期，闭包的魔力正是从这里展现。

## 在运行期创建真正的闭包

我们的虚拟机已经在运行闭包了。它不再直接执行 `*object.CompiledFunction`，而是在执行 `OpClosure` 指令时将它们包装成 `*object.Closure`，然后调用并执行这些闭包。

目前缺少的是创建“真正”闭包的部分：把自由变量传递给这些闭包，以及执行 `OpGetFree` 指令将它们加载到栈上。由于我们准备工作做得非常充分，可以轻松达成这一目标，只需迈出微小且易于理解的几步。

我们先写一个测试，期望虚拟机能够处理最简单的真实闭包：

```
// vm/vm_test.go

func TestClosures(t *testing.T) {
    tests := []vmTestCase{
        {
            input: `
let newClosure = fn(a) {
    fn() { a; };
};
let closure = newClosure(99);
closure();
`,
            expected: 99,
        },
    }

    runVmTests(t, tests)
}
```

在测试输入中，`newClosure` 返回一个闭包，该闭包捕获了一个自由变量——`newClosure` 的参数 `a`。当返回的闭包被调用时，它应该返回这个 `a`。一个闭包、一个自由变量、一个外层作用域。我们能搞定。

我们要做的第一件事，就是利用 `OpClosure` 的第二个操作数，它告诉虚拟机有多少个自由变量需要被转移到指定的闭包。我们之前已经解码了这个操作数，但一直忽略它，因为当时还没有自由变量。现在有了自由变量，我们必须用上它：

```
// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 
    case code.OpClosure:
        constIndex := code.ReadUint16(ins[ip+1:])
        numFree := code.ReadUint8(ins[ip+3:])
        vm.currentFrame().ip += 3

        err := vm.pushClosure(int(constIndex), int(numFree))
        if err != nil {
            return err
        }

        // [...] 
    }
    // [...] 
}
```

现在我们向 `pushClosure` 传递两个参数：编译函数在常量池中的索引，以及等待在栈上的自由变量数量。函数如下：

```
// vm/vm.go

func (vm *VM) pushClosure(constIndex, numFree int) error {
    constant := vm.constants[constIndex]
    function, ok := constant.(*object.CompiledFunction)
    if !ok {
        return fmt.Errorf("not a function: %+v", constant)
    }

    free := make([]object.Object, numFree)
    for i := 0; i < numFree; i++ {
        free[i] = vm.stack[vm.sp-numFree+i]
    }
    vm.sp = vm.sp - numFree

    closure := &object.Closure{Fn: function, Free: free}
    return vm.push(closure)
}
```

新增的是中间部分。这里我们使用第二个参数 `numFree` 来构建一个切片 `free`。然后，从栈中位置最低的一个开始，依次取出每个自由变量并复制到 `free` 中。最后，通过手动减少 `vm.sp` 来清理栈。

复制的顺序非常重要，因为这与自由变量在闭包体内被引用的顺序一致，也正是我们当初把它们压入栈的顺序。如果颠倒了顺序，`GetFree` 指令的操作数就会出错。这引出了我们的下一个要点：虚拟机还不知道 `OpGetFree`。

实现 `OpGetFree` 与其他 `OpGet*` 指令的差别不大，除了获取值的位置。这次是从虚拟机当前执行的 `*object.Closure` 的 `Free` 切片中获取：

```go
// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 
    case code.OpGetFree:
        freeIndex := code.ReadUint8(ins[ip+1:])
        vm.currentFrame().ip += 1

        currentClosure := vm.currentFrame().cl
        err := vm.push(currentClosure.Free[freeIndex])
        if err != nil {
            return err
        }

        // [...] 
    }
    // [...] 
}
```

正如我所说，只是获取的位置变了。我们解码操作数，用它作为索引从 `Free` 切片中取出值，然后压入栈。就这么简单。

现在，如果你用的是站立式办公桌，接下来这个消息可能会让你想坐下来。看：

```bash
$ go test ./vm
ok      monkey/vm   0.036s
```

是的，真的。我们实现了真正的闭包！完整实现！完成了！不信？那我们再扔一些测试给虚拟机，看看它会怎样：

```go
// vm/vm_test.go

func TestClosures(t *testing.T) {
    tests := []vmTestCase{
        // [...] 
```

```go
{
    input: `
let newAdder = fn(a, b) {
    fn(c) { a + b + c };
};
let adder = newAdder(1, 2);
adder(8);
`,
    expected: 11,
},
{
    input: `
let newAdder = fn(a, b) {
    let c = a + b;
    fn(d) { c + d };
};
let adder = newAdder(1, 2);
adder(8);
`,
    expected: 11,
}
runVmTests(t, tests)
}
```

这里我们有了引用多个自由变量的闭包，有些自由变量是外层函数的参数，有些是局部变量。交叉手指祈祷一下：

```shell
$ go test ./vm
ok      monkey/vm   0.035s
```

漂亮！让我们再提升一个难度：

```go
// vm/vm_test.go

func TestClosures(t *testing.T) {
    tests := []vmTestCase{
        // [...]
        {
            input: `
let newAdderOuter = fn(a, b) {
    let c = a + b;
    fn(d) {
        let e = d + c;
        fn(f) { e + f; };
    };
};
let newAdderInner = newAdderOuter(1, 2)
let adder = newAdderInner(3);
adder(8);
`,
            expected: 14,
        },
        {
            input: `
```

```
let a = 1;
let newAdderOuter = fn(b) {
    fn(c) {
        fn(d) { a + b + c + d };
    };
};
let newAdderInner = newAdderOuter(2)
let adder = newAdderInner(3);
adder(8);
`,
    expected: 14,
},
{
    input: `
let newClosure = fn(a, b) {
    let one = fn() { a; };
    let two = fn() { b; };
    fn() { one() + two(); };
};
let closure = newClosure(9, 90);
closure();
`,
    expected: 99,
},
}
runVmTests(t, tests)
}
```

现在，我们有了返回其他闭包的闭包、全局绑定、局部绑定、在闭包中调用多个闭包，这些特性全部混合在一起，而运行结果依然正确：

```
$ go test ./vm
ok      monkey/vm   0.039s
```

这已经是最接近“认证可用”的状态了。我们现在可以满怀信心地说：我们成功地在字节码编译器和字节码虚拟机上实现了闭包！我们为最耀眼的 Monkey 实现加上了皇冠上的明珠。该庆祝一下了。

## 稍作回顾

我们走到了旅程的终点。我们做到了。我们成功构建了一个字节码编译器和一个虚拟机。

我们已经实现了二元和前缀运算符、带跳转指令的条件判断、全局和局部绑定、字符串、数组、哈希、一等函数、高阶函数、内置函数，现在甚至还有闭包——所有特性中最为荣耀的一个。

是时候给自己一点小小的鼓励了。带着满满的满足感，那种付出努力后收获的充实感，我们现在可以看着我们的编译器编译、虚拟机执行下面这段 Monkey 代码。

这是展示一门编程语言时的经典示例。是的，这可能有点老套，但无论如何，它都是一个里程碑，而且总能让我会心一笑。我说的是计算斐波那契数的递归函数：

```
// vm/vm_test.go

func TestRecursiveFibonacci(t *testing.T) {
    tests := []vmTestCase{
        {
            input: `
            let fibonacci = fn(x) {
                if (x == 0) {
                    return 0;
                } else {
                    if (x == 1) {
                        return 1;
                    } else {
                        fibonacci(x - 1) + fibonacci(x - 2);
                    }
                }
            }
            `;
            fibonacci(15);
            `,
            expected: 610,
        },
    }

    runVmTests(t, tests)
}
```

啊，递归！很美，不是吗？开始吧，交叉手指，敲敲木头

