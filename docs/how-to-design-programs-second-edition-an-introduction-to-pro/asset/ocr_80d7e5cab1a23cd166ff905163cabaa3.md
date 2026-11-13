everyone else about the growth of a function. Any serious programmer and scientist must eventually become thoroughly familiar with this notion. It is the basis for analyzing performance attributes of programs. To understand the idea properly, you will need to work through a text book.

> > We thank Prabhakar Ragde for sharing his notes on connecting the first edition of this book with algorithmic analysis.

# ## Concrete Time, Abstract Time

Chapter 26.4 compares the running time of gcd and gcd-generative. In addition, it argues that the latter is better because it always uses fewer recursive steps than the former to compute an answer. We use this idea as the starting point to analyze the performance of how-many, a simple program from chapter 9:

```
```scheme
(define (how-many a-list)
  (cond
   [(empty? a-list) 0]
   [else (+ (how-many (rest a-list)) 1)]))
```
```

Suppose we want to know how long it takes to compute the length of some unknown, non-empty list. Using the rules of computation from intermezzo 1, we can look at this process as a series of algebraic manipulations:

```
```text
(how-many some-non-empty-list)
==
(cond
 [(empty? some-non-empty-list) 0]
 [else (+ (how-many (rest some-non-empty-list)) 1)])
==
(cond
 [#false 0]
 [else (+ (how-many (rest some-non-empty-list)) 1)])
==
(cond
 [else (+ (how-many (rest some-non-empty-list)) 1)])
==
```
```