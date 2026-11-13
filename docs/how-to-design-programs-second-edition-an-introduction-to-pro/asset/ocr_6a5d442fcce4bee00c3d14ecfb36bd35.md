Remember that the second step of the `local` rule replaces the `local` expression with its body. In this case, the body is just the name of the function, and its surrounding is an application to 1. The rest is arithmetic:

```
[(f-1 1)] == [(+ (* 4 (sqr 1)) 3)] == 7
```

**Exercise 265.** Use DrRacket’s stepper to fill in any gaps above.

**Exercise 266.** Use DrRacket’s stepper to find out how ISL evaluates

```
((local ((define (f x) (+ x 3))
         (define (g x) (* x 4))))
     (if (odd? (f (g 1)))
         f
         g))
  2)
```

to 5.