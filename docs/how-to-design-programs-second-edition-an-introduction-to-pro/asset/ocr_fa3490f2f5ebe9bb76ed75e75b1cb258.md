# 32.3 Transforming Functions into Accumulator Style

Articulating the accumulator statement is difficult, but, without formulating a good invariant, it is impossible to understand an accumulator-style function. Since the goal of a programmer is to make sure that others who follow understand the code easily, practicing this skill is critical. And formulating invariants deserves a lot of practice.

The goal of this section is to study the formulation of accumulator statements with three case studies: a summation function, the factorial function, and a tree-traversal function. Each such case is about the conversion of a structurally recursive function into accumulator style. None actually calls for the use of an accumulator parameter. But they are easily understood and, with the elimination of all other distractions, using such examples allows us to focus on the articulation of the accumulator invariant.

For the first example, consider these definitions of the `sum` function:

```
```scheme
(define (sum.v1 alon)
  (cond
    [(empty? alon) 0]
    [else (+ (first alon) (sum.v1 (rest alon)))]))
```
```

Here is the first step toward an accumulator version:

```
```scheme
(define (sum.v2 alon0)
  (local (; [List-of Number] ??? -> Number
          ; computes the sum of the numbers on alon
          ; accumulator ...
          (define (sum/a alon a)
            (cond
              [(empty? alon) ...]
              [else (... (sum/a (rest alon)
                              ... a ...) ...)])))
    (sum/a alon0 ...)))
```
```

Stop! Supply a signature and a test case that works for both.

As suggested by our first step, we have put the template for `sum/a` into a