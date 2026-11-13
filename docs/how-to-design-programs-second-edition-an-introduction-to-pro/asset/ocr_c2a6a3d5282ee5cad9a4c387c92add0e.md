This rule has the name cond_false.Here is cond_true:

```
(cond
    [#true answer-1]
    [condition2 answer2]
    ...)
== answer-1
```

The rule also applies when the first condition is else.

Consider the following evaluation:

```
(cond
    [(zero? 3) 1]
    [(= 3 3) (+ 1 1)]
    [else 3])
== ; by plain arithmetic and equals-for-equals
(cond
    [#false 1]
    [(= 3 3) (+ 1 1)]
    [else 3])
== ; by rule cond_false
(cond
    [(= 3 3) (+ 1 1)]
    [else 3])
== ; by plain arithmetic and equals-for-equals
(cond
    [#true (+ 1 1)]
    [else 3])
== ; by rule cond_true
(+ 1 1)
```

The calculation illustrates the rules of plain arithmetic, the replacement of equals by equals, and both cond rules.

# **Exercise 121.** Evaluate the following expressions step-by-step:

+   1. (+ (* (/ 12 8) 2/3)
+      (- 20 (sqrt 4)))