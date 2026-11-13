+   • Otherwise, the algorithm must generate a Sierpinski triangle of size side / 2 because juxtaposing two such triangles in either direction yields one of size side.

+   • If half-sized is the Sierpinski triangle of size side / 2, then
+   
+   (above half-sized
+    (beside half-sized half-sized))
+   
+   is a Sierpinski triangle of size side.

With these answers, it is straightforward to define the function. Figure 157 spells out the details. The “triviality condition” translates to (<= side SMALL) for some constant SMALL. For the trivial answer, the function returns a triangle of the given size. In the recursive case, a local expression introduces the name half-sized for the Sierpinski triangle that is half as big as the specified size. Once the recursive call has generated the small Sierpinski triangle, it composes this image via above and beside.

```
(define SMALL 4) ; a size measure in terms of pixels

(define small-triangle (triangle SMALL 'outline 'red))

; Number -> Image
; generative creates Sierpinski Δ of size side by generating
; one for (/ side 2) and placing one copy above two copies

(check-expect (sierpinski SMALL) small-triangle)
(check-expect (sierpinski (* 2 SMALL))
 (above small-triangle
  (beside small-triangle small-triangle)))

(define (sierpinski side)
 (cond
  [(<= side SMALL) (triangle side 'outline 'red)]
  [else
   (local ((define half-sized (sierpinski (/ side 2))))
    (above half-sized (beside half-sized half-sized)))])))
```

Figure 157: The Sierpinski algorithm

The figure highlights two other points. First, the purpose statement is