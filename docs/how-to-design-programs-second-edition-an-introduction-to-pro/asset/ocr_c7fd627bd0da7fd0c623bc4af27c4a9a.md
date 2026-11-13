with real boards and four identical queens. Figure 174 shows one of them, on the left, and the other one is this:

![](bbox=[0.405, 0.158, 0.592, 0.296])

In terms of data representations, however, there are many different ways to represent these two images. Figure 175 sketches some. Fill in the rest.

```
; N -> [Maybe [List-of QP]]
; finds a solution to the n queens problem

(define 0-1 (make-posn 0 1))
(define 1-3 (make-posn 1 3))
(define 2-0 (make-posn 2 0))
(define 3-2 (make-posn 3 2))

(check-member-of
 (n-queens 4)
 (list 0-1 1-3 2-0 3-2)
 (list 0-1 1-3 3-2 2-0)
 (list 0-1 2-0 1-3 3-2)
 (list 0-1 2-0 3-2 1-3)
 (list 0-1 3-2 1-3 2-0)
 (list 0-1 3-2 2-0 1-3)
 ...
 (list 3-2 2-0 1-3 0-1))

(define (n-queens n)
 (place-queens (board0 n) n))
```

# Figure 175: Solutions for the 4 queens puzzle

**Exercise 481.** The tests in figure 175 are awful. No real-world programmer ever spells out all these possible outcomes.

One solution is to use property testing again. Design the n-queens-solution? function, which consumes a natural number n and produces a predicate on queen placements that determines whether a given placement is a solution to an n queens puzzle: