
Of course, things get more complicated once we introduce functions and local variables, but that’s a bridge we’ll cross once we get there. For now, let’s head on over to our compiler.

```go
code.Make(code.OpGetGlobal, 0),
code.Make(code.OpPop),
},
},
{
    input: `
let one = 1;
let two = one;
two;
`,
expectedConstants: []interface{}{1},
expectedInstructions: []code.Instructions{
    code.Make(code.OpConstant, 0),
    code.Make(code.OpSetGlobal, 0),
    code.Make(code.OpSetGlobal, 0),
    code.Make(code.OpSetGlobal, 1),
    code.Make(code.OpGetGlobal, 1),
    code.Make(code.OpPop),
},
},
}

runCompilerTests(t, tests)
}
```

Same test setup as before, so let’s talk about *what* we test in these three test cases. The first one makes sure that a let statement leads to the correct `OpSetGlobal` instruction being emitted. The second one expects that an identifier resolves to a previous binding by testing for the `OpGetGlobal` instruction. Note here that the operands of the `OpSetGlobal` and `OpGetGlobal` instructions have to match. The third test case asserts that combining the setting and getting of global bindings works, too. Here, too, it’s important that the operands of the instructions match.

We’re going to fix these test cases one after the other, starting with the first one, which isn’t doing so well:

```text
$ go test ./compiler
--- FAIL: TestGlobalLetStatements (0.00s)
compiler_test.go:361: testInstructions failed: wrong instructions length.
want="0000 OpConstant 0\n0003 OpSetGlobal 0\n0006 OpConstant 1\n0009 OpSetGlobal 1\n"
got=""
FAIL
FAIL    monkey/compiler 0.009s
```

Looks like we’re not even close. But the reason for the empty result is that Monkey code consists solely of let statements and our compiler currently skips them. We can get better feedback from the test by adding a new case branch to the compiler’s `Compile` method:

```go
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
    // [...]

    case *ast.LetStatement:
        err := c.Compile(node.Value)
        if err != nil {
            return err
        }

    // [...]
    }

    // [...]
}
```

The first thing we do when we come across a let statement is to compile the expression on the right side of the equal sign. That’s the Value that will be bound to a name and compiling this expression means instructing the VM to put the value on to the stack:

```text
$ go test ./compiler
--- FAIL: TestGlobalLetStatements (0.00s)
compiler_test.go:361: testInstructions failed: wrong instructions length.
want="0000 OpConstant 0\n0003 OpSetGlobal 0\n0006 OpConstant 1\n\
    0009 OpSetGlobal 1\n"
got ="0000 OpConstant 0\n0003 OpConstant 1\n"
FAIL
FAIL    monkey/compiler  0.009s
```

Now we can bind it to a name. That means we need to follow up with an OpSetGlobal instruction that tells the VM to create the binding. But which number do we choose for our identifier? The answer comes from a new component we’re going to add to our compiler, a symbol table.

## Introducing: the Symbol Table

A [symbol table] is a data structure used in interpreters and compilers to associate identifiers with information. It can be used in every phase, from lexing to code generation, to store and retrieve information about a given identifier (which can be called a symbol). Information such as its location, its scope, whether it was previously declared or not, of which type the associated value is, and anything else that seems useful while interpreting or compiling.

We’re going to use a symbol table to associate identifiers with a scope and a unique number. For now, it should do two things:

1. Associate identifiers in the global scope with a unique number
2. Get the previously associated number for a given identifier

The common names for these two methods on a symbol table are “define” and “resolve”. You “define” an identifier in a given scope to associate some information with it. Later you “resolve” the identifier to this information. The information itself we’ll call the “symbol” – an identifier is associated with a symbol and the symbol itself is what contains information.

Working code helps to explain this. Here are the type definitions that make up our symbol table:

```go
// compiler/symbol_table.go

package compiler

type SymbolScope string

const (
    GlobalScope SymbolScope = "GLOBAL"
)

type Symbol struct {
    Name  string
    Scope SymbolScope
    Index int
}

type SymbolTable struct {
    store          map[string]Symbol
    numDefinitions int
}

func NewSymbolTable() *SymbolTable {
    s := make(map[string]Symbol)
    return &SymbolTable{store: s}
}
```

The first definition here is that of SymbolScope, a type alias for string. The value of a SymbolScope itself is not important. What’s important is that it’s unique, because we need to differentiate between different scopes. We use strings as the aliased type (as opposed to an integer, for example) for a better debugging experience.

more.

The next definition is that of Symbol. A Symbol is a struct that holds all the necessary information about a symbol we encounter in Monkey code: the Name, the Scope and the Index. Not much more to explain here.

The SymbolTable itself then associates strings with Symbols in its store and keeps track of the numDefinitions it has. The strings are the identifiers we come across in the Monkey code.

The names of the types and fields can feel unfamiliar, if you haven’t used a symbol table before, but worry not: we’re building a map that associates strings with information about them. There is no hidden wisdom or trick you need to wrap your head around. Tests make this much clearer by demonstrating what we expect from the missing Define and Resolve methods of the SymbolTable:

```go
// compiler/symbol_table_test.go

package compiler

import "testing"

func TestDefine(t *testing.T) {
    expected := map[string]Symbol{
        "a": Symbol{Name: "a", Scope: GlobalScope, Index: 0},
        "b": Symbol{Name: "b", Scope: GlobalScope, Index: 1},
    }

    global := NewSymbolTable()

    a := global.Define("a")
    if a != expected["a"] {
        t.Errorf("expected a=%v, got=%v", expected["a"], a)
    }

    b := global.Define("b")
    if b != expected["b"] {
        t.Errorf("expected b=%v, got=%v", expected["b"], b)
    }
}

func TestResolveGlobal(t *testing.T) {
    global := NewSymbolTable()
    global.Define("a")
    global.Define("b")

    expected := []Symbol{
        Symbol{Name: "a", Scope: GlobalScope, Index: 0},
        Symbol{Name: "b", Scope: GlobalScope, Index: 1},
    }

    for _, sym := range expected {
        result, ok := global.Resolve(sym.Name)
        if !ok {
            t.Errorf("name %s not resolvable", sym.Name)
            continue
        }
        if result != sym {
            t.Errorf("expected %s to resolve to %v, got=%v",
                sym.Name, sym, result)
        }
    }
}
```

In TestDefine we make assertions about the Define method. It should take an identifier as argument, create a definition and return the Symbol. Note that we don’t have to say in which scope we want to create the definition. It’s the job of the symbol table to keep track of that for us. We only call Define("a") and the symbol table associates the identifier "a" with a new Symbol, that contains the Name, the Scope and the Index. The Index is the unique number we’re after.

In TestResolveGlobal we do the reverse: we hand the symbol table an identifier that was previously defined and expect it to return the associated Symbol. Again, the only argument is the identifier: Resolve("a"). If the identifier is undefined, the second return value of Resolve has to be false.

The tests don’t compile, because both methods are missing and I’m going to spare you from reading through the results of running the tests repeatedly while adding the method definition step by step. Instead, let me give you the full version of Define:

```go
// compiler/symbol_table.go

func (s *SymbolTable) Define(name string) Symbol {
    symbol := Symbol{Name: name, Index: s.numDefinitions, Scope: GlobalScope}
    s.store[name] = symbol
    s.numDefinitions++
    return symbol
}
```

I told you, there’s nothing to worry about; we’re building a map with some additional features. Here’s the evidence. We create a new Symbol, associate it with the name in our store, increase the numDefinitions counter and return the new Symbol. Defined. Done.

The Resolve method is even simpler:
