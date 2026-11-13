```
; [List-of Number] -> [List-of Number]
; converts a list of relative to absolute distances
; the first number represents the distance to the origin
(check-expect (relative->absolute '(50 40 70 30 30))
 '(50 90 160 190 220))
(define (relative->absolute l)
 (cond
  [(empty? l) '()]
  [else (local ((define rest-of-l
                 (relative->absolute (rest l)))
             (define adjusted
              (add-to-each (first l) rest-of-l)))
       (cons (first l) adjusted))]))
; Number [List-of Number] -> [List-of Number]
; adds n to each number on l
(check-expect (cons 50 (add-to-each 50 '(40 110 140 170)))
 '(50 90 160 190 220))
(define (add-to-each n l)
 (cond
  [(empty? l) '()]
  [else (cons (+ (first l) n) (add-to-each n (rest l)))]))
```

# Figure 177: Converting relative distances to absolute distances

While designing the program is relatively straightforward, using it on larger and larger lists reveals a problem. Consider the evaluation of the following expression:

```
(relative->absolute (build-list size add1))
```

As we increase size, the time needed grows even faster:

| size | 1000 | 2000 | 3000 | 4000 | 5000 | 6000 | 7000 |
|---|---|---|---|---|---|---|---|
| time | 25 | 109 | 234 | 429 | 689 | 978 | 1365 |

Instead of doubling as we go from 1000 to 2000 items, the time quadruples. This is also the approximate relationship for going from 2000 to 4000, and so on. Using the terminology of intermezzo 5, we say that the function’s performance is _O_(_n_<sup>2</sup>) where _n_ is the length of the given list.