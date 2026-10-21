Recent studies (Hansen, 2007; Greene, 2008) suggest using feasible generalized least squares (GLS) to estimate an efficient estimator, supposing that v_gt (t = 1,2,...,T) is serially correlated and X_gt (t = 1,...,T) is strictly exogenous.⁴ This latter restriction is not required when OLS is solely used as T approaches infinity. However, this exogeneity restriction might be violated if the treatment (policy intervention) has been applied time by time. For cases when the number of groups is large enough, Hansen (2007) suggests using Bootstrap to compute consistent standard errors. To reduce estimation errors in δ̂_gt, we can aggregate the equations over individuals, if M_gt is not large, and obtain the following equation (124.6):

```
$$\bar{Y}_{gt} = A_t + B_g + \mathbf{X}_{gt}\beta + \bar{\mathbf{Z}}_{gt}\gamma + v_{gt} + \bar{u}_{gt}. \tag{124.6}$$
```

We can estimate equation (124.6) by using a fixed effects method to draw a fully robust inference because the composite error, (v_gt + \bar{u}_{gt}), is weakly dependent.

# 124.1.2.3 Casual inference

DID has been widely used to estimate the treatment (casual) effect on the treated (exposed) group. Further, DID can be used to estimate the average treatment effect (ATE) or the casual effect in the population, if the following assumptions hold (Lechner, 2011).

# A1. Stable Unit Treatment Value Assumption (SUTVA)

The members of treated and control groups remain stable across repeated cross-sectional design. Therefore, one, and only one, of the potential outcomes of treatment (policy intervention) is observable for all members of the population (Rubin, 1977). Moreover, no relevant interactions between the members of the population are assumed. In other words, there is not a spillover effect among populations.

# A2. Exogeneity Assumption

The control variables in the DID analysis are not influenced by the treatment in both the pre- and post-treatment periods. If we relax this assumption, the results can be interpreted as DID only captures part of the causal effect, which was not already captured by the endogenous variable.

# A3. Treatment Unrelated to the Outcome at Baseline

Treatment is not related to the outcome of control group.