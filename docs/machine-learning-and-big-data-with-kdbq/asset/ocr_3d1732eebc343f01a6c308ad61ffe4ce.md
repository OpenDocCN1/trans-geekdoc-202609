# Time Series Economics

(I) and consumption expenditure (C). The optimal number of lags is the number p such that the parameters $A_i 
eq 0, i \in [1, \dots, p]:

```
$$\begin{matrix} S_{t+p} & I_{t+p} & C_{t+p} \ S_{t+p+1} & I_{t+p+1} & C_{t+p+1} \ S_t & I_t & C_t \end{matrix} = \hat{v} + \hat{A}_1 \begin{matrix} S_{t+p-1} & I_{t+p-1} & C_{t+p-1} \ S_{t+p} & I_{t+p} & C_{t+p} \ \end{matrix} + \dots + \hat{A}_p \begin{matrix} S_t & I_t & C_t \ S_t & I_t & C_t \end{matrix}$
```

Given an upper bound M, the function .quantQ.ts.var[y;M] computes the likelihood ratio test statistic LR in (14.25) for $p=[1;M]$ and estimated p-value. The order p is significant at a 0.05 level if $lr(p) > q\chi_{95\%}(K^2)$. Based on the p-value, .quantQ.ts.var[d;4] shows that the optimal number of lags is 2.

| lr | pvalue |
|---|---|
| 0 | 14.47595 | 0.107063 |
| 1 | 4.32504 | -0.0794133 |
| 2 | 29.10602 | -0.0062164 |
| 3 | 22.597 | 0.00716978 |

We then forecast the three series (S, I and C) with a VAR(2) model and measure the precision of the estimation by computing an interval of confidence for the forecasted values. The function .quantQ.ts.ratios[y;p] computes the matrix of t-ratios (14.24) for a matrix of including data and lag p.

The result of .quantQ.ts.ratios[d;2] is

```
-0.9707203 -2.547745 0.2765425 1.446943 -1.285366 0.214387 1.4049
3.604272 1.37891 -1.021999 1.71015 1.577281 -0.141818 -0.006401993
3.66287 -0.0943528 2.013852 -1.941514 1.32533 3.243976 -0.1633211
```

The critical values of the t-distribution with $(3 \times 5) + (9 - 2) = 34$ degrees of freedom is around 2. The first column corresponds to the t-ratios of $
u$, the next three columns equate the t-ratios of $A_1$. The last columns are the t-ratios of $A_2$. The estimator of the VAR(2) model with the log-return times series data

```
var:quantQ.ts.var[d;2]
```

```
returns

0.01672199 -0.319631 0.1459888 0.961219 -0.1605511 0.114605
0.0943938
0.01577619 0.04393106 -0.1527319 0.2885016 0.00500384 0.01916576
-0.01202487
0.01292586 -0.00242666 0.2248127 -0.2963675 0.0388041 0.3549124
-0.02222032
```

It means that interest $\nu$, first parameter $A_1$, and second parameter $A_2$ are estimated as:

```
$$\begin{matrix} -0.015767199 & & -0.0319621 & 0.1459888 & 0.961219 \ \hat{v} = 0.01576719 & \hat{A}_1 = 0.04393106 & -0.1527319 & 0.2885016 \ 0.01292586 & & -0.002422666 & -0.2263675 \end{matrix}$
```