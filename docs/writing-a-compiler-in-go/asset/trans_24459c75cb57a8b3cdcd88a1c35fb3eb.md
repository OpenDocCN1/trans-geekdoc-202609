
}

这东西运行得像钟表一样精准：

```
$ go test ./vm
ok      monkey/vm   0.039s
```

我们甚至可以一丝不苟地为显式的 return 语句添加一个测试。我们已经知道这些会被编译成我们刚刚成功执行的相同指令，但添加它会在未来出现问题时为我们提供更好的反馈：

// vm/vm_test.go

func TestFunctionsWithReturnStatement(t *testing.T) {
    tests := []vmTestCase{
        {
            input: `
let earlyExit = fn() { return 99; 100; };
earlyExit();
`,
            expected: 99,
        },
        {
            input: `
let earlyExit = fn() { return 99; return 100; };
earlyExit();
`,
            expected: 99,
        }
    }

    runVmTests(t, tests)
}
```

即使这样运行也毫无问题：

```
$ go test ./vm
ok      monkey/vm   0.032s
```

神奇的 opcode！我们正在将函数调用编译为字节码，并在我们的字节码 VM 中拥有自己的调用栈，而且一切都正常工作！是时候好好表扬一下自己，坐下来深呼吸一下了。

但既然我们在这里…

## 它不是什么都不是，而是 Null

在继续之前，我们需要处理 OpReturn opcode。在编译器中，我们已经确保空函数会被编译成单个 opcode：OpReturn。我们还决定调用这些函数时应将 vm.Null 放入 VM 的栈中，现在是实现它的时机。

幸运的是，这段话是对期望行为的直接定义，可以改写成一个测试：

// vm/vm_test.go

func TestFunctionsWithoutReturnValue(t *testing.T) {
    tests := []vmTestCase{
        {
            input: `
let noReturn = fn() { };
noReturn();
`,
            expected: Null,
        },
        {
            input: `
let noReturn = fn() { };
let noReturnTwo = fn() { noReturn(); };
noReturn();
noReturnTwo();
`,
            expected: Null,
        },
    }

    runVmTests(t, tests)
}
```

我们的 VM 对 OpReturn 一无所知，它不会将 vm.Null 放在栈上：

```
$ go test ./vm
--- FAIL: TestFunctionsWithoutReturnValue (0.00s)
vm_test.go:546: object is not Null: <nil> (<nil>)
vm_test.go:546: object is not Null: <nil> (<nil>)
FAIL
FAIL    monkey/vm    0.037s
```

我们要如何修复这些测试用例？我们已经知道如何从函数返回，甚至知道如何返回值。现在我们要做得更少：

// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...]
case code.OpReturn:
    vm.popFrame()
    vm.pop()

    err := vm.push(Null)
    if err != nil {
        return err
    }

    // [...]
}
// [...]
}
```

弹出帧，弹出被调用的函数，压入 Null。完成：

```
$ go test ./vm
ok      monkey/vm   0.038s
```

### 一个小奖励

这里有一个小惊喜。在本节中，我们不仅仅达到了编译和执行我们设法使其工作的代码片段的里程碑。我们还在没有将其作为目标甚至没有考虑的情况下——实现了自 REPL 和快速单元测试以来最好的东西： 一等函数。是的，编译器和 VM 已经能够编译和执行以下 Monkey 代码：

```
let returnsOne = fn() { 1; };
let returnsOneReturner = fn() { returnsOne; };
returnsOneReturner()();
```

不信吗？没必要，我愿意用一个测试用例打赌：

// vm/vm_test.go

func TestFirstClassFunctions(t *testing.T) {
    tests := []vmTestCase{
        {
            input:
                `let returnsOne = fn() { 1; };
let returnsOneReturner = fn() { returnsOne; };
returnsOneReturner()();
`,
            expected: 1,
        },
    }

    runVmTests(t, tests)
}
```

这就是我们无意中取得的成果：

```
$ go test ./vm
ok    monkey/vm    0.038s
```

如果不是我们毫不羞耻地拍自己的背，我会说那是结束一个章节时能达到的最高音。

## 局部绑定

我们当前对函数和函数调用的实现不支持局部绑定。我们确实支持绑定，但仅限于全局绑定。局部绑定在关键细节上有所不同，即它们是 *函数本地的*，意味着它们仅在函数的范围内可见和可访问。这个细节至关重要，因为它将局部绑定的实现与函数的实现联系在一起。既然我们在后者上做得很好，我们现在就可以着手前者了。

在本节结束时，我们希望以下这段 Monkey 代码能够正常工作：

```monkey
let globalSeed = 50;
let minusOne = fn() {
  let num = 1;
  globalSeed - num;
}
let minusTwo = fn() {
  let num = 2;
  globalSeed - num;
}
minusOne() + minusTwo()
```

这里我们有一个全局绑定和局部绑定的混合。`globalSeed` 是一个全局绑定，可以在嵌套作用域中访问，例如 `minusOne` 和 `minusTwo` 函数。然后我们还有局部绑定 `num`，在两个函数中都出现。关于 `num` 重要的是，它在这些函数之外不可访问，并且每个函数中 `num` 的两个绑定是唯一的，互不覆盖。

为了让这段代码被编译和执行，我们需要做几件事。

首先，我们需要定义 opcode 来告诉 VM 创建局部绑定并检索它们。我敢打赌你已经猜到了。

然后我们需要扩展编译器，使其能够正确输出这些新的 opcode。这意味着，它需要区分局部绑定和全局绑定，并且还要区分不同函数中同名的局部绑定。

最后一步是在 VM 中实现这些新指令和局部绑定。我们已经知道如何存储和访问全局绑定，这方面的知识不会浪费，因为绑定背后的主要机制不会改变。但对于局部绑定，我们需要一个新的存储。

一如既往，我们将分小步进行，从开头开始。

### 局部绑定的 Opcodes

我们已经有了两个用于绑定的 opcode：OpSetGlobal 和 OpGetGlobal。现在我们需要为局部绑定提供等价物。我们甚至不需要在这里发挥创造力，我们只需创建全局版本的“本地版本”并将它们命名为 OpSetLocal 和 OpGetLocal。它们也将像全局版本一样，每个都有一个操作数，即所讨论的局部绑定的唯一索引。

命名并不起太大作用，正如你所知，因为底层只是字节。重要的是这些 opcode 与全局的有所区别。它们应该告诉 VM 该绑定是当前正在执行的函数本地的，并且它对全局绑定绝对没有影响。绑定不应覆盖全局绑定，它本身也不应被全局绑定覆盖。

而且由于定义 opcode 是一项相当枯燥的任务，我们会给自己一点点装饰：与其给这些新 opcode 像其全局表亲那样使用两个字节的操作数，我们将使用一个字节，这是我们之前没有用过的。而且，除此之外，每个函数 256 个局部绑定对于平均的 Monkey 程序来说肯定足够了，对吧？

以下是定义：

// code/code.go

const (
    // [...] 
    OpGetLocal
    OpSetLocal
)

var definitions = map[Opcode]*Definition{
    // [...] 
    OpGetLocal: {"OpGetLocal", []int{1}},
    OpSetLocal: {"OpSetLocal", []int{1}},
}
```

这里没有什么令人惊讶的，只有单字节操作数是新的。这意味着我们需要确保现有的工具可以处理它们：

// code/code_test.go

func TestMake(t *testing.T) {
    tests := []struct {
        op         Opcode
        operands   []int
        expected   []byte
    }{
        // [...] 
        {OpGetLocal, []int{255}, []byte{byte(OpGetLocal), 255}},
    }

    // [...] 
}
```

理所当然地，Make 被这个一个字节难住了：

```
$ go test ./code
--- FAIL: TestMake (0.00s)
    code_test.go:26: wrong byte at pos 1. want=255, got=0
FAIL
FAIL    monkey/code 0.007s
```

让 Make 工作意味着扩展其 switch 语句，自从它被引入以来我就承诺要这样做：

// code/code.go

func Make(op Opcode, operands ...int) []byte {
    // [...] 

    offset := 1
    for i, o := range operands {
        width := def.OperandWidths[i]
        switch width {
        case 2:
            binary.BigEndian.PutUint16(instruction[offset:], uint16(o))
        case 1:
            instruction[offset] = byte(o)
        }
        offset += width
    }

    return instruction
}
```

添加的 case 1 分支足以使其工作，因为只有一个字节只有一种处理方式：
