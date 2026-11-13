differences between the two coordinates remain the same. Which diagonal does
this idea describe?

**Hint** Once you have figured out the domain knowledge, formulate a test
suite that covers horizontals, verticals, and diagonals. Don't forget to include
arguments for which threatening? must produce #false.

**Exercise** 480. Design render-queens. The function consumes a natural
number n, a list of QPs, and an Image. It produces an image of an n by n chess
board with the given image placed according to the given QPs.

You may wish to look for an image for a chess queen on-line or create a
simplistic one with the available image functions.

As for a data representation for Boards, we postpone this step until we know
how the algorithm implements the process. Doing so is another exercise in data
abstraction. Indeed, a data definition for Board isn't even necessary to state the
signature for the algorithm proper:

```
; N -> [Maybe [List-of QP]]
; finds a solution to the n queens problem
; data example: [List-of QP]
(define 4QUEEN-SOLUTION-2
 (list  (make-posn 0 2) (make-posn 1 0)
        (make-posn 2 3) (make-posn 3 1)))

(define (n-queens n)
 #false)
```

The complete puzzle is about finding a placement for n queens on an n by n
chess board. So clearly, the algorithm consumes nothing else but a natural
number, and it produces a representation for the n queen placements—if a
solution exists. The latter can be represented with a list of QPs, which is why we
choose

```
; [List-of QP] or #false
```

as the result. Naturally, #false represents the failure to find a solution.

The next step is to develop examples and to formulate them as tests. We
know that n-queens must fail when given 2 or 3. For 4, there are two solutions