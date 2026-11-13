```
; N -> sequence?
; constructs the **infinite** sequence of natural numbers,
; starting from n
(define (in-naturals n) ...)

; N N N -> sequence?
; constructs the following **finite** sequence of natural numbers:
; start
; (+ start step)
; (+ start step step)
; ...
; until the number exceeds end
(define (in-range start end step) ...)
```

# Figure 109: Constructing sequences of natural numbers

With the first one, we can simplify the enumerate function a bit:

```
(define (enumerate.v2 lx)
  (for/list ([item lx] [ith (in-naturals 1)])
    (list ith item)))
```

Here in-naturals is used to generate the infinite sequence of natural numbers starting at 1; the for loop stops when 1 is exhausted.

With the second one, it is, for example, possible to step through the even numbers among the first n:

```
; N -> Number
; adds the even numbers between 0 and n (exclusive)
(check-expect (sum-evens 2) 0)
(check-expect (sum-evens 4) 2)
(define (sum-evens n)
  (for/sum ([i (in-range 0 n 2)]))
))
```

Although this use may appear trivial, many problems originating in mathematics call for just such loops, which is precisely why concepts such as in-range are found in many programming languages.

**Exercise 305.** Use loops to define convert-euro. See exercise 267.

**Exercise 306.** Use loops to define a function that

+   1. creates the list (list 0 ... (- n 1)) for any natural number n;