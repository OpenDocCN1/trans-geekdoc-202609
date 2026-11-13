# # INTERMEZZO 5: THE COST OF COMPUTATION

What do you know about program f once the following tests succeed:

```
(check-expect (f 0) 0)
(check-expect (f 1) 1)
(check-expect (f 2) 8)
```

If this question showed up on a standard test, you might respond with this:

```
(define (f x) (expt x 3))
```

But nothing speaks against the following:

```
(define (f x) (if (= x 2) 8 (* x x)))
```

Tests tell you only that a program works as expected on some inputs.

In the same spirit, timing the evaluation of a program application for specific inputs tells you how long it takes to compute the answers for those inputs—and nothing else. You may have two programs—prog-linear and prog-square—that compute the same answers when given the same inputs, and you may find that for all chosen inputs, prog-linear always computes the answer faster than prog-square. Chapter 26.4 presents just such a pair of programs: gcd, a structurally recursive program, and gcd-generative, an equivalent but generative-recursive program. The timing comparison suggests that the latter is much faster than the former.