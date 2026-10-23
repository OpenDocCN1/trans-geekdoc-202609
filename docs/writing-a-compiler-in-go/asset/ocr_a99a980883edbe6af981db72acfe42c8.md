```
    code.Make(code.OpPop),
},
{
    input: `fn() { 1; 2 }`,
    expectedConstants: []interface{}{
        // [...] 
    },
    expectedInstructions: []code.Instructions{
        code.Make(code.OpClosure, 2, 0),
        code.Make(code.OpPop),
    },
},
}

runCompilerTests(t, tests)
}
```

This looks like more than it is, but that’s only because I want to give you some context to these changes. In the expectedInstructions of each test case we change the previous OpConstant to OpClosure and add the second operand, 0. That’s it. Now we need to do the same in the other tests where we load functions:

```
// compiler/compiler_test.go

func TestFunctionsWithoutReturnValue(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `fn() { }`,
            expectedConstants: []interface{}{
                // [...] 
            },
            expectedInstructions: []code.Instructions{
                code.Make(code.OpClosure, 0, 0),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

```
func TestFunctionCalls(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `fn() { 24 }();`,
            expectedConstants: []interface{}{
                // [...] 
            },
            expectedInstructions: []code.Instructions{
                code.Make(code.OpClosure, 1, 0),
                code.Make(code.OpCall, 0),
                code.Make(code.OpPop),
            },
        },
```