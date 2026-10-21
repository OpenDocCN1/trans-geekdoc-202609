# Table 28.1: OLS estimates.

```
. regress c y
```

| Source | SS | df | MS |
|---|---|---|---|
| Model | 124.037966 | 1 | 124.037966 |
| Residual | 1.14964696 | 18 | .063869275 |
| Total | 125.187613 | 19 | 6.58882175 |

Number of obs = 20
F(1, 18) = 1942.06
Prob > F = 0.0000
R-squared = 0.9908
Adj R-squared = 0.9903
Root MSE = .25272

| c | Coef. | Std. Err. | t | P>|t| | [95% Conf. Interval] |
|---|---|---|---|---|---|
| y | .8228901 | .0186728 | 44.07 | 0.000 | .7836599 | .8621203 |
| _cons | 1.471811 | .4635378 | 3.18 | 0.005 | .4979544 | 2.445668 |

```
. estat vce
```

Covariance matrix of coefficients of regress model

| e(V) | y | _cons |
|---|---|---|
| y | .00034868 |  |
| _cons | -.00859101 | .21486729 |

# Table 28.2: Ramsey RESET test.

```
. estat ovtest
```

Ramsey RESET test using powers of the fitted values of c
Ho: model has no omitted variables
F(3, 15) = 2.38
Prob > F = 0.1100

of detecting all sources of bias in the model. From nonsample information (the nature of the data generating process), we know there is measurement error, and the DWH tests below support this. The power of tests is important and our knowledge of the particular data generating process we are modeling is critical in obtaining consistent and efficient estimates.

Next, consider IV to address the parameter bias (a result of the measurement error). IV estimates are for each of the following alternative instrument specifications:

+   (i) i_i
+   (ii) g_i
+   (iii) i_i and g_i