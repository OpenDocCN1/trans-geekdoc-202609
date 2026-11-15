# 4 Analysis of Variance (ANOVA)

# 4.1 Introduction

An important model belonging to the class of general linear hypothesis is the analysis of variance (ANOVA) model. In this chapter, we consider the ANOVA model in its simplest form, namely, we collect p samples of differing sample sizes n1, ..., np from p dimensions,

```
F(y_{ij} - \theta_i), \quad j = 1, ..., n_i, \quad i = 1, ..., p
```

where \theta = (\theta_1, ..., \theta_p)^\top is the unknown vector of p treatment effects. In the traditional methodology, one tests the hypothesis of equality of p treatments, i.e.

```
\theta_1 = ... = \theta_p = \theta_0 \quad (\text{unknown}).
```

In our case, we attempt to discover a subset of treatments which contains significant treatments relative to the complimentary subset.

In this chapter, we consider (i) the unrestricted R-estimator, and (ii) the restricted R-estimator, along with some penalty estimators, namely, (iii) the subset selection rule, (iv) the LASSO-type, (v) the aLASSO-type, (vi) the ridge-type, and (vii) the elastic net-type estimators together with the traditional shrinkage estimators such as (viii) preliminary test, and (ix) the Stein–Saleh estimators in a nonparametric setup to study their asymptotic distributional L2-risk properties.

# 4.2 Model, Estimation and Tests

Consider the ANOVA model

```
Y = B\theta + \varepsilon, \quad (4.2.1)
```