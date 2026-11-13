```
==
(define smallest-in-rest-1
  (inf (rest (list 2 1 3))))
⊕
(cond
  [(< (first (list 2 1 3)) smallest-in-rest-1)
   (first (list 2 1 3))]
  [else smallest-in-rest-1])
```

Curiously, the next expression we need to evaluate is the right-hand side of a constant definition in a local expression. But the point of computing is that you can replace expressions with their equivalents wherever you want:

```
==
(define smallest-in-rest-1
  (cond
    [(empty? (rest (list 1 3))) (first (list 1 3))]
    [else
     (local ((define smallest-in-rest
                (inf (rest (list 1 3)))))
       (cond
         [(< (first (list 1 3)) smallest-in-rest)
          (first (list 1 3))]
         [else smallest-in-rest])]))])
⊕
(cond
  [(< (first (list 2 1 3)) smallest-in-rest-1)
   (first (list 2 1 3))]
  [else smallest-in-rest-1])
```

Once again, we skip the conditional steps and focus on the else clause, which is also a local expression. Indeed it is another variant of the local expression in the definition of inf, with a different list value substituted for the parameter: