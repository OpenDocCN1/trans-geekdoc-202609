alternative of a conditional to leave a value on the stack. Otherwise, we couldn’t do this:

```
let result = if (5 > 3) { 5 } else { 3 };
```

That’s valid Monkey code and it won’t work if we emit an OpPop after the last expression statement in the node.Consequence. The value produced by the consequence would be popped off the stack, the expression wouldn’t evaluate to anything, and the let statement would end up without a value on the right side of its =.

What makes fixing this tricky is that we only want to get rid of the last OpPop instruction in the node.Consequence. Say we had Monkey code like this:

```
if (true) {
  3;
  2;
  1;
}
```

What we want here is the 3 and the 2 to be popped off the stack, but the 1 should be kept around so the whole conditional evaluates to 1. So before we tackle our main challenge of giving the OpJumpNotTruthy a real offset, here’s the plan for getting rid of the additional OpPop instruction.

We first change the compiler to keep track of the last two instructions we emitted, including their opcode and the position they were emitted to. For that, we need a new type and two more fields on the compiler:

```
// compiler/compiler.go

type EmittedInstruction struct {
    Opcode  code.Opcode
    Position int
}

type Compiler struct {
    // [...] 
    lastInstruction       EmittedInstruction
    previousInstruction   EmittedInstruction
}

func New() *Compiler {
    return &Compiler{
        // [...] 
        lastInstruction:      EmittedInstruction{},
        previousInstruction:  EmittedInstruction{},
```