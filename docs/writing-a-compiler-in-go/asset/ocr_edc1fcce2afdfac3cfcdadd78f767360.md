![](bbox=[0.35, 0.02, 0.65, 0.28])

As things stand, though, that solution poses a slight problem to our VM, because it wouldn’t know how many arguments are on top of the stack.

Think of our implementation of OpCall in the VM. Before we push a new frame, we take the function to be called right off the top of the stack. With this new calling convention, there could be zero or multiple arguments on the stack – on top of the function. How do we reach the function on the stack so we can execute it?

Since functions are ordinary Monkey object.Objects we can’t even choose the hacky way and traverse the stack to find the first object.CompiledFunction; that might just be an argument to the function call.

Thankfully, we don’t have to resort to hacky and ugh-this-feels-dirty fixes. There’s a simple and beautiful solution available: we give the OpCall opcode an operand that holds the number of arguments of the call. One byte is enough for that (or do you want to call functions with more than 256 arguments?) and allows us, by doing a little calculation, to find the function below the arguments.

So, let’s add an operand to OpCall:

```
// code/code.go

var definitions = map[Opcode]*Definition{
    // [...] 

    OpCall:    {"OpCall", []int{1}},

    // [...] 
}
```

With this change some tests are breaking due to panics and index errors, because we defined something neither the compiler nor the VM know about.