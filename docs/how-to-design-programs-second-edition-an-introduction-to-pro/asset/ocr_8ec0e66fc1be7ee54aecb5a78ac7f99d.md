```
[(and #true #false) "silver"]
[else "gold"])]
==
(cond
  [#false "silver"]
  [else "gold"]))
==
(cond
  [else "gold"]))
== "gold"
```

Like the first condition, the second one also evaluates to #false and thus the calculation proceeds to the third cond line. The else tells DrRacket to replace the entire cond expression with the answer from this clause.

**Exercise 48.** Enter the definition of reward followed by (reward 18) into the definitions area of DrRacket and use the stepper to find out **how** DrRacket evaluates applications of the function.

**Exercise 49.** A cond expression is really just an expression and may therefore show up in the middle of another expression:

```
(- 200 (cond [(> y 200) 0] [else y]))
```

Use the stepper to evaluate the expression for y as 100 and 210.

Nesting cond expressions can eliminate common expressions. Consider the function for launching a rocket, repeated in figure 20. Both branches of the cond expression have the same shape except as indicated with ...

```
(place-image ROCKET X ... MTSCN)
```