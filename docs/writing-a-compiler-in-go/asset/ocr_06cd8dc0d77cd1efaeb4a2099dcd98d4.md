Here’s how it will be used. First, we get the function we want to call on to the stack. For example, with an OpConstant instruction. Then, we issue an OpCall instruction. That tells the VM to execute the function on top of the stack and off we go.

This little instruction manual for OpCall is what’s called a calling convention. Once we add support for function call arguments it will have to change, but for now, it’s just two steps: put the function you want to call on to the stack, issue an OpCall instruction.

With OpCall defined, we are now – in theory – able to get a function on to the stack of our VM and call it. What we still need is a way to tell the VM to return from a called function.

More specifically, we need to differentiate between two cases where the VM has to return from a function. The first case is a function actually returning something, implicitly or explicitly. The second one is when the execution of a function ends without anything being returned, e.g. the function has an empty function body.

Let’s talk about the former case first, the explicit and implicit returning of values. Monkey supports both:

```
let explicitReturn = fn() { return 5 + 10; };
let implicitReturn = fn() { 5 + 10; };
```

An explicit return statement stops the execution of the rest of the function and returns the value produced by the expression following the return keyword. In the case above, that’s the infix expression 5 + 10.

Without a return statement, a function call evaluates to the last value produced inside the function. That’s what’s called implicit return.

In the evaluator we built in Writing An Interpreter In Go the implicit returning of values was the default case. Explicit return statements were an additional feature we had to build.

This time, though, the implicit return will be a slight variation of the explicit return. Or, in other words, these two will compile to the same bytecode: