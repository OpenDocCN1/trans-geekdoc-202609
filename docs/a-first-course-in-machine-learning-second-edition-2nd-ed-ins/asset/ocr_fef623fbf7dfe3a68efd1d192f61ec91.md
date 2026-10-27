of $D$ probabilities, $\mathbf{p}_k = [p_{k1},\dots,p_{kD}]^T$. For each component of these vectors we assume a Beta prior with parameters $\alpha$ and $\beta$:

$p(p_{kd}|\alpha,\beta) = \frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)} p_{kd}^{\alpha-1} (1-p_{kd})^{\beta-1}.$

The vector of prior probabilities for each component $\boldsymbol{\pi} = [\pi_1,\dots,\pi_K]^T$ is given a uniform Dirichlet prior with parameter $\gamma$. The likelihood of an observation $\mathbf{x}_n = [x_{n1},\dots,x_{nD}]^T$ being in component $k$ is:

$P(\mathbf{x}_n|\mathbf{p}_k) = \prod_{d=1}^{D} p_{kd}^{x_{nd}} (1-p_{kd})^{1-x_{nd}}.$

The posterior over all parameters is given by:

$p(\mathbf{Z},\boldsymbol{\pi},\mathbf{p}_1,\dots,\mathbf{p}_K|\mathbf{X},\alpha,\beta,\gamma) \propto p(\boldsymbol{\pi}|\gamma) \left[\prod_{k=1}^{K} p(\mathbf{p}_k|\alpha,\beta)\right] \left[\prod_{n=1}^{N} \sum_{k=1}^{K} (\pi_k p(\mathbf{x}_n|\mathbf{p}_k))^{z_{nk}}\right].$

To create a Gibbs sampler we require the conditional distributions for $z_{nk}$, $p_{kd}$ and $\pi_k$. The conditional density for $\boldsymbol{\pi}_k$ is the same as in the Gaussian case – a Dirichlet with parameters $\gamma + \sum_{n=1}^{N} z_{nk}$:

$p(\boldsymbol{\pi}|\dots) = Dir\left(\gamma + \sum_{n=1}^{N} z_{n1},\dots,\gamma + \sum_{n=1}^{N} z_{nK}\right).$

The conditional distribution for $z_{nk}$ is:

$P(z_{nk}=1|\dots) \propto \pi_k p(\mathbf{x}_n|\mathbf{p}_k),$

where the normalisation constant will be the sum of these terms over $j = 1 \dots K$. Finally, the conditional distribution for $p_{kd}$ is derived as follows:

$p(p_{kd}|\dots) \propto p_{kd}^{\alpha-1} (1-p_{kd})^{\beta-1} \prod_{n=1}^{N} (p_{kd}^{x_{nd}} (1-p_{kd})^{1-x_{nd}})^{z_{nk}}$\n$\propto p_{kd}^{\alpha-1} (1-p_{kd})^{\beta-1} p_{kd}^{\sum_n z_{nk} x_{nd}} (1-p_{kd})^{\sum_n z_{nk}(1-x_{nd})}$\n$\propto p_{kd}^{\alpha-1+\sum_n z_{nk} x_{nd}} (1-p_{kd})^{\beta-1+\sum_n z_{nk}(1-x_{nd})}$

which is a Beta density with parameters $\alpha^* = \alpha + \sum_n z_{nk} x_{nd}$ and $\beta^* = \beta + \sum_n z_{nk}(1-x_{nd}).$

EX 10.4. The conditional density of the mean parameter given in the book is:

$p(\boldsymbol{\mu}_k|\dots) = \mathcal{N}(\mathbf{a},\mathbf{B})$

where:

$\mathbf{B} = \left[\boldsymbol{\Sigma}_0^{-1} + \left(\sum_n z_{nk} \mathbf{I}\right)\right]^{-1},$