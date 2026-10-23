
```
// [...]
}
```

这些是为 *ast.FunctionLiteral 的 case 分支新增的最后两行代码。我们不再发出 OpConstant，而是发出 OpClosure 指令。需要改动的就这些，而且足以让测试重新通过：

```
$ go test ./compiler
ok monkey/compiler 0.008s
```

我们的 Monkey 实现的前端现在将每个函数都当作闭包来处理。不过，VM 还没有跟上这一变化：

```
$ go test ./vm
--- FAIL: TestCallingFunctionsWithoutArguments (0.00s)
panic: runtime error: index out of range [recovered]
...
FAIL	monkey/vm	0.038s
```

好的一面是我们不必修改任何 VM 测试，只需让它们再次通过即可。第一步：将正在执行的 mainFn 包装到一个闭包中，并更新 VM 的初始化代码。

```
// vm/vm.go
func New(bytecode *compiler.Bytecode) *VM {
mainFn := &object.CompiledFunction{Instructions: bytecode.Instructions}
mainClosure := &object.Closure{Fn: mainFn}
mainFrame := NewFrame(mainClosure, 0)
[...]
}
```

这还不足以让我们走很远，因为 NewFrame 以及底层的 Frames 还不知道如何处理闭包。我们需要做的是让 Frame 持有一个 *object.Closure 的引用：

```
// vm/frame.go
type Frame struct {
cl *object.Closure
ip int
basePointer int
}

func NewFrame(c *object.Closure, basePointer int) *Frame {
f := &Frame{
```
```
cl: cl,
ip: -1,
basePointer: basePointer,
}
return f
}
func (f *Frame) Instructions() code.Instructions {
return f.cl.Fn.Instructions
}
```

这些改动归根结底是增加了一层间接性。Frame 不再持有保存 *object.CompiledFunction 的 fn，而是拥有一个 cl 字段，指向 object.Closure。要获取 Instructions，我们现在必须先经过 cl 字段，再经过闭包所包装的 Fn。

既然我们的 frames 现在假定它们只需要处理闭包，那么我们在初始化并将它们压入 frame 栈时，实际上就需要给它们闭包。这个初始化此前发生在 vm 的 callFunction 方法中。现在是时候将其重命名为 callClosure，并用闭包来初始化 frames 了：

```
// vm/vm.go

func (vm *VM) executeCall(numArgs int) error {
callee := vm.stack[vm.sp-1-numArgs]
switch callee := callee.(type) {
case *object.Closure:
return vm.callClosure(callee, numArgs)
case *object.Builtin:
return vm.callBuiltin(callee, numArgs)
default:
return fmt.Errorf("calling non-closure and non-builtin")
}
}

func (vm *VM) callClosure(cl *object.Closure, numArgs int) error {
if numArgs != cl.Fn.NumParameters {
return fmt.Errorf("wrong number of arguments: want=%d, got=%d", cl.Fn.NumParameters, numArgs)
}

frame := NewFrame(cl, vm.sp-numArgs)
vm.pushFrame(frame)

vm.sp = frame.basePointer + cl.Fn.NumLocals

return nil
}
```

别搞错了：callClosure 只是 callFunction 的翻版。名称改了，局部变量也从 fn 重命名为 cl，因为现在被调用的是一个 *object.Closure。随之而来的是，我们不得不向 cl.Fn 询问 NumParameters 和 NumLocals。不过，该方法所做的事情是一样的。

当然，在 executeCall 中也需要进行同样的重命名，我们现在期望栈上放的是 *object.Closure，而不是 *object.CompiledFunction。

现在剩下要做的就是实际处理 OpClosure 指令。这意味着从常量池中取出函数、将它们包装成闭包，然后把闭包压入栈中，以便调用：

```
// vm/vm.go
func (vm *VM) Run() error {
// [...]
switch op {
// [...]
case code.OpClosure:
constIndex := code.ReadUint16(ins[ip+1:])
_ = code.ReadUint8(ins[ip+3:])
vm.currentFrame().ip += 3

err := vm.pushClosure(int(constIndex))
if err != nil {
return err
}

// [...]
}
 // [...]
}

func (vm *VM) pushClosure(constIndex int) error {
constant := vm.constants[constIndex]
function, ok := constant.(*object.CompiledFunction)
if !ok {
return fmt.Errorf("not a function: %v", constant)
}

closure := &object.Closure{Fn: function}
return vm.push(closure)
}
```

由于 OpClosure 指令有两个操作数，即使我们只需要其中一个，也必须对它们进行解码或跳过。如果做不到这一点，VM 的其余部分就会被未使用的操作数绊倒。虽然手动递增 ip 就足以让它越过两个操作数，但我们还是放了一个象征性的、完全无用的 ReadUint8 在那里，以标明我们稍后将解码第二个操作数的位置。这个 _ 是一个小小的提醒：我们还有工作要做。

然后，我们将第一个操作数 constIndex 传给新的 pushClosure 方法，该方法会负责在常量中查找指定的函数，将其转换为 *object.Closure 并放入栈中。在那里，它可以像之前的 *object.CompiledFunctions 一样被传递或调用，也就是说，它确实奏效了：

```
$ go test ./vm
ok      monkey/vm   0.051s
```

现在，一切都是闭包。是时候添加闭包了。

## 编译并解析自由变量

正如我之前所说，编译闭包的核心在于自由变量以及如何驯服它们。在这方面，我们做得不错。有了 `object.Closure` 上的 `Free` 字段，我们就有地方存储自由变量了；而通过 `OpClosure` 操作码，我们可以告诉 VM 将自由变量存储到那里。

但我们还需要一个操作码来检索 `Free` 字段中的值，并将它们压入栈中。既然我们其他用于检索值的操作码叫 `OpGetLocal`、`OpGetGlobal` 和 `OpGetBuiltin`，那么把这个操作码叫做 `OpGetFree` 也就顺理成章了：

```go
// code/code.go

const (
    // [...]

    OpGetFree
)

var definitions = map[Opcode]*Definition{
    // [...]

    OpGetFree: {"OpGetFree", []int{1}},
}
```

既然有了它，我们就可以编写第一个编译器测试，用 `OpGetFree` 来获取一个 *真正的* 闭包中引用的自由变量：

```go
// compiler/compiler_test.go

func TestClosures(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `
fn(a) {
    fn(b) {
        a + b
    }
}
`,
            expectedConstants: []interface{}{
                []code.Instructions{
                    code.Make(code.OpGetFree, 0),
                    code.Make(code.OpGetLocal, 0),
                    code.Make(code.OpAdd),
                    code.Make(code.OpReturnValue),
                },
```
```
```go
[]code.Instructions{
    code.Make(code.OpGetLocal, 0),
    code.Make(code.OpClosure, 0, 1),
    code.Make(code.OpReturnValue),
},
},
expectedInstructions: []code.Instructions{
    code.Make(code.OpClosure, 1, 0),
    code.Make(code.OpPop),
},
},
}

runCompilerTests(t, tests)
}
```
```

这个测试简洁地展示了我们的闭包实现应该如何工作。

测试输入中最内层的函数，也就是带有参数 b 的那个函数，是一个真正的闭包：它不仅引用了局部变量 b，还引用了 a，而 a 是在外层作用域中定义的。从这个函数的角度来看，a 是一个自由变量，我们期望编译器发出 OpGetFree 指令将它压入栈中。b 将通过普通的 OpGetLocal 压入栈中。

在外层函数中，a 应该通过 OpGetLocal 加载到栈上——尽管该函数本身从未引用它。但因为它被内层函数引用，所以必须在 VM 执行下一条指令 OpClosure 之前将其压入栈中。

OpClosure 的第二个操作数现在派上了用场，其值为 1，因为栈上有一个自由变量 a，正等待被保存到 object.Closure 的 Free 字段中。

在主程序的 expectedInstructions 中，另一个 OpClosure 负责创建一个闭包，但这次是我们已经了解的旧用例，不涉及任何自由变量。

这就是我们实现闭包的方式，以编译器测试中的预期结果表达出来。不过，这还没完。我们还希望支持深度嵌套的闭包：

```go
// compiler/compiler_test.go

func TestClosures(t *testing.T) {
tests := []compilerTestCase{
```

