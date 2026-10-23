
Now we just need to use it. The first task is to allocate said slice and push the outermost, the “main frame”, on to it:

```go
// vm/vm.go

const MaxFrames = 1024

func New(bytecode *compiler.Bytecode) *VM {
    mainFn := &object.CompiledFunction{Instructions: bytecode.Instructions}
    mainFrame := NewFrame(mainFn)

    frames := make([]*Frame, MaxFrames)
    frames[0] = mainFrame

    return &VM{
        constants: bytecode.Constants,

        stack: make([]object.Object, StackSize),
        sp:    0,

        globals: make([]object.Object, GlobalsSize),

        frames:      frames,
        framesIndex: 1,
    }
}
```

New here is the prelude before we initialize a new *VM*.

As the first thing, we create a `mainFn`. That’s the fictional main frame that contains the `bytecode.Instructions`, which make up the whole Monkey program. Then we allocate the frames stack with a maximum of `MaxFrames` slots. The value of 1024 is arbitrary but should be enough for us as long as we don’t nest function calls too much. The first frame on this new frames stack is the `mainFrame`. And then, following the fields we already know, we put the frames and the `framesIndex` of 1 into the newly created *VM*.

At the same time, we’ve also **removed** the initialization of the instructions field in this New function and now need to remove it from the definition of VM, too:

```go
// vm/vm.go

type VM struct {
    constants []object.Object

    stack []object.Object
    sp    int
```

```
globals []object.Object

frames     []*Frame
framesIndex int
}
```

With the instructions slice gone, we now need to change the way we access the instructions and the instruction pointer inside the VM and make sure that we always access them by going through the current frame.

The first change we need to make is in the VM’s main loop. Since the ip can’t be initialized in the loop anymore, but only incremented there, we need to change from an old school for loop to Go’s version of a while loop, where we have just one condition and increment the ip manually in its body:

```
// vm/vm.go

func (vm *VM) Run() error {
    var ip int
    var ins code.Instructions
    var op code.Opcode

    for vm.currentFrame().ip < len(vm.currentFrame().Instructions())-1 {
        vm.currentFrame().ip++

        ip = vm.currentFrame().ip
        ins = vm.currentFrame().Instructions()
        op = code.Opcode(ins[ip])

        switch op {
        // [...] 
        }
    }

    return nil
}
```

We add the three helper variables – ip, ins and op – at the top of the Run method, so the rest of it doesn’t become too crowded with calls to currentFrame(). Especially since we now need to update every place in Run where we either read in operands or access or modify the instruction pointer:

```
// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    case code.OpConstant:
        constIndex := code.ReadUint16(ins[ip+1:])
        vm.currentFrame().ip += 2
    // [...] 
}
```

```
case code.OpJump:
    pos := int(code.ReadUint16(ins[ip+1:]))
    vm.currentFrame().ip = pos - 1
// [...]

case code.OpJumpNotTruthy:
    pos := int(code.ReadUint16(ins[ip+1:]))
    vm.currentFrame().ip += 2

    condition := vm.pop()
    if !isTruthy(condition) {
        vm.currentFrame().ip = pos - 1
    }
// [...]

case code.OpSetGlobal:
    globalIndex := code.ReadUint16(ins[ip+1:])
    vm.currentFrame().ip += 2
// [...]

case code.OpGetGlobal:
    globalIndex := code.ReadUint16(ins[ip+1:])
    vm.currentFrame().ip += 2
// [...]

case code.OpArray:
    numElements := int(code.ReadUint16(ins[ip+1:]))
    vm.currentFrame().ip += 2
// [...]

case code.OpHash:
    numElements := int(code.ReadUint16(ins[ip+1:]))
    vm.currentFrame().ip += 2
// [...]

}
    // [...] 
}
```

And that was it: our VM is now fully converted to frames! And the best bit is that all the tests are still green:

```
$ go test ./vm
ok      monkey/vm  0.036s
```

Time to add function calls.

## Executing Function Calls

It’s high time and we know exactly what we want:

~~~go
// vm/vm_test.go

func TestCallingFunctionsWithoutArguments(t *testing.T) {
	tests := []vmTestCase{
		{
			input: `
let fivePlusTen = fn() { 5 + 10; };
fivePlusTen();
`,
			expected: 15,
		},
	}

	runVmTests(t, tests)
}
~~~

That’s what we’re after! Remember? It’s the goal of this section. Question is, can we already get it to work?

~~~text
$ go test ./vm
--- FAIL: TestCallingFunctionsWithoutArguments (0.00s)
vm_test.go:443: testIntegerObject failed: object is not Integer.\
    got=*object.CompiledFunction (&{Instructions:\
0000 OpConstant 0
0003 OpConstant 1
0006 OpAdd
0007 OpReturnValue
})
FAIL
FAIL    monkey/vm  0.036s
~~~

Well, we always do, don’t we?

Most of the things we need are in place already. We know how to handle global bindings, check. We know how to handle integer expressions, check. We know how to load constants, which compiled functions are, check. And we know how to execute frames, so check here too. What we haven’t yet implemented is the OpCall opcode.

But we already know pretty well what to do when we come across an OpCall:

~~~go
// vm/vm.go

func (vm *VM) Run() error {
	// [...]
	switch op {
	// [...]

	case code.OpCall:
		fn, ok := vm.stack[vm.sp-1].(*object.CompiledFunction)
		if !ok {
			return fmt.Errorf("calling non-function")
```

```
}
    frame := NewFrame(fn)
    vm.pushFrame(frame)

    // [...] 
}
    // [...] 
```
```

We get the compiled function off the stack and check if it’s indeed an *object.CompiledFunction. If it’s not, we return an error. If it is, we create a new frame that contains a reference to this function and push it on to the frames stack. As a result, the next iteration of the VM’s main loop fetches the next instruction from the *object.CompiledFunction.

Cross your fingers and awkwardly try to type go test ./vm with them:

```
$ go test ./vm
--- FAIL: TestCallingFunctionsWithoutArguments (0.00s)
    vm_test.go:169: testIntegerObject failed: object has wrong value.\
    got=10, want=15
FAIL
FAIL    monkey/vm    0.034s
```

Huh. Okay. We got 10 when we wanted 15 to be returned. Shouldn’t 10 be popped off the stack when we come across the OpAdd instruction? Why is it stil– ahh! We always check for the “last popped element” in our tests! And the 15 hasn’t been popped off the stack yet.

Come to think of it: why did we even expect that this would work? We haven’t even told the VM yet to handle OpReturnValue instructions!

```
// vm/vm.go
```

```go
func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 

    case code.OpReturnValue:
        returnValue := vm.pop()

        vm.popFrame()
        vm.pop()

        err := vm.push(returnValue)
        if err != nil {
            return err
        }
    }
```

```
// [...] 
    }
// [...] 
}
```

We first pop the return value off the stack and put it on the side. That’s the first part of our calling convention: in the case of an OpReturnValue instruction, the return value sits on top of the stack. Then we pop the frame we just executed off the frame stack so that the next iteration of the VM’s main loop continues executing in the caller context.

And then there’s another vm.pop() call to get the just-called *object.CompiledFunction off the stack. Remember that we said it’s the VM’s implicit task to get the executed function off the stack? This is it.

## Watch this:

```
$ go test ./vm
ok      monkey/vm  0.035s
```

We just called and executed a function. Remember this moment! This is a milestone when developing a bytecode VM. Our VM is now not just humming along, it’s roaring. We can even execute multiple functions – sequentially or nested in one another:

```
// vm/vm_test.go

func TestCallingFunctionsWithoutArguments(t *testing.T) {
    tests := []vmTestCase{
        // [...] 
        {
            input: `
let one = fn() { 1; };
let two = fn() { 2; };
one() + two()
`
            expected: 3,
        },
        {
            input: `
let a = fn() { 1 };
let b = fn() { a() + 1 };
let c = fn() { b() + 1 };
c();
`
            expected: 3,
        }
    }

runVmTests(t, tests)
```
