```
Make(OpAdd),
Make(OpGetLocal, 1),
Make(OpConstant, 2),
Make(OpConstant, 65535),
Make(OpClosure, 65535, 255),
}

expected := `0000 OpAdd
0001 OpGetLocal 1
0003 OpConstant 2
0006 OpConstant 65535
0009 OpClosure 65535 255
`

// [...] 
}
```

```
func TestReadOperands(t *testing.T) {
    tests := []struct {
        op Opcode
        operands []int
        bytesRead int
    }{
        // [...] 
        {OpClosure, []int{65535, 255}, 3},
    }

    // [...] 
}
```

When we now run the tests of the code package, we see this:

```
$ go test ./code
--- FAIL: TestInstructionsString (0.00s)
code_test.go:56: instructions wrongly formatted.
    want="0000 OpAdd\n0001 OpGetLocal 1\n0003 OpConstant 2\n\
0006 OpConstant 65535\n0009 OpClosure 65535 255\n"
    got="0000 OpAdd\n0001 OpGetLocal 1\n0003 OpConstant 2\n\
0006 OpConstant 65535\n\
0009 ERROR: unhandled operandCount for OpClosure\n\n"
FAIL
FAIL    monkey/code 0.007s
```

Looks like we only need to fix the fmtInstruction method on Instructions:

```
// code/code.go

func (ins Instructions) fmtInstruction(def *Definition, operands []int) string {
    // [...] 

    switch operandCount {
    case 0:
        return def.Name
    case 1:
        return fmt.Sprintf("%s %d", def.Name, operands[0])
    case 2:
```