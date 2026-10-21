![](bbox=[0.12, 0.08, 0.9, 0.27])

# 11.3 Gaussian mixture models

The Gaussian mixture model (GMM) is a simple linear superposition of Gaussian components over the data, aimed at providing a rich class of density models. We turn to a formulation of Gaussian mixtures in terms of discrete latent variables: the K hidden classes to be discovered.

Differences compared to K-means:

+   - Whereas the K-means algorithm performs a hard assignment of data points to clusters, in which each data point is associated uniquely with one cluster, the GMM algorithm makes a soft assignment based on posterior probabilities.
+   - Whereas the classic K-means is only based on Euclidean distances, classic GMM use a Mahalanobis distances that can deal with non-spherical distributions. It should be noted that Mahalanobis could be plugged within an improved version of K-Means clustering. The Mahalanobis distance is unitless and scale-invariant, and takes into account the correlations of the data set.

The Gaussian mixture distribution can be written as a linear superposition of K Gaussians in the form:

$$p(x) = \sum_{k=1}^{K} \mathcal{N}(x | \mu_k, \Sigma_k) p(k),$$

where:

+   - The p(k) are the mixing coefficients also know as the class probability of class k, and they sum to one: $\sum_{k=1}^{K} p(k) = 1$.
+   - $\mathcal{N}(x | \mu_k, \Sigma_k) = p(x | k)$ is the conditional distribution of x given a particular class k. It is the multivariate Gaussian distribution defined over a P-dimensional vector x of continuous variables.

The goal is to maximize the log-likelihood of the GMM:

$$\ln \prod_{i=1}^{N} p(x_i) = \ln \prod_{i=1}^{N} \left\{ \sum_{k=1}^{K} \mathcal{N}(x_i | \mu_k, \Sigma_k) p(k) \right\} = \sum_{i=1}^{N} \ln \left\{ \sum_{k=1}^{K} \mathcal{N}(x_i | \mu_k, \Sigma_k) p(k) \right\}.$$

To compute the classes parameters: p(k), μ_k, Σ_k we sum over all samples, by weighting each sample i by its responsibility or contribution to class k: p(k | x_i) such that for each point its