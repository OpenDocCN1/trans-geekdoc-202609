Let’s talk about the second and much rarer case when returning from a function: a function returning nothing. Neither explicitly nor implicitly. Since nearly everything in Monkey is an expression that produces a value, it’s an achievement to even come up with such a function, but they do exist. Here’s one:

```
fn() { }
```

That’s a function with an empty body. Compiling it would produce a valid *object.CompiledFunction that can be called, but doesn’t have any instructions. Another example, which we’ll meet later on again, when we talk about local bindings, is this one:

```
fn() { let a = 1; }
```

Granted, a function that returns nothing is an edge case. We didn’t even handle it in the first book. But now it sits in front of us, next to an unanswered question: what should these functions produce? Since a function call is an expression and expressions produce values, to be consistent, these functions, too, should produce a value.

We could ignore the whole issue by putting it in a file called undefined_behaviour.txt and calling it a day. We could. Or we could make these functions return *object.Null. Since in Monkey an *object.Null signifies the absence of a value, it does make sense for a function that didn’t produce a value to return it.

Decision made, which means we need to tell our VM to return vm.Null from a function in case it has no OpReturnValue instruction at its end. We’ll do that by introducing another opcode.

The previously-defined OpReturnValue tells the VM to return the value sitting on top of the stack. The new opcode, which we’ll call OpReturn, will also tell the VM to return from the current function, except this time, there’s nothing on the stack, no return value, nothing. Just go back to what you were doing before calling this function.

Here is its definition:

```
// code/code.go
const (
  // [...]
```