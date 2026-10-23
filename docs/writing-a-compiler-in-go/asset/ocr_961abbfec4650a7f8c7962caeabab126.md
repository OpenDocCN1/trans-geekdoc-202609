```
// compiler/compiler.go

func (c *Compiler) leaveScope() code.Instructions {
    // [...] 

    c.symbolTable = c.symbolTable.Outer

    return instructions
}
```

Again, it’s only one new line, but it’s enough to fix this test:

```
$ go test -run TestCompilerScopes ./compiler
ok      monkey/compiler 0.006s
```

However, the test that’s been haunting us for a while now is still failing:

```
$ go test ./compiler
--- FAIL: TestLetStatementScopes (0.00s)
compiler_test.go:947: testConstants failed:\
constant 1 - testInstructions failed: wrong instructions length.
want="0000 OpConstant 0\n0003 OpSetLocal 0\n0005 OpGetLocal 0\n\
0007 OpReturnValue\n"
got ="0000 OpConstant 0\n0003 OpSetGlobal 0\n0006 OpGetGlobal 0\n\
0009 OpReturnValue\n"
FAIL
FAIL    monkey/compiler 0.009s
```

But we’re finally ready to fix it. We have all the necessary parts in place and now we just need to use them and to finally listen to what our symbol table really has to say.

Up until now, we always emitted OpSetGlobal and OpGetGlobal instructions – no matter what the symbol table might say about the scope of a symbol. Granted, “might” is the important word here. Because even if we would have listened, the symbol table would’ve always replied with GlobalScope. That’s changed and we can now use a Symbol’s scope to emit the correct instructions.

The first place to do that is the case branch for *ast.LetStatements:

```
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 

    case *ast.LetStatement:
        err := c.Compile(node.Value)
        if err != nil {
            return err
```