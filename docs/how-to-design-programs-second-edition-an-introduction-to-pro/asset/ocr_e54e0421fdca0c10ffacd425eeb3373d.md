```
(define (!.v2 n0)
  (local (; N N -> N
          ; computes (* n (- n 1) (- n 2) ... 1)
          ; accumulator a is the product of the
          ; natural numbers in the interval [n0,n)
          (define (!/a n a)
            (cond
              [(zero? n) a]
              [else (!/a (sub1 n) (* n a))]))))
  (!/a n0 1)))
```

It also follows from the accumulator statement that when n is 0, the accumulator is the product of n through 1, meaning it is the desired result. So, like sum, !/a returns a in this case and uses the result of the recursion in the second case.

**Exercise 497.** Like sum, !.v1 performs the primitive computations, multiplication in this case, in reverse order. Surprisingly, this affects the performance of the function in a negative manner.

Measure how long it takes to evaluate `(!.v1 20)` 1,000 times. Recall that `(time an-expression)` function determines how long it takes to run an-expression.

For the third and last example, we use a function that measures the height of simplified binary trees. The example illustrates that accumulator-style programming applies to all kinds of data, not just those defined with single self-references. Indeed, it is as commonly used for complicated data definitions as it is for lists and natural numbers.

Here are the relevant definitions:

```
(define-struct node [left right])
; A Tree is one of:
; -- '()
; -- (make-node Tree Tree)
(define example
  (make-node (make-node '() (make-node '() '())) '()))
```

These trees carry no information; their leafs are '(). Still, there are many different trees, as figure 184 shows; it also uses suggestive graphics to bring