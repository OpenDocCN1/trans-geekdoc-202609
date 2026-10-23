as long as a function call. Guess what? We already have that and call it Frame. We only need to add one more field to it, the so called basePointer:

```
// vm/frame.go

type Frame struct {
    fn          *object.CompiledFunction
    ip          int
    basePointer int
}

func NewFrame(fn *object.CompiledFunction, basePointer int) *Frame {
    f := &Frame{
        fn:          fn,
        ip:          -1,
        basePointer: basePointer,
    }

    return f
}
```

The name “base pointer” is not something I made up. On the contrary, it’s common practice to give this name to the pointer that points to the bottom of the stack of the current call frame. It’s the base for a lot of references while executing a function. Sometimes it’s also called “frame pointer”. In the upcoming sections of this book we’ll use it even more. Right now, we just need to initialize it before we push a new frame:

```
// vm/vm.go

func New(bytecode *compiler.Bytecode) *VM {
    // [...] 

    mainFrame := NewFrame(mainFn, 0)

    // [...] 
}

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 

    case code.OpCall:
        fn, ok := vm.stack[vm.sp-1].(*object.CompiledFunction)
        if !ok {
            return fmt.Errorf("calling non-function")
        }
        frame := NewFrame(fn, vm.sp)
        vm.pushFrame(frame)

    // [...] 
}
```