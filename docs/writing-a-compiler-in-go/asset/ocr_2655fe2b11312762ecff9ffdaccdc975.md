```
{
    input: `
    let manyArg = fn(a, b, c) { };
    manyArg(24, 25, 26);
    `,
    expectedConstants: []interface{}{
        []code.Instructions{
            code.Make(code.OpReturn),
        },
        24,
        25,
        26,
    },
    expectedInstructions: []code.Instructions{
        code.Make(code.OpConstant, 0),
        code.Make(code.OpSetGlobal, 0),
        code.Make(code.OpGetGlobal, 0),
        code.Make(code.OpConstant, 1),
        code.Make(code.OpConstant, 2),
        code.Make(code.OpConstant, 3),
        code.Make(code.OpCall, 3),
        code.Make(code.OpPop),
    },
    },
}
    runCompilerTests(t, tests)
}
```

It’s worth noting that the functions used in these new test cases have an empty body and don’t make use of their parameters. That’s by design. We first want to make sure that we can compile function calls and once we have that in place, we’ll reference the parameters in the same tests and update our expectations.

As you can see in the expectedInstructions of these test cases, the first argument to the function call should end up lowest on the stack. From our current point of view, it doesn’t really matter, but soon we’ll see how much nicer that makes things in the VM once we start to reference parameters.

The output of these new tests is quite instructive:

```
$ go test ./compiler
--- FAIL: TestFunctionCalls (0.00s)
    compiler_test.go:889: testInstructions failed: wrong instructions length.
    want="0000 OpConstant 0\n0003 OpSetGlobal 0\n0006 OpGetGlobal 0\n\
    0009 OpConstant 1\n0012 OpCall 1\n0014 OpPop\n"
    got ="0000 OpConstant 0\n0003 OpSetGlobal 0\n0006 OpGetGlobal 0\n\
    0009 OpCall 0\n0011 OpPop\n"
FAIL
FAIL    monkey/compiler 0.008s
```

The missing OpConstant instructions tell us that we need to compile the