defined symbol has and in which scope it was defined.

It doesn’t take a lot of code to implement that – once me make our SymbolTable recursive. But before we do that, here’s the list of requirements, translated into a test:

```
// compiler/symbol_table_test.go

func TestResolveLocal(t *testing.T) {
    global := NewSymbolTable()
    global.Define("a")
    global.Define("b")

    local := NewEnclosedSymbolTable(global)
    local.Define("c")
    local.Define("d")

    expected := []Symbol{
        Symbol{Name: "a", Scope: GlobalScope, Index: 0},
        Symbol{Name: "b", Scope: GlobalScope, Index: 1},
        Symbol{Name: "c", Scope: LocalScope, Index: 0},
        Symbol{Name: "d", Scope: LocalScope, Index: 1},
    }

    for _, sym := range expected {
        result, ok := local.Resolve(sym.Name)
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

In the first line of TestResolveLocal we create a new symbol table, global, just like we previously did by calling NewSymbolTable. Then we define two symbols in this global symbol table: a and b. After that, we use a new function, called NewEnclosedSymbolTable, to create another symbol table, called local, that’s enclosed in global. In local we then define two new symbols: c and d.

That’s the setup. The expectation is that when we then try to resolve all four symbols by calling Resolve on local, the symbols with the correct Scope and Index fields are returned.

And that’s not all of it. We also want to make sure that the SymbolTable can handle arbitrarily nested and enclosed symbol tables: