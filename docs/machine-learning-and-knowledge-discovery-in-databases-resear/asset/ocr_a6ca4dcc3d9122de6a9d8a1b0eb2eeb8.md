from the test set. For each of their 512 dimensions, we construct a histogram with 100 bins, showing how all activations of the dataset for an individual dimension are spread. Figure 4 displays the histograms for a selected set of dimensions. SIM's activations consistently follow a Gaussian distribution, aligning with our design goal of regularizing the latent space toward a standard normal distribution. This predictable structure helps post-hoc interpretability tools by clearly describing the regions of interest. In contrast, the latent representations produced by GIM show greater variation. In particular, dimension 9 for the artificial dataset, and dimensions 13 and 14 for LibriSpeech are shifted away from the origin or differ from the other dimensions. Note that in GIM's current implementation, the latent spaces are implicitly constrained to center around the origin due to the use of a bias-free discriminator in Eq. 2. If the discriminator were non-linear or had a bias term, the shape of the latent space could potentially be even less predictable.

![](bbox=[0.225, 0.358, 0.795, 0.625])

Fig. 4. Top rows: Artificial Dataset, bottom: LibriSpeech. Distribution of activations per dimension. SIM's activations have a consistent shape across dimensions, whereas GIM enforces no latent space constraints, resulting in greater variation in certain dimensions. Other dimensions are available here.

# 5 Related Work

This work uses the benefits of \(\beta\)-VAE's regularization, applying them across multiple layers to improve post-hoc analysis of the network.

In terms of *interpretability through regularization*, various approaches have been explored. For instance, sparsity regularization in the activations of hidden representations [2,10,30] has been shown to improve the compression of