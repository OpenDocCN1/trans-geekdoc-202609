

## 执行跳转

在为条件语句编写编译器测试之前，我们确实需要仔细思考我们希望它们表达什么，以及希望编译器做什么。但现在为 VM 编写同样的测试时，情况就不是这样了。我们已经知道 Monkey 中的条件语句应该如何工作，并且可以在测试用例和断言中清晰地表达出来：

```
// vm/vm_test.go
```

```
func TestConditionals(t *testing.T) {
	tests := []vmTestCase{
		{"if (true) { 10 }", 10},
		{"if (true) { 10 } else { 20 }", 10},
		{"if (false) { 10 } else { 20 }", 20},
		{"if (1) { 10 }", 10},
		{"if (1 < 2) { 10 }", 10},
		{"if (1 < 2) { 10 } else { 20 }", 10},
		{"if (1 > 2) { 10 } else { 20 }", 20},
	}

	runVmTests(t, tests)
}
```

这些测试用例即使只写一半也足够了。但它们写起来容易、表达清晰、简洁，而且几乎不花什么成本！把我们的意图表达得极其清楚也没有什么坏处。

我们测试 VM 是否按照 Monkey 的“truthy”标准正确求值布尔表达式，以及是否执行了条件语句的正确分支。由于条件语句是产生值的表达式，因此可以通过测试整个条件语句产生的值来推断执行了哪个分支。

虽然测试本身很简洁，但它们产生的错误信息却很糟糕：

```
$ go test ./vm
--- FAIL: TestConditionals (0.00s)
panic: runtime error: index out of range [recovered]
    panic: runtime error: index out of range

goroutine 20 [running]:
testing.tRunner.func1(0xc4200bc2d0)
/usr/local/go/src/testing/testing.go:742 +0x29d
panic(0x11190e0, 0x11f1fd0)
/usr/local/go/src/runtime/panic.go:502 +0x229
```

```
/monkey/vm.(*VM).Run(0xc420050e38, 0x800, 0x800)
/Users/mrnugget/code/04/src/monkey/vm/vm.go:46 +0x39c
monkey/vm.runVmTests(0xc4200bc2d0, 0xc420079e88, 0x7, 0x7)
/Users/mrnugget/code/04/src/monkey/vm/vm_test.go:101 +0x35a
monkey/vm.TestConditionals(0xc4200bc2d0)
/Users/mrnugget/code/04/src/monkey/vm/vm_test.go:80 +0x114
testing.tRunner(0xc4200bc2d0, 0x1149b40)
/usr/local/go/src/testing/testing.go:777 +0xd0
created by testing.(*T).Run
/usr/local/go/src/testing/testing.go:824 +0x2e0
FAIL monkey/vm 0.011s
```

唉。这甚至算不上错误，而是 panic。

不过，在你深入代码并试图找出错误来源之前，让我解释一下：VM 在字节码上绊倒了，因为它包含 VM 不知道如何解码的操作码。这本身不应该是个问题，因为未知操作码会被跳过，但不一定会跳过它们的操作数。记住，操作数只是整数，它们可能与某个编码后的操作码具有相同的值，这可能会让 VM 将它们误认为操作码。这当然是错误的。是时候让我们的 VM 认识跳转指令了。

我们从 `OpJump` 开始，因为它使我们拥有的最直接的跳转指令。它有一个 16 位操作数，表示 VM 应该跳转到的指令的偏移量。这就是实现它所需的全部信息：

```go
// vm/vm.go

func (vm *VM) Run() error {
  // [ ... ]
  switch op {
    // [ ... ]

case code.OpJump:
  pos := int(code.ReadInt16(vm.instructions[ip+1:]))
  ip = pos - 1

// [ ... ]
}
// [ ... ]
```

我们使用 `code.ReadInt16` 来解码紧跟在操作码之后的操作数。这是第 1 步。第 2 步是将指令指针 `ip` 设置为跳转的目标位置。在这里我们遇到一个有趣的实现细节：由于我们处于一个每次迭代都会递增 `ip` 的循环中，我们需要将 `ip` 设置为我们想要的目标位置前一个偏移量。这样循环才能正常工作，并在下一个周期将 `ip` 设置为我们要的值。

不过，仅仅实现 `OpJump` 并不能给我们带来多大好处，因为 `OpJumpNotTruthy` 才是条件语句实现的核心。但为 `code.OpJumpNotTruthy` 添加一个 case 分支虽然会多写一点代码，却并不复杂多少：

```go
// vm/vm.go

func (vm *VM) Run() error {
    for ip := 0; ip < len(vm.instructions); ip++ {
        op := code.Opcode(vm.instructions[ip])

        switch op {
        // [...]

        case code.OpJumpNotTruthy:
            pos := int(code.ReadUint16(vm.instructions[ip+1:]))
            ip += 2

            condition := vm.pop()
            if !isTruthy(condition) {
                ip = pos - 1
            }

        // [...]
        }
    }
    // [...]
}

func isTruthy(obj object.Object) bool {
    switch obj := obj.(type) {

    case *object.Boolean:
        return obj.Value

    default:
        return true
    }
}
```

我们再次使用 `code.ReadUint16` 来读取并解码操作数。之后，我们手动将 `ip` 增加 2，以便在下一个循环中正确跳过操作数的两个字节。这并不新鲜——在执行 `OpConstant` 指令时我们已经这么做了。

新的是其余部分。我们弹出栈顶元素，并用辅助函数 `isTruthy` 检查它是否为真值。如果它不是真值，我们就跳转，这意味着将 `ip` 设置为目标指令前一条指令的索引，让 for 循环完成它的工作。

如果该值为真值，我们什么都不做，开始主循环的下一次迭代。

结果是，我们执行了条件语句的结果分支，该分支由紧跟在 `OpJumpNotTruthy` 指令之后的指令组成。

现在，在你最喜欢的音频播放器中打开你选的 `drumroll.wav`，倒上你最喜欢的饮料，点击播放，然后看看这个：

~~~text
$ go test ./vm
ok      monkey/vm   0.009s
~~~

我们做到了。是的，我们做到了！我们的字节码编译器和 VM 现在能够编译并执行 Monkey 的条件语句了！

~~~text
$ go build -o monkey . && ./monkey
Hello mrnugget! This is the Monkey programming language!
Feel free to type in commands
>> if (10 > 5) { 10; } else { 12; }
10
>> if (5 > 10) { 10; } else { 12; }
12
>>
~~~

就在这一刻，我们从“嗯，这不过是个玩具，不是吗？”变成了“哦，哇，我们有进展了！”。栈运算是一回事，跳转指令又是另一回事。我们现在可是进入大联盟了。只不过……

~~~text
>> if (false) { 10; }
panic: runtime error: index out of range

goroutine 1 [running]:
monkey/vm.(*VM).pop(...)
    /Users/mrnugget/code/04/src/monkey/vm/vm.go:117
monkey/vm.(*VM).Run(0xc42005be48, 0x800, 0x800)
    /Users/mrnugget/code/04/src/monkey/vm/vm.go:60 +0x40e
monkey/repl.Start(0x10f1080, 0xc42000e010, 0x10f10a0, 0xc42000e018)
    /Users/mrnugget/code/04/src/monkey/repl/repl.go:43 +0x47a
main.main()
    /Users/mrnugget/code/04/src/monkey/main.go:18 +0x107
~~~

我们忘了点什么。

## 欢迎回来，Null！

在本章开头，我们回顾了《用 Go 编写解释器》中条件语句的实现，现在我们已经实现了其中大部分行为。但还缺少一件事：当条件语句的条件不为真值，而条件语句本身又没有替代分支时，会发生什么？在上一本书中，这个问题的答案是 `*object.Null`，也就是 Monkey 的 null 值。

这说得通，因为条件语句是表达式，而表达式按定义会产生值。那么，一个没有产生任何值的表达式会求值为什么？Null。等等，让我再试一次，只不过这一次请想象背景中响起*巨大的管风琴声*，*乌鸦从头顶飞过，尖叫着，雷声隆隆*：它们……*闪电劈下……* 求值为……*警笛声*…… null。

听着，null 和我并不是最好的朋友。我不太确定该怎么看待它，它是好是坏。它是许多咒骂的根源，但我确实理解，有些语言中有些东西会求值为“无”，而“无”必须以某种方式表示。在 Monkey 中，条件为假且没有替代分支的条件语句就是其中之一，而“无”由 `*object.Null` 表示。长话短说：是时候将 `*object.Null` 引入我们的编译器和 VM，并让这类条件语句正常工作了。

我们需要做的第一件事是在 VM 中定义 `*object.Null`。由于它的值是常量，我们可以像之前全局定义 `vm.True` 和 `vm.False` 一样，把它定义为一个全局变量：

```
// vm/vm.go

var Null = &object.Null{}
```

这一点与 `vm.True` 和 `vm.False` 类似，它在比较 Monkey 对象时能为我们节省很多工作。我们可以简单地通过检查一个 `object.Object` 是否等于 `vm.Null` 来判断它是否为 `*object.Null`，而不必解包并查看它的值。

我们之所以在编写任何编译器测试之前（我们通常的做法）先定义 `vm.Null`，是因为这次我们想先编写一个 VM 测试。这是因为 VM 测试能让我们非常简洁地表达我们的需求：

