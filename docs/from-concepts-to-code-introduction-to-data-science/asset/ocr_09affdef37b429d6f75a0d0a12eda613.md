![](bbox=[0.325, 0.178, 0.672, 0.348])

FIGURE 13.1: Scatter Plot with Line of Best Fit

$\epsilon_i \sim \mathcal{N}(0, \sigma^2)$

The normality assumption is not necessary for fitting the model, but it is a requirement in the statistical testing.

Next, let's look at the mathematical form for linear regression, which is stated for each observation $i$ and $p$ predictors:

$y_i = eta_0 + eta_1 x_{i1} + \dots + eta_p x_{ip} + \epsilon_i, \quad i=1, \dots, n$

where

+   - $y_i$ is the target for observation $i$
-* $eta_0$ is an intercept parameter
-* $eta_1, \dots, eta_p$ are slope parameters or $weights$
-* $x_{i1}, \dots, x_{ip}$ are predictors for observation $i$
-* $\epsilon_i$ is the error for observation $i$

In this setup, we assume that the target can be modeled by a linear combination of predictors. There is a linear equation for each observation, for a total of $n$ equations. There are $p-1$ unknown, represented by the weights $eta_0, eta_1, \dots, eta_p$, applied to each predictor. The weighted combination of predictors is an attempt to match the target value.

As a small example, imagine we have collected three observations $(1,2), (2,3), (3,5)$. There is one predictor, and the first observation has predictor value 1 and target value 2. Given this data, we can write three linear equations with two unknowns: