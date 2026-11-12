# # Absolute error loss function

Absolute error loss is the difference between the predicted and actual values, irrespective of the sign. It is also known as L1 loss and is given as follows:

```
L = |t - p|
```

Example 4: Let us consider the following instances shown in table 2.6 and find the absolute error loss:

| S.No. | Targeted value (t) | Predicted value (p) | Error | Absolute Error Loss |
|---|---|---|---|---|
| 1. | 4.5 | 3.4 | 4.5 - 3.4 = 1.1 | | 1.1 | = 1.1 |
| 2. | 1.5 | 2.1 | 1.5 - 2.1 = - 0.6 | | - 0.6 | = 0.6 |
| 3. | 11.4 | 12.1 | 11.4 - 12.1 = - 0.7 | | - 0.7 | = 0.7 |
| 4. | 13.3 | 10.2 | 13.3 - 10.2 = 3.1 | | 3.1 | = 3.1 |
| 5. | 11.0 | 12.0 | 11.0 - 12.0 = - 1.0 | | - 1.0 | = 1.0 |
| 6. | 10.9 | 14.2 | 10.9 - 14.2 = - 3.3 | | - 3.3 | = 3.3 |
| 7. | 8.5 | 7.3 | 8.5 - 7.3 = 1.2 | | 1.2 | = 1.2 |
| 8. | 11.2 | 9.8 | 11.2 - 9.8 = 1.4 | | 1.4 | = 1.4 |
| 9. | 10.2 | 11.1 | 10.2 - 11.1 = - 0.9 | | - 0.89 | = 0.89 |
| 10. | 9.0 | 7.5 | 9.0 - 7.5 = 1.5 | | 1.5 | = 1.5 |

Table 2.6: Absolute error loss calculation

The absolute error loss calculation is shown in table 2.6.

# # Huber loss

It is the combination of both mean square error and mean absolute error. It is quadratic in nature for small errors and linear for large errors. It is denoted by the delta parameter.

```
L_\delta = \{ 0.5(t - p)^2, \quad \text{if } |t - p| < \tau \\
\tau |t - p| - 0.5\tau^2, \quad \text{Otherwise}
```

where \(\tau\) is a parameter such that \(\tau \in \mathbb{R}^+\), and R is a real number.