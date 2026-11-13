```
expr = ...
   | (match expr [pattern expr] ...)

pattern = variable
   | literal-constant
   | (cons pattern pattern)
   | (structure-name pattern ...)
   | (? predicate-name)
```

# Figure 110: ISL+ match expressions

Roughly speaking,

```
(match expr
  [pattern1 expr1]
  [pattern2 expr2]
  ...)
```

proceeds like a cond expression in that it evaluates expr and sequentially tries to match its result with pattern1, pattern2, ... until it succeeds with patterni. At that point, it determines the value of expr_i, which is also the result of the entire match expression.

The key difference is that match, unlike cond, introduces a new scope, which is best illustrated with a screen shot from DrRacket:

![](bbox=[0.31, 0.58, 0.69, 0.71])

As the image shows, each pattern clause of this function binds variables. Furthermore, the scope of a variable is the body of the clause, so even if two patterns introduce the same variable binding—as is the case in the above code snippet—their bindings cannot interfere with each other.

Syntactically, a pattern resembles nested, structural data whose leaves are literal constants, variables, or predicate patterns of the shape

```
(? predicate-name)
```