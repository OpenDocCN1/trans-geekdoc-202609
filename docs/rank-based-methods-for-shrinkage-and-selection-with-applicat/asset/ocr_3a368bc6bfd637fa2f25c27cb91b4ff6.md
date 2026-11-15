shrinking the previous estimates in each iteration by a factor less than 1 given by \((1 - 2\ell\lambda_2)\).

LASSO can be applied to log-likelihood logistic regression as follows:

\(J^{LLR-LASSO}(\boldsymbol{\beta}) = -\sum_{i=1}^n [y_i \log p_i + (1-y_i)\log(1-p_i)] + \lambda_1 \sum_{j=1}^p |\beta_j|\) (11.5.4)

where \(\lambda_1\) is the tuning parameter. The penalized estimates, \(\hat{\boldsymbol{\beta}}_n^{LLR-LASSO}\), are obtained by minimizing Eq. (11.5.4). The optimization technique to minimize Eq. (11.5.4) is gradient descent with a modified set of partial derivatives. The update equation to compute the new parameter values is given by

\(\boldsymbol{\beta}^{(t+1)} = \boldsymbol{\beta}^{(t)} - \ell \times [\mathbf{X}^\top(p(\mathbf{X}) - \mathbf{y}) + \lambda_1 \text{sgn}(\boldsymbol{\beta}^{(t)})].\) (11.5.5)

Similarly, to obtain \(\hat{\boldsymbol{\beta}}_n^{LLR-aLASSO}\), we minimize the objective function

\(J^{LLR-aLASSO}(\boldsymbol{\beta}) = -\sum_{i=1}^n [y_i \log p_i + (1-y_i)\log(1-p_i)] + \lambda_1 \sum_{j=1}^p \frac{|\beta_j|}{|\hat{\beta}_j^R|}.\) (11.5.6)

# 11.5.2 Rank-based Expressions

Ridge regression can be applied to rank-based logistic regression as follows,

\(J^{RLR-ridge}(\boldsymbol{\beta}) = D_n(\boldsymbol{\beta}) + \lambda_2 \boldsymbol{\beta}^\top \boldsymbol{\beta},\) (11.5.7)

and in expanded form, we have

\(J^{RLR-ridge}(\boldsymbol{\beta}) = \sum_{i=1}^n (y_i - f(\mathbf{x}_i^\top \boldsymbol{\beta})a_n(R_{n_i}(\boldsymbol{\beta})) + \lambda_2 \boldsymbol{\beta}^\top \boldsymbol{\beta}.\) (11.5.8)

The penalized rank estimates, \(\hat{\boldsymbol{\beta}}_n^{RLR-ridge}\), are obtained by minimizing Eq. (11.5.8). The optimization technique to minimize Eq. (11.5.8) is gradient descent but we will need a modified set of partial derivatives. For convenience, let us again define \(p_i = p(\mathbf{x}_i)\). Following the steps outlined earlier, we obtain

\(\frac{\partial J^{RLR-ridge}(\boldsymbol{\beta})}{\partial \beta_j} = -\sum_{i=1}^n p_i(1-p_i)x_{ij}a_n(R_{n_i}(\boldsymbol{\beta})) + 2\lambda_2 \beta_j.\) (11.5.9)

The update equation for each \(\beta_j\) to compute the new parameter values is given by

\(\beta_j^{(t+1)} = \beta_j^{(t)} - \ell \times \frac{\partial J^{RLR-ridge}(\boldsymbol{\beta})}{\partial \beta_j},\) (11.5.10)