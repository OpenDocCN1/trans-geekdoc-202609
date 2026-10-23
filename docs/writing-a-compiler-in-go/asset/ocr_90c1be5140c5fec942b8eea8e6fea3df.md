```
}
}
```

lastInstruction is the very last instruction we emitted and previousInstruction is the one before that. We’ll see why we need to keep track of both in a moment. For now, we change the compiler’s emit method to populate both fields:

```
// compiler/compiler.go

func (c *Compiler) emit(op code.Opcode, operands ...int) int {
    ins := code.Make(op, operands...)
    pos := c.addInstruction(ins)

    c.setLastInstruction(op, pos)

    return pos
}

func (c *Compiler) setLastInstruction(op code.Opcode, pos int) {
    previous := c.lastInstruction
    last := EmittedInstruction{Opcode: op, Position: pos}

    c.previousInstruction = previous
    c.lastInstruction = last
}
```

With this in place, we can check opcode of the last emitted instruction in a type-safe way, without having to cast from and to bytes. And that’s exactly what we’re going to do. After compiling the node.Consequence of the *ast.IfExpression we check whether the last instruction we emitted was an OpPop instruction and if so, we remove it:

```
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 

    case *ast.IfExpression:
        // [...] 
        c.emit(code.OpJumpNotTruthy, 9999)

        err = c.Compile(node.Consequence)
        if err != nil {
            return err
        }

        if c.lastInstructionIsPop() {
            c.removeLastPop()
        }
    }
```