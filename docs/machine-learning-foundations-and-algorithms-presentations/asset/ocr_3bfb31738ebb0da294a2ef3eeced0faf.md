# Bayes Rule for obtaining denoising distribution

# Bayes Rule for denoising:

$q(\mathbf{x}_{t-1}|mathbf{x}_t, \mathbf{x}_0) = \frac{q(\mathbf{x}_t|\mathbf{x}_{t-1})q(\mathbf{x}_{t-1}|mathbf{x}_0)}{q(\mathbf{x}_t|\mathbf{x}_0)}$

# Gaussian Bayes Rule:

$p(\mathbf{x}) = \mathcal{N}(\mathbf{x}|oldsymbol{\mu}_x, oldsymbol{\Sigma}_x)$

$p(\mathbf{y}|\mathbf{x}) = \mathcal{N}(\mathbf{y}|\mathbf{F}\mathbf{x}, \sigma_y^2\mathbf{I})$

$$oldsymbol{\mu}_x = oldsymbol{\mu}_{t-1|0} = \sqrt{\alpha_t}\mathbf{x}_0, \quad oldsymbol{\Sigma}_x = oldsymbol{\Sigma}_{t-1|0} = (1-	ilde{\alpha}_t)\mathbf{I}$

$$oldsymbol{\mu}_{x|y} = oldsymbol{\mu}_x + oldsymbol{\Sigma}_x\mathbf{F}^T\frac{\sigma_y^2\mathbf{I} + \mathbf{F}oldsymbol{\Sigma}_x\mathbf{F}^T}{	ext{Gain}}(\mathbf{y}-oldsymbol{\mu}_y)_{	ext{Correction Term}}$

$$\mathbf{F} = \sqrt{\alpha_t}, \quad \sigma_y^2 = (1-\alpha_t)\mathbf{I}$

... some deep math ...

$q(\mathbf{x}_{t-1}|\mathbf{x}_t, \mathbf{x}_0)$ is **tractable** and can be calculated **exactly** without any approximation:

$q(\mathbf{x}_{t-1}|\mathbf{x}_t, \mathbf{x}_0) = \mathcal{N}(\mathbf{x}_{t-1}; ar{\mu}_t, ar{\Sigma}_t)$

$$ar{\mu}_t = \frac{\sqrt{\alpha_t}(1-	ilde{\alpha}_t)}\mathbf{x}_t + \sqrt{	ilde{\alpha}_{t-1}}(1-\alpha_t)}\mathbf{x}_0}{1-ar{\alpha}_t}, \quad ar{\Sigma}_t = \frac{(1-\alpha_t)(1-ar{\alpha}_t)}{1-ar{\alpha}_t}$

Gerhard Neumann | Machine Learning | KIT | SS 2024