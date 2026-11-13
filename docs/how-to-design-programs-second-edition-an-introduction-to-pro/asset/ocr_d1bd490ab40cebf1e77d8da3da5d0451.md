define functions that distinguish various situations:

sign(x) = \begin{cases} +1 \text{ if } x > 0 \\ 0 \text{ if } x = 0 \\ -1 \text{ if } x < 0 \end{cases}

This *sign* function distinguishes three kinds of inputs: those numbers that are larger than 0, those equal to 0, and those smaller than 0. Depending on the input, the result of the function is +1, 0, or -1.

You can define this function in DrRacket without much ado using a conditional expression:

```
(define (sign x)
  (cond
    [(> x 0) 1]
    [(= x 0) 0]
    [(< x 0) -1]))
```

After you click *RUN*, you can interact with *sign* like any other function:

```
> (sign 10)
1
> (sign -5)
-1
> (sign 0)
0
```

Open a new tab in DrRacket and start with a clean slate.

In general, a *conditional expression* has the shape

```
(cond
  [ConditionExpression1 ResultExpression1]
  [ConditionExpression2 ResultExpression2]
  ...
  [ConditionExpressionN ResultExpressionN])
```

This is a good time to explore what the *STEP* button does. Add *(sign -5)* to the definitions area and