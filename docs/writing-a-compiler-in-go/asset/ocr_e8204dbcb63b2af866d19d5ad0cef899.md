```
/\ [\. . .\]
}
```

These are the new last two lines of the case branch for \*ast\_FunctionLiteral. Instead of emitting OpConstant, we emit an OpClosure instruction. That’s all that needs to be changed and it’s enough to get the tests working again:

```
$ go test ./compiler
ok monkey/compiler 0.008s
```

The frontend of our Monkey implementation now treats every function as a closure. The VM, however, isn’t on the same page yet:

```
$ go test ./vm
--- FAIL: TestCallingFunctionsWithoutArguments (0.00s)
panic: runtime error: index out of range [recovered]
p\:\]\n\[\.\_\_\.
FAIL	monkey/vm	0.038s
```

The upside is that we don’t have to change any VM tests, we just have to get them to pass again. First step: wrap the mainFn we’re executing in a closure and update the initialization code for the VM.

```
/\ vm/vm.go
func New(bytecode \*compiler\_Bytecode) \*VM {
mainFn : = &object\_CompiledFunction\{Instructions: bytecode\_Instructions\}
mainClosure : = &object\_Closure\{Fn: mainFn\}
mainFrame : = NewFrame(mainClosure, 0)
\[\. . .\]
}
```

That doesn’t get us too far, because NewFrame and the underlying Frames do not know how to work with closures yet. What we need to do is make Frame keep a reference to a \*object\_Closure:

```
/\ vm/frame.go
type Frame struct {
c\_\_\_\*object\_Closure
\_\_\_ip\_\_\_int
\_\_\_basePointer int
}

func NewFrame(c\*object\_Closure, basePointer int) \*Frame {
f\_\_\_\_\_\_: = &Frame\{
```