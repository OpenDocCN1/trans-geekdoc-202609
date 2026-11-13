interval in which we expect to find a root:

```
; [Number -> Number] Number Number -> ...
(define (find-root f left right) ...)
```

The three parameters can’t be just any function and numbers. For find-root to work, we must assume that the following holds:

```
(or (<= (f left) 0 (f right))
(<= (f right) 0 (f left)))
```

that is, (f left) and (f right) must be on opposite sides of the x-axis.

> DrRacket allows the use of Greek symbols such as ε. But you can also write EPSILON instead.

Next we need to fix the function’s result and formulate a purpose statement. Simply put, find-root finds an interval that contains a root. The search divides the interval until its size, (- right left), is tolerably small, say, smaller than some constant ε. At that point, the function could produce one of three results: the left boundary, the right one, or a representation of the interval. Any one of them completely identifies the interval, and since it is simpler to return numbers, we pick the left boundary. Here is the complete header material:

```
; [Number -> Number] Number Number -> Number
; determines R such that f has a root in [R,(+ R ε)]
; assume f is continuous
; (2) (or (<= (f left) 0 (f right)) (<= (f right) 0 (f left)))
; generative divides interval in half, the root is in
; one of the two halves, picks according to (2)
(define (find-root f left right)
0)
```

# **Exercise 445.** Consider the following function definition:

```
; Number -> Number
(define (poly x)
(* (- x 2) (- x 4)))
```