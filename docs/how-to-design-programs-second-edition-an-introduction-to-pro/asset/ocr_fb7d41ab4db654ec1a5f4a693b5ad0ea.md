The hand-evaluation shows just how much the use of an accumulator simplifies the conversion process. Each item in the list is processed once. When relative->absolute/a reaches the end of the argument list, the result is completely determined and no further work is needed. In general, the function performs on the order of N natural recursion steps for a list with N items.

One problem is that, unlike relative->absolute, the new function consumes two arguments, not just one. Worse, someone might accidentally misuse relative->absolute/a by applying it to a list of numbers and a number that isn’t 0. We can solve both problems with a function definition that uses a local definition to encapsulate relative->absolute/a; figure 178 shows the result. Now, relative->absolute is indistinguishable from relative->absolute.v2 with respect to input-output.

```
```racket
; [List-of Number] -> [List-of Number]
; converts a list of relative to absolute distances
; the first number represents the distance to the origin

(check-expect (relative->absolute.v2 '(50 40 70 30 30))
             '(50 90 160 190 220))

(define (relative->absolute.v2 l)
  (local (; [List-of Number] Number -> [List-of Number]
          (define (relative->absolute/a l accu-dist)
            (cond
              [(empty? l) '()]
              [else
               (local ((define accu (+ (first l) accu-dist)))
                 (cons accu
                       (relative->absolute/a (rest l) accu)))])))
    (relative->absolute/a l 0)))
```
```

# Figure 178: Converting relative distances with an accumulator

Now let’s look at how this version of the program performs. To this end, we evaluate

```
(relative->absolute.v2 (build-list size add1))
```

and tabulate the results for several values of size: