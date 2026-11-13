```
; ShotWorld -> ShotWorld
(define (main w0)
  (big-bang w0
    [on-tick tock]
    [on-key keyh]
    [to-draw to-image])))

; ShotWorld -> ShotWorld
; moves each shot up by one pixel
(define (tock w)
  (cond
    [(empty? w) '()]
    [else (cons (subl (first w)) (tock (rest w)))]))

; ShotWorld KeyEvent -> ShotWorld
; adds a shot to the world if the space bar is hit
(define (keyh w ke)
  (if (key=? ke " ") (cons HEIGHT w) w))

; ShotWorld -> Image
; adds each shot y on w at (XSHOTS,y) to BACKGROUND
(define (to-image w)
  (cond
    [(empty? w) BACKGROUND]
    [else (place-image SHOT XSHOTS (first w)
                       (to-image (rest w)))]))
```

Figure 61: A list-based world program

Let’s start with the design of to-image. We have its signature, purpose statement, and header, so we need examples next. Since the data definition has two clauses, there should be at least two examples: ’() and a consed list, say, (cons 9 ’()). The expected result for ’() is obviously BACKGROUND; if there is a y-coordinate, though, the function must place the image of a shot at MID and the specified coordinate:

```
(check-expect (to-image (cons 9 ’()))
 (place-image SHOT XSHOTS 9 BACKGROUND))
```

Before you read on, work through an example that applies to-image to a list of two Shots. Doing so helps understand how the function works.

The fourth step is about translating the data definition into a template: