# Regression With Qualitative and Quantitative Variables

a 0 on $X_{D2}$; scores at $A_2$ receive 0 on $X_{D1}$ and a 1 on $X_{D2}$; scores at $A_1$ receive values of 0 on both $X_{D1}$ and $\hat{X}_{D2}$. As we see in panel B of Table 23.1, the regression of $Y$ on $X_{D1}$ and $X_{D2}$ also produces a $SS_{regression}$ equal to the $SS_A$ obtained the standard ANOVA. Although the variance accounted for by the regression is the same whether we use dummy or effect coding, the regression coefficients are different. If we use dummy coding, the intercept, $b_{D0}$, takes on the value of the mean of the reference group (the group that has 0 on all the indicator variables). For example, in Table 23.1, the value of the intercept is equal to the mean of $A_1$. The regression coefficients for each of the dummy variables, $b_{D1}$ and $b_{D2}$, take on values equal to the differences between the group coded as 1 on the dummy variable and the mean of the reference group. We can see this by noting that because the regression accounts for all the between-group variability, the prediction for each score will be its mean.

For the scores at $A_1$, each dummy variable has the value 0 so that

```
$$\tilde{Y}_3 = b_{D0} + b_{D1}(0) + b_{D2}(0) = b_{D0}$
```

Therefore, $b_{D0} = 	ilde{Y}_3$. For scores at $A_1$, we have $\hat{Y} = \hat{Y}_1$. Substituting $X_{D1} = 1$, and $X_{D2} = 0$ into the equation for the regression of $Y$ on $X_{D1}$ and $X_{D2}$ we obtain

```
$$\hat{Y}_1 = b_{D0} + b_{D1}(1) + b_{D2}(0) = b_{D0} + b_{D1}$
```

Therefore, $b_{D1} = \hat{Y}_1 - b_{D0} = \hat{Y}_1 - 	ilde{Y}_3$. Similarly, for scores at $A_2$ we have

```
$$\hat{Y}_2 = b_{D0} + b_{D1}(0) + b_{D2}(1) = b_{D0} + b_{D2}$
```

so that $b_{D2} = \hat{Y}_2 - b_{D0} = \hat{Y}_2 - 	ilde{Y}_3$.

Dummy coding might be particularly useful if the design contains a control group. If so, we let the control group serve as the reference group, and the regression coefficients would then equal the differences between the treatment and control means. There are many other possible ways to code categorical variables. For example, categorical variables may be coded such that regression coefficients take on values of contrasts of possible interest. Detailed discussions of these methods may be found in sources such as Cohen et al. (2003).

No matter coding procedure is used to code a factor A, when the dependent variable $Y$ is regressed on the $a - 1$ dummy variables,

```
$SS_{between} = R_{Y,A}^2. SS_Y$
```

where $R_{Y,A}^2$ is the square of the multiple correlation when $Y$ is regressed on the $a - 1$ dummy variables that code factor A, and

```
$SS_{within} = SS_{S/A} = (1 - R_{Y,A}^2) SS_Y$
```

so that the test statistic for $A$ is given by

```
$F = \frac{R_{Y,A}^2 SS_Y / (a - 1)}{(1 - R_{Y,A}^2) SS_Y / (N - a)}$
```