```
// [...] 
} 

// [...] 
}
```

node.Name is the *ast.Identifier on the left side of the let statement’s equal sign. And node.Name.Value holds the string representation of that identifier. We pass it to the symbol table’s Define method and thus define it in the GlobalScope. The returned symbol now has a Name, a Scope and, most importantly, an Index.

We can now use that Index as operand of a OpSetGlobal instruction and emit that:

```
// compiler/compiler.go
```

```
func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 

    case *ast.LetStatement:
        err := c.Compile(node.Value)
        if err != nil {
            return err
        }
        symbol := c.symbolTable.Define(node.Name.Value)
        c.emit(code.OpSetGlobal, symbol.Index)

    // [...] 
    }

    // [...] 
}
```

With that we just took a huge step towards our goal:

```
$ go test ./compiler
--- FAIL: TestGlobalLetStatements (0.00s)
    compiler_test.go:361: testInstructions failed: wrong instructions length.
        want="0000 OpConstant 0\n0003 OpSetGlobal 0\n0006 OpGetGlobal 0\n\
        0009 OpPop\n"
        got ="0000 OpConstant 0\n0003 OpSetGlobal 0\n0006 OpPop\n"
FAIL
FAIL    monkey/compiler 0.011s
```

Now we’re talki– wait a second! The test is still failing? No, this is the second test case. The first one is passing! What’s failing now is the test case that makes sure resolving a global binding works.