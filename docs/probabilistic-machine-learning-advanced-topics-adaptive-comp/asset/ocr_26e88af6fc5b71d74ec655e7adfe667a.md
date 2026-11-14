# Latent variables are identical to observed variables

# Latent variables allow for parallel generation

Figure 21.14: Left: a hierarchical VAE which emulates an autoregressive model using an identify encoder, autoregressive prior, and identity decoder. Right: a hierarchical VAE with a 2 layer hierarchical latent code. The bottom hidden nodes (black) are conditionally independent given the top layer. From Figure 2 of [Chi21a]. Used with kind permission of Rewon Child.

likelihood and sample quality, while using fewer parameters and much less computing power [Chi21a; VK20a; Maa+19].

To see why this is possible, note that we can represent any AR model as a degenerate VAE, as shown in Figure 21.14(left). The idea is simple: the encoder copies the input into latent space by setting \(\mathbf{z}_{1:D} = \mathbf{x}_{1:D}\) (so \(q_\phi(z_i = x_i | \mathbf{z}_{>i}, \mathbf{x}) = 1\)), then the model learns an autoregressive prior \(p_\theta(\mathbf{z}_{1:D}) = \prod_d p(z_d | \mathbf{z}_{1:d-1})\), and finally the likelihood function just copies the latent vector to output space, so \(p_\theta(x_i = z_i | \mathbf{x}) = 1\). Since the encoder computes the exact (albeit degenerate) posterior, we have \(q_\phi(\mathbf{z}|\mathbf{x}) = p_\theta(\mathbf{z}|\mathbf{x})\), so the ELBO is tight and reduces to the log likelihood,

\(\log p_\theta(\mathbf{x}) = \log p_\theta(\mathbf{z}) = \sum_d \log p_\theta(x_d | \mathbf{x}_{<d})\) (21.69)

Thus we can emulate any AR model with a VAE providing it has at least \(D\) stochastic layers, where \(D\) is the dimensionality of the observed data.

In practice, data usually lives in a lower-dimensional manifold (see e.g., [DW19]), which can allow for a much more compact latent code. For example, Figure 21.14(right) shows a hierarchical code in which the latent factors at the lower level are conditionally independent given the higher level, and hence can be generated in parallel. Such a tree-like structure can enable sample generation in \(O(\log D)\) time, whereas an autoregressive model always takes \(O(D)\) time. (Recall that for an image \(D\) is the number of pixels, so it grows quadratically with image resolution. For example, even a tiny \(32 \times 32\) image has \(D = 3072\).)

In addition to speed, hierarchical models also require many fewer parameters than “flat” models. The typical architecture used for generating images is a **multi-scale** approach: the model starts from a small, spatially arranged set of latent variables, and at each subsequent layer, the spatial resolution is increased (usually by a factor of 2). This allows the high level to capture global, long-range correlations (e.g., the symmetry of a face, or overall skin tone), while letting lower levels capture fine-grained details.