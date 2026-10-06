# Basics: Gaussian Bayes rules

Bayes rule for Gaussian distribution:

+   - Marginal: $p(oldsymbol{x}) = \mathcal{N}(oldsymbol{x}|oldsymbol{\mu}_{oldsymbol{x}}, oldsymbol{\Sigma}_{oldsymbol{x}})$
- Conditional: $p(\mathbf{y}|oldsymbol{x}) = \mathcal{N}(\mathbf{y}|Foldsymbol{x}, \sigma_y^2 I)$

+   - Gaussian Bayes Rule 2: The posterior $p(oldsymbol{x}|\mathbf{y})$ is Gaussian with
  - Mean: $\mu_{oldsymbol{x}|\mathbf{y}} = oldsymbol{\mu}_{oldsymbol{x}} + (\sigma_y^2 \mathbf{I} + oldsymbol{\Sigma}_{oldsymbol{x}}F^T F)^{-1} oldsymbol{\Sigma}_{oldsymbol{x}}F^T(\mathbf{y}-Foldsymbol{\mu}_{oldsymbol{x}})$
  - Covariance: $oldsymbol{\Sigma}_{oldsymbol{x}|\mathbf{y}} = (oldsymbol{\Sigma}_{oldsymbol{x}}^{-1} + \sigma_y^{-2} F^T F)^{-1} \sigma_y^2(\sigma_y^2 \mathbf{I} + oldsymbol{\Sigma}_{oldsymbol{x}}F^T F)^{-1} oldsymbol{\Sigma}_{oldsymbol{x}}$

+   - Derivation: Use following identities for Bayes rule 1 from the matrix cookbook...
  - Use identity $\mathbf{A}(\mathbf{I} + \mathbf{BA})^{-1} = (\mathbf{I} + \mathbf{AB})^{-1}\mathbf{A}$ for the mean (Searl identity)
  - Use identity $(\mathbf{A} + \mathbf{BC}^T)^{-1} = \mathbf{A}^{-1} - \mathbf{A}^{-1}\mathbf{C}(\mathbf{B}^{-1} + \mathbf{C}^T\mathbf{A}^{-1}\mathbf{C})^{-1}\mathbf{C}^T\mathbf{A}^{-1}$ for the covariance (Woodbury identity)