+   Ordinary least squares (OLS). The most common form of estimation in linear regression, OLS involves minimizing the sum of squared residuals.

+   Regularization, shrinkage, or penalized likelihood. An alternative form of estimation often used in regression to reduce the propensity to overfit or perform variable selection.

+   Variable selection. A common goal in statistics where alternative type of regression (regularization or stepwise) is used to remove predictor variables from the model.

+   Standardization. An important step when applying regularization, standardization involves transforming predictor variables to have a mean of 0 (centering) and standard deviation (scaling) of 1. This does not alter the relationship between variables can have a number of benefits for estimation.

+   Interaction. Testing for interactions (also referred to as moderation) in regression involves adding additional terms to the linear model, of a form $b_{12}X_1X_2$ to determine if the effect of $X_1$ varies across the values of $X_2$.

# 4.2 Linear Regression

Ordinary squares (OLS) regression has been, both historically and currently, the estimation method of choice for linear regression in the social and behavioral sciences. Particularly when the sample size is small and the number of predictors is not large, OLS will have the smallest standard errors and be unbiased, if the assumptions are met. However, it is increasingly common for researchers to have a larger number of predictors, along with the desire to make inferences into more than just a functional of predictors. In these cases, OLS no longer the best suited tool.

With respect to the assumptions of OLS and how to test these, we refer to one of the many exceptional regression textbooks (e.g. Cohen, Cohen, West, & Aiken, 2003; Darlington & Hayes, 2017). In many respects, the methods that we discuss have many of the same assumptions. In the rest of this chapter, we discuss various applications of regularization, and how this addresses a change from the desire to make inferences with respect to only a small number of initial variables to scenarios with a larger number of variables.

Switching from the context of a single continuous dependent variable, to an analysis with a binary, count, or multinomial requires a switch in the