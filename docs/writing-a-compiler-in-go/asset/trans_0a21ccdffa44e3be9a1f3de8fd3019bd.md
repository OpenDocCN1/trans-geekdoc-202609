
在测试用例中，这些是 *ast.StringLiterals，我们现在可以成功编译它们。

接下来，我们为 VM 编写一个测试，以确保相同的 Monkey 代码在编译为字节码指令后可以由 VM 执行：

// vm/vm_test.go
```go
func TestStringExpressions(t *testing.T) {
    tests := []vmTestCase{
        {`"monkey"`, "monkey"},
        {`"mon" + "key"`, "monkey"},
        {`"mon" + "key" + "banana"`, "monkeybanana"},
    }

    runVmTests(t, tests)
}
```

这些测试用例与编译器测试中的相同，只是额外断言将两个以上的字符串相加也应该有效——因为为什么不呢？

这里同样，我们需要一个新的 testStringObject 辅助函数来确保最终进入 VM 栈的是 *object.Strings。它也是其 testIntegerObject 对应的副本，并确保 VM 生成的字符串是我们期望的：

// vm/vm_test.go
```go
func testExpectedObject(
    t *testing.T,
    expected interface{},
    actual object.Object,
) {
    t.Helper()

    switch expected := expected.(type) {
    // [...] 

    case string:
        err := testStringObject(expected, actual)
        if err != nil {
            t.Errorf("testStringObject failed: %s", err)
        }
    }
}

func testStringObject(expected string, actual object.Object) error {
    result, ok := actual.(*object.String)
    if !ok {
```
```
```go
if op != code.OpAdd {
    return fmt.Errorf("unknown string operator: %d", op)
}

leftValue := left.(*object.String).Value
rightValue := right.(*object.String).Value

return vm.push(&object.String{Value: leftValue + rightValue})
}
```

在 executeBinaryOperation 中，条件判断已被更改为带有字符串新 case 分支的 switch 语句。在那里，我们将两个字符串的实际相加委托给 executeBinaryStringOperation，后者解包 *object.Strings，连接底层的 Go 字符串并将结果推回 VM 的栈。

就这样：
```text
$ go test ./vm
ok   	monkey/vm	0.028s
```

Monkey 字符串现已完全实现，包括字符串连接。接下来：数组。

## 数组

数组是我们添加到此 Monkey 实现中的第一个复合数据类型。也就是说，大致来说，数组是由 *组成* 其他数据类型组成的。对我们来说实际的后果是，我们不能将数组字面量视为常量表达式。

由于数组由多个元素组成，而数组字面量由产生这些元素的多个表达式组成，因此数组字面量本身的值可能在编译时和运行时之间发生变化。这里有一个例子：
```
[1 + 2, 3 + 4, 5 + 6]
```

不要被这些整数表达式分散注意力。它们非常简单，优化编译器可以预先计算它们，是的，但重点是这些可以是 *任何* 类型的表达式——整数字面量、字符串连接、函数字面量、函数调用等等。只有在运行时我们才能可靠地确定它们求值的结果。

从整数和字符串字面量来看，我们现在必须稍微改变一下方法。与其在编译时构建数组并将其作为常量池传递给 VM，不如告诉 VM 如何自行构建它。

为此，我们定义了一个新的操作码，称为 `OpArray`，它有一个操作数：数组字面量中元素的数量。然后当我们编译 `*ast.ArrayLiteral` 时，我们首先编译其所有元素。由于这些是 `ast.Expressions`，编译它们会产生使 VM 栈上留下 N 个值的指令，其中 N 是数组字面量中元素的数量。然后，我们将发出一个 `OpArray` 指令，其操作数为 N，即元素的数量。编译完成。

当 VM 执行 `OpArray` 指令时，它从栈中取出 N 个元素，从中构建一个 `*object.Array`，并将其推回栈。完成。我们告诉了 VM 如何构建数组。

让我们立即将此计划付诸实践。以下是 `OpArray` 的定义：

// code/code.go
```
const (
    // [...] 
    OpArray
)

var definitions = map[Opcode]*Definition{
    // [...] 
    OpArray: {"OpArray", []int{2}},
}
```

唯一的操作数宽度为两个字节。这使我们得到 65535 作为数组字面量中元素的最大可能数量。如果你有一个需要超过该数量的 Monkey 程序，请告诉我。

在我们将此新操作码的计划翻译成编译器代码之前，我们需要像往常一样编写一个测试：

// compiler/compiler_test.go
```go
func TestArrayLiterals(t *testing.T) {
    tests := []compilerTestCase{
        {
            input:           "[]",
            expectedConstants: []interface{}{},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpArray, 0),
                code.Make(code.OpPop),
            },
        },
        {
            input:           "[1, 2, 3]",
            expectedConstants: []interface{}{1, 2, 3},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpConstant, 1),
                code.Make(code.OpConstant, 2),
                code.Make(code.OpArray, 3),
                code.Make(code.OpPop),
            },
        },
        {
            input:           "[1 + 2, 3 - 4, 5 * 6]",
            expectedConstants: []interface{}{1, 2, 3, 4, 5, 6},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpConstant, 1),
                code.Make(code.OpAdd),
                code.Make(code.OpConstant, 2),
                code.Make(code.OpConstant, 3),
                code.Make(code.OpSub),
                code.Make(code.OpConstant, 4),
                code.Make(code.OpConstant, 5),
                code.Make(code.OpMul),
                code.Make(code.OpArray, 3),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

这也是我们计划的翻译，只是它以断言的形式表达，而非工作代码。我们期望编译器将数组字面量中的元素编译为使值留在栈上的指令，并且我们期望它发出一个 OpArray 指令，其操作数为数组字面量中元素的数量。

不出所料，这还没有发生：
```
$ go test ./compiler
--- FAIL: TestArrayLiterals (0.00s)
    compiler_test.go:477: testInstructions failed: wrong instructions length.
        want="0000 OpArray 0\n0003 OpPop\n"
        got ="0000 OpPop\n"
FAIL
FAIL    monkey/compiler 0.009s
```

幸运的是，修复此测试的代码并不比解释它所需的文字长：
// compiler/compiler.go
```go
func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 
    case *ast.ArrayLiteral:
        for _, el := range node.Elements {
            err := c.Compile(el)
            if err != nil {
                return err
            }
        }

        c.emit(code.OpArray, len(node.Elements))

    // [...] 
    }

    // [...] 
}
```

正如我们计划的那样：
```
$ go test ./compiler
ok      monkey/compiler 0.011s
```

我们计划的下一部分包括 VM，在那里我们也需要实现 OpArray。我们从一个测试开始：
```go
// vm/vm_test.go

func TestArrayLiterals(t *testing.T) {
    tests := []vmTestCase{
        {"[]", []int{}},
        {"[1, 2, 3]", []int{1, 2, 3}},
        {"[1 + 2, 3 * 4, 5 + 6]", []int{3, 12, 11}},
    }

    runVmTests(t, tests)
}

func testExpectedObject(
    t *testing.T,
    expected interface{},
    actual object.Object,
) {
    t.Helper()

    switch expected := expected.(type) {
    // [...] 
    case []int:
        array, ok := actual.(*object.Array)
        if !ok {
            t.Errorf("object not Array: %T (%v)", actual, actual)
            return
        }

        if len(array.Elements) != len(expected) {
            t.Errorf("wrong num of elements. want=%d, got=%d",
                len(expected), len(array.Elements))
            return
        }

        for i, expectedElem := range expected {
            err := testIntegerObject(int64(expectedElem), array.Elements[i])
            if err != nil {
                t.Errorf("testIntegerObject failed: %s", err)
            }
        }

    }
}
```

这些测试用例中的 Monkey 代码与编译器测试中的完全相同。不过，这里更重要的是确保空数组字面量能正常工作，因为在 VM 中遇到差一错误比在
