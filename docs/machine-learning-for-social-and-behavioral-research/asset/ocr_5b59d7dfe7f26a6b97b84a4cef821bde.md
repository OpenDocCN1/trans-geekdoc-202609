# Machine Learning with Mixed-Effects Models

+   - Regularization. The application of penalties to shrink coefficients in the model. See Chapter 4 for additional details.

+   - Decision trees. An algorithm that recursively partitions values of covariates in order to place observations in hierarchically clustered groups. See Chapter 5 for additional details.

# 9.2 Mixed-Effects Models

The linear mixed-effects model can be written as

```
$y_{ij} = x_{ij}\beta_p + z_{ij}u_{ij} + e_{ij} \quad (9.1)$
```

where $y_{ij}$ is the observed outcome score for observation $i$ in cluster $j$, $x_{ij}$ is the $p$th predictor variable for observation $i$ in cluster $j$, $eta_p$ is the $p$th fixed effects parameter, $z_{ij}$ is the $q$th predictor variable for observation $i$ in cluster $j$, $u_{ij}$ is the $q$th random effect for cluster $j$, and $e_{ij}$ is the residual for observation $i$ in cluster $j$. The q random effects are not estimated, but assumed to follow a multivariate normal distribution with a mean of 0 and unknown variance-covariance matrix. That is, $u_{ij} \sim N(0, G)$, where $G$ is a covariance matrix. Typically, the residuals $e_{ij}$ are assumed to follow a normal distribution with a mean of 0 and an unknown variance. That is, $e_{ij} \sim N(0, R)$, where $R$ is equal to $I\sigma_e^2$. Lastly, the random effects are assumed to be uncorrelated with the random effects (i.e., $cov(e_{ij}, u_{ij}) = 0$).

As an example of a mixed-effects model, let's assume we're trying to predict mathematics achievement for students enrolled in schools from a student-level, teacher-rated externalizing behavior. Also, assume we allow each school to have a random effect for the intercept (random intercept) and a random effect for the slope for externalizing behavior (random slope). Such a model can be written as

```
$mathit_{ij} = (\beta_0 + u_{0j}) + (\beta_{10} + u_{10j})ext_{ij} + e_{ij} \quad (9.2)$
```

where $math_{ij}$ is the mathematics achievement score for student $i$ in school $j$ and $ext_{ij}$ is the externalizing behavior score for student $i$ in school $j$. In this model, $eta_0$ is the fixed effect for the intercept representing the mathematics achievement score across schools when $ext_{ij} = 0$, $u_{0j}$ is the random effect for the intercept for school $j$ which allows each school to have a different predicted level of mathematics achievement when $ext_{ij} = 0$, $eta_{10}$ is the average effect of externalizing behavior across schools, $u_{10j}$ is the random effect for externalizing behavior for school $j$, which allows each school to have a different slope for the association between externalizing