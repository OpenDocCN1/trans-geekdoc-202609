point in time, the box should contain one piece of food. To keep things simple, a piece of food is of the same size as a worm segment. When the worm’s head is located at the same position as the food, the worm eats the food, meaning the worm’s tail is extended by one segment. As the piece of food is eaten, another one shows up at a different location.

Adding food to the game requires changes to the data representation of world states. In addition to the worm, the states now also include a representation of the food, especially its current location. A change to the game representation suggests new functions for dealing with events, though these functions can reuse the functions for the worm (from exercise 218) and their test cases. It also means that the tick handler must not only move the worm; in addition it must manage the eating process and the creation of new food.

Your program should place the food randomly within the box. To do so properly, you need a design technique that you haven’t seen before—so-called generative recursion, which is introduced in part V—so we provide these functions in figure 80. Before you use them, however, explain how these functions work—assuming MAX is greater than 1—and then formulate purpose statements.

```
; Posn -> Posn
; ???
(check-satisfied (food-create (make-posn 1 1)) not=-1-1?)
(define (food-create p)
  (food-check-create
   p (make-posn (random MAX) (random MAX))))
; Posn Posn -> Posn
; generative recursion
; ???
(define (food-check-create p candidate)
  (if (equal? p candidate) p (food-create p) candidate))
; Posn -> Boolean
; use for testing only
(define (not=-1-1? p)
  (not (and (= (posn-x p) 1) (= (posn-y p) 1))))
```

Figure 80: Random placement of food