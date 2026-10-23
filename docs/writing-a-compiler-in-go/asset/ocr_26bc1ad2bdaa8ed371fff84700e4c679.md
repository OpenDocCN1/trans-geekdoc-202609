lines to the compilers loadSymbol method to fix this particular test:

```
// compiler/compiler.go

func (c *Compiler) loadSymbol(s Symbol) {
    switch s.Scope {
    case GlobalScope:
        c.emit(code.OpGetGlobal, s.Index)
    case LocalScope:
        c.emit(code.OpGetLocal, s.Index)
    case BuiltinScope:
        c.emit(code.OpGetBuiltin, s.Index)
    case FreeScope:
        c.emit(code.OpGetFree, s.Index)
    }
}
```

That gives us the correct OpGetFree instructions inside a closure. But outside, things still don’t work as expected:

```
$ go test ./compiler
--- FAIL: TestClosures (0.00s)
    compiler_test.go:900: testConstants failed: constant 1 -\
    testInstructions failed: wrong instructions length.
    want="0000 OpGetLocal 0\n0002 OpClosure 0 1\n0006 OpReturnValue\n"
    got ="0000 OpClosure 0 0\n0004 OpReturnValue\n"
FAIL
FAIL    monkey/compiler 0.009s
```

This tells us that we’re not loading the free variables on to the stack after we compiled a function and that the second operand for the OpClosure instruction is still the hardcoded 0.

What we have to do, right after we compiled a function’s body, is iterate through the FreeSymbols of the SymbolTable we just “left” and loadSymbol them. That should result in instructions in the enclosing scope that put the free variables on to the stack.

Here, too, the code explains things much more concisely than I can in prose:

```
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 
    case *ast.FunctionLiteral:
        // [...] 
        if !c.lastInstructionIs(code.OpReturnValue) {
            c.emit(code.OpReturn)
        }
    }
```