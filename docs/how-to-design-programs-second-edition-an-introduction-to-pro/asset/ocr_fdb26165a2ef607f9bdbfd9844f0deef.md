```
[(>= p 10000) ...]))
```

5. When you have finished the template, you are ready to define the function.
Given that the function body already contains a schematic cond
expression, it is natural to start from the various cond lines. For each cond
line, you may assume that the input parameter meets the condition and so
you exploit the corresponding test cases. To formulate the corresponding
result expression, you write down the computation for this example as an
expression that involves the function parameter. Ignore all other possible
kinds of input data when you work on one line; the other cond clauses take
care of those.

```
(define (sales-tax p)
  (cond
    [(and (<= 0 p) (< p 1000)) 0]
    [(and (<= 1000 p) (< p 10000)) (* 0.05 p)]
    [(>= p 10000) (* 0.08 p)])))
```

6. Finally, run the tests and ensure that they cover all cond clauses.

What do you do when one of your test cases fails? Review the end of
chapter 3.1 concerning test failures.

**Exercise 58.** Introduce constant definitions that separate the intervals for low
prices and luxury prices from the others so that the legislators in Tax Land can
easily raise the taxes even more.