so that we have $f(\boldsymbol{\beta}, E(\mathbf{r})) = \boldsymbol{\beta}' E(\mathbf{r})/\boldsymbol{\beta}'\boldsymbol{\beta} = \gamma_1$. For the second term, we have to find the second-order derivatives in the Hessian matrix $\boldsymbol{H}_{\hat{\beta}\hat{\beta}}$. The derivative of $f(\hat{\boldsymbol{\beta}}, \tilde{\mathbf{r}})$ with respect to $\hat{\beta}_i$ is

$$\frac{\partial f}{\partial \hat{\beta}_i} = \frac{1}{\boldsymbol{\beta}'\boldsymbol{\beta}} \tilde{r}_i - 2\frac{\hat{\boldsymbol{\beta}}'\tilde{\mathbf{r}}}{(\boldsymbol{\beta}'\boldsymbol{\beta})^2}\hat{\beta}_i.$$

The second order derivative of $f(\hat{\boldsymbol{\beta}}, \tilde{\mathbf{r}})$ with respect to $\hat{\beta}_i$ and $\hat{\beta}_j$ is

$$\frac{\partial f}{\partial \hat{\beta}_i \partial \hat{\beta}_j} = -2\frac{\hat{\boldsymbol{\beta}}'\tilde{\mathbf{r}}}{(\boldsymbol{\beta}'\boldsymbol{\beta})^2}\delta_{ij} - \frac{2}{(\boldsymbol{\beta}'\boldsymbol{\beta})^2}(\hat{\beta}_j\tilde{r}_i + \hat{\beta}_i\tilde{r}_j) + \frac{8\hat{\boldsymbol{\beta}}'\tilde{\mathbf{r}}}{(\boldsymbol{\beta}'\boldsymbol{\beta})^2}\frac{\hat{\beta}_i\hat{\beta}_j}{\boldsymbol{\beta}'\boldsymbol{\beta}},$$

where $\delta_{ij}=1$ if $i=j$ and zero otherwise. Evaluating the second-order derivatives at the point $\hat{\boldsymbol{\beta}}=\boldsymbol{\beta}$ and $\tilde{\mathbf{r}}=E(\mathbf{r})$, we find the matrix elements of the Hessian matrix:

$$\{\boldsymbol{H}_{\hat{\beta}\hat{\beta}}\}_{ij} = \left.\frac{\partial^2 f}{\partial \hat{\beta}_i \partial \hat{\beta}_j}\right|_{\substack{\hat{\beta}=\beta \\ \tilde{\mathbf{r}}=E(\mathbf{r})}} = -2\gamma_1\frac{\delta_{ij}}{\boldsymbol{\beta}'\boldsymbol{\beta}} + 4\gamma_1\frac{(\beta_i-\bar{\beta})(\beta_j-\bar{\beta})}{(\boldsymbol{\beta}'\boldsymbol{\beta})^2},$$

where we used $E(r_i)-\overline{E(r)} = \gamma_1(\beta_i-\bar{\beta})$ and $\boldsymbol{\beta}'E(\mathbf{r})/\boldsymbol{\beta}'\boldsymbol{\beta} = \gamma_1$. In matrix notation, we can write

$$\boldsymbol{H}_{\hat{\beta}\hat{\beta}} = -2\gamma_1\frac{1}{\boldsymbol{\beta}'\boldsymbol{\beta}}\mathbf{I} + 4\gamma_1\frac{1}{(\boldsymbol{\beta}'\boldsymbol{\beta})^2}\boldsymbol{\beta}\boldsymbol{\beta}',$$

where $\mathbf{I}$ is the identity matrix and $\boldsymbol{\beta}\boldsymbol{\beta}'$ is the matrix created by multiplication of the column vector $\boldsymbol{\beta}$ with the row vector $\boldsymbol{\beta}'$ (outer product).

We finally arrive at the approximation of the expected value of the slope estimator:

$$E[\hat{\gamma}_1] \approx \gamma_1\left(1 - \frac{E[\mathbf{u}'\mathbf{u}]}{\boldsymbol{\beta}'\boldsymbol{\beta}} + 2\frac{\boldsymbol{\beta}'E[\mathbf{u}\mathbf{u}']\boldsymbol{\beta}}{(\boldsymbol{\beta}'\boldsymbol{\beta})^2}\right).$$

Note that in the second term, we used the fact that we can rearrange

$$\mathbf{u}'\boldsymbol{\beta}\boldsymbol{\beta}'\mathbf{u} = \sum_{ij}(\beta_i-\bar{\beta})(\beta_j-\bar{\beta})(u_i-\bar{u})(u_j-\bar{u}) = \boldsymbol{\beta}'\mathbf{u}\mathbf{u}'\boldsymbol{\beta}.$$

The expected value $E[\mathbf{u}'\mathbf{u}]$ is a scalar:

$$E[\mathbf{u}'\mathbf{u}] = E\left[\sum_{i=1}^N (u_i-\bar{u})^2\right] = E\left[\frac{N-1}{N}\sum_{i=1}^N u_i^2 - \frac{1}{N}\sum_{\substack{i,j=1 \\ i\neq j}}^N u_i u_j\right]$$