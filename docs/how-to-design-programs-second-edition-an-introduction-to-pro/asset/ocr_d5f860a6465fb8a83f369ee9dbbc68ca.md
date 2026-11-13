Now we take the diagram from above and extend it to the signatures with the additional inputs:

```
[List-of Number] Number (Number Number -> Number) -> Number
[List-of Posn] Image (Posn Image -> Image) -> Image
```

From this diagram, you can easily see that the two revised signatures share even more organization than the original two. Furthermore, the pieces that describe the base cases correspond to each other and so do the pieces of the sub-signature that describe the combination function. All in all there are six pairs of differences, but they boil down to just two:

+   1. some occurrences of Number correspond to Posn, and

+   2. other occurrences of Number correspond to Image.

So to abstract we need two variables, one per kind of correspondence.

Here then is the signature for fold2, the abstraction from exercise 252:

```
; [X Y] [List-of X] Y [X Y -> Y] -> Y
```

Stop! Make sure that replacing both parameters of the signature, X and Y, with Number yields the signature for pr* and that replacing the same variables with Posn and Image, respectively, yields the signature for im*.

The two examples illustrate how to find general signatures. In principle the process is just like the one for abstracting functions. Due to the informal nature of signatures, however, it cannot be checked with running examples the way code is checked. Here is a step-by-step formulation:

+   1. Given two similar function definitions, f and g, compare their signatures for similarities and differences. The goal is to discover the organization of the signature and to mark the places where one signature differs from the other. Connect the differences as pairs just like you do when you analyze function bodies.