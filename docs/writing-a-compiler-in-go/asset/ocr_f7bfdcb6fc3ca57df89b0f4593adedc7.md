```
```go
)

var definitions = map[Opcode]*Definition{
    // [...]

    OpReturn: {"OpReturn", []int{}},
}
```
```

That makes three new opcodes – enough to get started in the compiler.

# Compiling Function Literals

Before we start opening our `compiler/compiler_test.go` file, a little inventory check. We now have in place:

+   - `object.CompiledFunction` to hold the instructions of a compiled function and to pass them from the compiler to the VM as part of the bytecode, as a constant.
+   - `code.OpCall` to tell the VM to start executing the `*object.CompiledFunction` sitting on top of the stack.
+   - `code.OpReturnValue` to tell the VM to return the value on top of the stack to the calling context and to resume execution there.
+   - `code.OpReturn`, which is similar to `code.OpReturnValue`, except that there is no explicit value to return but an implicit `vm.Null`.

That’s enough for us to start compiling. But, again, baby steps. Before we can start compiling a function *call*, we’re going to make sure that we can compile the function being called.

That gives us a clear first task: compile function literals. We’ll take this snippet as our starting point:

```
```go
fn() { return 5 + 10 }
```
```

A function without arguments, an integer arithmetic expression in the body, and an *explicit return statement*. The last point is important. We need to turn the function literal into an `*object.CompiledFunction` with these instructions in its `Instructions` field: