```
(+ (* 20 2) (/ 20 2))
```

the addition cannot take place before the multiplication or division. Similarly,
the shaded division in

```
(cond
[ (= 0 0) "inf"]
[else (/ 1 0)])
```

cannot be substituted for the complete cond expression until the corresponding
line is the first condition in the cond.

As a rule of thumb, it is best to keep the following in mind:

_Always choose the outermost and left-most nested expression that
is ready for evaluation._

While this guideline may look simplistic, it always explains BSL’s results.

In some cases, programmers also want to define functions that raise errors.
Recall the checked version of area-of-disk from chapter 6.3:

```
(define (checked-area-of-disk v)
(cond
 [(number? v) (area-of-disk v)]
 [else (error "number expected")]))
```

Now imagine applying checked-area-of-disk to a string:

```
(- (checked-area-of-disk "a")
  (checked-area-of-disk 10))
==
(- (cond
    [(number? "a") (area-of-disk "a")]
    [else (error "number expected")])
  (checked-area-of-disk 10))
==
(- (cond
    [#false (area-of-disk "a")]
```