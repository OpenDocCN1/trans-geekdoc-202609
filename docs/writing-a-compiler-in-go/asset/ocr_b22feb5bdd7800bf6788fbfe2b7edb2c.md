# String

Since the value of string literals doesn’t change between compile and run time, we can treat them as constant expressions. Similar to our implementation of integer literals, we can turn them into *object.String at compile time and add them to the constant pool in compiler.Bytecode.

From integer literals we also know that this doesn’t take more than a handful of lines of code in the compiler. So why not keep things challenging? Instead of only implementing string literals, we’ll also make it a goal for this section to implement string concatenation, which allows us to concatenate two strings with the + operator.

Our first compiler test in this chapter expects both to work:

```
// compiler/compiler_test.go

func TestStringExpressions(t *testing.T) {
    tests := []compilerTestCase{
        {
            input: `"monkey"`,
            expectedConstants: []interface{}"monkey"},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpPop),
            },
        },
        {
            input: `"mon" + "key"`,
            expectedConstants: []interface{}"mon", "key"},
            expectedInstructions: []code.Instructions{
                code.Make(code.OpConstant, 0),
                code.Make(code.OpConstant, 1),
                code.Make(code.OpAdd),
                code.Make(code.OpPop),
            },
        },
    }

    runCompilerTests(t, tests)
}
```

The first of these two test cases makes sure that the compiler knows how to treat string literals as constants; the second test asserts that it’s possible to concatenate them with the + infix operator.

Of note is that we do not expect any new opcodes. We already have those we