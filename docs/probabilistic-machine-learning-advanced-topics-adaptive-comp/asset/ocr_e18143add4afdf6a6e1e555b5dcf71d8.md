# 20.4.1 Likelihood-based evaluation

A standard way to measure how close a model q is to a true distribution p is in terms of the KL divergence (Section 5.1):

```
$$D_{\text{KL}}(p \| q) = \int p(\boldsymbol{x}) \log \frac{p(\boldsymbol{x})}{q(\boldsymbol{x})} = - \mathbb{H}(p) + \mathbb{H}_{\text{ce}}(p, q)$$
```

where $\mathbb{H}(p)$ is a constant, and $\mathbb{H}_{ce}(p, q)$ is the cross entropy. If we approximate $p(\boldsymbol{x})$ by the empirical distribution, we can evaluate the cross entropy in terms of the empirical **negative log likelihood** on the dataset:

```
$$\text{NLL} = -\frac{1}{N} \sum_{n=1}^N \log q(\boldsymbol{x}_n)$$
```

Usually we care about negative log likelihood on a held-out test set.

# 20.4.1.1 Computing the log-likelihood

For models of discrete data, such as language models, it is easy to compute the (negative) log likelihood. However, it is common to measure performance using a quantity called **perplexity**, which is defined as $2^H$, where $H = \text{NLL}$ is the cross entropy or negative log likelihood.

For image and audio models, one complication is that the model is usually a continuous distribution $p(\boldsymbol{x}) \ge 0$ but the data is usually discrete (e.g., $\boldsymbol{x} \in \{0, \dots, 255\}^D$ if we use one byte per pixel). Consequently the average log likelihood can be arbitrary large, since the pdf can be bigger than 1. To avoid this it is standard practice to use **uniform dequantization** [TOB16], in which we add uniform random noise to the discrete data, and then treat it as continuous-valued data. This gives a lower bound on the average log likelihood of the discrete model on the original data.

To see this, let $\boldsymbol{z}$ be a continuous latent variable, and $\boldsymbol{x}$ be a vector of binary observations computed by rounding, so $p(\boldsymbol{x}|\boldsymbol{z}) = \delta(\boldsymbol{x} - \text{round}(\boldsymbol{z}))$, computed elementwise. We have $p(\boldsymbol{x}) = \int p(\boldsymbol{x}|\boldsymbol{z})p(\boldsymbol{z})d\boldsymbol{z}$. Let $q(\boldsymbol{z}|\boldsymbol{x})$ be a probabilistic inverse of $\boldsymbol{x}$, that is, it has support only on values where $p(\boldsymbol{x}|\boldsymbol{z})=1$. In this case, Jensen's inequality gives

```
$$\log p(\boldsymbol{x}) \ge \mathbb{E}_{q(\boldsymbol{z}|\boldsymbol{x})} [\log p(\boldsymbol{x}|\boldsymbol{z}) + \log p(\boldsymbol{z}) - \log q(\boldsymbol{z}|\boldsymbol{x})]$$
```

```
$$= \mathbb{E}_{q(\boldsymbol{z}|\boldsymbol{x})} [\log p(\boldsymbol{z}) - \log q(\boldsymbol{z}|\boldsymbol{x})]$$
```

Thus if we model the density of $z \sim q(\boldsymbol{z}|\boldsymbol{x})$, which is a dequantized version of $\boldsymbol{x}$, we will get a lower bound on $p(\boldsymbol{x})$.

# 20.4.1.2 Likelihood can be hard to compute

Unfortunately, for many models, computing the likelihood can be computationally expensive, since it requires knowing the normalization constant of the probability model. One solution is to use variational inference (Chapter 10), which provides a way to efficiently compute lower (and sometimes

4. In some applications, we report **bits per dimension**, which is the log likelihood using log base 2, divided by the dimensionality of $\boldsymbol{x}$. To compute this metric, recall that $\log_2 L = \frac{\log_e L}{\log_e 2}$, and hence $\text{bpd} = \text{NLL} \log_e(2) \frac{1}{|\boldsymbol{x}|}$.