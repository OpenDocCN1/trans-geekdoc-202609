It’s my unwavering opinion that the `Instructions.String` method is worth its bytes in gold.

This failing test now tells us – nicely formatted and readable! – that we need to emit an `OpAdd` instruction. And since we already came across an `*ast.InfixExpression` in the compiler’s `Compile` method, we know where to do that:

```
```go
// compiler/compiler.go

import (
    "fmt"
    // [...]
)

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...]

    case *ast.InfixExpression:
        err := c.Compile(node.Left)
        if err != nil {
            return err
        }

        err = c.Compile(node.Right)
        if err != nil {
            return err
        }

        switch node.Operator {
        case "+":
            c.emit(code.OpAdd)
        default:
            return fmt.Errorf("unknown operator %s", node.Operator)
        }

    // [...]
    }

    // [...]
}
```
```

In the new `switch` statement we check the `Operator` field of the `*ast.InfixExpression` node. In case we have a + at hand (which we do in our test) we `c.emit` an `OpAdd` instruction. Then, to be safe, we add a default branch that returns an error in case we don’t know how to compile a specific infix operator. And yes, you guessed it, we’re going to add more case branches later on.