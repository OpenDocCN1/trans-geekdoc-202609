
0.196 and 0.414, respectively. Although both sets of analyses see a decrease in performance across training and test sets, the SEM model still has higher explained variance values. We note the large decrease in performance from assessment on the training set versus test set, particularly for Grit2 which saw the $R^2$ decrease by 0.312. This decrement can most likely be attributed to the large number of predictors, inflating the $R^2$ estimate in the training sample.

## 8.4 Using Latent Variables as Outcomes and Predictors

Given the large number of predictors used in the previous example, the next step is to determine if a dimension reduction, based on the theoretical formulation of the predictors, can improve our interpretation, and possibly our prediction of both Grit latent variables. More specifically, what is to be gained by modeling the latent structure of each of the five facets of personality? Diagrammatically, this is shown in Figure 8.4.

In this model, we are able to hone in on a smaller number of parameters, namely the regression coefficients from each of the personality latent variables to both Grit latent variables. The parameter estimates, both unstandardized and standardized, are displayed in Table 8.2.

In Table 8.2, it is clear that the conscientiousness latent variable is the most influential predictor of both Grit latent variables, with standardized coefficients of 0.57 and -0.2. As opposed to examining the influence of each indicator of the big five traits, we can now look at the specific contributions of each latent variable. What remains to see what is lost by modeling the latent structure to the predictors. First, our model evidenced mixtures of model fit, with an RMSE of 0.051, CFI and TTLI of 0.74 and 0.73, respectively. Secondly, the percentage of variance accounted for each of the Grit latent variables decreased from the model with manifest predictors. Our latent variable predictor formulation explained 45.8% and 60.2% of the variance in Grit latent variables, respectively, while the manifest formulation explained 48.7% and 63.8% (note that these values are different from those in the earlier example in the chapter, as we used a larger sample size for this analysis). To overcome this level of model misfit, while also attempting to improve our prediction of Grit, we will test the use of regularized SEM.

### TABLE 8.2. Parameter Estimates from the MIMIC Model with Personality Latent Variables and Demographics as Predictors

| outcome | predictor | est | se | F | std |
|---|---|---|---|---|--|
| grit1 | agree | -0.05 | 0.04 | 0.18 | -0.04 |
| grit1 | consc | 0.57 | 0.05 | 0.00 | 0.57 |
| grit1 | open | -0.16 | 0.05 | 0.00 | -0.12 |
| grit1 | extra | -0.01 | 0.03 | 0.68 | -0.01 |
| grit1 | neuro | -0.15 | 0.03 | 0.00 | -0.20 |
| grit1 | education | 0.03 | 0.02 | 0.19 | 0.04 |
| grit1 | urban | -0.03 | 0.05 | 0.24 | 0.04 |
| grit1 | gender | 0.06 | 0.04 | 0.14 | 0.09 |
| grit1 | engat | -0.02 | 0.05 | 0.73 | -0.02 |
| grit1 | age | 0.00 | 0.00 | 0.46 | 0.00 |
| grit1 | hand | -0.03 | 0.05 | 0.39 | -0.04 |
| grit1 | religion | 0.01 | 0.01 | 0.04 | 0.02 |
| grit1 | orientation | -0.04 | 0.02 | 0.09 | -0.05 |
| grit1 | race | -0.01 | 0.02 | 0.56 | -0.01 |
| grit1 | voted | 0.04 | 0.05 | 0.39 | -0.05 |
| grit1 | married | -0.01 | 0.04 | 0.77 | -0.02 |
| grit1 | familsize | 0.02 | 0.01 | 0.08 | 0.03 |
| grit2 | agree | 0.12 | 0.03 | 0.00 | 0.14 |
| grit2 | consc | -0.46 | 0.04 | 0.00 | -0.60 |
| grit2 | open | -0.21 | 0.04 | 0.00 | -0.12 |
| grit2 | extra | -0.07 | 0.02 | 0.00 | -0.12 |
| grit2 | neuro | 0.03 | 0.02 | 0.19 | 0.04 |
| grit2 | education | -0.06 | 0.02 | 0.00 | -0.10 |
| grit2 | urban | 0.01 | 0.02 | 0.62 | 0.62 |
| grit2 | gender | -0.08 | 0.03 | 0.01 | -0.14 |
| grit2 | engat | 0.11 | 0.05 | 0.00 | 0.20 |
| grit2 | age | -0.00 | 0.00 | 0.51 | -0.00 |
| grit2 | hand | 0.00 | 0.04 | 0.92 | 0.01 |
| grit2 | religion | -0.01 | 0.03 | 0.08 | -0.01 |
| grit2 | orientation | 0.04 | 0.02 | 0.10 | 0.06 |
| grit2 | race | -0.01 | 0.01 | 0.23 | -0.05 |
| grit2 | voted | -0.01 | 0.03 | 0.71 | -0.02 |
| grit2 | married | -0.03 | 0.03 | 0.29 | -0.06 |
| grit2 | familsize | -0.01 | 0.01 | 0.30 | -0.02 |

**FIGURE 8.4.** MIMIC model using latent variables for the five personality factors. Note that the demographic variables are not pictured.

![](img/5047f0f064e22688ceb5d0cdf3e964_227.png)

## 8.5 Can Regularization Improve Generalizability?

In Chapter 4, we looked at how the use of regularization, whether it be ridge, lasso, or any, can reduce the complexity of models and produce estimates that result in higher performance in holdout sets. Extending this to our prediction of latent factors, we have two avenues where we can explore the utility of regularization. The first is using regularized regression in the second step with predicting factor scores, and the second option is building regularization directly into our SEM estimation. This latter approach has been referred to as regularized SEM (Jacobucci, Grimm, & McArdle, 2016) or penalized likelihood for SEM (Huang et al., 2017). Equivalent in the results produced using the same type of regularization, there are different software implementations of these approaches. For our application, we will use the regsem package (Li, Jacobucci, & Ammerman, 2021).

### 8.5.1 Regularized SEM

As maximum likelihood estimation (MLE) is the most common form of estimation for SEM, RegSEM adds a penalty function to the MLE for structural equation models (SEMs)

$F_{regsem} = F_{ML} + \lambda P(), (8.1)$

where $\lambda$ is the regularization parameter and takes a value between zero and infinity. When $\lambda$ is zero, MLE is performed, and when $\lambda$ is infinity, all penalized parameters are shrunk to zero. $P()$ is a general function for summing the values of one or more of the model's matrices (i.e., a norm). Two common forms of $P()$ include $\|\cdot\|_1$, which penalizes the sum of the absolute values of the parameters, and ridge $\|\cdot\|_2$, which penalizes the sum of the squared values of the predictors. In comparison to regularized regression, where all predictors are typically penalized, in RegSEM it is more common to penalize only a subset of parameters. This takes place because there are dependencies between parameters in SEM, most notably the factor loadings and residual variances. Therefore, it is most typical to only penalize paths in SEM, either penalizing all or just a subset.

In our example, we may wish to penalize the regression parameters (which can be labeled r11-r621 for those regressed on Grit1, and r12-r622 for those regressed on Grit2) from the covariates to latent factors. In total, there are 124 regression parameters, each of which could be penalized with the justification that by shrinking their estimates, we may produce a more generalizable solution in the test sample. Using lasso penalties, the absolute value of these 124 parameters would be summed after being multiplied by the penalty $\lambda$, added to Equation 8.1, resulting in

$F_{lasso} = F_{ML} + \lambda * \begin{pmatrix} r11 \\ r21 \\ \vdots \\ r621 \\ r12 \\ \vdots \\ r622 \end{pmatrix} \quad (8.2)$

If we wished to perform ridge regularization, we could change the $l_1$ norm to the $l_2$. Additionally, many sparser alternatives are available (see Jacobucci, 2017, for more detail). Applying regularization to SEM carries with similar requirements as regression: the sequence of penalties must be selected as well as selecting a fit index to choose a final model. Very little research has gone into comparing fit indices, and that limited research supports the use of the Bayesian information criterion (Jacobucci et al., 2016; Huang et al., 2017). Alternatively, one could use cross-validation or bootstrapping, which is more computationally burdensome, but allows us to more explicitly test the model on a sample not used to estimate the model.

For our example, we used regularization for two purposes, to produce more generalizable $R^2$ estimates and the other to perform variable selection among regression coefficients. We used lasso penalties ranging from 0 to 0.19 (20 total) and the BIC.

**FIGURE 8.5.** BIC values using lasso SEM.

![](img/5047f0f064e22688ceb5d0cdf3e964_229.png)

In Figure 8.5 we can see that as the penalties increase, the BIC generally decreases. This sequence of penalties corresponds to changes in the regression coefficients, as displayed in Figure 8.6. In this figure, the penalty increases, there is mostly a monotonic shrinkage toward zero in coefficient size, with some parameters set to zero at low penalties, and some never reaching zero. In smaller models, it is typical to test a vector of penalties that results in a range of coefficients from the MLE (unpenalized estimates) to all coefficients set to zero. In our example, the large model size produced difficulties in reaching convergence at
