```
; [X Y] [X Y -> Y] Y [List-of X] -> Y
; applies f from right to left to each item in lx and b
; (foldr f b (list x-1 ... x-n)) == (f x-1 ... (f x-n b))
(define (foldr f b lx) ...)

(foldr + 0 '(1 2 3 4 5))
== (+ 1 (+ 2 (+ 3 (+ 4 (+ 5 0))))))
== (+ 1 (+ 2 (+ 3 (+ 4 5)))))
== (+ 1 (+ 2 (+ 3 9))))
== (+ 1 (+ 2 12)))
== (+ 1 14)

; [X Y] [X Y -> Y] Y [List-of X] -> Y
; applies f from left to right to each item in lx and b
; (foldl f b (list x-1 ... x-n)) == (f x-n ... (f x-1 b))
(define (foldl f b lx) ...)

(foldl + 0 '(1 2 3 4 5))
== (+ 5 (+ 4 (+ 3 (+ 2 (+ 1 0))))))
== (+ 5 (+ 4 (+ 3 (+ 2 1)))))
== (+ 5 (+ 4 (+ 3 3))))
== (+ 5 (+ 4 6)))
== (+ 5 10)
```

# Figure 96: ISL’s abstract functions for list processing (2)

Mathematics calls functions associative if the order makes no difference. ISL’s = is associative on integers but not on inexacts. See below.

# Exercise 256. Explain the following abstract function:

```
; [X] [X -> Number] [NEList-of X] -> X
; finds the (first) item in lx that maximizes f
; if (argmax f (list x-1 ... x-n)) == x-i,
; then (>= (f x-i) (f x-1)), (>= (f x-i) (f x-2)), ...
(define (argmax f lx) ...)
```

Use it on concrete examples in ISL. Can you articulate an analogous purpose statement for argmin?

Figure 97 illustrates the power of composing the functions from figures 95 and 96. Its main function is listing. The purpose is to create a string from a list of addresses. Its purpose statement suggests three tasks and thus the design of three functions: