Figure 191 shows the result of translating these answers into a skeletal definition. Since each midpoint is used twice, the skeleton uses local to formulate the generative step in ISL+. The local expression introduces the three new midpoints plus three recursive applications of add-sierpinski. The dots in its body suggest a combination of the scenes.

```
; Image Posn Posn Posn -> Image
; generative adds the triangle (a, b, c) to s,
; subdivides it into three triangles by taking the
; midpoints of its sides; stop if (a, b, c) is too small
(define (add-sierpinski scene0 a b c)
  (cond
    [(too-small? a b c) scene0]
    [else
     (local
       ((define scene1 (add-triangle scene0 a b c))
        (define mid-a-b (mid-point a b))
        (define mid-b-c (mid-point b c))
        (define mid-c-a (mid-point c a))
        (define scene2
          (add-sierpinski scene0 a mid-a-b mid-c-a))
        (define scene3
          (add-sierpinski scene0 b mid-b-c mid-a-b))
        (define scene4
          (add-sierpinski scene0 c mid-c-a mid-b-c)))
      ; ---IN---
      (... scene1 ... scene2 ... scene3 ...)))]
```

# Figure 191: Accumulators as results of generative recursions, a skeleton

# **Exercise 525.** Tackle the wish list that the skeleton implies:

```
; Image Posn Posn Posn -> Image
; adds the black triangle a, b, c to scene
(define (add-triangle scene a b c) scene)
```

```
; Posn Posn Posn -> Boolean
; is the triangle a, b, c too small to be divided
(define (too-small? a b c)
  #false)
```

```
; Posn Posn -> Posn
; determines the midpoint between a and b
```