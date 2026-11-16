

1, ..., p, which is an n-dimensional set of observations for one variable. The standardization can be either univariate or multivariate. The classical univariate approach is simply

$$
\frac{\mathbf{x}_j - \hat{\mu}_j}{\hat{\sigma}_j},
$$

for $\hat{\mu}_j$ and $\hat{\sigma}_j$ the sample mean and standard deviation of variable $j$, respectively, for $j = 1, \dots, p$. The classic multivariate approach is

$$
\hat{\mathbf{\Sigma}}^{-1/2} (\mathbf{X} - \hat{\boldsymbol{\mu}}),
$$

where $\hat{\mathbf{\Sigma}}$ is the estimated variance–covariance matrix, and $\hat{\boldsymbol{\mu}}$ is the estimated vector of means. Robust standardizations can also be considered, as in [8,9], and these utilize robust estimates of the mean and covariance.

When the variables are related, regardless of whether the relationship is linear or nonlinear, then the standardization method used can dramatically change which variables appear to be shifted. In other words, the shifted variables in the raw data may not be preserved in the transformed data. The stronger the relationship between two variables, the stronger the propagation of the fault from one variable to another can be. To illustrate, Fig. 3.1 shows two sets of three variables. The first set of variables, $\mathbf{x}_1$, $\mathbf{x}_2$, and $\mathbf{x}_3$, are linearly related and are simulated from a multivariate normal distribution with mean $\boldsymbol{\mu} = (0, 0, 0)'$ and covariance

$$
\mathbf{\Sigma} = \begin{bmatrix} 1.00 & 0.15 & -0.30 \\ 0.15 & 1.00 & 0.85 \\ -0.30 & 0.85 & 1.00 \end{bmatrix} . \quad (3.1)
$$

The second set of variables are nonlinearly related, governed by the following equation set, as introduced by [10]:

$$
\mathbf{y}_1 = \mathbf{s} + \mathbf{e}_1, \quad \mathbf{y}_2 = \mathbf{s}^2 - 3\mathbf{s} + \mathbf{e}_2, \quad \mathbf{y}_3 = -\mathbf{s}^3 + 3\mathbf{s}^2 + \mathbf{e}_3, \quad (3.2)
$$

where the noise factors are $\mathbf{e}_1, \mathbf{e}_2, \mathbf{e}_3 \sim N(\mathbf{0}, 0.01 \times \mathbf{I})$ with $\mathbf{I}$ a $3 \times 3$ identity matrix and underlying latent factor $\mathbf{s} \sim \text{Unif}(0.01, 2)$. 

A fault is introduced at the vertical dashed line in Figs. 3.2 and 3.3. For the linearly related variables, Fig. 3.2 shows a strong drift fault in the first variable, and in the second column wherein a multivariate standardization has been applied to the data, a slight drift is also apparent in both $\mathbf{x}_2$ and $\mathbf{x}_3$. The first variable is most strongly correlated with the third, so a stronger drift is observed in $\mathbf{x}_3$ versus $\mathbf{x}_2$. However, no such contamination of $\mathbf{x}_2$ and $\mathbf{x}_3$ is present for the univariate standardization. Similarly, Fig. 3.3 shows a sharp downward shift in the second variable of the nonlinearly related variable set. In the multivari-

### Linearly Related Variables

### Non-linearly Related Variables

![](img/aa2f42c739937b682075082233e335bb_85_0.png)

FIGURE 3.1 Pairwise scatterplots of linearly (left) and nonlinearly (right) related variable sets, each from an IC process. On the left, the variables x1, x2, and x3 are simulated from a multivariate normal distribution, and on the right, a set of nonlinear equations is used to generate y1, y2, and y3.

In fact for the multivariate standardization, when the unique symmetric square-root is computed with the eigenvector-eigenvalue decomposition, it makes $\hat{\Sigma}^{-1/2}$ dense, so a fault affecting only one variable in the original data shifts the mean of all the variables. If the Cholesky factorization is used, a fault affecting variable $k$ shifts the mean of variables $k, k+1, ..., p$. Either way, the fault is not preserved in the original variable unless the fault occurs in only variable $p$, and the Cholesky factorization is used to obtain $\hat{\Sigma}^{-1/2}$.

![](img/aa2f42c739937b682075082233e335bb_86_0.png)

FIGURE 3.2 Linearly related variables with a drift fault in x1 introduced at vertical dashed line (left). The center and right columns show the same variables after multivariate and univariate standardization, respectively.

### Original Non-linear Variables--Shift Fault

### Non-linear Variables---Multivariate Standardization

### Non-linear Variables--Univariate Standardization

![](img/aa2f42c739937b682075082233e335bb_87_0.png)

FIGURE 3.3 Nonlinearly related variables with a shift fault in y2 introduced at vertical dashed line (left). The center and right columns show the same variables after multivariate and univariate standardization, respectively.

## 3.1.2 Shortcomings of contribution plots/scores

A very common first approach to isolating the variables associated with a fault is to use contribution scores or plots that quantify the contribution of each variable to the monitoring statistic [11,12]. Then, those variables with the largest contribution are deemed shifted. With a small number of features and a single shifted variable, this approach is simple to implement and interpret, but it is not advisable for multiple reasons. First, contribution scores are subject to variable smearing. This occurs when variable i shifts, and its shift contaminates the contribution scores of all other variables. Secondly, even under IC conditions, the contributions of all variables are unequal, so misdiagnoses can occur when variables whose contributions are small under IC conditions still do not have the largest contribution in OC conditions.

We will show the variable smearing effect for the Q statistic, using notation adapted from [13]. First, the covariance of X is estimated with S = (1/(n-1))X'X. Then, principal component analysis (PCA) decomposes S as follows:

$$ \mathbf{S} = \mathbf{P}\mathbf{\Lambda}\mathbf{P}' + \tilde{\mathbf{P}}\tilde{\mathbf{\Lambda}}\tilde{\mathbf{P}}' = \hat{\mathbf{S}} + \tilde{\mathbf{S}}, $$

where \(\hat{\mathbf{S}} = \mathbf{P}\mathbf{\Lambda}\mathbf{P}'\); \(\tilde{\mathbf{S}} = \tilde{\mathbf{P}}\tilde{\mathbf{\Lambda}}\tilde{\mathbf{P}}'\); **P** is a matrix of size \(p \times l\) of eigenvectors termed principal loadings; \(\tilde{\mathbf{P}}\) is a matrix of size \(p \times (p-l)\) of eigenvectors termed residual loadings; \(l\) is the number of principal components (PCs) retained to explain the variability in **S**; and \(\mathbf{\Lambda}\) and \(\tilde{\mathbf{\Lambda}}\) are diagonal matrices containing the principal and residual eigenvalues, respectively. An individual measurement, \(\mathbf{x}_i\), can be rewritten as \(\mathbf{x}_i = \hat{\mathbf{x}}_i + \tilde{\mathbf{x}}_i = \mathbf{PP}'\mathbf{x}_i + \tilde{\mathbf{P}}\tilde{\mathbf{P}}'\mathbf{x}_i = \mathbf{Cx}_i + \tilde{\mathbf{C}}\mathbf{x}_i\), where \(\mathbf{C} = \mathbf{PP}'\) is the projection matrix into the principal component subspace (PCS), and \(\tilde{\mathbf{C}} = \tilde{\mathbf{P}}\tilde{\mathbf{P}}'\) is the projection matrix into the residual subspace (RS).

The Q statistic, also commonly known as the Squared Prediction Error (SPE), measures the goodness of fit in the lower dimensional model (i.e., \(l < p\)) via the squared norm of the residual vector, \(\tilde{\mathbf{x}}_i\), computed as

$$ Q = \|\tilde{\mathbf{x}}_i\|^2 = \mathbf{x}'_i\tilde{\mathbf{C}}\tilde{\mathbf{C}}\mathbf{x}_i = \mathbf{x}'_i\tilde{\mathbf{C}}\mathbf{x}_i = \|\tilde{\mathbf{C}}^{1/2}\mathbf{x}_i\|^2. $$

The contribution of a variable to the Q statistic is called that variable's *contribution score*, with variables with the largest contribution scores presumed to be those most likely to be shifted. The contribution scores for the Q statistic are

$$ c_j^Q = \left( \mathbf{d}'_j \tilde{\mathbf{C}} \mathbf{x}_i \right)^2 , $$

where \(\mathbf{d}_j\) is a vector of zeroes of length \(p\) except for a one in the \(j\)th row and is referred to as the direction vector.

Now, consider that variable \(j\) is shifted, resulting in a faulty measurement with \(\mathbf{x}_i = \mathbf{x}^*_i + \mathbf{d}_j\delta\), where \(\mathbf{x}^*_i\) is the fault-free part of the measurement, and \(\mathbf{d}_j\delta\) is the faulty part. The faulty part is composed of the fault direction, \(\mathbf{d}_j\), and \(\delta$ is

