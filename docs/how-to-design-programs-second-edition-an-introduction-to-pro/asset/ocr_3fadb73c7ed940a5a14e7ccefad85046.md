# 32.2 Adding Accumulators

Once you have decided that an existing function should be equipped with an accumulator, take these two steps:

+   • Determine the knowledge that the accumulator represents, what kind of data to use, and how the knowledge is acquired as data.

For example, for the conversion of relative distances to absolute distances, it suffices to accumulate the total distance encountered so far. As the function processes the list of relative distances, it adds each new relative distance found to the accumulator’s current value. For the routing problem, the accumulator remembers every node encountered. As the path-checking function traverses the graph, it conses each new node on to the accumulator.

In general, you will want to proceed as follows.

+   1. Create an accumulator template:

```
; Domain -> Range
(define (function d0)
  (local (; Domain AccuDomain -> Range
          ; accumulator ...
          (define (function/a d a)
            ...))
    (function/a d0 a0)))
```

Sketch a manual evaluation of an application of function to understand the nature of the accumulator.

+   2. Determine the kind of data that the accumulator tracks.

Write down a statement that explains the accumulator as a relationship between the argument d of the auxiliary function/a and the original argument d0.

**Note** The relationship remains constant, also called **invariant**, over the course of the evaluation. Because of this property, an accumulator statement is often called an _invariant_.