data definition; continue with the other one, using the first example where the clause refers to the definition itself. For the data definition in figure 51, you thus get lists like the following three:

```
' ()
(cons "a" ' () )         by the first clause
(cons "b"                 by the second clause, previous example
   (cons "a"
   ' () ))
```

If it is impossible to generate examples from the data definition, it is invalid. If you can generate examples but you can’t see how to generate increasingly larger examples, the definition may not live up to its interpretation.

2. Nothing changes about the header material: the signature, the purpose statement, and the dummy definition. When you do formulate the purpose statement, focus on what the function computes not how it goes about it, especially not how it goes through instances of the given data.

Here is an example to make this design recipe concrete:

```
; List-of-strings -> Number
; counts how many strings alos contains
(define (how-many alos)
 0)
```

The purpose statement clearly states that the function just counts the strings on the given input; there is no need to think ahead about how you might formulate this idea as a BSL function.

3. When it comes to functional examples, be sure to work through inputs that use the self-referential clause of the data definition several times. It is the best way to formulate tests that cover the entire function definition later.

For our running example, the purpose statement almost generates functional examples by itself from the data examples: