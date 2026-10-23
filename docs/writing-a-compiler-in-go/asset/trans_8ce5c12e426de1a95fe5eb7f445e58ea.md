
```go
secondLocal := NewEnclosedSymbolTable(firstLocal)

expected := []Symbol{
    Symbol{Name: "a", Scope: BuiltinScope, Index: 0},
    Symbol{Name: "c", Scope: BuiltinScope, Index: 1},
    Symbol{Name: "e", Scope: BuiltinScope, Index: 2},
    Symbol{Name: "f", Scope: BuiltinScope, Index: 3},
}

for i, v := range expected {
    global.DefineBuiltin(i, v.Name)
}

for _, table := range []*SymbolTable{global, firstLocal, secondLocal} {
    for _, sym := range expected {
        result, ok := table.Resolve(sym.Name)
        if !ok {
            t.Errorf("name %s not resolvable", sym.Name)
            continue
        }
        if result != sym {
            t.Errorf("expected %s to resolve to %+v, got=%+v", sym.Name, sym, result)
        }
    }
}
```

在这个测试中，我们定义了三个相互嵌套的作用域，并期望使用 DefineBuiltin 在全局作用域中定义的所有符号都能解析到新的 BuiltinScope。

由于 DefineBuiltin 和 BuiltinScope 尚不存在，目前无需运行测试，但确保它们按预期报错也无妨：

```bash
$ go test -run TestDefineResolveBuiltins ./compiler
# monkey/compiler
compiler/symbol_table_test.go:162:28: undefined: BuiltinScope
compiler/symbol_table_test.go:163:28: undefined: BuiltinScope
compiler/symbol_table_test.go:164:28: undefined: BuiltinScope
compiler/symbol_table_test.go:165:28: undefined: BuiltinScope
compiler/symbol_table_test.go:169:9: global.DefineBuiltin undefined\
(type *SymbolTable has no field or method DefineBuiltin)
FAIL    monkey/compiler [build failed]
```

正如预期。定义 BuiltinScope 是两个必要步骤中较容易的一个，所以我们先做这个：

```go
// compiler/symbol_table.go

const (
    // [...]
    BuiltinScope SymbolScope = "BUILTIN"
```

但编写 DefineBuiltin 方法也并不困难：

```
// compiler/symbol_table.go

func (s *SymbolTable) DefineBuiltin(index int, name string) Symbol {
    symbol := Symbol{Name: name, Index: index, Scope: BuiltinScope}
    s.store[name] = symbol
    return symbol
}
```

与现有的 Define 方法相比，这里的方法要简单得多。用给定的索引在 BuiltinScope 中定义给定的名称，忽略是否被包含在另一个符号表中，然后完成：

```
$ go test -run TestDefineResolveBuiltins ./compiler
ok      monkey/compiler 0.007s
```

现在我们可以回到编译器中使用 DefineBuiltin 方法：

```
// compiler/compiler.go

func New() *Compiler {
    // [...] 
    symbolTable := NewSymbolTable()
    for i, v := range object.Builtins {
        symbolTable.DefineBuiltin(i, v.Name)
    }
    return &Compiler{
        // [...] 
        symbolTable:    symbolTable,
        // [...] 
    }
}
```

在初始化新的 *Compiler 时，我们遍历 object.Builtins 中的所有函数，并使用全局符号表上的 DefineBuiltin 方法将它们定义在 BuiltinScope 中。

这应该能修复我们的编译器测试，因为编译器现在可以解析对内置函数的引用：

```
$ go test ./compiler
--- FAIL: TestBuiltins (0.00s)
    compiler_test.go:1056: testInstructions failed: wrong instruction at 0.
    want="0000 OpGetBuiltin 0\n0002 OpArray 0\n0005 OpCall 1\n0007 OpPop\n\
```

0008 OpGetBuiltin 5\n0010 OpArray 0\n0013 OpConstant 0\n\
0016 OpCall 2\n0018 OpPop\n"
got ="0000 OpGetLocal 0\n0002 OpArray 0\n0005 OpCall 1\n0007 OpPop\n\
0008 OpGetLocal 5\n0010 OpArray 0\n0013 OpConstant 0\n\
0016 OpCall 2\n0018 OpPop\n"
FAIL
FAIL      monkey/compiler 0.009s

不过，并没有，而且这是因为我们的编译器忽略了符号表所说内容的一半。在当前状态下，使用符号表解析名称后，编译器只检查符号的作用域是否为 GlobalScope。但我们不能再用 if-else 检查来应付了。

我们现在有了第三个作用域，必须真正听从符号表所说的内容。最好在单独的方法中实现这一点：

```
// compiler/compiler.go

func (c *Compiler) loadSymbol(s Symbol) {
    switch s.Scope {
    case GlobalScope:
        c.emit(code.OpGetGlobal, s.Index)
    case LocalScope:
        c.emit(code.OpGetLocal, s.Index)
    case BuiltinScope:
        c.emit(code.OpGetBuiltin, s.Index)
    }
}
```

当我们现在使用 loadSymbol 来编译 *ast.Identifier 时，我们会为解析到的每个符号发出正确的指令：

```
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
        // [...] 
    case *ast.Identifier:
        symbol, ok := c.symbolTable.Resolve(node.Value)
        if !ok {
            return fmt.Errorf("undefined variable %s", node.Value)
        }
        c.loadSymbol(symbol)
        // [...] 
    }
    // [...] 
}
```

没错，这就对了：

```
$ go test ./compiler
ok      monkey/compiler 0.008s
```

这意味着，编译器现在可以编译对内置函数的引用。最好的部分是，它也保持了我们现有的调用约定——而我们无需做任何事情。太棒了！

是时候开始担心内置函数的执行这一实现细节了。

## 执行内置函数

“实现细节”听起来总是像在谈论更改的大小，而实际上它关乎可见性和抽象。功能的使用者不应该担心 *如何* 实现它——细节——而只应关注如何使用它。

Monkey 用户不应该担心如何执行内置函数。编译器也不应该担心。这完全是 VM 的职责。这给了我们很大的自由：实现的自由以及测试的自由。我们可以先写下我们希望 VM 做什么，然后再担心 *如何* 实现：

```
// vm/vm_test.go

func TestBuiltinFunctions(t *testing.T) {
   tests := []vmTestCase{
      {`len("")`, 0},
      {`len("four")`, 4},
      {`len("hello world")`, 11},
      {
         `len(1)`,
         &object.Error{
            Message: "argument to `len` not supported, got INTEGER",
         },
      },
      {`len("one", "two")`,
         &object.Error{
            Message: "wrong number of arguments. got=2, want=1",
         },
      },
      {`len([1, 2, 3])`, 3},
      {`len([])`, 0},
      {`puts("hello", "world!")`, Null},
      {`first([1, 2, 3])`, 1},
      {`first([])`, Null},
      {`first(1)`,
         &object.Error{
            Message: "argument to `first` must be ARRAY, got INTEGER",
         },
      },
      {`last([1, 2, 3])`, 3},
      {`last([])`, Null},
      {`last(1)`,
         &object.Error{
            Message: "argument to `last` must be ARRAY, got INTEGER",
         },
      },
      {`rest([1, 2, 3])`, []int{2, 3}},
      {`rest([])`, Null},
      {`push([], 1)`, []int{1}},
      {`push(1, 1)`,
```

```
&object.Error{
    Message: "argument to `push` must be ARRAY, got INTEGER",
}
}
}

runVmTests(t, tests)
}

```

```
func testExpectedObject(
    t *testing.T,
    expected interface{},
    actual object.Object,
) {
    t.Helper()

    switch expected := expected.(type) {
    // [...]

    case *object.Error:
        errObj, ok := actual.(*object.Error)
        if !ok {
            t.Errorf("object is not Error: %T (%+v)", actual, actual)
            return
        }
        if errObj.Message != expected.Message {
            t.Errorf("wrong error message. expected=%q, got=%q",
                expected.Message, errObj.Message)
        }
    }
}

```

这个测试是 evaluator 包中 TestBuiltinFunctions 测试的更新版本。evaluator.NULL 的引用已更改为 vm.Null，并且结果的测试已更新为使用我们的新测试助手。除此之外，它与前身做的事情相同：确保所有内置函数按预期工作，包括错误处理。

当然，这些函数目前都还不能工作。相反，运行测试时会发生 panic。我不会向你展示——为了节省半页书的篇幅，也为了免去你查看时的头痛。可以放心，主要原因是 VM 尚未解码和执行 OpGetBuiltin 指令。这就是我们的第一个任务：

```go
// vm/vm.go

func (vm *VM) Run() error {
    // [...]
    switch op {
        // [...]
        case code.OpGetBuiltin:

