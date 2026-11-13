where $\mu$ is the vector of expected (excess) returns. Taking $\mu = \mathbf{1}$ yields the minimum variance portfolio, which is agnostic in terms of the first moment of expected returns (and, as such, usually more robust than most alternatives which try to estimate $\boldsymbol{\mu}$ and often fail).

Usually, the traditional way is to estimate $\boldsymbol{\Sigma}$ and to invert it to get the MSR weights. However, several approaches aim at estimating $\boldsymbol{\Sigma}^{-1}$ *directly* and we present one of them below. We proceed one asset at a time, that is, one line of $\boldsymbol{\Sigma}^{-1}$ at a time. If we decompose the matrix $\boldsymbol{\Sigma}$ into:

$\boldsymbol{\Sigma} = \left[ \begin{array}{ c c } \sigma^2 & \mathbf{c}' \\ \mathbf{c} & \mathbf{C} \end{array} \right] ,$

classical partitioning results (e.g., Schur complements) imply

$\boldsymbol{\Sigma}^{-1} = \left[ \begin{array}{ c c } (\sigma^2 - \mathbf{c}'\mathbf{C}^{-1}\mathbf{c})^{-1} & -(\sigma^2 - \mathbf{c}'\mathbf{C}^{-1}\mathbf{c})^{-1}\mathbf{c}'\mathbf{C}^{-1} \\ -(\sigma^2 - \mathbf{c}'\mathbf{C}^{-1}\mathbf{c})^{-1}\mathbf{C}^{-1}\mathbf{c} & \mathbf{C}^{-1} + (\sigma^2 - \mathbf{c}'\mathbf{C}^{-1}\mathbf{c})^{-1}\mathbf{C}^{-1}\mathbf{c}\mathbf{c}'\mathbf{C}^{-1} \end{array} \right] .$

We are interested in the first line, which has 2 components: the factor $(\sigma^2 - \mathbf{c}'\mathbf{C}^{-1}\mathbf{c})^{-1}$ and the line vector $\mathbf{c}'\mathbf{C}^{-1}$. $\mathbf{C}$ is the covariance matrix of assets 2 to $N$ and $\mathbf{c}$ is the covariance between the first asset and all other assets. The first line of $\boldsymbol{\Sigma}^{-1}$ is

$(\sigma^2 - \mathbf{c}'\mathbf{C}^{-1}\mathbf{c})^{-1} \left[ \begin{array}{ c c } 1 & - \underline{\mathbf{c}'\mathbf{C}^{-1}} \\ & N-1 \text{ terms} \end{array} \right] .$ (5.9)

We now consider an alternative setting. We regress the returns of the first asset on those of all other assets:

$r_{1,t} = a_1 + \sum_{n=2}^N \beta_{1|n} r_{n,t} + \epsilon_t, \quad \text{i.e.,} \quad \mathbf{r}_1 = a_1 \mathbf{1}_T + \mathbf{R}_{-1} \beta_1 + \epsilon_1, \quad$ (5.10)

where $\mathbf{R}_{-1}$ gathers the returns of all assets except the first one. The OLS estimator for $\beta_1$ is

$\hat{\beta}_1 = \mathbf{C}^{-1}\mathbf{c}, \quad$ (5.11)

and this is the partitioned form (when a constant is included to the regression) stemming from the Frisch-Waugh-Lovell theorem (see chapter 3 in Greene (2018)).

In addition,

$(1 - R^2)\sigma^2_{\mathbf{r}_1} = \sigma^2_{\mathbf{r}_1} - \mathbf{c}'\mathbf{C}^{-1}\mathbf{c} = \sigma^2_{\epsilon_1} .$ (5.12)

The proof of this last fact is given below.

With $\mathbf{X}$ being the concatenation of $\mathbf{1}_T$ with returns $\mathbf{R}_{-1}$ and with $\mathbf{y} = \mathbf{r}_1$, the classical expression of the $R^2$ is

$R^2 = 1 - \frac{\epsilon' \epsilon}{T \sigma_Y^2} = 1 - \frac{\mathbf{y}'\mathbf{y} - \hat{\beta}\mathbf{X}'\mathbf{X}\hat{\beta}}{T \sigma_Y^2} = 1 - \frac{\mathbf{y}'\mathbf{y} - \mathbf{y}'\mathbf{X}\hat{\beta}}{T \sigma_Y^2} ,$