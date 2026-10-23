# 5.7.2.2 E step

We see that the lower bound is a sum of N terms, each of which has the following form:

$$Q(\boldsymbol{\theta}, q_n) = \sum_{\mathbf{z}_n} q_n(\mathbf{z}_n) \log \frac{p(\mathbf{y}_n, \mathbf{z}_n | \boldsymbol{\theta})}{q_n(\mathbf{z}_n)}\tag{5.150}$$

$$= \sum_{\mathbf{z}_n} q_n(\mathbf{z}_n) \log \frac{p(\mathbf{z}_n | \mathbf{y}_n, \boldsymbol{\theta}) p(\mathbf{y}_n | \boldsymbol{\theta})}{q_n(\mathbf{z}_n)}\tag{5.151}$$

$$= \sum_{\mathbf{z}_n} q_n(\mathbf{z}_n) \log \frac{p(\mathbf{z}_n | \mathbf{y}_n, \boldsymbol{\theta})}{q_n(\mathbf{z}_n)} + \sum_{\mathbf{z}_n} q_n(\mathbf{z}_n) \log p(\mathbf{y}_n | \boldsymbol{\theta})\tag{5.152}$$

$$= -\mathbb{KL}\big(q_n(\mathbf{z}_n) \| p(\mathbf{z}_n | \mathbf{y}_n, \boldsymbol{\theta})\big) + \log p(\mathbf{y}_n | \boldsymbol{\theta})\tag{5.153}$$

where $\mathbb{KL}(q \| p) \triangleq \sum_z q(z) \log \frac{q(z)}{p(z)}$ is the Kullback-Leibler divergence (or KL divergence for short) between probability distributions $q$ and $p$. We discuss this in more detail in Sec. 6.2, but the key property we need here is that $\mathbb{KL}(q \| p) \ge 0$ and $\mathbb{KL}(q \| p) = 0$ iff $q = p$. Hence we can maximize the lower bound $Q(\boldsymbol{\theta}, \{q_n\})$ wrt $\{q_n\}$ by setting each one to $q_n^* = p(\mathbf{z}_n | \mathbf{y}_n, \boldsymbol{\theta})$. This is called the E step. This makes the lower bound tight, in the sense that $Q(\boldsymbol{\theta}, \{q_n^*\}) = \sum_n \log p(\mathbf{y}_n | \boldsymbol{\theta}) = \ell(\boldsymbol{\theta})$.

# 5.7.2.3 M step

In the M step, we need to maximize $Q(\boldsymbol{\theta}, \{q_n^t\})$ wrt $\boldsymbol{\theta}$, where $q_n^t$ are the distributions computed in the E step at iteration $t$. Since the entropy terms $\mathbb{H}(q_n)$ are constant wrt $\boldsymbol{\theta}$, so we can drop them in the M step. We are left with

$$\ell^t(\boldsymbol{\theta}) = \sum_n \mathbb{E}_{q_n^t(\mathbf{z}_n)}[\log p(\mathbf{y}_n, \mathbf{z}_n | \boldsymbol{\theta})]\tag{5.154}$$

This is called the expected complete data log likelihood. If the joint probability is in the exponential family (Sec. 12.2), we can rewrite this as

$$\ell^t(\boldsymbol{\theta}) = \sum_n \mathbb{E}[\mathbf{t}(\mathbf{y}_n, \mathbf{z}_n)^\top \boldsymbol{\theta} - A(\boldsymbol{\theta})] = \sum_n (\mathbb{E}[\mathbf{t}(\mathbf{y}_n, \mathbf{z}_n)]^\top \boldsymbol{\theta} - A(\boldsymbol{\theta}))\tag{5.155}$$

where $\mathbb{E}[\mathbf{t}(\mathbf{y}_n, \mathbf{z}_n)]$ are called the expected sufficient statistics.

In the M step, we maximize the expected complete data log likelihood to get

$$\boldsymbol{\theta}^{t+1} = \arg \max_{\boldsymbol{\theta}} \sum_n \mathbb{E}_{q_n^t}[\log p(\mathbf{y}_n, \mathbf{z}_n | \boldsymbol{\theta})]\tag{5.156}$$

In the case of the exponential family, the maximization can be solved in closed-form by matching the moments of the expected sufficient statistics (Sec. 12.2.4).

We see from the above that the E step does not in fact need to return the full set of posterior distributions $\{q(\mathbf{z}_n) : n = 1 : N\}$, but can instead just return the sum of the expected sufficient statistics, $\sum_n \mathbb{E}_{q(\mathbf{z}_n)}[\mathbf{t}(\mathbf{y}_n, \mathbf{z}_n)]$. This will become clearer in the examples below.