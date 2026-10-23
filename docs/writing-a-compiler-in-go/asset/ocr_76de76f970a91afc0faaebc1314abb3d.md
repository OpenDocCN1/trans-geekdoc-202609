```
```go
// vm/vm.go

func (vm *VM) StackTop() object.Object {
    if vm.sp == 0 {
        return nil
    }
    return vm.stack[vm.sp-1]
}
```
```

Now the only thing that’s keeping us from running the tests is the missing Run method of the VM:

```
```text
$ go test ./vm
# monkey/vm
vm/vm_test.go:41:11: vm.Run undefined (type *VM has no field or method Run)
FAIL    monkey/vm [build failed]
```
```

The Run method is what turns the VM into a virtual machine. It contains its heartbeat, the main loop, the fetch-decode-execute cycle:

```
```go
// vm/vm.go

func (vm *VM) Run() error {
    for ip := 0; ip < len(vm.instructions); ip++ {
        op := code.Opcode(vm.instructions[ip])

        switch op {
        }
    }

    return nil
}
```
```

That’s the first part of the cycle, the “fetch”. We iterate through vm.instructions by incrementing the instruction pointer, ip, and fetch the current instruction by directly accessing vm.instructions. Then we turn the byte into an opcode. It’s important that we do not use code.Lookup here to get from a byte to an opcode. That would be far too slow. It costs time to move the byte around, lookup the opcode’s definition, return it and take it apart.

I know that this doesn’t sound like my usual chant of “we’re here to learn, not to build the fastest thing ever”, but we’re in *the hot path* here; everything we can get rid of, we should throw out. Using code.Lookup here would be like putting a sleep statement in the loop. And in contrast to a generic method that wants to lookup an opcode (like our mini-disassembler in Instructions.String) we have to encode our knowledge about the instructions into the VM’s Run method anyway. We can’t just delegate the execution away and treat every instruction