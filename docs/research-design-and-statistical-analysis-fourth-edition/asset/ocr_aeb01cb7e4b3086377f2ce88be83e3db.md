# Inference, Assumptions, and Power in Multiple Regression 577

$\alpha = .05$. In the TC case, we are not justified in testing any of the mental health measures on their own, because they failed to reach significance as a group. The logic of this extends Fisher's t test (Fisher, 1935) to multiple regression analyses (Cohen et al., 2003).

Fisher's protected t procedure applied to ANOVA is as follows. First test for the significance of a categorical independent variable with $a$ levels using $\alpha$ as the significance level. If the overall test is significant, then each of $(a-1)/2$ pairwise comparisons between the levels of the variable may be tested at significance level $\alpha$. Tests of the individuals are said to be “protected” by the overall test. If the overall test is not significant, we are not allowed to perform significance tests on any of the pairwise comparisons in the set (unless, presumably, specified them $a priori$). As applied to multiple regression, a significant $R^2$ or increment in $R^2$ for a meaningful set of predictors would allow us to look at the significance tests for each of the regression coefficients in the set the same level of significance. If the overall test for the set of predictors is not significant, we cannot consider the tests for the individual predictors in the set, no matter how large their $t$ statistics might be. This means that the researcher must resist the temptation to rely on the regression output provided by software, which routinely includes a value of $t$ for each of the predictor variables. Instead, those individual test results must be reviewed only after a statistically significant family-wise assessment.

The hierarchical strategy inherent in defining predictor variables has limitations. Most obviously, if no related sets of predictors are included in the regression analysis, then no families of predictors can be identified. Additionally, the Fisher protected test does not completely control Type 1 error in ANOVA when the independent variable has more than three levels (Hayter, 1986), and Cohen et al. (2003) acknowledge some problems with this procedure. Nevertheless, the modified Fisher procedure acknowledges the issue of inflation of Type 1 error in multiple regression and offers an easily applied, imperfect, control for it.

# 21.6 Inferences About the Predictions of Y

In some situations, the goal of a regression analysis is to make predictions. For example, a university admissions office might want to know the expected year GPA for all students entering the university with a high school GPA of 3.0. In this case, we would want to get a confidence interval on the predicted mean university GPA for all students with a high school GPA of 3.0. Alternatively, an individual student with a high school GPA of 3.0 might want to estimate her first year GPA.

In bivariate regression, the expected value of Y corresponding to a value $X$, of $X$ is given by $\mu_{Y,X} = eta_0 + eta_1X_i$, which can be estimated by $\hat{Y}_i = \hat{\mu}_{Y,X_i} = b_0 + b_1X_i$. We showed in Chapter 19 that bivariate regression, the estimated standard error associated with the prediction of $Y$ at $X=X$, is given

```
$SE(\hat{\mu}_{Y,X}) = s_e\sqrt{b_{jj}}$
```

and that the standard error with an individual score is

```
$SE(\hat{Y}_i) = s_e\sqrt{1+b_{jj}}$
```