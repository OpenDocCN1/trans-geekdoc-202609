The curious thing about function literals is that the value they produce doesn’t change. Ever. It’s constant. And that’s the last hint we need.

We’ll treat function literals like the other literals that produce constant values and pass them to the VM as – here it comes – constants. We’ll compile them into sequences of instructions and add those to the compiler’s pool of constants. An `OpConstant` instruction then takes care of putting the compiled function on to the stack – just like any other value.

Now, the remaining question is how to exactly represent these sequences of instructions, so they can be added to the constant pool and loaded on to the stack.

In *Writing An Interpreter In Go* we defined `object.Function`, a Monkey object that represents evaluated function literals which itself can be evaluated. Now we need an updated version of that: a function object that holds bytecode instead of AST nodes.

For that, we open up our object package and introduce the new `object.CompiledFunction`:

```
```go
// object/object.go

import (
    // [...]
    "monkey/code"
    // [...]
)

const (
    // [...]

    COMPILED_FUNCTION_OBJ = "COMPILED_FUNCTION_OBJ"
)

type CompiledFunction struct {
    Instructions code.Instructions
}

func (cf *CompiledFunction) Type() ObjectType { return COMPILED_FUNCTION_OBJ }
func (cf *CompiledFunction) Inspect() string {
    return fmt.Sprintf("CompiledFunction[%p]", cf)
}
```
```

`object.CompiledFunction` is everything we need: it can hold the `code.Instructions` we get from the compilation of a function literal and it’s an