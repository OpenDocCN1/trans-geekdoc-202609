# Table 28.11: Random effects (RE) model.

```
. xtreg return beta
```

Random-effects GLS regression
Group variable: firm_ident

Number of obs = 8,846
Number of groups = 1,729

R-sq:
  within = 0.0012
  between = 0.0001
  overall = 0.0000

Obs per group:
  min = 1
  avg = 5.1
  max = 11

corr(u_i, X) = 0 (assumed)

Wald chi2(1) = 2.80
Prob > chi2 = 0.0944

| return | Coef. | Std. Err. | z | P>|z| | [95% Conf. Interval] |
|---|---|---|---|---|---|
| beta | -.0054027 | .0032305 | -1.67 | 0.094 | -.0117344 | .0009289 |
| _cons | .0063386 | .0036912 | 1.72 | 0.086 | -.000896 | .0135733 |
| sigma_u | .02854326 |  |  |  |  |  |
| sigma_e | .05077864 |  |  |  |  |  |
| rho | .24010397 (fraction of variance due to u_i) |  |  |  |  |  |

# Table 28.12: LM test of random effects.

```
. xttest0
```

Breusch and Pagan Lagrangian multiplier test for random effects

return[firm_ident,t] = Xb + u[firm_ident] + e[firm_ident,t]

Estimated results:

|  | Var | sd = sqrt(Var) |
|---|---|---|
| return | .0027362 | .0523089 |
| e | .0025785 | .0507786 |
| u | .0008147 | .0285433 |

Test: Var(u) = 0
chibar2(01) = 1.54
Prob > chibar2 = 0.1072