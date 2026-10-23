```
```text
testing.tRunner(0xc4200a82d0, 0x1149f40)
/usr/local/go/src/testing/testing.go:777 +0xd0
created by testing.(*T).Run
/usr/local/go/src/testing/testing.go:824 +0x2e0
FAIL    monkey/vm    0.012s
```
```

The cause for this panic are the OpPop instructions we emit after the conditionals. Since they produced no value, the VM crashes trying to pop something off the stack. Time to change that, time to put vm.Null on to the stack.

We’re going to do two things to pull that off. First, we’re going to define an opcode that tells the VM to put vm.Null on the stack. Then we’re going to modify the compiler to insert an alternative when a conditional doesn’t have one. And the only thing this alternative branch will contain is the new opcode that pushes vm.Null on to the stack.

We define the opcode first so we can use it in our updated compiler tests:

```
```go
// code/code.go

const (
    // [...]

    OpNull
)

var definitions = map[Opcode]*Definition{
    // [...]

    OpNull: {"OpNull", []int{}},
}
```
```

That’s also similar to the boolean counterparts, OpTrue and OpFalse. OpNull doesn’t have any operands and only instructs the VM to push one value on to the stack.

Instead of now writing a new compiler test, we’re going to update an existing test case in TestConditionals and expect to find OpNull in the generated instructions. Please note that we need to change the first test case, the one in which the conditional doesn’t have an alternative; the other test case stays as it is:

```
```go
// compiler/compiler_test.go

func TestConditionals(t *testing.T) {
    tests := []compilerTestCase{
        {
```
```