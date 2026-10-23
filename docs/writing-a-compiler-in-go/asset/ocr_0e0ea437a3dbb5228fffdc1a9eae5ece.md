The input in this test is pretty close to our compiler test, isn’t it? That means we’re on the right track, but we still have something to do. We have to make sure that the symbol table doesn’t automatically mark every symbol as a free variable if it can’t resolve it:

```
// compiler/symbol_table_test.go

func TestResolveUnresolvableFree(t *testing.T) {
    global := NewSymbolTable()
    global.Define("a")

    firstLocal := NewEnclosedSymbolTable(global)
    firstLocal.Define("c")

    secondLocal := NewEnclosedSymbolTable(firstLocal)
    secondLocal.Define("e")
    secondLocal.Define("f")

    expected := []Symbol{
        Symbol{Name: "a", Scope: GlobalScope, Index: 0},
        Symbol{Name: "c", Scope: FreeScope, Index: 0},
        Symbol{Name: "e", Scope: LocalScope, Index: 0},
        Symbol{Name: "f", Scope: LocalScope, Index: 1},
    }

    for _, sym := range expected {
        result, ok := secondLocal.Resolve(sym.Name)
        if !ok {
            t.Errorf("name %s not resolvable", sym.Name)
            continue
        }
        if result != sym {
            t.Errorf("expected %s to resolve to %v, got=%v",
                sym.Name, sym, result)
        }
    }

    expectedUnresolvable := []string{
        "b",
        "d",
    }

    for _, name := range expectedUnresolvable {
        _, ok := secondLocal.Resolve(name)
        if ok {
            t.Errorf("name %s resolved, but was expected not to", name)
        }
    }
}
```

Before we can get feedback from the tests, we need to define the FreeSymbols field on the SymbolTable. Otherwise they won’t compile:

```
// compiler/symbol_table.go
```