Instead of defining an identifier and emitting an `OpSetGlobal` instruction we now have to do the opposite. When we come across an `*ast.Identifier` we need to check with our symbol table whether the identifier was previously used as part of a `let` statement and if so, we need to emit an `OpGetGlobal` instruction with the correct operand. “Correct” here means that the operand holds the same number that was used in the previously emitted `OpSetGlobal` instruction. We can manage that, can’t we?

First we have to tell the compiler about `*ast.Identifiers`. It should try to resolve the identifier at hand with the symbol table:

```
```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...]

    case *ast.Identifier:
        symbol, ok := c.symbolTable.Resolve(node.Value)
        if !ok {
            return fmt.Errorf("undefined variable %s", node.Value)
        }

    // [...]
    }

    // [...]
}
```
```

We take the `Value` of the `*ast.Identifier` and ask the symbol table whether it can `Resolve` it. If not, we return an error. Looks just like any other map access in Go, doesn’t it? But I want you to note that this is a *compile time error*! Previously, in our evaluator, we could only determine whether a variable was defined or not at *run time*, while executing the Monkey program. Now we can throw an error before we pass bytecode to the VM. Pretty cool, isn’t it?

In case the identifier can be resolved we have the symbol at hand and can use it to emit the `OpGetGlobal` instruction:

```
```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...]

    case *ast.Identifier:
        symbol, ok := c.symbolTable.Resolve(node.Value)
        if !ok {
```
```