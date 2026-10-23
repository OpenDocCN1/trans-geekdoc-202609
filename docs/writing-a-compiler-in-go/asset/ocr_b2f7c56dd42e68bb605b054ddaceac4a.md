When we take a closer look at the compiler, however, the cause is easy to spot: in the Compile method we don’t handle *ast.PrefixExpression nodes yet, we skip over them and that means we never compile the integer and boolean literals. Here’s what we need to change:

```
```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 

    case *ast.PrefixExpression:
        err := c.Compile(node.Right)
        if err != nil {
            return err
        }

        switch node.Operator {
        case "!":
            c.emit(code.OpBang)
        case "-":
            c.emit(code.OpMinus)
        default:
            return fmt.Errorf("unknown operator %s", node.Operator)
        }

    // [...] 
    }

    // [...] 
}
```
```

With that we walk the AST down one level further and first compile the node.Right branch of the *ast.PrefixExpression node. That results in the operand of the expression being compiled to either an OpTrue or an OpConstant instruction. That’s the first of the two missing instructions.

And we also need to emit the opcode for the operator itself. For that we make use of our trusted friend the switch statement and either generate a OpBang or a OpMinus instruction, depending on the node.Operator at hand.

And now we have passing tests:

```
```bash
$ go test ./compiler
ok      monkey/compiler 0.008s
```
```

Another milestone reached! By now you know where we’re headed next: the tests of our VM. Here, just like in our compiler tests, we add test cases to the existing TestIntegerArithmetic and TestBooleanExpressions functions: