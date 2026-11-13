```
#true
> (posn? 42)
#false
> (posn? #true)
#false
> (posn? (make-posn 3 4))
#true
```

Similarly, entry? distinguishes entry structures from all other values:

```
> (entry? pl)
#true
> (entry? 42)
#false
> (entry? #true)
#false
```

In general, a predicate recognizes exactly those values constructed with a constructor of the same name. Intermezzo 1 explains this law in detail, and it also collects the laws of computing for BSL in one place.

**Exercise 71.** Place the following into DrRacket’s definitions area:

```
; distances in terms of pixels:
(define HEIGHT 200)
(define MIDDLE (quotient HEIGHT 2))
(define WIDTH 400)
(define CENTER (quotient WIDTH 2))

(define-struct game [left-player right-player ball])

(define game0
 (make-game MIDDLE MIDDLE (make-posn CENTER CENTER)))
```

Click RUN and evaluate the following expressions:

```
(game-ball game0)
(posn? (game-ball game0))
(game-left-player game0)
```

Explain the results with step-by-step computations. Double-check your computations with DrRacket’s stepper.