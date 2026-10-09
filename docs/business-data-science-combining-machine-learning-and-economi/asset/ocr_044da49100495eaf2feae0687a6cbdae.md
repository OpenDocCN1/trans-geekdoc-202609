There are many information criteria out there: AICc, AIC, BIC, and so on. All of these approximate the distance between a fitted model and “the truth” for different definitions of truth and using different analytic approximations. Since the IC measure a distance, you can apply them in model selection by choosing the model with minimum IC.

The most common is Akaike’s criterion,

```
$$\mathrm{AIC}=\mathrm{deviance}+2df, \qquad\qquad(3.6)$$
```

where the deviance is calculated $in-sample$ and the $df$ are your $model$ degrees of freedom.

For example, the $summary.glm$ output reports the following:

```
`\begin{aligned}\quad&\text{Null deviance:}\quad731.59\text{ on }1476\text{ degrees of freedom}\\\quad&\text{Residual deviance:}\quad599.04\text{ on }1451\text{ degrees of freedom}\\\quad&\text{AIC:}\quad651.04\end{aligned}`
```

Note again that the degrees of freedom in R output is “degrees of freedom left after fit”: $n-df$ in our terminology. Many statistics books recommend the model with smallest AIC.

In an MLE fit, the $df$ is simply the number of parameters in the model. More generally, it measures the correlation between $\hat{y}$ and $y$ — how much flexibility you have to make the model fit look like the observed data. For deep theoretical reasons,${ }^{6}$ the lasso, like for MLE models, has $df$ simply equal to the number of nonzero $\hat{\beta}_{j}$ at a given $\lambda$. This is *not* true for any other penalization cost function and is yet another advantage of lasso regression (for example, with ridge regression all coefficients will be nonzero, but $df$ will be less than the full model dimensions because the coefficients are shrunk toward zero). Hence, one can apply the AIC for lasso penalty selection by calculating the full-sample $\mathrm{gam}\lrr$ path and feeding the number of nonzero coefficients and the in-sample deviance into Equation 3.6. As usual, R has a function to do this.