```
(inf (list 2 1 3))
==
(cond
  [(empty? (rest (list 2 1 3)))
   (first (list 2 1 3))]
  [else
   (local ((define smallest-in-rest
             (inf (rest (list 2 1 3)))))
     (cond
       [(< (first (list 2 1 3)) smallest-in-rest)
        (first (list 2 1 3))]
       [else smallest-in-rest])))])
```

We substitute (list 2 1 3) for 1.

Since the list isn’t empty, we skip the steps for evaluating the conditional and focus on the next expression to be evaluated:

```
...
==
```

```
(local ((define smallest-in-rest
         (inf (rest (list 2 1 3)))))
  (cond
    [(< (first (list 2 1 3)) smallest-in-rest)
     (first (list 2 1 3))]
    [else smallest-in-rest]]))
```

Applying the two steps for the rule of local yields two parts: the local definition lifted to the top and the body of the local expression. Here is how we write this down: