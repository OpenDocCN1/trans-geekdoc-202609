Therefore,

```
$var(\hat{Y}_i) = \sigma_e^2 b_{ij}^2$
```

And so the standard error for the mean of Y at $X_i$

```
$SE(\hat{Y}_i) = s_e \sqrt{b_{ij}^2}$
```

Finally, to derive the standard error of the residual of the $j$th case, $SE(e_j)$, we begin with

```
$e_i = Y_i - \hat{Y}_i = Y_i - \sum b_{ij} Y$
```

So

```
$var(e_i) = var(Y_i) + var(\sum b_{ij} Y) - 2cov(Y_i, \sum b_{ij} Y)$
```

The first term on the right-hand side of the equation is equal to $\sigma_e^2$. The second term equals $\sigma_e^2 b_{ij}^2$. The last term is equal to $-2\sigma_e^2 b_{ij}^2$ because $cov(Y_i, Y_j) = \sigma_e^2$ and $cov(Y_j, Y_{j'}) = 0$ for $j \neq j'$. Therefore, $var(e_i) = \sigma_e^2(1 - b_{ij}^2)$ and

```
$SE(e_i) = s_e \sqrt{1 - b_{ij}^2}$
```

# Exercises

+   19.1 [Using software for regression and prediction] Use statistical software to analyze the statistics class data (file statistics class data on the book's website).
a) Regression on pretest.
b) Write out the regression equation. What are the values of the standard errors for estimate for $b_0$ and $b_1$, and $SE(b_1)$?
c) Using the regression equation, estimate the mean of the population of final exam scores with a pretest score of (i) 24; (ii) 37. The 95% confidence interval for each of these population means.
d Based on your answers to (c), which estimate is more likely to be closer to the actual population value? Explain why, in terms of the leverages associated with the two preset values.
e) Find the 95% confidence interval for the final score of an individual student with a pretest score of 24.

+   19.2 [Testing assumptions using residuals] The data set $EX19\_2$ contains response time (Y) to a target on a screen as a function of intensity level (X); the intensity levels