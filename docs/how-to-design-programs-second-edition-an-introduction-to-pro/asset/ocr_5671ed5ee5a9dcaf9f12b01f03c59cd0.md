```
(define (undeclareds le0)
(local
  (; Lam ??? -> Lam
  ; accumulator a represents ...
  (define (undeclareds/a le a)
  (cond
    [(is-var? le) ....]
    [(is-λ? le)
    (... (undeclareds/a (λ-body le)
        ... a ....) ....)]
    [(is-app? le)
    (... (undeclareds/a (app-fun le)
        ... a ....)
    ... (undeclareds/a (app-arg le)
        ... a ....) ....)]))))
(undeclareds/a le0 ....)))
```

In this context, we can now formulate an accumulator invariant:
a represents the list of λ parameters encountered on the path from
the top of 1e0 to the top of 1e.

For example, if 1e0 is

```
' ( ((λ (y) (λ (x) y)) (λ (z) z)) (λ (w) w))
```

and 1e is the highlighted subtree, then a contains y. The left side of figure 186
presents a graphical illustration of the same example. It shows a Lam expression
as an upside-down tree; that is, the root is at the top. A @ node represents an
application with two descendants; the other nodes are self-explanatory. In this
tree diagram, the bold path leads from 1e0 to 1e through a single variable
declaration.