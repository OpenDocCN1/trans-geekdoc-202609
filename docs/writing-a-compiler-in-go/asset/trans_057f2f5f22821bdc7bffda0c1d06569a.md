

## 实参

让我们从简要回顾开始这一节。在 Monkey 中，我们可以定义带有参数的函数，如下所示：

```
let addThree = fn(a, b, c) {
  a + b + c;
}
```

这个函数有三个参数：a、b 和 c。当我们调用它时，可以在调用表达式中使用实参：

```
addThree(1, 2, 3);
```

在函数执行期间，这会将传入的实参值绑定到参数名上。现在，“绑定”这个词听起来应该很耳熟，但我不想拐弯抹角，所以直接说出来：函数调用的实参是局部绑定的一种特殊情况。

它们具有相同的生命周期、相同的作用域，并以相同的方式解析。唯一的区别在于它们的创建方式。局部绑定由用户通过 let 语句显式创建，编译器会为此生成 OpSetLocal 指令。另一方面，实参是隐式绑定到名称上的，这是由编译器和虚拟机在幕后完成的。这就引出了我们本节的任务列表。

我们本节的目标是完整实现函数参数和函数调用的实参。最后，我们要编译并执行这段 Monkey 代码：

```
let globalNum = 10;

let sum = fn(a, b) {
  let c = a + b;
  c + globalNum;
};

let outer = fn() {
  sum(1, 2) + sum(3, 4) + globalNum;
};

outer() + globalNum;
```

乍一看，这看起来相当混乱。这是有意为之。它混合了我们已实现的所有东西和我们将要构建的东西：全局和局部绑定、带参数和不带参数的函数、带实参和不带实参的函数调用。

那么我们的计划是什么？首先，我们需要重新思考我们的调用约定。目前的形态无法容纳实参。然后，作为第二步也是最后一步，我们需要实现这个更新后的调用约定。但让我们从头开始。

## 编译带实参的函数调用

我们当前调用约定的简要版本是：将要调用的函数压入栈中，发出 OpCall，然后就行了。我们现在面临的问题是把函数调用的实参放在哪里——不仅是“哪里”这个内存位置的含义，还有在调用约定中的位置。

我们不必花太久寻找内存位置，因为我们已经有了一个存储与当前函数调用相关数据的地方：栈。就像我们用栈来存储要调用的函数一样，我们也可以用栈来存储调用的实参。

但如何让它们进入栈呢？最简单的方法是在函数被压入之后，立即将它们压入栈中。出乎意料的是，这个务实的解决方案没有任何反对的理由。实际上它相当优雅，我们稍后会看到。

因此，如果我们采用这种方法，它会把我们的调用约定改为：将要调用的函数压入栈中，然后将调用的所有实参压入栈中，发出 OpCall，然后就行了。此时，在执行 OpCall 之前，栈会看起来像这样：

![](img/ab2ef57dcaaed64759b089e71bfdb58d_265_0.png)

然而，就目前情况而言，这个解决方案给我们的虚拟机带来了一个小问题，因为它不知道栈顶有多少个实参。

想想我们在虚拟机中对 OpCall 的实现。在推送新帧之前，我们直接从栈顶取出要调用的函数。使用这种新的调用约定，栈上可能有零个或多个实参——位于函数之上。我们如何访问栈上的函数以便执行它？

由于函数是普通的 Monkey object.Objects，我们甚至不能选择 hacky 的方式，遍历栈来找到第一个 object.CompiledFunction；那可能只是函数调用的一个实参。

值得庆幸的是，我们不必诉诸那些 hacky 且“唉，这感觉真脏”的修复。有一个简单而优雅的解决方案：我们给 OpCall 操作码一个操作数，用来保存调用的实参数量。一个字节就足够了（或者你想调用超过 256 个实参的函数吗？），并且通过一点计算，我们就能找到实参下方的函数。

所以，让我们给 OpCall 添加一个操作数：

```
// code/code.go

var definitions = map[Opcode]*Definition{
    // [...] 

    OpCall:    {"OpCall", []int{1}},

    // [...] 
}
```

随着这一更改，一些测试因 panic 和索引错误而失败，因为我们定义了编译器和虚拟机都不知道的东西。

这本身不是问题，但新操作数的定义会导致我们的 code.Make 函数在相应位置创建一个空字节——即使我们不传入操作数。我们最终陷入了某种困境，系统中不同部分基于不同假设运作，没人知道到底发生了什么。我们需要重新恢复秩序。

我们将从更新现有的编译器测试开始，确保在创建 opCall 指令时确实传入操作数：

```
// compiler/compiler_test.go

func TestFunctionCalls(t *testing.T) {
    tests := []compilerTestCase{
        {
            // [...] 
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 1), // The compiled function
                code.Make(code.OpCall, 0),
                code.Make(code.OpPop),
            },
        },
        {
            // [...] 
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 1), // The compiled function
                code.Make(code.OpSetGlobal, 0),
                code.Make(code.OpGetGlobal, 0),
                code.Make(code.OpCall, 0),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

这使编译器测试正确，编译器本身目前也没问题，因为编译器也使用 code.Make 来生成指令，而 code.Make 同样会为新操作数添加一个空字节，即使没有传入操作数。

不过，虚拟机在面对新操作数时会踉跄跌倒，不管是否为空。目前的解决方案，至少在我们编写测试来告诉我们真正想要什么之前，就是简单地跳过它：

```
// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...]
```

```
case code.OpCall:
    vm.currentFrame().ip += 1
        // [...] 

        // [...] 
    }
    // [...] 
}
```

### 秩序已恢复：

```
$ go test ./...
?       monkey [no test files]
ok      monkey/ast 0.014s
ok      monkey/code 0.014s
ok      monkey/compiler 0.011s
ok      monkey/evaluator 0.014s
ok      monkey/lexer 0.011s
ok      monkey/object 0.014s
ok      monkey/parser 0.009s
?       monkey/repl [no test files]
?       monkey/token [no test files]
ok      monkey/vm 0.037s
```

我们回到了正轨，现在可以编写一个测试，确保编译器通过发出将实参压入栈的指令，符合更新后的调用约定。由于我们已经有了 TestFunctionCalls，我们可以用新的测试用例扩展它，而不必添加新的测试函数：

```
// compiler/compiler_test.go
```

```
func TestFunctionCalls(t *testing.T) {
    tests := []compilerTestCase{
        // [...] 
        {
            input: `
                let oneArg = fn(a) {};
                oneArg(24);
            `,
            expectedConstants: []interface{}{
                []code.Instructions{
                    code.Make(code.OpReturn),
                },
                24,
            },
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpSetGlobal, 0),
                code.Make(code.OpGetGlobal, 0),
                code.Make(code.OpConstant, 1),
                code.Make(code.OpCall, 1),
                code.Make(code.OpPop),
            },
        },
```

```
{
    input: `
    let manyArg = fn(a, b, c) { };
    manyArg(24, 25, 26);
    `,
    expectedConstants: []interface{}{
        []code.Instructions{
            code.Make(code.OpReturn),
        },
        24,
        25,
        26,
    },
    expectedInstructions: []code.Instructions{
        code.Make(code.OpConstant, 0),
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
```

值得注意的是，这些新测试用例中使用的函数体为空，没有使用它们的参数。这是有意为之。我们首先要确保能够编译函数调用，一旦实现，我们将引用同一测试中的参数并更新预期。

如这些测试用例的 expectedInstructions 所示，函数调用的第一个实参应该最终位于栈的最低处。从我们目前的角度来看，这并不重要，但很快我们就会看到，一旦我们开始引用参数，这会让虚拟机中的事情变得更加美好。

这些新测试的输出相当有启发性：

```
$ go test ./compiler
--- FAIL: TestFunctionCalls (0.00s)
    compiler_test.go:889: testInstructions failed: wrong instructions length.
    want="0000 OpConstant 0\n0003 OpSetGlobal 0\n0006 OpGetGlobal 0\n\
    0009 OpConstant 1\n0012 OpCall 1\n0014 OpPop\n"
    got ="0000 OpConstant 0\n0003 OpSetGlobal 0\n0006 OpGetGlobal 0\n\
    0009 OpCall 0\n0011 OpPop\n"
FAIL
FAIL    monkey/compiler 0.008s
```

缺少的 OpConstant 指令告诉我们，我们需要编译

