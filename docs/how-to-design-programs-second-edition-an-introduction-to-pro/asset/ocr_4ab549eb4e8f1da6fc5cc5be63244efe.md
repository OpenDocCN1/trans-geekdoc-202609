miles north from its starting point and 10 miles west after one hour of driving.
After two hours, it will be 120 miles north from the starting point and 20 miles
to its west.

As always, a function that consumes a structure instance can (and probably
must) extract information from the structure to compute its result. So once again
we add selector expressions to the function definition:

```
(define (ufo-move-1 u)
 (... (ufo-loc u) ... (ufo-vel u) ...))
```

**Note** The selector expressions raise the question whether we need to refine
this sketch even more. After all, the two expressions extract instances of Posn
and Vel, respectively. These two are also structure instances, and we could
extract values from them in turn. Here is what the resulting skeleton would look
like:

```
; UFO -> UFO
(define (ufo-move-1 u)
 (... (posn-x (ufo-loc u)) ...
 ... (posn-y (ufo-loc u)) ...
 ... (vel-deltax (ufo-vel u)) ...
 ... (vel-deltay (ufo-vel u)) ...))
```

Doing so obviously makes the sketch look quite complex, however. For truly
realistic programs, following this idea to its logical end would create incredibly
complex program outlines. More generally,

*If a function deals with nested structures, develop one function
per level of nesting.*

In the second part of the book, this guideline becomes even more important and
we refine it a bit. **End**

Here we focus on how to combine the given Posn and the given Vel in order
to obtain the next location of the UFO—because that’s what our physics
knowledge tells us. Specifically, it says to “add” the two together, where
“adding” can’t mean the operation we usually apply to numbers. So let us
imagine that we have a function for adding a Vel to a Posn: