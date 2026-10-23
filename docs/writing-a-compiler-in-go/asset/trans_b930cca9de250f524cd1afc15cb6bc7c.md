
```
				return newError("wrong number of arguments. got=%d, want=1",
						len(args))
			}
			if args[0].Type() != ARRAY_OBJ {
				return newError("argument to `last` must be ARRAY, got %s",
					args[0].Type())
			}

			arr := args[0].(*Array)
			length := len(arr.Elements)
			if length > 0 {
				return arr.Elements[length-1]
			}

			return nil
		},
	},
},
}
```

除了获取数组的第一个和最后一个元素外，有时获取除第一个之外的所有元素也非常有用，这就是我们拥有 `rest` 的原因：

```
// object/builtins.go

var Builtins = []struct {
Name		string
Builtin	*Builtin
}{
// [ ... ]
{
"rest",
&Builtin{Fn: func(args ...Object) Object {
if len(args) != 1 {
return newError("wrong number of arguments. got=%d, want=1",
len(args))
}
if args[0].Type() != ARRAY_OBJ {
return newError("argument to `rest` must be ARRAY, got %s",
args[0].Type())
}

arr := args[0].(*Array)
length := len(arr.Elements)
if length > 0 {
newElements := make([]Object, length-1, length-1)
copy(newElements, arr.Elements[1:length])
return &Array{Elements: newElements}
}

return nil
},
},
}
```

然后我们定义 `push`，它向数组中添加一个元素。它并不改变原数组，而是保持原数组不变，并分配一个新数组，其中包含原数组的元素以及新添加的元素：

```
// object/builtins.go

var Builtins = []struct {
    Name     string
    Builtin  *Builtin
}{}
    // [...]
    {
        "push",
        &Builtin{Fn: func(args ...Object) Object {
            if len(args) != 2 {
                return newError("wrong number of arguments. got=%d, want=2", len(args))
            }
            if args[0].Type() != ARRAY_OBJ {
                return newError("argument to `push` must be ARRAY, got %s", args[0].Type())
            }

            arr := args[0].(*Array)
            length := len(arr.Elements)

            newElements := make([]Object, length+1, length+1)
            copy(newElements, arr.Elements)
            newElements[length] = args[1]

            return &Array{Elements: newElements}
        },
    },
},
```

这就完成了我们要实现的所有内置函数。现在它们都定义在 `object.Builtins` 中，去除了对 `object` 包的冗余引用，也不再提及 `evaluator.NULL`。

现在我们可以回到 `evaluator/builtins.go`，将所有目前重复的定义替换为对 `object.GetBuiltinByName` 的调用：

```
// evaluator/builtins.go

import (
    "monkey/object"
)

var builtins = map[string]*object.Builtin{
    "len":   object.GetBuiltinByName("len"),
    "puts":  object.GetBuiltinByName("puts"),
    "first": object.GetBuiltinByName("first"),
```

```
"last": object.GetBuiltinByName("last"),
"rest": object.GetBuiltinByName("rest"),
"push": object.GetBuiltinByName("push"),
}
```

是不是很巧妙？这就是整个文件！现在我们需要进行健全性检查，以确保一切仍然正常运行：

```
$ go test ./evaluator
ok      monkey/evaluator   0.009s
```

太好了！这样一来，内置函数现在就可以被所有导入 `object` 包的软件包使用了。它们不再依赖于 `evaluator.NULL`，而是遵循自带空值（bring-your-own-null）的方法。求值器的运行方式与 *Writing An Interpreter In Go* 结尾时保持一致，所有测试都通过了。

完美。这就是我所称的重构。它让我们现在需要做的一切都变得更加容易。

## 实施变更：计划

你知道我喜欢什么吗？消除边缘案例，并尽可能减少边缘案例。

这就是为什么我想保持现有的调用约定不变，即使是针对内置函数也是如此。这意味着，为了调用内置函数，你需要做的与其他任何函数相同：将内置函数压入栈，压入调用参数，然后使用 `OpCall` 指令调用该函数。

内置函数*如何*被执行，这是 VM 的实现细节，我们稍后再担心。

从编译器的角度来看，在编译涉及内置函数的调用表达式时，唯一不同的地方是函数如何进入栈。为此，我们确实需要引入另一种情况，但这不是一个边缘案例。

内置函数既不在全局作用域中定义，也不在局部作用域中定义。它们存在于自己的作用域中。我们需要将这个作用域引入编译器及其符号表，以便正确解析对内置函数的引用。

我们将把这个作用域称为 `BuiltinScope`，并在其中按刚刚移动到 `object.Builtins` 定义切片中的顺序定义所有内置函数。这是一个重要的细节，因为这是我们的支线任务（sidequest）。

当编译器（在符号表的帮助下）检测到对内置函数的引用时，它将发出 `OpGetBuiltin` 指令。该指令的操作数将是被引用函数在 `object.Builtins` 中的索引。

由于 VM 也可以访问 `object.Builtins`，它可以使用指令的操作数从 `object.Builtins` 中获取正确的函数，并将其压入栈中，以便随后可以调用它。

同样，我们可以稍后再担心*那*是如何发生的，一旦我们编写了第一个 VM 测试。但作为下一步，我们需要确保编译器知道如何解析对内置函数的引用。为此，我们需要一个新的操作码和一个

## 内置函数新作用域

首先，正如我们现在所知，这通常意味着一个新的操作码。这次它被称为 OpGetBuiltin：

```
// code/code.go

const (
    // [...] 
    OpGetBuiltin
)

var definitions = map[Opcode]*Definition{
    // [...] 
    OpGetBuiltin: {"OpGetBuiltin", []int{1}},
}
```

该操作码带有一个宽一字节的操作数。这意味着我们可以定义多达 256 个内置函数。听起来很少吗？让我们只说，一旦我们达到这个限制，我们可以始终将其改为两个字节。

你知道流程：先操作码，然后是编译器测试。现在有了 OpGetBuiltin，我们可以编写一个测试，期望我们的编译器将对内置函数的引用转换为 OpGetBuiltin 指令。

```
// compiler/compiler_test.go

func TestBuiltins(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `
len([]);
push([], 1);
`
            expectedConstants: []interface{}{1},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpGetBuiltin, 0),
                code.Make(code.OpArray, 0),
                code.Make(code.OpCall, 1),
                code.Make(code.OpPop),
                code.Make(code.OpGetBuiltin, 5),
                code.Make(code.OpArray, 0),
                code.Make(code.OpConstant, 0),
                code.Make(code.OpCall, 2),
                code.Make(code.OpPop),
            },
        },
        {

```

```
input: `fn() { len([]) }`,
expectedConstants: []interface{}{
    []code.Instructions{
        code.Make(code.OpGetBuiltin, 0),
        code.Make(code.OpArray, 0),
        code.Make(code.OpCall, 1),
        code.Make(code.OpReturnValue),
    },
},
expectedInstructions: []code.Instructions{
    code.Make(code.OpConstant, 0),
    code.Make(code.OpPop),
},
},
}

runCompilerTests(t, tests)
}
```

这两个测试用例中的第一个确保了两件事。首先，调用内置函数遵循我们既定的调用约定，其次，OpGetBuiltin 指令的操作数是被引用函数在 object.Builtins 中的索引。

第二个测试用例则确保对内置函数的引用被正确解析，无论它们出现在哪个作用域中，这与局部和全局作用域的现有行为不同。

如果我们运行测试，我们会得到一个编译器错误：

```
$ go test ./compiler
--- FAIL: TestBuiltins (0.00s)
compiler_test.go:1049: compiler error: undefined variable len
FAIL
FAIL    monkey/compiler 0.008s
```

由于修复此失败测试包含我们的编译器正确解析引用，我们下一站是编译器解决解析需求的地方：符号表。

在这里，我们同样需要编写一个测试，以确保无论符号表被嵌套多少层，内置函数始终解析为 BuiltinScope 中的一个符号：

```
// compiler/symbol_table_test.go

func TestDefineResolveBuiltins(t *testing.T) {
    global := NewSymbolTable()
    firstLocal := NewEnclosedSymbolTable(global)

