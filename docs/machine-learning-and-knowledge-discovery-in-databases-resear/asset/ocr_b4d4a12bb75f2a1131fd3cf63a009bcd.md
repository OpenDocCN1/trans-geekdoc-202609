distribution and produces an output representation. In practice, sampling from \( q^m \) is achieved through a reparameterization trick, as introduced in [16]. The equation to compute \( \mathbf{z}_t^m \) then becomes:

\(\mathbf{z}_t^m = \mu + \sigma \odot \epsilon,\)

where \( \epsilon \) corresponds to a sampled value \( \epsilon \sim \mathcal{N}(\mathbf{0}, \mathbf{I}) \) and \( \odot \) is element-wise multiplication. The two blocks are depicted in Fig. 1. The optional autoregressive module \( g_{ar}(.) \) has been untouched, and remains identical as in GIM, resulting in deterministic representations.

![](bbox=[0.2, 0.27, 0.75, 0.36])

Fig. 1. A single module.

# ## 3.2 The Loss Function

Instead of training the NN's modules end-to-end with a global loss function, each module is optimized greedily with its own loss. Through the introduction of the _Smooth-InfoNCE_ loss, mutual information between temporally nearby representations is maximized, while regularizing the latent space to be approximate to the standard Gaussian \( \mathcal{N}(\mathbf{0}, \mathbf{I}) \). This loss is defined as follows:

\(\mathcal{L}_{\text{S-NCE}}^m = - \sum_{k, \mathbf{z}_{t+k}^m \sim q^m(.|\mathbf{z}_t^{m-1}) \mathbf{z}^m \sim q^m(.|\mathbf{z}_t^{m-1})} \left[ \log \frac{f_k^m(\mathbf{z}_{t+k}^m, \mathbf{z}^m)}{\sum_{\mathbf{z}^j \in X} f_k^m(\mathbf{z}^j, \mathbf{z}^m)} \right] + \beta \underbrace{D_{KL}\left(q^m(.|\mathbf{z}_t^{m-1}) || \mathcal{N}(\mathbf{0}, \mathbf{I})\right)}_{\text{Regularisation}} \tag{7}\)

Here, \( m \in \mathbb{N} \) refers to the \( m \)’th module and \( k \in \mathbb{N} \) the number of follow-up patches the similarity score \( f_k^m(\mathbf{z}_{t+k}^m, \mathbf{z}_t^m) \) must rate. The latent representations \( \mathbf{z}_{t+k}^m \) and \( \mathbf{z}_t^m \) are encoded samples produced by \( g_{enc}^m(\mathbf{z}_{t+k}^{m-1}) \) and \( g_{enc}^m(\mathbf{z}_t^{m-1}) \), respectively and \( X \) is a set of samples \( \{ \mathbf{z}_{t+k}^m, \mathbf{z}_t^1, \mathbf{z}_t^2, \dots \} \) where \( \mathbf{z}_t^j \) with \( j \neq t+k \) are random samples. In practice, the set can be based on the training batch. The parameter \( \beta \ge 0 \) is a hyper-parameter indicating the relative importance between the two terms. When \( \beta = 0 \), SIM is identical to GIM but with an altered architecture supporting probabilistic representations. The similarity score \( f_k^m(.) \) remains identical as in GIM:

\( f_k^m(\mathbf{z}_{t+k}^m, \mathbf{z}_t^m) = \exp(\mathbf{z}_{t+k}^m \, ^T W_k^m \, \mathbf{z}_t^m). \tag{8} \)

\( \mathcal{L}_{\text{S-NCE}}^m \) consists of two terms. The first term ensures that latent representations of temporally nearby patches maximally preserve their shared information. The second pushes the latent representations close to the origin.