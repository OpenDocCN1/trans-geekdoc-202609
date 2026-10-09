We then use interaction terms to fit $\mathbb{E}[y | d, x] = \alpha + d\gamma + x'\beta d$, so that the coefficient on $d$ (i.e., on selected) is the ATE estimate.

```
> linadj <- glm(doc_any_12m ~ selected*x, data=P)
> summary(linadj)
```

Coefficients:

| | Estimate | Std. Error | t value | Pr(>|t|) |
|---|---|---|---|---|
| (Intercept) | 0.570410 | 0.004562 | 125.040 | < 2e-16 *** |
| selected | 0.064230 | 0.006460 | 9.943 | < 2e-16 *** |
| xnumhh2 | -0.051951 | 0.010407 | -4.992 | 6.02e-07 *** |
| xnumhh3+ | -0.420160 | 0.199162 | -2.110 | 0.0349 * |
| selected:xnumhh2 | -0.025518 | 0.014173 | -1.801 | 0.0718 . |
| selected:xnumhh3+ | 0.272023 | 0.210619 | 1.292 | 0.1965 |

The new ATE estimate is 0.064, practically unchanged from the model that controlled for main effects of *numhh* but did not have the effect of *selected* change with *numhh*. As a general rule, when you have systematic covariate imbalance, I favor using this later “full-interaction” regression adjustment to the more simple control for confounders in Equation 5.6. Practitioners often use the simpler no-interaction model, but the full interaction model is more robust to heterogeneous (covariate-dependent) treatment effects. When there is a covariate that has a large effect on $y$, there is good reason to suspect that it also moderates the effect of $d$ on $y$.

The second problem with our earlier OHIE analysis is the possibility of dependence between observations due to the inclusion of multiple people from the same household in the study. Like covariate imbalance, this is a common issue in experiments. It turns out that linear (i.e., OLS) regression is *robust* to this type of misspecification: the regression parameter estimates, and the estimate for the ATE, will approach the truth even if you have dependent errors. However, the out-of-the-box standard error calculations will be wrong (and hence your confidence intervals will be wrong).

One way to correct this is to estimate effects on the household rather than person level. This is easy here because the treatment (*selected*) and covariates (*numhh*) are always constant across a household—we can just average the response and collapse across covariates to get a single household level ATE.9 The model is then

$\mathbb{E}[\bar{y} | d, x] = \alpha + d\gamma + x'\beta$. (5.8)