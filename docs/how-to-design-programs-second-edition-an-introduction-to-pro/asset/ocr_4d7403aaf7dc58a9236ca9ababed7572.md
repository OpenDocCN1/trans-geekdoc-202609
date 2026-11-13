This solution traverses sØ four times:

+   1. via all-but-last,
+   2. via last,
+   3. via all-but-last again, and
+   4. via reverse, which is ISL+’s version of invert.

Even with local definition for the result of all-but-last, the function needs three traversals. While these traversals aren’t “stacked” and therefore don’t have a disastrous impact on the function’s performance, an accumulator version can compute the same result with a single traversal.

**Exercise 503**. Exercise 467 implicitly asks for the design of a function that rotates a Matrix until the first coefficient of the first row differs from 0. In the context of Exercise 467, the solution calls for a generative-recursive function that creates a new matrix by shifting the first row to the end when it encounters a 0 in the first position. Here is the solution:

```
; Matrix -> Matrix
; finds a row that doesn’t start with 0 and
; uses it as the first one
; **generative** moves the first row to last place
; **no termination** if all rows start with 0
(check-expect (rotate-until.v2 ’((0 4 5) (1 2 3)))
               ’((1 2 3) (0 4 5)))

(define (rotate M)
  (cond
    [(not (= (first (first M)) 0)) M]
    [else
     (rotate (append (rest M) (list (first M))))]))
```

Stop! Modify this function so that it signals an error when all rows start with 0.

If you measure this function on large instances of Matrix, you get a surprising result: