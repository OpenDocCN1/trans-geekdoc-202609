# TABLE 9.4. Parameter Estimates from the Relaxed Lasso

| Parameter | Estimate (S.E.) | t-value | p-value |
|---|---|---|--|
| $\beta0$ | -1.39 (0.013) | -105.77 | < .001 |
| $\beta01$ (father's education) | 0.08 (0.002) | 36.61 | < .001 |
| $\beta02$ (poverty status) | 0.24 (0.01) | 18.01 | < .001 |
| $\beta10$ | 1.03 (0.003) | 390.76 | < .001 |
| $\sqrt{s00}$ | 0.16 | | |
| $\sqrt{s11}$ | -0.53 | | |
| $d_r$ | 0.24 | | |

# 9.6 Additional Strategies for Mining Longitudinal Data

In this chapter we focused on machine learning methods to examine cluster-level predictors in linear-effects models. We did not focus on methods that could explore the nature of the association between observation-level variables. For example, in our illustrative work we assumed a linear association between reading achievement and time in school. Two popular machine learning algorithms that can be used to explore associations between observation-level variables in a mixed-effects modeling context are piecewise splines models and generalized additive models.

# 9.6.1 Piecewise Spline Models

Piecewise spline models are a commonly applied algorithm in single-level data. With single-level data, splines are able to model nonlinear relationships between a predictor and outcome by partitioning the predictor and fitting a simple model (typically a linear model) within each partition. The type of function within each partition of the predictor variable is referred to as the *basis* function. In addition to specifying the basis function, researchers typically need to specify the location of the knot point, or point on the predictor variable where the functions join, and the number of knot points. Although these aspects of piecewise spline models are typically specified by the researcher, multivariate adaptive regression splines (MARS; Friedman, 1991) were developed to automate variable selection, as well as the number and location of knot points. Typically, linear basis functions are used; however, higher-level terms (e.g., squared terms and product terms) can be included when performing variable selection.
The piecewise spline model with linear segments can be written as