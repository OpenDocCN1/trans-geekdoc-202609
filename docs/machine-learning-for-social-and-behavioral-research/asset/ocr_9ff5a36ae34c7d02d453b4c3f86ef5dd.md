where X and Z are known design matrices, $eta$ is a matrix of fixed-effects parameters, $\Phi$ is the variance-covariance matrix for the random effects, $\sigma^2$ is the observation residual variance, $n$ is the sample size and I is an identity matrix. In the lasso mixed-effects models,

```
$$f_{lasso} = -ZLL\beta + \lambda\sum_{p=1}^P |\beta_p| \quad (9.6)$
```

where $\lambda$ is the penalty and $\Sigma_{p=1}^P$ is the sum of absolute values of the $P$ fixed-effects parameter estimates. As the penalty, $\lambda$, increases, the fixedeffects estimates shrink and will eventually be set to 0. If the penalty is 0, then the fixed-effects parameters are not penalized and the estimates are equal to those obtained through a standard mixed-effects modeling program. The value of $\lambda$ is varied from a low value to a high value, and an optimal value is often chosen through cross-validation (i.e., k-fold cross-validation) or through an index of model fit that accounts for model complexity (e.g., Bayesian information criterion).

# Software

There are multiple packages for incorporating regularization into mixed-effects models. Specific to our goals is the method developed by Scheldorfer, Bühlmann, and van Geer (2011) and implemented in the R package lmasso (Scheldorfer, 2011). For generalized linear mixed-effects models, there exists an extension (Scheldorfer, Meier, &hlmann, 2014) of the method developed by Scheldorfer et al. (2011) and implemented in the glmlasso package (Scheldorfer, 2012). We note that Groll and Tutz (2014) developed a similar approach, which is implemented in the glmLasso package (Groll, 2017), however, the fixed effects are penalized in this approach to random effects.

# 9.5 Illustrative Example

Longitudinal data are analyzed from the ECLS-K. Our goal is to determine whether this set of easily collected variables measured at the beginning of kindergarten can account for differences in the change trajectories for reading abilities assessed during the first two years of school.

The outcomes of interest are the reading theta scores based on the public use dataset. These scores are estimated ability based on the questions asked and answered by the children. These scores ranged -2.644 to 2.122 for the children assessed in kindergarten through first grade. Observing reading trajectories from a 1% random sample of children