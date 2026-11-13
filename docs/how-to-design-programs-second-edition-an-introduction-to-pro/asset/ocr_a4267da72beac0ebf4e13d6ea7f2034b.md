```
(check-expect (launch "resting" "a") "resting")
(check-expect (launch -3 " ") -3)
(check-expect (launch -1 " ") -1)
(check-expect (launch 33 " ") 33)
(check-expect (launch 33 "a") 33)
```

An inspection of these six examples shows that the first two are about the first sub-class of LRCD, the third and fourth concern the countdown, and the last two are about key events when the rocket is already in the air.

Since writing down the sketch of a cond expression worked well for the design of the show function, we do it again:

```
(define (launch x ke)
  (cond
    [(string? x) ...]
    [(<= -3 x -1) ...]
    [(>= x 0) ...])))
```

Looking back at the examples suggests that nothing changes when the world is in a state that is represented by the second or third sub-class of data. Meaning, launch should produce x when this happens:

```
(define (launch x ke)
  (cond
    [(string? x) ...]
    [(<= -3 x -1) x]
    [(>= x 0) x])))
```

Finally, the first example identifies the exact case when the launch function produces a new world state:

```
(define (launch x ke)
  (cond
    [(string? x) (if (string=? " " ke) -3 x)]
    [(<= -3 x -1) x]
    [(>= x 0) x])))
```

Specifically, when the state of the world is "resting" and the user presses the space bar, the function starts the countdown with -3.

Copy the code into the definitions area of DrRacket and ensure that the