```
(define (extract R l t)
 (cond
  [(empty? l) '()]
  [else (cond
         [(R (first l) t)
          (cons (first l)
                (extract R (rest l) t))]
         [else
          (extract R (rest l) t)]]))
```

To apply this new function, we must supply three arguments: a function R that compares two numbers, a list l of numbers, and a threshold t. The function then extracts all those items i from l for which (R i t) evaluates to #true.

Stop! At this point you should ask whether this definition makes any sense. Without further fuss, we have created a function that consumes a function—something that you probably have not seen before. It turns out, however, that your simple little teaching language ISL supports these kinds of functions, and that defining such functions is one of the most powerful tools of good programmers—even in languages in which function-consuming functions do not seem to be available.

> If you have taken a calculus course, you have encountered the differential operator and the indefinite integral. Both of those are functions that consume and produce functions. But we do not assume that you have taken a calculus course.

Testing shows that `(extract < l t)` computes the same result as `(small l t):

```
(check-expect (extract < '() 5) (small '() 5))
(check-expect (extract < '(3) 5) (small '(3) 5))
(check-expect (extract < '(1 6 4) 5)
             (small '(1 6 4) 5))
```

Similarly, `(extract > l t)` produces the same result as `(large l t)`, which means that you can define the two original functions like this: