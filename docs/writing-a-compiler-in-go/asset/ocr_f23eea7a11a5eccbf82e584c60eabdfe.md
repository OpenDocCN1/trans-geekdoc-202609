![](bbox=[0.173, 0.023, 0.826, 0.123])

That means we don’t need to run the program to know what these expressions evaluate to. A compiler can find them in the code and store the value they evaluate to. After that, it can reference the constants in the instructions it generates, instead of embedding the values directly in them. And while “reference” sounds like a special data type, it’s far easier than that. A plain integer does the job just fine and can serve as an index into a data structure that holds all constants, often called a constant pool.

And that’s exactly what our compiler is going to do. When we come across an integer literal (a constant expression) while compiling, we’ll evaluate it and keep track of resulting *object.Integer by storing it in memory and assigning it a number. In the bytecode instructions we’ll refer to the *object.Integer by this number. After we’re done compiling and pass the instructions to the VM for execution, we’ll also hand over all the constants we’ve found by putting them in a data structure – our constant pool – where the number that has been assigned to each constant can be used as an index to retrieve it.

Back to our first opcode. It’s called OpConstant and it has one operand: the number we previously assigned to the constant. When the VM executes OpConstant it retrieves the constant using the operand as an index and pushes it on to the stack. Here’s out first opcode definition:

```
```go
// code/code.go

// [...]

const (
    OpConstant Opcode = iota
)
```
```

While this looks exactly like the meager three lines of code that they are, this addition is the groundwork for all future opcode definitions. Each definition will have an Op prefix and the value it refers to will be determined by iota. We let iota generate increasing byte values for us, because we just don’t care about the actual values our opcodes represent. They only need to be distinct from each