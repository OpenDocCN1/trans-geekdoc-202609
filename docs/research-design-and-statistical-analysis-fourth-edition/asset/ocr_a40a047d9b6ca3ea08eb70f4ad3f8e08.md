# Chapter 22

# Additional Topics in Multiple Regression

# 22.1 Overview

If our goal is to maximize prediction accuracy, we should look at measures of fit such as $R$ or $R^2$ when we perform regression analyses. However, $R$ is not a reasonable measure for assessing the usefulness of explanatory models because it is not necessarily an index of causal effects, or is not comparable across samples. If our concern is with explanation or theory development, our goal is to understand the direct and indirect effects of the independent variables on the dependent variable of interest. Therefore, our focus should be on interpreting the regression coefficients. In Chapter 22, we discuss several issues that affect our ability to interpret regression coefficients. We introduced many of these issues in the three preceding chapters and we expand upon them here. The topics in Chapter 22 are as follows:

+   * The consequences of model mis-specification, either by omitting an important predictor or by including an extraneous variable.
* Measurement error and missing data.
* Multicollinearity, which occurs when predictor variables are completely or highly redundant.
* Direct vs indirect effects and mediating variables.
* Testing for curvlinearity.
* Testing for interactions between predictors.
* Distinguishing curvlinearity from interactions.
* Limitations of OLS regression, such as application to situations with dichotomous dependent variables or to designs in which variables are nested.

# 22.2 Specification Errors and Their Consequences

A regression equation is correctly specified if it contains the same variables as the true population model. Some properties of the population model

```
$Y_i = eta_0 + eta_1X_{i1} + eta_2X_{i2} + \dots + eta_pX_{ip} + \varepsilon_i$
```

are estimated by the coefficients of the sample regression equation,

```
$\hat{Y}_i = b_0 + b_1X_{i1} + b_2X_{i2} + \dots + b_pX_{ip}$
```