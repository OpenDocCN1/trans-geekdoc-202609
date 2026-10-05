# Parse Trees

When the functional query is called from within a function, it perceives `tab as a global variable. In such a case, we have to refer to the local variable within the function, and thus we pass the name by value. We can illustrate it as follows: Let us call the functional select from a dummy function, where we first pass the table by reference and then by value. Before we call the functional select, though, we define the local table with the same name as a global variable, tab.

The call when the table is passed by reference returns the globally defined table:

```
[]
tab: ([][] aa:til 5);
?:[`tab`();0b;)
()
```

| a b c |
|---|---|--|
| 0 9 1 |
| 1 8 1 |
| 2 7 1 |
| 3 6 1 |
| 4 5 1 |
| 5 4 1 |
| 6 3 1 |
| 7 2 1 |
| 8 1 1 |
| 9 0 1 |

On the other hand, when we pass the argument by value, we refer to the locally defined table:

```
[]
tab: ([][] d:til 5);
?:[`tab`();0b;)
()
```

| d |
|--|
| 0 |
| 1 |
| 2 |
| 3 |
| 4 |

We can confirm the difference by using the standard select:

```
[]
tab: ([][] d:til 5);
:select from tab
()
```