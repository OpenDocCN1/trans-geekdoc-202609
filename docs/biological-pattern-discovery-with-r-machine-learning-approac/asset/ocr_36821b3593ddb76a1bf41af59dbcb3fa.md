selection approach using the L1 constraint. During learning, it minimises the sum of absolute coefficients [Tibshirani, 1996]. The L1 constraint used in Lasso is defined as below, where $s$ is a positive constant,

```
$$\sum_{i=0}^R |w_i| \leq s \quad (4.41)$
```

Based on this constraint, the objective function of Lasso is shown below, where $\lambda >0$ is a constant constraint and $d$ stands for the number of independent variables,

```
$O = |\mathbf{X}^t\mathbf{w} - \mathbf{y}|^2 + \lambda \sum_{i=0}^d |w_i| \quad (4.42)$
```

The L1 constraint effect is more stringent. For instance, suppose there are two variables, there are two regression coefficients, i.e., $w_1$ and $w_2$. Because $|w_1| + |w_2| \leq s$, if $|w_1|$ increases, $|w_2|$ decreases. Suppose $w_1$ and $w_2$ are positive. If $w_1$ increases by $\delta$, $w_2$ will be decreased because $w_2 = s - w_1$. The relationship between the old value of $w_2$ and the new value of $w_2$ is shown below,

```
$w_2^{new} \leq s - (w_1 + \\delta) < s - w_1 = w_2^{old} \quad (4.43)$
```

Because of the use of L1 constraint, when $w_1$ increases, the decreasing speed of $w_2$ in a Lasso model is faster than in a RLR model. This can be analysed using Figure 4.20(a). Suppose $w_2$ is fixed and suppose two types of the models have the same constraint constant $C$. The of $w_1$ from the RLR model and the Lasso model will have different strength, which are shown below,

```
$w_1^{Ridge} = \sqrt{s - w_2} = \sqrt{C} \nw_1^{Lasso} = s - w_2 = C \quad (4.44)$
```

It is no doubt that the following inequality is valid,

```
$w_1^{Ridge} = \sqrt{C} < C = w_1^{Lasso} \quad (4.45)$
```