+   - Push 1 on to the stack
+   - Push 2 on to the stack
+   - Add the two topmost elements together

We need to create three instructions. As programmers, though, we know that we only need to define two separate instruction types, since pushing 2 on to the stack should be the same as pushing 1, except that the “argument” is different. So, two instruction types in total: one for pushing something on to the stack and one for adding things that are already on the stack.

We’ll implement both in the same way. First we define their opcodes and how they are encoded in bytecode. Then we extend the compiler so it can produce these instructions. As soon as the compiler knows how to do that, we can create the VM that decodes and executes them. And we start with the instructions that tell the VM to push something on to the stack.

# Starting With Bytes

Here we are. We need to define our first bytecode instruction. How do we do that? Well, since creating definitions while programming is not much more than telling the computer what we know, let’s ask ourselves: what do we know about bytecode?

We know that it’s made up of instructions. And we also know, that the instructions themselves are a series of bytes and a single instruction consists of an opcode and an optional number of operands. An opcode is exactly one byte wide, has an arbitrary but unique value and is the first byte in the instruction. Looks like we know quite a lot and the best thing is, that this is precise enough to be turned into code – literally.

As our first official practical act of coding in this book, we create a new package, called code, where we start to define our Monkey bytecode format:

```
```go
// code/code.go

package code

type Instructions []byte

type Opcode byte
```
```