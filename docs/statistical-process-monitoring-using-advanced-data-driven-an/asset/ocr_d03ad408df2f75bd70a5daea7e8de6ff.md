1, ..., p, which is an n-dimensional set of observations for one variable. The standardization can be either univariate or multivariate. The classical univariate approach is simply

```
$$\frac{\mathbf{x}_j - \hat{\mu}_j}{\hat{\sigma}_j},$$
```

for $\hat{\mu}_j$ and $\hat{\sigma}_j$ the sample mean and standard deviation of variable $j$, respectively, for $j = 1, \dots, p$. The classic multivariate approach is

```
$$\hat{\mathbf{\Sigma}}^{-1/2} (\mathbf{X} - \hat{\boldsymbol{\mu}}),$$
```

where $\hat{\mathbf{\Sigma}}$ is the estimated variance–covariance matrix, and $\hat{\boldsymbol{\mu}}$ is the estimated vector of means. Robust standardizations can also be considered, as in [8,9], and these utilize robust estimates of the mean and covariance.

When the variables are related, regardless of whether the relationship is linear or nonlinear, then the standardization method used can dramatically change which variables appear to be shifted. In other words, the shifted variables in the raw data may not be preserved in the transformed data. The stronger the relationship between two variables, the stronger the propagation of the fault from one variable to another can be. To illustrate, Fig. 3.1 shows two sets of three variables. The first set of variables, $\mathbf{x}_1$, $\mathbf{x}_2$, and $\mathbf{x}_3$, are linearly related and are simulated from a multivariate normal distribution with mean $\boldsymbol{\mu} = (0, 0, 0)'$ and covariance

```
$$\mathbf{\Sigma} = \begin{bmatrix} 1.00 & 0.15 & -0.30 \\ 0.15 & 1.00 & 0.85 \\ -0.30 & 0.85 & 1.00 \end{bmatrix} . \quad (3.1)$$
```

The second set of variables are nonlinearly related, governed by the following equation set, as introduced by [10]:

```
$$\mathbf{y}_1 = \mathbf{s} + \mathbf{e}_1, \quad \mathbf{y}_2 = \mathbf{s}^2 - 3\mathbf{s} + \mathbf{e}_2, \quad \mathbf{y}_3 = -\mathbf{s}^3 + 3\mathbf{s}^2 + \mathbf{e}_3, \quad (3.2)$$
```

where the noise factors are $\mathbf{e}_1, \mathbf{e}_2, \mathbf{e}_3 \sim N(\mathbf{0}, 0.01 \times \mathbf{I})$ with $\mathbf{I}$ a $3 \times 3$ identity matrix and underlying latent factor $\mathbf{s} \sim \text{Unif}(0.01, 2)$. 

A fault is introduced at the vertical dashed line in Figs. 3.2 and 3.3. For the linearly related variables, Fig. 3.2 shows a strong drift fault in the first variable, and in the second column wherein a multivariate standardization has been applied to the data, a slight drift is also apparent in both $\mathbf{x}_2$ and $\mathbf{x}_3$. The first variable is most strongly correlated with the third, so a stronger drift is observed in $\mathbf{x}_3$ versus $\mathbf{x}_2$. However, no such contamination of $\mathbf{x}_2$ and $\mathbf{x}_3$ is present for the univariate standardization. Similarly, Fig. 3.3 shows a sharp downward shift in the second variable of the nonlinearly related variable set. In the multivari-