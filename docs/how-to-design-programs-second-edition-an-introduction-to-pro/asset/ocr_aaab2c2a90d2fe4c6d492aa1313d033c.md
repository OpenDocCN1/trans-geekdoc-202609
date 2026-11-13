When you evaluate (how-many some-non-empty-list) by hand, n applications of add1 are pending by the time the function reaches '()—where n is the number of items on the list. Computer scientists sometime say that how-many needs O(n) space to represent these pending function applications. Does the accumulator reduce the amount of space needed to compute the result?

# Exercise 501. Design an accumulator-style version of add-to-pi. The function adds a natural number to pi without using +:

```
; N -> Number
; adds n to pi without using +
(check-within (add-to-pi 2) (+ 2 pi) 0.001)
(define (add-to-pi n)
  (cond
    [(zero? n) pi]
    [else (add1 (add-to-pi (sub1 n)))]))
```

Stop when you have formulated the accumulator invariant and have someone check it.

# Exercise 502. Design the function palindrome, which accepts a non-empty list and constructs a palindrome by mirroring the list around the last item. When given (explode "abc"), it yields (explode "abcba").

Hint Here is a solution designed by function composition:

```
; [NEList-of 1String] -> [NEList-of 1String]
; creates a palindrome from s0
(check-expect
 (mirror (explode "abc")) (explode "abcba"))
(define (mirror s0)
  (append (all-but-last s0)
          (list (last s0))
          (reverse (all-but-last s0))))
```

See chapter 11.4 for last; design all-but-last in an analogous manner.