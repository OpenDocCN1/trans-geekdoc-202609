That’s not a problem per se, but the definition of the new operand causes our code.Make function to create an empty byte in its place – even if we don’t pass in an operand. We end up in this sort of limbo, where different parts in our system act on different assumptions and nobody knows what’s really happened. We need to restore order again.

We’ll start by updating our existing compiler tests and making sure that we do pass in an operand when creating opCall instructions:

```
// compiler/compiler_test.go

func TestFunctionCalls(t *testing.T) {
    tests := []compilerTestCase{
        {
            // [...] 
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 1), // The compiled function
                code.Make(code.OpCall, 0),
                code.Make(code.OpPop),
            },
        },
        {
            // [...] 
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 1), // The compiled function
                code.Make(code.OpSetGlobal, 0),
                code.Make(code.OpGetGlobal, 0),
                code.Make(code.OpCall, 0),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

That makes the compiler tests correct and the compiler itself is fine for now, because it also uses code.Make to emit instructions, which, again, adds an empty byte for the new operand, even if none was passed in as argument.

The VM, though, stumbles and trips over the new operand, empty or not. The solution for now, at least until we’ve written the tests to tell us what we actually want, is to simply skip it:

```
// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...]
```