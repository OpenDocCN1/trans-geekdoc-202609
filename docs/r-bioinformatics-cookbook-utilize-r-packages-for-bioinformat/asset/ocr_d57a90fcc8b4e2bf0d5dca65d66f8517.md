```
## Multiple R-squared: 0.2641, Adjusted R-squared: 0.2096
## F-statistic: 4.846 on 2 and 27 DF, p-value: 0.01591
```

There are four blocks:

+   - **Model call:** This is a restatement of the function we called.
- **Residuals:** This is a set of measures of the distribution of the residuals. We'll look at this later.
- **Coefficients:** These are the terms of the equation and their statistics, meaning the intercept and the coefficient of each of the levels of the variables.
- **Estimate:** (computed values of those). We also see columns of statistics for each Model level statistics summary - some statistics that apply to the whole model

Let's start at the bottom and look at the model-level summary.

**Residual error** is a measure of how well the line fits the data. In essence, residual standard error is the average distance from each real data point to the line (the width forth), the bigger the residual error. If you look at the plots again with distances drawn in, the right area, you can see clearly that the residual standard error for the second model is much bigger than the first.

$R^2$ is another measure of how well the model fits the data. If you're thinking about the correlation coefficient here, you're in the right area. $R^2$ describes the proportion of variance in the values that can be explained by the values. It always falls between zero and one. A value closer to one is usually better, but it is very domain and dataset-dependent. With small biological datasets, we don't always see values close to one because of the noise of the system. The proper one to use in most cases is the adjusted R-squared.

The F statistic is an indicator of a relationship between the output and input values of the model. In effect, F-tests show how much better the relationship is in your model than a model where the relationship is completely random. Its ratio such that F is one, the relationship is no stronger than a random relationship. The further above it one, the more likely it is that there is a real relationship in the model. The p-value is the frequency at this size of F would occur in a random relationship with a similar dataset. With the other statistics, the significance of the actual size is dependent on the domain and data being analyzed.

Along with these model-level statistics, linear modeling with $lm()$ gives us a set of statistics per input variable (called here the coefficients and in that block). These measure the effect that each coefficient has on the output variable. Basically, a significant coefficient is one that has a non-zero slope and is an important determinant of the output value. $Estimate$ is the actual value of the coefficient from the model. These are given in the units of the data. $Std$. Error is a measure of the variability of the strength of the effect, so if some data points give more pronounced values at