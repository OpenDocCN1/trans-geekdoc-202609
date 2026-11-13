# Design the function circle-pt:

```
(define CENTER (make-posn 200 200))
(define RADIUS 200)
; the radius in pixels

; Number -> Posn
; determines the point on the circle with CENTER
; and RADIUS whose angle is

; examples
; what are the x and y coordinates of the desired
; point, when given: 120/360, 240/360, 360/360

(define (circle-pt factor)
 (make-posn 0 0))
```

Domain Knowledge This design problem calls on knowledge from mathematics. One way to view the problem is as a conversion of a complex number from the polar-coordinate representation to the Posn representation. Read up on make-polar, real-part, and imag-part in ISL+. Another way is to use trigonometry, sin and cos, to determine the coordinates. If you choose this route, recall that these trigonometry functions compute the sine and cosine in terms of radians, not degrees. Also keep in mind that on-screen positions grow downward, not upward.

# Exercise 527. Take a look at the following two images:

![](bbox=[0.28, 0.689, 0.428, 0.813])

![](bbox=[0.552, 0.689, 0.708, 0.813])

They demonstrate how to generate a fractal Savannah tree in the same way that figure 156 shows how to draw a Sierpinski triangle. The image on the left shows what a fractal Savannah tree looks like. The right one explains the generative