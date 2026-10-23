```
oneArg(24);
`
expectedConstants: []interface{}{
    []code.Instructions{
        code.Make(code.OpGetLocal, 0),
        code.Make(code.OpReturnValue),
    },
    24,
},
expectedInstructions: []code.Instructions{
    code.Make(code.OpConstant, 0),
    code.Make(code.OpSetGlobal, 0),
    code.Make(code.OpGetGlobal, 0),
    code.Make(code.OpConstant, 1),
    code.Make(code.OpCall, 1),
    code.Make(code.OpPop),
},
},
{
    input: `
let manyArg = fn(a, b, c) { a; b; c };
manyArg(24, 25, 26);
`
expectedConstants: []interface{}{
    []code.Instructions{
        code.Make(code.OpGetLocal, 0),
        code.Make(code.OpPop),
        code.Make(code.OpGetLocal, 1),
        code.Make(code.OpPop),
        code.Make(code.OpGetLocal, 2),
        code.Make(code.OpReturnValue),
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

Instead of empty function bodies, we now have references to the parameters of the functions. And the updated expectations tell the compiler that these references should be turned into OpGetLocal instructions that load the arguments on to the stack. The indexes to these OpGetLocal instructions start at 0 for the