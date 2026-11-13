```
; [List-of Number] -> Number                   ; [List-of Posn] -> Image
(define (product l)                        (define (image* l)
(cond                                  (cond
 [(empty? l) 1]                          [(empty? l) emt]
[else                                    [else
 (* (first l)                                (place-dot
  (product                                   (first l)
   (rest l)))))))                            (image* (rest l)))))))

; Posn Image -> Image
(define (place-dot p img)
(place-image
dot
(posn-x p) (posn-y p)
img))

; graphical constants:
(define emt
(empty-scene 100 100))
(define dot
(circle 3 "solid" "red"))
```

# Figure 94: The similar functions for exercise 252

Lastly, when you are dealing with data definitions, the abstraction process proceeds in an analogous manner. The extra parameters to data definitions stand for collections of values, and testing means spelling out a data definition for some concrete examples. All in all, abstracting over data definitions tends to be easier than abstracting over functions, and so we leave it to you to adapt the design recipe appropriately.