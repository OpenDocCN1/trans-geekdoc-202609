
$$
\mathcal{L}_{\text{NCE}}^m = - \sum_k \mathbb{E}_{\boldsymbol{\chi}} \left[ \log \frac{f_k^m(\mathbf{z}_{t+k}^m, \mathbf{z}_t^m)}{\sum_{\mathbf{z}_j^m \in X} f_k^m(\mathbf{z}_j^m, \mathbf{z}_t^m)} \right].
$$

One can prove that minimizing the InfoNCE loss is equivalent to maximizing a lower bound on the mutual information between \(\mathbf{z}_t^m\) and \(\mathbf{z}_{t+k}^m\) [25]:

\(I(\mathbf{z}_{t+k}^m; \mathbf{z}_t^m) \ge \log(N) - \mathcal{L}_{\text{NCE}}^m.\)

As a result of GIM's greedy approach, a conventional neural network architecture can be divided into modules. These modules can be trained either in parallel on distributed devices or sequentially, enabling the training of models larger than device memory and reducing the vanishing gradient problem. In the following section, we discuss how we can preserve these benefits in SIM, while also allowing for better interpretability.

## 3 Smooth InfoMax

While optimizing for the InfoNCE bound, as done in GIM, is remarkably successful for downstream classification, analyzing the learned representations remains difficult. In what follows we introduce Smooth InfoMax (SIM), maintaining the computational benefits obtained from optimizing the InfoNCE objective, while introducing easily traversable latent spaces and better disentangled representations at different depths in the network due to techniques borrowed from \(\beta\)-VAEs.

### 3.1 Towards Decoupled Training for Probabilistic Representations

The architecture is again based on modules, where the modules \(g_{enc}^1(\cdot), g_{enc}^2(\cdot), \dots, g_{enc}^M(\cdot)\) are each greedily optimized without gradients flowing between them. However, rather than producing a single deterministic point \(\mathbf{z}_t^m\), the output from \(g_{enc}^m(\cdot)\) is now a multivariate Gaussian distribution \(q(\mathbf{z}_t^m \mid \mathbf{z}_t^{m-1})\), parameterized by the mean vector \(\boldsymbol{\mu}\) and covariance matrix \(\text{diag}(\boldsymbol{\sigma})\). More precisely, we have:

\(g_{enc}^m(\mathbf{z}_t^{m-1}) = q(\mathbf{z}_t^m \mid \mathbf{z}_t^{m-1}) = \mathcal{N}(\boldsymbol{\mu}, \text{diag}(\boldsymbol{\sigma})),\)

with \(\boldsymbol{\mu}\) and \(\boldsymbol{\sigma}\) dependent on \(\mathbf{z}_t^{m-1}\). A point \(\mathbf{z}_t^m\) is then obtained by sampling from this distribution, denoted respectively, as follows:

\(\mathbf{z}_t^m \sim q^m(\cdot \mid \mathbf{z}_t^{m-1}).\)

The encoding modules are thus stochastic and obtaining two representations from the same input will not necessarily produce the same result. This is in contrast to GIM's latent representations which remain fixed with respect to the input.

We obtain these stochastic modules by defining each module \(g_{enc}^m(\cdot)\) consisting of two blocks. The first block receives as input \(\mathbf{z}_t^{m-1}\) and predicts the parameters \(\boldsymbol{\mu}\) and \(\boldsymbol{\sigma}\). The second block samples \(\mathbf{z}_t^m \sim q^m(\cdot \mid \mathbf{z}_t^{m-1})\) from this distribution and produces an output representation. In practice, sampling from \( q^m \) is achieved through a reparameterization trick, as introduced in [16]. The equation to compute \( \mathbf{z}_t^m \) then becomes:

\(\mathbf{z}_t^m = \mu + \sigma \odot \epsilon,\)

where \( \epsilon \) corresponds to a sampled value \( \epsilon \sim \mathcal{N}(\mathbf{0}, \mathbf{I}) \) and \( \odot \) is element-wise multiplication. The two blocks are depicted in Fig. 1. The optional autoregressive module \( g_{ar}(.) \) has been untouched, and remains identical as in GIM, resulting in deterministic representations.

![](img/f56761e6196132d5b74909d98468408f_575_0.png)

Fig. 1. A single module.

### 3.2 The Loss Function

Instead of training the NN's modules end-to-end with a global loss function, each module is optimized greedily with its own loss. Through the introduction of the _Smooth-InfoNCE_ loss, mutual information between temporally nearby representations is maximized, while regularizing the latent space to be approximate to the standard Gaussian \( \mathcal{N}(\mathbf{0}, \mathbf{I}) \). This loss is defined as follows:

\(\mathcal{L}_{\text{S-NCE}}^m = - \sum_{k, \mathbf{z}_{t+k}^m \sim q^m(.|\mathbf{z}_t^{m-1}) \mathbf{z}^m \sim q^m(.|\mathbf{z}_t^{m-1})} \left[ \log \frac{f_k^m(\mathbf{z}_{t+k}^m, \mathbf{z}^m)}{\sum_{\mathbf{z}^j \in X} f_k^m(\mathbf{z}^j, \mathbf{z}^m)} \right] + \beta \underbrace{D_{KL}\left(q^m(.|\mathbf{z}_t^{m-1}) || \mathcal{N}(\mathbf{0}, \mathbf{I})\right)}_{\text{Regularisation}} \tag{7}\)

Here, \( m \in \mathbb{N} \) refers to the \( m \)’th module and \( k \in \mathbb{N} \) the number of follow-up patches the similarity score \( f_k^m(\mathbf{z}_{t+k}^m, \mathbf{z}_t^m) \) must rate. The latent representations \( \mathbf{z}_{t+k}^m \) and \( \mathbf{z}_t^m \) are encoded samples produced by \( g_{enc}^m(\mathbf{z}_{t+k}^{m-1}) \) and \( g_{enc}^m(\mathbf{z}_t^{m-1}) \), respectively and \( X \) is a set of samples \( \{ \mathbf{z}_{t+k}^m, \mathbf{z}_t^1, \mathbf{z}_t^2, \dots \} \) where \( \mathbf{z}_t^j \) with \( j \neq t+k \) are random samples. In practice, the set can be based on the training batch. The parameter \( \beta \ge 0 \) is a hyper-parameter indicating the relative importance between the two terms. When \( \beta = 0 \), SIM is identical to GIM but with an altered architecture supporting probabilistic representations. The similarity score \( f_k^m(.) \) remains identical as in GIM:

\( f_k^m(\mathbf{z}_{t+k}^m, \mathbf{z}_t^m) = \exp(\mathbf{z}_{t+k}^m \, ^T W_k^m \, \mathbf{z}_t^m). \tag{8} \)

\( \mathcal{L}_{\text{S-NCE}}^m \) consists of two terms. The first term ensures that latent representations of temporally nearby patches maximally preserve their shared information. The second pushes the latent representations close to the origin.

**The Gradient.** To estimate the expectation term in $\mathcal{L}_{\text{S-NCE}}$, we apply the same approximation method as in VAEs, achieved through Monte Carlo estimates [16]. The first term in $\mathcal{L}_{\text{S-NCE}}$ then becomes:

\[- \sum_k \frac{1}{L} \left[ \sum_{l=1}^L \log \frac{f_k^m(\mathbf{z}_{t+k}^m, \mathbf{z}_t^{m(l)})}{\sum_{\mathbf{z}_j^m \in \mathcal{X}} f_k^m(\mathbf{z}_j^m, \mathbf{z}_t^{m(l)})} \right] .\]

Here, $L$ refers to the number of samples drawn. Each $\mathbf{z}_{t+k}^{m(l)}$ and $\mathbf{z}_t^{m(l)}$ are different samples produced by their respective distributions. However, similar to [16], we can set $L=1$ without significantly hurting performance.

With regards to the second term in $\mathcal{L}_{\text{S-NCE}}$, since $q^m(\cdot \mid \mathbf{z}_t^{m-1})$ is a Gaussian defined by parameters $\boldsymbol{\mu}$ and $\boldsymbol{\sigma}$, a closed-form solution exists [16]. The closed-form equation is the following:

\[D_{KL} \left( q^m(\cdot \mid \mathbf{z}_t^{m-1}) \parallel \mathcal{N}(\mathbf{0}, \mathbf{I}) \right) = \frac{1}{2} \sum_{i=1}^D \left( - \log \sigma_i^2 - 1 + \sigma_i^2 + \mu_i^2 \right) .\]

The variable $D$ refers to the number of dimensions of $\boldsymbol{\mu}$ and $\boldsymbol{\sigma}$. This term can thus, be directly computed and does not need to be approximated through Monte Carlo estimates. The gradient for the two terms can then be computed using automatic differentiation tools such as PyTorch.

### 3.3 Properties of the Latent Space

Here, we present two conjectures regarding the structure of the latent space defined by each of SIM's modules. They will serve as the main argument for why SIM's representations are more easily analyzable. Meanwhile, alternative contrastive approaches such as GIM lack these benefits.

### **Conjecture 1.** $\mathcal{L}_{\text{S-NCE}}$ *enforces an uninterrupted and well-covered space around the origin.*

In SIM, a latent representation $\mathbf{z}_t^m \in \mathcal{Z}^m$ of a data point $\mathbf{z}_t^{m-1} \in \mathcal{Z}^{m-1}$ is a sample from a Gaussian distribution. Thus, encoding the same $\mathbf{z}_t^{m-1}$ an infinite number of times results in a spherical region (around a particular mean $\boldsymbol{\mu}$) in $\mathcal{Z}^m$ that is covered by the latent representations corresponding to $\mathbf{z}_t^{m-1}$, without any interruptions in this region. This is different from GIM where a data point merely covers a single point of the latent space (and not an entire region). Furthermore, because the KL divergence requires each region to be close to the origin, the regions are more likely to utilize the limited space efficiently around the origin, resulting in a lower chance of obtaining gaps between two regions from different data points.

### **Conjecture 2.** $\mathcal{L}_{\text{S-NCE}}$ *enforces smooth and consistent transitions in the latent space with respect to the shared information between temporally nearby patches.*

The argument on why this holds true is similar to the argument made for VAEs [16]. In the case of a VAE, a smooth space implies that a small change to
