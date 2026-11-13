```
(define (si-render s)
  (cond
    [(aim? s) (... (aim-tank s) ... (aim-ufo s) ...)]
    [(fired? s) (... (fired-tank s) ... (fired-ufo s)
      ... (fired-missile s) ...)]))
```

The template contains nearly everything we need to finish our task. To complete the definition, we figure out for each cond line how to combine the values we have in order to compute the expected result. Beyond the pieces of the input, we may also use globally defined constants, for example, BACKGROUND, which is obviously of help here; primitive or built-in operations; and, if all else fails, wish-list functions, that is, we describe functions we wish we had.

Consider the first cond clause, where we have a data representation of a tank, that is, (aim-tank s), and the data representation of a UFO, that is, (aim-ufo s). From the first example in figure 32, we know that we need to add the two objects to the background scenery. In addition, the design recipe suggests that if these pieces of data come with their own data definition, we are to consider defining helper (auxiliary) functions and to use those to compute the result:

```
... (tank-render (aim-tank s)
   (ufo-render (aim-ufo s) BACKGROUND))
```

Here tank-render and ufo-render are wish-list functions:

```
; Tank Image -> Image
; adds t to the given image im
(define (tank-render t im) im)

; UFO Image -> Image
; adds u to the given image im
(define (ufo-render u im) im)
```

With a bit of analogy, we can deal with the second cond clause in the same way. Figure 33 shows the complete definition. Best of all, we can immediately reuse our wish-list functions, tank-render and ufo-render, and all we need to add is a function for including a missile in the scene. The appropriate wish-list entry is: