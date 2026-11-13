```
(define (height.v2 abt0)
 (local (; Tree ??? -> N
          ; measures the height of abt
          ; accumulator ...
         (define (height/a abt a)
           (cond
             [(empty? abt) ...]
             [else
              (... (height/a (node-left abt)
                             ... a ...) ...)
              ... (height/a (node-right abt)
                            ... a ...) ...)])))
   (height/a abt0 ...)))
)
```

As always, the problem is to determine what knowledge the accumulator represents. One obvious choice is the number of traversed branches:

a is the number of steps it takes to reach abt from abt0.

Illustrating this accumulator invariant is best done with a graphical example. Take a second look at figure 184. The bottom-most tree comes with two annotations, each pointing out one subtree:

+   1. If abt0 is the complete tree and abt is the subtree pointed to by the circled 1, the accumulator’s value must be 1 because it takes exactly one step to get from the root of abt to the root of abt0.

+   2. In the same spirit, for the subtree labeled 2 the accumulator is 2 because it takes two steps to get to this place.

As for the preceding two examples, the invariant basically dictates how to follow the rest of the design recipe for accumulators: the initial value for a is 0; the update operation is add1; and the base case uses the accumulated knowledge by returning it. Translating this into code yields the following skeleton definition: