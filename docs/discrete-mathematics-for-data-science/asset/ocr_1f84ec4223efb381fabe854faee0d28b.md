Similar to the Mean Absolute Error is the _Mean Squared Error_:

```
MSE = \frac{\sum_{i=1}^n (estimate_i - actual_i)^2}{n}
```

With MSE, squaring rids us of negative errors that offset positive errors when computing an average of errors.

The square root of the MSE makes the magnitude of the error consistent with the original data. Hence, this is called the _Root Mean Squared Error_.

```
RMSE = \sqrt{MSE}
```

# EXERCISES

+   1. List and explain the steps involved with performing K-fold cross-validation.

+   2. For sampling data, explain the purpose and application of a programming language's pseudo-random number generator.

+   3. Suppose that a business has the following advertising costs (A) and revenues (R, in $1000s) over the past eight quarters Q:

| Q | A | R |
|---|---|---|
| 1 | 10 | 93 |
| 2 | 12 | 90 |
| 3 | 12 | 94 |