# 546 Research and Statistical Analysis

![](bbox=[0.335, 0.098, 0.663, 0.273])

![](bbox=[0.335, 0.313, 0.663, 0.477])

```
$R_{Y,1}^2 = a + b$
$R_{Y,2}^2 = b + c$
$R_{Y,12}^2 = a + b + c$
$r_{Y(2|1)}^2 = c$
$r_{Y(1|2)}^2 = a$
```

**Figure 2.6** Representations of variability in the criterion Y, Y accounted for by uncorrelated and correlated predictor variables. (a) Uncorrelated predictors: Variables accounted for by $X_1$ and $X_2$ do not overlap so that $R_{Y,12}^2=r_{Y,1}^2+r_{Y,2}^2$ (b) Correlated predictors: Variables accounted by $X_1$ and $X_2$ overlap so that $R_{Y,12}^2$ is not the sum of $r_{Y,1}^2+r_{Y,2}^2$.

If the $p$ predictor variables in a multiple regression are mutually uncorrelated, $SS_{regression}$ can be partitioned into nonoverlapping components associated with each of the predictors. This situation typically occurs when we have a true experiment. Panel (a) of Figure 2.6 represents this situation: $X_1$ and $X_2$ overlap with $Y$ but not with each other, indicating that the variability in $Y$ collectively accounted for by $X_1$ and $X_2$ is the sum of variabilities accounted for separately by $X_1$ and $X_2$. In this situation,

```
$SS_{regression} = SS_{Y,1} + SS_{Y,2}$
```

where $SS_{Y,j} = r_{Y,j}^2 SS_Y$ and $r_{Y,j}$ is the correlation between $Y$ and $X_j$. Because for two predictors $SS_{regression} = R_{Y,12}^2 SS_Y$, it follows that when the predictors are uncorrelated,

```
$R_{Y,12}^2 = r_{Y,1}^2 + r_{Y,2}^2 = \sum r_{Y,j}^2$
```