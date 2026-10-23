the compiler.

And to make sure that an *object.Array is what ends up on the VM’s stack, we extend the testExpectedObject with a new case []int branch that turns our expected []int slices into expectations about an *object.Array.

Neat and reusable! I like it. The bad news is that if we run the tests, we don’t get a helpful error message, but a panic – I’ll spare you the stack trace. The reason the VM panics is because it doesn’t know about OpArray and its operand yet, and interprets the operand as another instruction. Nonsense guaranteed.

But regardless of whether we get a panic or a nice, readable error message from a failing test, it’s clear that we have to implement OpArray in the VM. Decode the operand, take the specified number of elements off the stack, construct an *object.Array, push it back on to the stack. We can do all of that with one case branch and one method:

```
// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 
    case code.OpArray:
        numElements := int(code.ReadUint16(vm.instructions[ip+1:]))
        ip += 2

        array := vm.buildArray(vm.sp-numElements, vm.sp)
        vm.sp = vm.sp - numElements

        err := vm.push(array)
        if err != nil {
            return err
        }

        // [...] 
    }
    // [...] 
}

func (vm *VM) buildArray(startIndex, endIndex int) object.Object {
    elements := make([]object.Object, endIndex-startIndex)

    for i := startIndex; i < endIndex; i++ {
        elements[i-startIndex] = vm.stack[i]
    }

    return &object.Array{Elements: elements}
}
```