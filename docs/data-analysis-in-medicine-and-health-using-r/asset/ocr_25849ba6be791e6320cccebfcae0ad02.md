# 9 Multinomial Logistic Regression

```
## weight:1 0.0260899 0.0142834 1.827 0.06776
## weight:2 0.0514503 0.0165054 3.117 0.00183 **
## totchol:weight:1 -0.0006015 0.0023804 -0.253 0.80052
## totchol:weight:2 -0.0051091 0.0028023 -1.823 0.06828 .
## --
## Signif. codes: 0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
##
## Names of linear predictors: log(mu[1]/mu[3]), log(mu[2]/mu[3])
##
## Residual deviance: 5473.004 on 816 degrees of freedom
##
## Log-likelihood: -2736.50 on 816 degrees of freedom
##
## Number of Fisser scoring iterations: 5
##
## Warning: Hauck-Donner effect detected in the following estimate(s):
## '(Intercept):1', '(Intercept):2'
##
## Reference group is level 3 of the response
```

The interaction term in our model showed p-values above 0.05 (p-values of 0.80 and 0.07, respectively). As the p-value is bigger than the level of significance at 5% and the value of regression parameters for the interaction terms are not clinically meaningful, we have decided not to use the model with an interaction term.

# 9.8 Inferences

For the inference, we will

+   - calculate the 95% CI (interval estimates)
- calculate the p-values (hypothesis testing)

There is no facility inside broom::tidy() function to generate confidence intervals for object with class vglm. Because of that we use the coef(), conf(o) and cind(o) functions to produce a rather nice table of inferences.

We are going to follow these steps:

+   - set the number of digits equal to 2 to limit the decimal numbers
- return the regression coefficients for all β as an object named b_fitlog2
- return the confidence intervals for all β as an object named ci_fitlog2
- combine the β and the corresponding 95% CIs