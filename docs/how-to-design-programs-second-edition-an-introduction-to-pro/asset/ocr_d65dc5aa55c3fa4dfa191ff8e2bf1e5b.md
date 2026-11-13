```
; [X Y] [X -> Y] [List-of X] -> [List-of Y]
```

It tells us that map consumes a function from x to Y and a list of xs. Given that add-3-to-all consumes a list of Posns, we know that x stands for Posn. Similarly, add-3-to-all is to produce a list of Posns, and this means we replace Y with Posn.

From the analysis of the signature, we conclude that map can do the job of add-3-to-all when given the right function from Posns to Posns. With local, we can express this idea as a template for add-3-to-all:

```
(define (add-3-to-all lop)
  (local (; Posn -> Posn
          ; ...
          (define (fp p)
            ... p ...))
        (map fp lop))))
```

Doing so reduces the problem to defining a function on Posns.

Given the example for add-3-to-all and the abstract example for map, you can actually imagine how the evaluation proceeds:

```
(add-3-to-all (list (make-posn 3 1) (make-posn 0 0)))
==
(map fp (list (make-posn 3 1) (make-posn 0 0)))
==
(list (fp (make-posn 3 1)) (fp (make-posn 0 0)))
```

And that shows how fp is applied to every single Posn on the given list, meaning it is its job to add 3 to the x-coordinate.

From here, it is straightforward to wrap up the definition:

```
(define (add-3-to-all lop)
  (local (; Posn -> Posn
          ; adds 3 to the x-coordinate of p
          (define (add-3-to-1 p)
            (make-posn (+ (posn-x p) 3) (posn-y p))))
        (map add-3-to-1 lop))))
```