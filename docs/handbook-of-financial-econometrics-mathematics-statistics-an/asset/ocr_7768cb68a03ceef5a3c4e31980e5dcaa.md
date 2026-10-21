# LS using GMM with heteroskedasticity consistent standard errors.

```
. gmm (c-{B1}*y-{B0}), instruments(y)
```

Step 1
Iteration 0: GMM criterion Q(b) = 479.1339
Iteration 1: GMM criterion Q(b) = 8.715e-23
Iteration 2: GMM criterion Q(b) = 7.633e-32

Step 2
Iteration 0: GMM criterion Q(b) = 2.439e-30
Iteration 1: GMM criterion Q(b) = 2.439e-30

GMM estimation

Number of parameters = 2
Number of moments = 2
Initial weight matrix: Unadjusted
GMM weight matrix: Robust
Number of obs = 20

|  | Coef. | Robust Std. Err. | z | P>|z| | [95% Conf. Interval] |
|---|---|---|---|---|---|---|
| /B1 | .8228901 | .0205302 | 40.08 | 0.000 | .7826517 | .8631285 |
| /B0 | 1.471811 | .5383418 | 2.73 | 0.006 | .4166806 | 2.526942 |

Instruments for equation 1: y _cons

# GMM with instrument i and robust (heteroskedasticity consistent) standard errors.

```
. gmm (c-{B1}*y-{B0}), instruments(i)
```

Step 1
Iteration 0: GMM criterion Q(b) = 477.32698
Iteration 1: GMM criterion Q(b) = 1.561e-22
Iteration 2: GMM criterion Q(b) = 7.126e-31

Step 2
Iteration 0: GMM criterion Q(b) = 6.706e-30
Iteration 1: GMM criterion Q(b) = 4.294e-30

GMM estimation
Number of parameters = 2
Number of moments = 2
Initial weight matrix: Unadjusted
GMM weight matrix: Robust
Number of obs = 20

|  | Coef. | Robust Std. Err. | z | P>|z| | [95% Conf. Interval] |
|---|---|---|---|---|---|---|
| /B1 | .7904662 | .0200564 | 39.41 | 0.000 | .7511563 | .829776 |
| /B0 | 2.270704 | .5372718 | 4.23 | 0.000 | 1.21767 | 3.323737 |

Instruments for equation 1: i _cons