Which offset do we use when we don’t even know how far we have to jump yet? The answer is a rather pragmatic “let’s just put garbage in there and fix it later”. You chuckle, but I’m serious. Let’s use a bogus offset and worry about fixing it later:

```
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...] 
    
    case *ast.IfExpression:
        err := c.Compile(node.Condition)
        if err != nil {
            return err
        }
        
        // Emit an `OpJumpNotTruthy` with a bogus value
        c.emit(code.OpJumpNotTruthy, 9999)
        
        err = c.Compile(node.Consequence)
        if err != nil {
            return err
        }
        
        // [...] 
    }
    
    // [...] 
}
```

Even though most programmers already squint their eyes and instinctively know that something fishy is going on when they see a 9999 in code, an inline code comment here helps making the intention clear. Because here we really do want to emit an OpJumpNotTruthy instruction with a garbage offset and then compile the node.Consequence. Again, the 9999 is not what will end up in the VM and we’ll later take care of it. But for now, it should get us a lot more correct instructions in our test.

But, no, we only get one more right and that’s the OpJumpNotTruthy instruction itself:

```
$ go test ./compiler
--- FAIL: TestConditionals (0.00s)
compiler_test.go:195: testInstructions failed: wrong instructions length.
want="0000 OpTrue\n0001 OpJumpNotTruthy 7\n0004 OpConstant 0\n0007 OpPop\n\
0008 OpConstant 1\n0011 OpPop\n"
got ="0000 OpTrue\n0001 OpJumpNotTruthy 9999\n0004 OpPop\n\
0005 OpConstant 0\n0008 OpPop\n"
FAIL
```