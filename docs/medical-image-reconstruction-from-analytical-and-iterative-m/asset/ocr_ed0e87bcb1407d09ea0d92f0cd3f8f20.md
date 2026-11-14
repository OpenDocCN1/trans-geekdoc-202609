worsens the image noise. Therefore, Inouye's algorithm is the preferred algorithm between these two algorithms.

As presented in Section 4.5.2, Inouye's algorithm converts the uniformly attenuated Radon transform into unattenuated Radon transform, as expressed by eq. (4.26). Therefore, the regular FBP algorithm can be used for image reconstruction.

In order to further control noise, the Landweber-FBP algorithm presented in Section 8.4.3 as well as the algorithms presented in Sections 8.5, 8.6, and 8.7 can be directly applied to the corrected, unattenuated projections provided by eq. (4.26).

# 8.10 Other applications of the Landweber-FBP algorithm

# 8.10.1 The Landweber-FBP version of the iterative FBP algorithm

In a regular iterative image reconstruction algorithm, the projection-domain data is directly backprojected into the image domain. Before backprojection, a noise-weighing function, w, is assigned to projection-domain data, which is the projection-domain discrepancy in an iterative Landweber algorithm.

In an iterative FBP algorithm, the projection-domain data is filtered with prespecified filter. This filter can be chosen as the ramp filter, a Laplacian filter, or a lowpass filter. In a Bayesian algorithm, the Bayesian terms in the objective function can also contain filters. As an example, an objective function can be expressed as follows:

```
\(\chi^2 = (AX - P)^T M (AX - P) + \beta(FX)^T \hat{M} (FX),\quad (8.59)\)
```

where _M_ and \(\hat{M}\) are two Toeplitz square matrices. We must point out that if the matrix _M_ is a diagonal matrix, it acts as noise weighting instead of a filter. Noise weighting only scales a value up or down. On the other hand, a filter uses neighboring values as well.

A linear convolution can always be expressed as a Toeplitz matrix multiplication. A Landweber algorithm can be used to minimize this objective function. Using the similar method in Section 8.5, a Landweber Bayesian algorithm can be obtained as

```
\(X^{(k)} = (A^TMA + \beta F^T\hat{M}F)^{-1} \left[ I - \left( I - \alpha A^TMA - \alpha \beta F^T\hat{M}F \right)^k \right] A^TMP\)
\(+ \left( I - \alpha A^TMA - \alpha \beta F^T\hat{M}F \right)^k X^{(0)},\quad (8.60)\)
```

To illustrate how this can be translated into the Fourier domain, let's consider an example of \(\beta = 0\), \(X^{(0)} = 0\), and _M_ is the Laplacian filter (that is, a second-order derivative filter). The transfer function of the 1D Laplacian filter is \(\omega^2\), and the transfer function of the 2D Laplacian filter is \(\|\vec{\omega}\|^2\). Thus, eq. (8.60) has a 2D transfer function of