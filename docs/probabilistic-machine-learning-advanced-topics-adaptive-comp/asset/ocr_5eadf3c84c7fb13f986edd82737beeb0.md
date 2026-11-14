# 6.5.3.1 Lower bound

The goal of EM is to maximize the log likelihood of the observed data:

```
\ell(\boldsymbol{\theta}) = \sum_{n=1}^N \log p(\boldsymbol{y}_n | \boldsymbol{\theta}) = \sum_{n=1}^N \log \left[ \sum_{\boldsymbol{z}_n} p(\boldsymbol{y}_n, \boldsymbol{z}_n | \boldsymbol{\theta}) \right]
```

where \(\boldsymbol{y}_n\) are the visible variables and \(\boldsymbol{z}_n\) are the hidden variables. Unfortunately this is hard to optimize, since the log cannot be pushed inside the sum.

EM gets around this problem as follows. First, consider a set of arbitrary distributions \(q_n(\boldsymbol{z}_n)\) over each hidden variable \(\boldsymbol{z}_n\). The observed data log likelihood can be written as follows:

```
\ell(\boldsymbol{\theta}) = \sum_{n=1}^N \log \left[ \sum_{\boldsymbol{z}_n} q_n(\boldsymbol{z}_n) \frac{p(\boldsymbol{y}_n, \boldsymbol{z}_n | \boldsymbol{\theta})}{q_n(\boldsymbol{z}_n)} \right]
```

Using Jensen’s inequality, we can push the log (which is a concave function) inside the expectation to get the following lower bound on the log likelihood:

```
\ell(\boldsymbol{\theta}) \ge \sum_n \sum_{\boldsymbol{z}_n} q_n(\boldsymbol{z}_n) \log \frac{p(\boldsymbol{y}_n, \boldsymbol{z}_n | \boldsymbol{\theta})}{q_n(\boldsymbol{z}_n)}
= \sum_n \underbrace{\mathbb{E}_{q_n} [\log p(\boldsymbol{y}_n, \boldsymbol{z}_n | \boldsymbol{\theta})]}_{\mathbb{L}(\boldsymbol{\theta}, q_n | \boldsymbol{y}_n)} + \mathbb{H}(q_n)
= \sum_n \mathbb{L}(\boldsymbol{\theta}, q_n | \boldsymbol{y}_n) \triangleq \mathbb{L}(\boldsymbol{\theta}, \{q_n\} | \mathcal{D})
```

where \(\mathbb{H}(q)\) is the entropy of probability distribution \(q\), and \(\mathbb{L}(\boldsymbol{\theta}, \{q_n\} | \mathcal{D})\) is called the **evidence lower bound** or **ELBO**, since it is a lower bound on the log marginal likelihood, \(\log p(\boldsymbol{y}_{1:N} | \boldsymbol{\theta})\), also called the evidence. Optimizing this bound is the basis of variational inference, as we discuss in Section 10.1.

# 6.5.3.2 E step

We see that the lower bound is a sum of \(N\) terms, each of which has the following form:

```
\mathbb{L}(\boldsymbol{\theta}, q_n | \boldsymbol{y}_n) = \sum_{\boldsymbol{z}_n} q_n(\boldsymbol{z}_n) \log \frac{p(\boldsymbol{y}_n, \boldsymbol{z}_n | \boldsymbol{\theta})}{q_n(\boldsymbol{z}_n)}
= \sum_{\boldsymbol{z}_n} q_n(\boldsymbol{z}_n) \log \frac{p(\boldsymbol{z}_n | \boldsymbol{y}_n, \boldsymbol{\theta}) p(\boldsymbol{y}_n | \boldsymbol{\theta})}{q_n(\boldsymbol{z}_n)}
= \sum_{\boldsymbol{z}_n} q_n(\boldsymbol{z}_n) \log \frac{p(\boldsymbol{z}_n | \boldsymbol{y}_n, \boldsymbol{\theta})}{q_n(\boldsymbol{z}_n)} + \sum_{\boldsymbol{z}_n} q_n(\boldsymbol{z}_n) \log p(\boldsymbol{y}_n | \boldsymbol{\theta})
= - D_{KL}(q_n(\boldsymbol{z}_n) \| p(\boldsymbol{z}_n | \boldsymbol{y}_n, \boldsymbol{\theta})) + \log p(\boldsymbol{y}_n | \boldsymbol{\theta})
```

where \(D_{KL}(q \| p) \triangleq \sum_z q(z) \log \frac{q(z)}{p(z)}\) is the Kullback-Leibler divergence (or KL divergence for short) between probability distributions \(q\) and \(p\). We discuss this in more detail in Section 5.1, but the key