# Parse Trees

we can evaluate it as

```
value str
-1
```

+   - list of (func;arg1;arg2;...) - it executes function func with arguments arg1,arg2,...

We see that the last case is similar in definition to a parse tree and both value and eval can evaluate the same expression. There are subtle differences, though, and the two functions do slightly different things: eval will evaluate a correctly constructed parse tree. value will execute a list of functions and arguments and returns its result, as well as performing the other utilities described in the above list.
 therefore have:

```
value "1+2" / value the expression
3
eval "1+2" / evaluate the constant string, just returns the constat
string
```

```
eval (+;1;2) / evaluation the parse-tree
3
value (;;somevar;2)
2
```

```
somevar
'somevar / variable doesnt exist
[0] somevar
^
eval (;;`somevar;2)
2
somevar
2
```