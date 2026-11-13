```
; -- (cons Number Row)
```

Note the constraints on matrices. Study the data definition and translate the two-by-two matrix consisting of the numbers 11, 12, 21, and 22 into this data representation. Stop, don’t read on until you have figured out the data examples.

Here is the solution for the five-second puzzle:

```
(define row1 (cons 11 (cons 12 '())))
(define row2 (cons 21 (cons 22 '())))
(define mat1 (cons row1 (cons row2 '())))
```

If you didn’t create it yourself, study it now.

The function in figure 70 implements the important mathematical operation of transposing the entries in a matrix. To transpose means to mirror the entries along the diagonal, that is, the line from the top-left to the bottom-right.

```
; Matrix -> Matrix
; transposes the given matrix along the diagonal
(define worl (cons 11 (cons 21 '())))
(define wor2 (cons 12 (cons 22 '())))
(define taml (cons worl (cons wor2 '())))

(check-expect (transpose mat1) taml)

(define (transpose lln)
  (cond
    [(empty? (first lln)) '()]
    [else (cons (first* lln) (transpose (rest* lln)))]))
```

# Figure 70: Transpose a matrix

Stop! Transpose mat1 by hand, then read figure 70. Why does transpose ask (empty? (first lln))?

The definition assumes two auxiliary functions:

+   • first*, which consumes a matrix and produces the first column as a list of numbers; and

+   • rest*, which consumes a matrix and removes the first column. The result