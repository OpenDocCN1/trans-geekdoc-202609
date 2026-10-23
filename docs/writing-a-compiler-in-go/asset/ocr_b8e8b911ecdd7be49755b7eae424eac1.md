![](bbox=[0.256, 0.022, 0.702, 0.117])

And in the main program, contained in `Bytecode.Instructions`, we need an `OpConstant` instruction that loads this function on to the stack. Followed by an `OpPop`, of course, since the returned value is unused.

We can do this. Let’s write the test for it.

```
```go
// compiler/compiler_test.go

func TestFunctions(t *testing.T) {
	tests := []compilerTestCase{
		{
			input: `fn() { return 5 + 10 }`,
			expectedConstants: []interface{}{
				5,
				10,
				[]code.Instructions{
					code.Make(code.OpConstant, 0),
					code.Make(code.OpConstant, 1),
					code.Make(code.OpAdd),
					code.Make(code.OpReturnValue),
				},
			},
			expectedInstructions: []code.Instructions{
				code.Make(code.OpConstant, 2),
				code.Make(code.OpPop),
			},
		},
	}

	runCompilerTests(t, tests)
}
```
```

At first glance, it doesn’t look like there’s anything new in this test, but `expectedConstants` now also includes `[]code.Instructions`.

These are the instructions we want to see in the `Instructions` field of the `*object.CompiledFunction`, which is passed around as the constant with the index 2. We could’ve put an `*object.CompiledFunction` directly into `expectedConstants`, but since we’re only interested in the instructions, we might as well skip the outer layer and make the tests more readable.

Nonetheless, we need to update our tooling so it can now make assertions about