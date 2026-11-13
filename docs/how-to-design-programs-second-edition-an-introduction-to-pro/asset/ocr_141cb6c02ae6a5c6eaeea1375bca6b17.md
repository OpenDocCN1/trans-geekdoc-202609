```
`(define (blue-eyed-ancestor? an-ftree)
 (cond
  [(no-parent? an-ftree) #false]
  [else
   (or
    (blue-eyed-ancestor?
     (child-father an-ftree)))
    (blue-eyed-ancestor?
     (child-mother an-ftree)))])`)

```

Explain why this function fails one of its tests. What is the result of `(blue-eyed-ancestor? A)` no matter which `A` you choose? Can you fix your friend's solution?