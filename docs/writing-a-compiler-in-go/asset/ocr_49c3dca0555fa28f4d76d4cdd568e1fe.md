decide to bend over backwards by changing our VM to only use frames when calling and executing a function. Or, we can go right and choose a much more elegant and smoother approach, which modifies the VM so that it not only uses frames for functions, but also treats the main program, the bytecode.Instructions, as if it were a function.

Yes, of course we’re going right.

And even better news than the fact that we’re going to build something smooth and elegant is that we don’t even have to write tests, since this is another prime example for the term “implementation detail”: the visible behaviour of the VM should not change one bit when we now change it to use frames. It’s an internal change only. And to make sure that our VM keeps on working the way it currently does, we already have our test suite.

So, let’s build a stack for frames:

```
// vm/vm.go

type VM struct {
    // [...] 
    
    frames      []*Frame
    framesIndex int
}

func (vm *VM) currentFrame() *Frame {
    return vm.frames[vm.framesIndex-1]
}

func (vm *VM) pushFrame(f *Frame) {
    vm.frames[vm.framesIndex] = f
    vm.framesIndex++
}

func (vm *VM) popFrame() *Frame {
    vm.framesIndex--
    return vm.frames[vm.framesIndex]
}
```

Private and still unused changes – all the tests are still green, but now we have a stack for frames in place. Just like with our other stacks, we use a slice as the underlying data structure and an integer as index. Since it’s nice to have a little bit of performance here, we use a slightly different approach than the one used in the compiler for the scopes stack. Instead of appending and slicing off, we pre-allocate the frames slice.