got=2, want=-1
vm_test.go:30: testIntegerObject failed: object has wrong value.\
got=5, want=55
vm_test.go:30: testIntegerObject failed: object has wrong value.\
got=12, want=60
vm_test.go:30: testIntegerObject failed: object has wrong value.\
got=2, want=32
vm_test.go:30: testIntegerObject failed: object has wrong value.\
got=12, want=20
vm_test.go:30: testIntegerObject failed: object has wrong value.\
got=12, want=25
vm_test.go:30: testIntegerObject failed: object has wrong value.\
got=12, want=60
FAIL
FAIL    monkey/vm    0.007s

My point is how minimal the required changes are to make all of them pass. First, we replace the existing case code.OpAdd in our VM with this:

```
// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 

    case code.OpAdd, code.OpSub, code.OpMul, code.OpDiv:
        err := vm.executeBinaryOperation(op)
        if err != nil {
            return err
        }

    }
    // [...] 
}
```

Everything that has to with binary operations is now neatly tucked away behind the executeBinaryOperation method:

```
// vm/vm.go

func (vm *VM) executeBinaryOperation(op code.Opcode) error {
    right := vm.pop()
    left := vm.pop()

    leftType := left.Type()
    rightType := right.Type()

    if leftType == object.INTEGER_OBJ && rightType == object.INTEGER_OBJ {
        return vm.executeBinaryIntegerOperation(op, left, right)
    }

    return fmt.Errorf("unsupported types for binary operation: %s %s",
        leftType, rightType)
}
```