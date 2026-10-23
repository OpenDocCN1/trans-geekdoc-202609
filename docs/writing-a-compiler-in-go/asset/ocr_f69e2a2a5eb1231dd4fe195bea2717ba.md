Now we can finally get feedback from our three failing tests in symbol_table_test.go:

```
$ go test ./compiler
--- FAIL: TestLetStatementScopes (0.00s)
compiler_test.go:935: testConstants failed:\
constant 1 - testInstructions failed: wrong instructions length.
want="0000 OpConstant 0\n0003 OpSetLocal 0\n0005 OpGetLocal 0\n\
0007 OpReturnValue\n"
got ="0000 OpConstant 0\n0003 OpSetGlobal 0\n0006 OpGetGlobal 0\n\
0009 OpReturnValue\n"

--- FAIL: TestDefine (0.00s)
symbol_table_test.go:31: expected c={Name:c Scope:LOCAL Index:0},\
got={Name:c Scope:GLOBAL Index:0}
symbol_table_test.go:36: expected d={Name:d Scope:LOCAL Index:1},\
got={Name:d Scope:GLOBAL Index:1}
symbol_table_test.go:43: expected e={Name:e Scope:LOCAL Index:0},\
got={Name:e Scope:GLOBAL Index:0}
symbol_table_test.go:48: expected f={Name:f Scope:LOCAL Index:1},\
got={Name:f Scope:GLOBAL Index:1}

--- FAIL: TestResolveLocal (0.00s)
symbol_table_test.go:94: name a not resolvable
symbol_table_test.go:94: name b not resolvable
symbol_table_test.go:98: expected c to resolve to\
{Name:c Scope:LOCAL Index:0}, got={Name:c Scope:GLOBAL Index:0}
symbol_table_test.go:98: expected d to resolve to\
{Name:d Scope:LOCAL Index:1}, got={Name:d Scope:GLOBAL Index:1}

--- FAIL: TestResolveNestedLocal (0.00s)
symbol_table_test.go:145: name a not resolvable
symbol_table_test.go:145: name b not resolvable
symbol_table_test.go:149: expected c to resolve to\
{Name:c Scope:LOCAL Index:0}, got={Name:c Scope:GLOBAL Index:0}
symbol_table_test.go:149: expected d to resolve to\
{Name:d Scope:LOCAL Index:1}, got={Name:d Scope:GLOBAL Index:1}
symbol_table_test.go:145: name a not resolvable
symbol_table_test.go:145: name b not resolvable
symbol_table_test.go:149: expected e to resolve to\
{Name:e Scope:LOCAL Index:0}, got={Name:e Scope:GLOBAL Index:0}
symbol_table_test.go:149: expected f to resolve to\
{Name:f Scope:LOCAL Index:1}, got={Name:f Scope:GLOBAL Index:1}
FAIL
FAIL    monkey/compiler 0.008s
```

Besides the three test functions concerning themselves with SymbolTable, there’s also TestLetStatementScopes failing and reminding us that we need to go back to our compiler once we’re done with extending SymbolTable. That won’t take too long – we can make all of the other tests pass with a tiny number of changes.

Now that we have the Outer field on SymbolTable, the Resolve and Define