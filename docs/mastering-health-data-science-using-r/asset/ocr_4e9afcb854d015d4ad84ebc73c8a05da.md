```
xlab = "Blood Lead Level", ylab = "Systolic Blood Pressure",
pch = 16)
```

![](bbox=[0.125, 0.245, 0.825, 0.465])

Despite our observations, we continue by fitting a simple linear regression model to explain the association between SBP and LEAD. The function lm(formula = y ~ x, data) fits a linear model in R. The first argument is the formula of the linear model: on the left-hand side of the ~ we put the outcome variable, and on the right-hand side we put the independent variable. When we have multiple independent variables, we separate them with a + (e.g., y~x1+x2). The output of this function is an lm object.

We can call the summary() function on this object to print a summary of the model, which includes the estimated coefficients, information about the residuals, the R-squared and adjusted R-squared values, and the F-statistic. Recall, that we previously used the summary() function to get summary statistics about a vector. This is an example of how multiple functions can have the same name. R figures out which summary() function to use by identifying that the argument we passed in is a lm object.

```
simp_model <- lm(formula = SBP ~ LEAD, data = nhanes_df)
summary(simp_model)
#>
#> Call:
#> lm(formula = SBP ~ LEAD, data = nhanes_df)
#>
```