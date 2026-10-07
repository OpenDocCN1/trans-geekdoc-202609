# Evaluating Regression Models Performance

# 2.7.1 R Squared
[Compare models w.r.t R$^2$]

We talked about the simple linear regression built through the ordinary least squares method where we are minimizing
$\sum(Y_i - \hat{Y}_i)^2$

We were counting that sum and the line that has smallest sum will be the best fitting line or will be this simple linear regression model.

Residual sum of squares: For out fitted-line (model line) the residual sum of squares $SS_{res}$ or sum of squared error is : 
$SS_{res} = \sum_{i=1}^n (Y_i - \hat{Y}_i)^2$

![](bbox=[0.438, 0.293, 0.893, 0.643])

Total sum of squares: Using the average line we get the total sum of squares: 
$SS_{tot} = \sum_{i=1}^n (Y_i - Y_{avg})^2$

R-square: The following equation is the R-squared
$R^2 = 1 - \frac{SS_{res}}{SS_{tot}}$

> R-square says that "How the best fitting line (or model) is with respect to the average line". Minimizing $SS_{res}$ to maximize the $R^2$, $R^2 = 1$ is the best scenario (and will never happen you!).

> So $R^2$ near 1 is better model and 0 is the bad model. $R^2$ can also be negative (model is worse than the average line).

# 2.7.2 Adjusted $R^2$
[Compare models w.r.t $R^2$ and Increase/Decrease Feature variable]

We talked about $R^2$ for a Simple Linear Regression while the same concepts apply for a multiple linear regression. We R-squared as a goodness of fit parameters, the bigger it is (close to 1) the better the model.

Impact on Increase/Decrease of feature variables: $R^2$ is biased. Reason: when we add new feature variable. $SS_{res}$ always decreases or stays. The $SS_{res}$ doesn't increase because of the model, if new variable effect in the negative way, the co-efficient of the variable get just smaller, so that the effect to be negligible.