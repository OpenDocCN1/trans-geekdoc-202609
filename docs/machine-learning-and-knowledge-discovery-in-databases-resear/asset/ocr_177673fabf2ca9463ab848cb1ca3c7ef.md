**The Gradient.** To estimate the expectation term in $\mathcal{L}_{\text{S-NCE}}$, we apply the same approximation method as in VAEs, achieved through Monte Carlo estimates [16]. The first term in $\mathcal{L}_{\text{S-NCE}}$ then becomes:

```
\[- \sum_k \frac{1}{L} \left[ \sum_{l=1}^L \log \frac{f_k^m(\mathbf{z}_{t+k}^m, \mathbf{z}_t^{m(l)})}{\sum_{\mathbf{z}_j^m \in \mathcal{X}} f_k^m(\mathbf{z}_j^m, \mathbf{z}_t^{m(l)})} \right] .\]
```

Here, $L$ refers to the number of samples drawn. Each $\mathbf{z}_{t+k}^{m(l)}$ and $\mathbf{z}_t^{m(l)}$ are different samples produced by their respective distributions. However, similar to [16], we can set $L=1$ without significantly hurting performance.

With regards to the second term in $\mathcal{L}_{\text{S-NCE}}$, since $q^m(\cdot \mid \mathbf{z}_t^{m-1})$ is a Gaussian defined by parameters $\boldsymbol{\mu}$ and $\boldsymbol{\sigma}$, a closed-form solution exists [16]. The closed-form equation is the following:

```
\[D_{KL} \left( q^m(\cdot \mid \mathbf{z}_t^{m-1}) \parallel \mathcal{N}(\mathbf{0}, \mathbf{I}) \right) = \frac{1}{2} \sum_{i=1}^D \left( - \log \sigma_i^2 - 1 + \sigma_i^2 + \mu_i^2 \right) .\]
```

The variable $D$ refers to the number of dimensions of $\boldsymbol{\mu}$ and $\boldsymbol{\sigma}$. This term can thus, be directly computed and does not need to be approximated through Monte Carlo estimates. The gradient for the two terms can then be computed using automatic differentiation tools such as PyTorch.

# 3.3 Properties of the Latent Space

Here, we present two conjectures regarding the structure of the latent space defined by each of SIM's modules. They will serve as the main argument for why SIM's representations are more easily analyzable. Meanwhile, alternative contrastive approaches such as GIM lack these benefits.

# **Conjecture 1.** $\mathcal{L}_{\text{S-NCE}}$ *enforces an uninterrupted and well-covered space around the origin.*

In SIM, a latent representation $\mathbf{z}_t^m \in \mathcal{Z}^m$ of a data point $\mathbf{z}_t^{m-1} \in \mathcal{Z}^{m-1}$ is a sample from a Gaussian distribution. Thus, encoding the same $\mathbf{z}_t^{m-1}$ an infinite number of times results in a spherical region (around a particular mean $\boldsymbol{\mu}$) in $\mathcal{Z}^m$ that is covered by the latent representations corresponding to $\mathbf{z}_t^{m-1}$, without any interruptions in this region. This is different from GIM where a data point merely covers a single point of the latent space (and not an entire region). Furthermore, because the KL divergence requires each region to be close to the origin, the regions are more likely to utilize the limited space efficiently around the origin, resulting in a lower chance of obtaining gaps between two regions from different data points.

# **Conjecture 2.** $\mathcal{L}_{\text{S-NCE}}$ *enforces smooth and consistent transitions in the latent space with respect to the shared information between temporally nearby patches.*

The argument on why this holds true is similar to the argument made for VAEs [16]. In the case of a VAE, a smooth space implies that a small change to