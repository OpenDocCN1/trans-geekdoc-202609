# Clustering 143

![](bbox=[0.171, 0.093, 0.833, 0.237])

**Figure 6.2** GMM clustering. Left: Normalized histogram of T-weighted intensities of a brain MRI image. The peaks correspond to the three tissues. Middle: likelihood functions for each of the three clusters (red, green and blue lines) fitted to the image histogram. Right: overall likelihood for image intensities (black line), fitted as GMM, fitted to the image histogram.

with mean $\mu_k$ and variance $\sigma_k^2$. The intensity distributions of the whole MRI image are drawn from a mixture of Gaussian distributions (the **Gaussian Mixture Model**, GMM)

```
$p(x) = \sum_{k=1}^{K} \varrho_k G(x, \mu_k, \sigma_k^2) \quad (6.5)$
```

as visualized in Fig. 6,2, right. The mixing coefficients $\varrho_k$ represent the proportion of samples assigned to class k and they sum to one $\sum_{k=1}^{K}\varrho_k=1$. The cluster dependent conditional probability $p(x|y=k)$ and the overall image probability $p(x)$ of observing an intensity value $x$ are referred to as **likelihoods**.

# 6.2.1 GMM algorithm

The purpose of the GMM clustering algorithm is to fit the Gaussian Mixture Model (Eq. (6.5)) to the histogram of observed image intensities (Fig. 6,2, right). In others, we want to maximize the likelihood $p(X|\phi)$ of observing a particular set of image intensities $X = \{x_1, \dots, x_N\}$, given the parameters of GMM $\phi = \{\mu_k, \sigma_k, \varrho_k\}_{k=1}^{K}-$. Therefore, to fit a GMM to the image intensity distribution, we need to find the GMM parameters $\phi$ that maximize the likelihood of observing intensities X

```
$$\phi = \arg \max p(X|\phi)$
```

If we assume the voxel intensities $x_i$ are independent of each other, we can multiply the individual likelihoods $p(x_i|\phi) = \prod_{i=1}^{N}p(x_i|\phi)$, which will change to the sum if we take a logarithm of this. By using (6.5), we get a sum of log-likelihoods of the individual voxels:

```
$$\phi = \arg \max \sum_{i=1}^{N} \log p(x_i|\phi) = \arg \max \sum_{i=1}^{N} \sum_{k=1}^{K} \varrho_k G(x_i, \mu_k, \sigma_k^2). \quad (6.6)$
```