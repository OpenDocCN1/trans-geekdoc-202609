# 4.4 Intervals

Imagine yourself responding to the following sample design task:

**Sample Problem** Design a program that simulates the descent of a UFO.

After a bit of thinking, you could come up with something like figure 22. Stop! Study the definitions and replace the dots before you read on.

```
; A WorldState is a Number.
; interpretation number of pixels between the top and the UFO
(define WIDTH 300) ; distances in terms of pixels
(define HEIGHT 100)
(define CLOSE (/ HEIGHT 3))
(define MTSCN (empty-scene WIDTH HEIGHT))
(define UFO (overlay (circle 10 "solid" "green") ...))

; WorldState -> WorldState
(define (main y0)
  (big-bang y0
    [on-tick nxt]
    [to-draw render]))

; WorldState -> WorldState
; computes next location of UFO
(check-expect (nxt 11) 14)
(define (nxt y)
  (+ y 3))

; WorldState -> Image
; places UFO at given height into the center of MTSCN
(check-expect (render 11) (place-image UFO ... 11 MTSCN))
(define (render y)
  (place-image UFO ... y MTSCN))
```

Figure 22: UFO, descending

Before you release this “game” program, however, you may wish to add the display of the status line to the canvas:

**Sample Problem** Add a status line. It says “descending” when the UFO’s height is above one third of the height of the canvas. It switches to "closing in" below that. And finally, when the UFO has reached the bottom of the canvas, the status notifies the player