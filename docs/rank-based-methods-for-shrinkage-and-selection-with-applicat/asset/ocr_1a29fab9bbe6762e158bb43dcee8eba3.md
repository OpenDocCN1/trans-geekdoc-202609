# 6 Multiple Linear Regression Models

# 6.1 Introduction

This chapter considers rank-based shrinkage estimation for the non-orthogonal multiple linear model. This subject was studied extensively in Chapter 2 where the practical aspects for machine learning with penalized rank estimators were described. Here, we provide a theoretical treatment and investigate the comparative performance characteristics of the primary penalty estimators, namely, ridge, LASSO, elastic net and aLASSO, together with the restricted, unrestricted, preliminary test and Stein–Saleh-type R-estimators when the dimension of the parameter space is less than the dimension of the sample space. We use marginal distribution theory to evaluate the asymptotic distributional L2-risks of the R-estimators.

# 6.2 Multiple Linear Model and R-estimation

Consider the multiple regression model

$y = X\beta + \varepsilon$ (6.2.1)

where $y = (y_1, \dots, y_n)^T$ is the response vector, $X$ is an $n \times p (n > p)$ matrix of real numbers, and $\beta$ is a $p$-vector of regression coefficients. We assume the following conditions due to Jurečková (1971):
(i) $\varepsilon = (\varepsilon_1, \dots, \varepsilon_n)^T$ are i.i.d. components with c.d.f. $F$, having absolutely continuous p.d.f. $f$ with finite Fisher information

$0 < I(f) = \int_{-\infty}^{+\infty} \left( \frac{f'(x)}{f(x)} \right)^2 f(x) \, dx < \infty.$ (6.2.2)