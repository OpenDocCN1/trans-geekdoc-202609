The new case string branch in testConstants is accompanied by the new testStringObject function, which mirrors the existing testIntegerObject and makes sure that the constants are the strings we expect them to be.

When we now run the tests, we can see that the expected constants are not the issue (yet), but the instructions are:

```
$ go test ./compiler
--- FAIL: TestStringExpressions (0.00s)
    compiler_test.go:410: testInstructions failed: wrong instructions length.
    want="0000 OpConstant 0\n0003 OpPop\n"
    got ="0000 OpPop\n"
FAIL
FAIL    monkey/compiler 0.009s
```

It’s not like we didn’t expect that. We need to emit OpConstant instructions when compiling string literals. To do that, we have to change the Compile method of the compiler to handle *ast.StringLiterals and create *object.String out of them:

```
// compiler/compiler.go
```

```
func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 
    case *ast.StringLiteral:
        str := &object.String{Value: node.Value}
        c.emit(code.OpConstant, c.addConstant(str))
    // [...] 
    }
    // [...] 
}
```

Except for one variable name and one identifier, this is a copy of the case branch for *ast.IntegerLiterals. We take the value out of the AST node, we create an object, and we add it to the constant pool.

# A step into the right direction:

```
$ go test ./compiler
ok      monkey/compiler 0.009s
```

Sweet, both tests pass. And notice that we didn’t have to do anything special to emit the OpAdd instruction for the concatenation to work. The compiler already takes care of *ast.InfixExpressions by compiling their Left and Right nodes.