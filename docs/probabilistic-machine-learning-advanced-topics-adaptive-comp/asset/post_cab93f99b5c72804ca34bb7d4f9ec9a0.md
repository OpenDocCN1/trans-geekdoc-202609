
![](img/ca72c1626f4850f058a9edc138c1ac73_831_0.png)

Figure 21.11: Hierarchical VAEs with 3 stochastic layers. Left: generative model. Right: inference network. Diamond is a residual network, \(\oplus\) is feature combination (e.g., concatenation), and h is a trainable parameter. We first do bottom-up inference, by propagating \(\boldsymbol{x}\) up to \(\boldsymbol{z}_3\) to compute \(\boldsymbol{z}_3^s \sim q_{\phi}(\boldsymbol{z}_3|\boldsymbol{x})\), and then we perform top-down inference by computing \(\boldsymbol{z}_2^s \sim q_{\phi}(\boldsymbol{z}_2|\boldsymbol{x}, \boldsymbol{z}_3^s)\) and then \(\boldsymbol{z}_1^s \sim q_{\phi}(\boldsymbol{z}_1|\boldsymbol{x}, \boldsymbol{z}_{2:3}^s)\). From Figure 2 of [VK20a]. Used with kind permission of Arash Vahdat.

### 21.5.1 Bottom-up vs top-down inference

To perform inference in a hierarchical VAE, we could use a bottom-up inference model of the form

\[
q_\phi(\boldsymbol{z}|\boldsymbol{x}) = q_\phi(\boldsymbol{z}_1|\boldsymbol{x}) \prod_{l=2}^L q_\phi(\boldsymbol{z}_l|\boldsymbol{x}, \boldsymbol{z}_{1:l-1})
\]

However, a better approach is to use a top-down inference model of the form

\[
q_\phi(\boldsymbol{z}|\boldsymbol{x}) = q_\phi(\boldsymbol{z}_L|\boldsymbol{x}) \prod_{l=L-1}^1 q_\phi(\boldsymbol{z}_l|\boldsymbol{x}, \boldsymbol{z}_{l+1:L})
\]

Inference for \(\boldsymbol{z}_1\) combines bottom-up information from \(\boldsymbol{x}\) with top-down information from higher layers, \(\boldsymbol{z}_{>l} = \boldsymbol{z}_{l+1:L}\). See Figure 21.11(right) for an illustration.\(^7\)

7. Note that it is also possible to have a stochastic bottom-up encoder and a stochastic top-down encoder, as discussed in the **BIVA** paper [Maa+19]. (BIVA stands for “bidirectional-inference variational autoencoder”.)

With the above model, the ELBO can be written as follows (using the chain rule for KL):

\[
\mathbf{L}(\boldsymbol{\theta}, \boldsymbol{\phi}|\boldsymbol{x}) = \mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{z}|\boldsymbol{x})}[\log p_{\boldsymbol{\theta}}(\boldsymbol{x}|\boldsymbol{z})] - D_{\mathrm{KL}}(q_{\boldsymbol{\phi}}(\boldsymbol{z}_L|\boldsymbol{x}) \| p_{\boldsymbol{\theta}}(\boldsymbol{z}_L)) - \sum_{l=L-1}^1 \mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{z}_{>l}|\boldsymbol{x})}[D_{\mathrm{KL}}(q_{\boldsymbol{\phi}}(\boldsymbol{z}_l|\boldsymbol{x}, \boldsymbol{z}_{>l}) \| p_{\boldsymbol{\theta}}(\boldsymbol{z}_l|\boldsymbol{z}_{>l}))]
\]

where

\[
q_{\boldsymbol{\phi}}(\boldsymbol{z}_{>l}|\boldsymbol{x}) = \prod_{i=l+1}^L q_{\boldsymbol{\phi}}(\boldsymbol{z}_i|\boldsymbol{x}, \boldsymbol{z}_{>i})
\]

is the approximate posterior above layer $l$ (i.e., the parents of $\boldsymbol{z}_l$).

The reason the top-down inference model is better is that it more closely approximates the true posterior of a given layer, which is given by

\[
p_{\boldsymbol{\theta}}(\boldsymbol{z}_l|\boldsymbol{x}, \boldsymbol{z}_{l+1:L}) \propto p_{\boldsymbol{\theta}}(\boldsymbol{z}_l|\boldsymbol{z}_{l+1:L})p_{\boldsymbol{\theta}}(\boldsymbol{x}|\boldsymbol{z}_l, \boldsymbol{z}_{l+1:L})
\]

Thus the posterior combines the top-down prior term $p_{\boldsymbol{\theta}}(\boldsymbol{z}_l|\boldsymbol{z}_{l+1:L})$ with the bottom-up likelihood term $p_{\boldsymbol{\theta}}(\boldsymbol{x}|\boldsymbol{z}_l, \boldsymbol{z}_{l+1:L})$. We can approximate this posterior by defining

\[
q_{\boldsymbol{\phi}}(\boldsymbol{z}_l|\boldsymbol{x}, \boldsymbol{z}_{l+1:L}) \propto p_{\boldsymbol{\theta}}(\boldsymbol{z}_l|\boldsymbol{z}_{l+1:L})\tilde{q}_{\boldsymbol{\phi}}(\boldsymbol{z}_l|\boldsymbol{x}, \boldsymbol{z}_{l+1:L})
\]

where $\tilde{q}_{\boldsymbol{\phi}}(\boldsymbol{z}_l|\boldsymbol{x}, \boldsymbol{z}_{l+1:L})$ is a learned Gaussian approximation to the bottom-up likelihood. If both prior and likelihood are Gaussian, we can compute this product in closed form, as proposed in the **ladder network** paper [Sn+16; Son+16].$^8$ A more flexible approach is to let $q_{\boldsymbol{\phi}}(\boldsymbol{z}_l|\boldsymbol{x}, \boldsymbol{z}_{l+1:L})$ be learned, but to force it to share some of its parameters with the learned prior $p_{\boldsymbol{\theta}}(\boldsymbol{z}_l|\boldsymbol{z}_{l+1:L})$, as proposed in [Kin+16]. This reduces the number of parameters in the model, and ensures that the posterior and prior remain somewhat close.

### 21.5.2 Example: very deep VAE

There have been many papers exploring different kinds of HVAE models (see e.g., [Kin+16; Sn+16; Chi21a; VK20a; Maa+19]), and we do not have space to discuss them all. Here we focus on the “very deep VAE” or VD-VAE model of [Chi21a], since it is simple but yields state of the art results (at the time of writing).

The architecture is a simple convolutional VAE with bidirectional inference, as shown in Figure 21.12. For each layer, the prior and posterior are diagonal Gaussians. The author found that nearest-neighbor upsampling (in the decoder) worked much better than transposed convolution, and avoided posterior collapse. This enabled training with the vanilla VAE objective, without needing any of the tricks discussed in Section 21.5.4.

The low-resolution latents (at the top of the hierarchy) capture a lot of the global structure of each image; the remaining high-resolution latents are just used to fill in details, that make the image look more realistic, and improve the likelihood. This suggests the model could be useful for lossy compression, since a lot of the low-level details can be drawn from the prior (i.e., “hallucinated”), rather than having to be sent by the encoder.

We can also use the model for unconditional sampling at multiple resolutions. This is illustrated in Figure 21.13, using a model with 78 stochastic layers trained on the FFHQ-256 dataset.^9.

9. This is a 256^2 version of the Flickr-Faces High Quality dataset from https://github.com/NVlabs/ffhq-dataset, which has 80k images at 1024^2 resolution.

### 21.5.3 Connection with autoregressive models

Until recently, most hierarchical VAEs only had a small number of stochastic layers. Consequently the images they generated have not looked as good, or had as high likelihoods, as images produced by other models, such as the autoregressive PixelCNN model (see Section 22.3.2). However, by endowing VAEs with many more stochastic layers, it is possible to outperform AR models in terms of likelihood and sample quality, while using fewer parameters and much less computing power [Chi21a; VK20a; Maa+19].

To see why this is possible, note that we can represent any AR model as a degenerate VAE, as shown in Figure 21.14(left). The idea is simple: the encoder copies the input into latent space by setting \(\mathbf{z}_{1:D} = \mathbf{x}_{1:D}\) (so \(q_\phi(z_i = x_i | \mathbf{z}_{>i}, \mathbf{x}) = 1\)), then the model learns an autoregressive prior \(p_\theta(\mathbf{z}_{1:D}) = \prod_d p(z_d | \mathbf{z}_{1:d-1})\), and finally the likelihood function just copies the latent vector to output space, so \(p_\theta(x_i = z_i | \mathbf{x}) = 1\). Since the encoder computes the exact (albeit degenerate) posterior, we have \(q_\phi(\mathbf{z}|\mathbf{x}) = p_\theta(\mathbf{z}|\mathbf{x})\), so the ELBO is tight and reduces to the log likelihood,

\[
\log p_\theta(\mathbf{x}) = \log p_\theta(\mathbf{z}) = \sum_d \log p_\theta(x_d | \mathbf{x}_{<d}) \tag{21.69}
\]

Thus we can emulate any AR model with a VAE providing it has at least \(D\) stochastic layers, where \(D\) is the dimensionality of the observed data.

In practice, data usually lives in a lower-dimensional manifold (see e.g., [DW19]), which can allow for a much more compact latent code. For example, Figure 21.14(right) shows a hierarchical code in which the latent factors at the lower level are conditionally independent given the higher level, and hence can be generated in parallel. Such a tree-like structure can enable sample generation in \(O(\log D)\) time, whereas an autoregressive model always takes \(O(D)\) time. (Recall that for an image \(D\) is the number of pixels, so it grows quadratically with image resolution. For example, even a tiny \(32 \times 32\) image has \(D = 3072\).)

In addition to speed, hierarchical models also require many fewer parameters than “flat” models. The typical architecture used for generating images is a **multi-scale** approach: the model starts from a small, spatially arranged set of latent variables, and at each subsequent layer, the spatial resolution is increased (usually by a factor of 2). This allows the high level to capture global, long-range correlations (e.g., the symmetry of a face, or overall skin tone), while letting lower levels capture fine-grained details.

![](img/ca72c1626f4850f058a9edc138c1ac73_833_0.png)

Figure 21.12: The top-down encoder used by the hierarchical VAE in [Chi21a]. Each convolution is preceded by the GELU nonlinearity. The model uses average pooling and nearest-neighbor upsampling for the pool and unpool layers. The posterior q_phi and prior p_theta are diagonal Gaussians. From Figure 3 of [Chi21a]. Used with kind permission of Rewon Child.

![](img/ca72c1626f4850f058a9edc138c1ac73_833_1.png)

Figure 21.13: Samples from a VD-VAE model (trained on FFHQ dataset) from different levels of the hierarchy. From Figure 1 of [Chi21a]. Used with kind permission of Rewon Child.

Latent variables are identical to observed variables

Latent variables allow for parallel generation

Figure 21.14: Left: a hierarchical VAE which emulates an autoregressive model using an identity encoder, autoregressive prior, and identity decoder. Right: a hierarchical VAE with a 2 layer hierarchical latent code. The bottom hidden nodes (black) are conditionally independent given the top layer. From Figure 2 of [Chi21a]. Used with kind permission of Rewon Child.
