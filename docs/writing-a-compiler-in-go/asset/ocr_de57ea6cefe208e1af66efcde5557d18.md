```
```go
secondLocal := NewEnclosedSymbolTable(firstLocal)

expected := []Symbol{
    Symbol{Name: "a", Scope: BuiltinScope, Index: 0},
    Symbol{Name: "c", Scope: BuiltinScope, Index: 1},
    Symbol{Name: "e", Scope: BuiltinScope, Index: 2},
    Symbol{Name: "f", Scope: BuiltinScope, Index: 3},
}

for i, v := range expected {
    global.DefineBuiltin(i, v.Name)
}

for _, table := range []*SymbolTable{global, firstLocal, secondLocal} {
    for _, sym := range expected {
        result, ok := table.Resolve(sym.Name)
        if !ok {
            t.Errorf("name %s not resolvable", sym.Name)
            continue
        }
        if result != sym {
            t.Errorf("expected %s to resolve to %+v, got=%+v", sym.Name, sym, result)
        }
    }
}
```
```

In this test we define three scopes, nested within each other, and expect every symbol that’s been defined in the global scope with DefineBuiltin to resolve to the new BuiltinScope.

Since DefineBuiltin and BuiltinScope do not exist yet, there’s no need to run the tests yet, but it also doesn’t hurt to make sure that they blow up as expected:

```
```bash
$ go test -run TestDefineResolveBuiltins ./compiler
# monkey/compiler
compiler/symbol_table_test.go:162:28: undefined: BuiltinScope
compiler/symbol_table_test.go:163:28: undefined: BuiltinScope
compiler/symbol_table_test.go:164:28: undefined: BuiltinScope
compiler/symbol_table_test.go:165:28: undefined: BuiltinScope
compiler/symbol_table_test.go:169:9: global.DefineBuiltin undefined\
(type *SymbolTable has no field or method DefineBuiltin)
FAIL    monkey/compiler [build failed]
```
```

As expected. Defining BuiltinScope is the easier of the two necessary steps, so we do that first:

```
```go
// compiler/symbol_table.go

const (
    // [...]
    BuiltinScope SymbolScope = "BUILTIN"
```
```