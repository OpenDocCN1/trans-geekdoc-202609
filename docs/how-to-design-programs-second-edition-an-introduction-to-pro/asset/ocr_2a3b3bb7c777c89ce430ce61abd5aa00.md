above definitions work. At that point, you may wish to add a function for running the program:

```
; LRCD -> LRCD
(define (main1 s)
 (big-bang s
   [to-draw show]
   [on-key launch]))
```

This function does **not** specify what to do when the clock ticks; after all, we haven't designed `fly` yet. Still, with `main1` it is possible to run this incomplete version of the program and to check that you can start the countdown. What would you provide as the argument in a call to `main1`?

The design of `fly`—the clock-tick handler—proceeds just like the design of the preceding two functions, and figure 25 displays the result of the design process. Once again the key is to cover the space of possible input data with a goodly bunch of examples, especially for the two intervals. These examples ensure that the countdown and the transition from the countdown to the liftoff work properly.

```
; LRCD -> LRCD
; raises the rocket by YDELTA if it is moving already
(check-expect (fly "resting") "resting")
(check-expect (fly -3) -2)
(check-expect (fly -2) -1)
(check-expect (fly -1) HEIGHT)
(check-expect (fly 10) (- 10 YDELTA))
(check-expect (fly 22) (- 22 YDELTA))

(define (fly x)
 cond
   [(string? x) x]
   [(<= -3 x -1) (if (= x -1) HEIGHT (+ x 1))]
   [(>= x 0) (- x YDELTA)]))
```

# Figure 25: Launching a countdown and a liftoff

**Exercise 56.** Define `main2` so that you can launch the rocket and watch it lift off. Read up on the on-tick clause to determine the length of one tick and how to change it.