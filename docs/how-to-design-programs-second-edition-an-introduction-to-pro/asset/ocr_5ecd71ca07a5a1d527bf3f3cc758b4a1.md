```
(define (posn+ p v)
 (...) (posn-x p) ... (posn-y p) ...
 ... (vel-deltax v) ... (vel-deltay v) ...))
```

Because posn+ consumes instances of Posn and Vel and because each piece of data is an instance of a two-field structure, we get four expressions. In contrast to the nested selector expressions from above, these are simple applications of a selector to a parameter.

If we remind ourselves what these four expressions represent, or if we recall how we computed the desired results from the two structures, our completion of the definition of posn+ is straightforward:

```
(define (posn+ p v)
 (make-posn (+ (posn-x p) (vel-deltax v))
            (+ (posn-y p) (vel-deltay v))))
```

The first step is to add the velocity in the horizontal direction to the x-coordinate and the velocity in the vertical direction to the y-coordinate. This yields two expressions, one per new coordinate. With make-posn we can combine them into a single Posn again.

**Exercise** 75. Enter these definitions and their test cases into the definitions area of DrRacket and make sure they work. This is the first time that you have dealt with a “wish,” and you need to make sure you understand how the two functions work together.