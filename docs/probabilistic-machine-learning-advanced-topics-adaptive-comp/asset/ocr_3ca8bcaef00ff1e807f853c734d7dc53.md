where we have assumed $\mathbf{K} = \mathbf{K}_x + \mathbf{K}_{y|x}$ is invertible (although the prior or likelihood on their own may be singular).
The $K$ rows of $\mathbf{G} = [\mathbf{g}_1^\mathsf{T}; \dots ; \mathbf{g}_K^\mathsf{T}]$ and the $M$ rows of $\mathbf{H} = [\mathbf{h}_1^\mathsf{T}; \dots ; \mathbf{h}_M^\mathsf{T}]$ can be combined into the $L$ rows of $\mathbf{F} = [\mathbf{f}_1^\mathsf{T}; \dots ; \mathbf{f}_L^\mathsf{T}]$, which define the linear constraints of the system. If we assume that $\mathbf{\Sigma}_p$ and $\mathbf{\Sigma}_n$ are diagonal, then the structure of the graphical model is uniquely determined by the sparsity of $\mathbf{F}$. The resulting posterior factorizes as a product of $L$ Gaussian "experts":

```
$p(\mathbf{x}|\mathbf{y}) \propto \prod_{l=1}^L \exp(-\frac{1}{2}\mathbf{x}^\mathsf{T}\mathbf{K}_l\mathbf{x} + \mathbf{h}_l^\mathsf{T}\mathbf{x}) \propto \prod_{l=1}^L \mathcal{N}(\mathbf{f}_l^\mathsf{T}\mathbf{x}; \boldsymbol{\mu}_l, \boldsymbol{\Sigma}_l)$ (9.101)
```

where $\boldsymbol{\Sigma}_l$ equals $\mathbf{\Sigma}_{p,t,l}$ for $l = 1 : K$ and equals $\mathbf{\Sigma}_{n,v,l'}$ for $l = K + 1 : L$ where $l' = l - K$. Similarly $\boldsymbol{\mu}_l = \boldsymbol{\mu}_{p,t}$ for $l = 1 : K$ and $\boldsymbol{\mu}_l = (y_{l'} - c_{l'})$ for $l = K + 1 : L$.

To apply perturb and MAP, we proceed as follows. First perturb the prior mean by sampling $\tilde{\boldsymbol{\mu}}_p \sim \mathcal{N}(\boldsymbol{\mu}_p, \mathbf{\Sigma}_p)$, and perturb the measurements by sampling $\tilde{\mathbf{y}} \sim \mathcal{N}(\mathbf{y}, \mathbf{\Sigma}_n)$. (Note that this is equivalent to first perturbing the linear term in each information form potential, using $\tilde{\mathbf{h}}_l = \mathbf{h}_l + \mathbf{f}_l \mathbf{\Sigma}_l^{-\frac{1}{2}} \boldsymbol{\epsilon}_l$, where $\boldsymbol{\epsilon}_l \sim \mathcal{N}(0,1)$.) Then compute the MAP estimate for $\mathbf{x}$ using the perturbed parameters:

```
$\tilde{\mathbf{x}} = \mathbf{K}^{-1}\mathbf{G}^\mathsf{T}\mathbf{\Sigma}_p^{-1} \tilde{\boldsymbol{\mu}}_p + \mathbf{K}^{-1}\mathbf{H}^\mathsf{T}\mathbf{\Sigma}_n^{-1}(\tilde{\mathbf{y}} - \mathbf{c})$ (9.102)
$= \mathbf{K}^{-1}\mathbf{G}^\mathsf{T}\mathbf{\Sigma}_p^{-1}(\boldsymbol{\mu}_p + \boldsymbol{\epsilon}_{\mu}) + \mathbf{K}^{-1}\mathbf{H}^\mathsf{T}\mathbf{\Sigma}_n^{-1}(\mathbf{y} + \boldsymbol{\epsilon}_y - \mathbf{c})$ (9.103)
$= \boldsymbol{\mu} + \mathbf{A}\boldsymbol{\epsilon}_{\mu} + \mathbf{B}\boldsymbol{\epsilon}_y$ (9.104)
```

We see that $\mathbb{E}[\tilde{\mathbf{x}}] = \boldsymbol{\mu}$ and $\mathbb{E}[(\tilde{\mathbf{x}} - \boldsymbol{\mu})(\tilde{\mathbf{x}} - \boldsymbol{\mu})^\mathsf{T}] = \mathbf{K}^{-1} = \mathbf{\Sigma}$, so the method produces exact samples.

This approach is very scalable, since we compute the MAP estimate of sparse GMRFs (i.e., posterior mean) can be done efficiently using conjugate gradient solvers. Alternatively we can use loopy belief propagation (Section 9.4), which can often compute the exact posterior mean (see e.g., [WF01a; JMW06; Bic09; Du+18]).

# 9.7.2.2 Discrete case

In [PY11; PY14] they extend perturb-and-MAP to the case of discrete graphical models. This setup is more complicated, and requires the use of Gumbel noise, which can be sampled using $\epsilon = -\log(-\log(u))$, where $u \sim \text{Unif}(0,1)$. This noise should be added to all the potentials in the model, but as a simple approximation, it can just be added to the unary terms, i.e., the local evidence potentials. Let the score, or unnormalized log probability, of configuration $\mathbf{x}$ given inputs $\mathbf{c}$ be

```
$S(\mathbf{x}; \mathbf{c}) = \log p(\mathbf{x}|\mathbf{c}) + \text{const} = \sum_i \log \phi_i(x_i) + \sum_{ij} \log \psi_{ij}(x_{i,j})$ (9.105)
```

where we have assumed a pairwise CRF for notational simplicity. If we perturb the local evidence potentials $\phi_i(k)$ by adding $\epsilon_{ik}$ to each entry, where $k$ indexes the discrete latent states, we get $\tilde{S}(\mathbf{x}; \mathbf{c})$. We then compute a sample $\tilde{\mathbf{x}}$ by solving $\tilde{\mathbf{x}} = \text{argmax } \tilde{S}(\mathbf{x}; \mathbf{c})$. The advantage of this approach is that it can leverage efficient MAP solvers for discrete models, such as those discussed in Supplementary Section 9.3. This can in turn be used for parameter learning, and estimating the partition function [HJ12; Erm+13].