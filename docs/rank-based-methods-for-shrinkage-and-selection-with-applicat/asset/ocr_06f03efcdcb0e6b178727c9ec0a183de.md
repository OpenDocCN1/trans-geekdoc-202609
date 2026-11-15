```
$$\hat{\boldsymbol{\beta}}_n^{\text{EnetR}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ D(\boldsymbol{\beta}) + \lambda_1 \sum_{j=1}^p |\beta_j| + \lambda_2 \sum_{j=1}^p \beta_j^2 \right\}, \quad (8.7.2)$$
```

where \(\lambda_1\) is the LASSO penalty parameter for penalizing the sum of the absolute values of the regression coefficients and \(\lambda_2\) is the ridge penalty parameter for penalizing the sum of the squared regression coefficients, respectively.

**MNET** Huang et al. (2016) introduced the MNET estimation which use MCP penalty term instead of the \(L_1\)-penalty in (8.7.2). The Mnet R-estimator is defined as

```
$$\hat{\boldsymbol{\beta}}_n^{\text{MnetR}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ D(\boldsymbol{\beta}) + \sum_{j=1}^p \rho(|\beta_j|; \lambda_1) + \lambda_2 \sum_{j=1}^p \beta_j^2 \right\}.$$
```

Similar to the Enet of Zou and Hastie (2005) the MNET also tends to select or drop highly correlated predictors together. However, unlike the Enet, the MNET is selection consistent and equal to the oracle ridge estimator with high probability under reasonable conditions.

# ## 8.7.2 Performance Analysis

The performance of any of the methods described above is assessed by the bootstrapped prediction error criteria. The average prediction errors are calculated via five-fold CV for each bootstrap replicate.

In order to construct the suggested methods, we consider a two-step approach here since the prior information is not available as long as there is no one who knows which predictor explains significantly the response variable. In the first step, a candidate sub-model may be selected with the help of step-wise or subset selection procedures and a model selection criteria. Here, we used the forward selection method to pick important covariates. It shows that the variables of AGE, S3 and S6 may be ignored and the other variables can be used a sub model. Hence, in the second step, the suggested methods can be constructed by using this candidate sub-model.

We consider the unknown regression parameters, with the aid of the forward selection method, to be

```
$$\boldsymbol{\beta}_{\text{true}} = (0, -11.3, 25.2, 15.9, -29.3, 16.8, 0, 6.4, 33.6, 0)^\top,$$
```

as the true parameters in the bootstrap method. In the following, \(K\)-fold cross validation is used to obtain an estimate of the prediction errors of the model. In a \(K\)-fold cross validation, the data set is randomly divided into \(K\) subsets of