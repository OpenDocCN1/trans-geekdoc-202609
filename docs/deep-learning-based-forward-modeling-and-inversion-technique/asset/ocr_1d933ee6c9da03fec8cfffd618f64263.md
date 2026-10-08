![](bbox=[0.185, 0.98, 0.812, 0.35])

# FIGURE 4.12

The denoising results for two different samples.

It is lucid that for the noisy data with the SNR of 5dB, the proposed denoising module is able to attenuate the Gaussian noise to a fairly low level (PSNR: 45.3dB/SSIM: 0.99), undoubtedly proving the excellent denoising performance.

# ## 4.4 Comparisons with Other Approaches

Here, the U-net and conventional denoising methods are compared from the perspective of PSNR and running time. The results are presented in Table 4.2.

# TABLE 4.2

| Noise (dB) | U-net Before | U-net After | SVD Before | SVD After | Wavelet Before | Wavelet After |
|---|---|---|---|---|---|---||
| 0 | 24.3 | 42.6 | 24.3 | 41.3 | 24.3 | 40.9 |
| 5 | 30.2 | 45.3 | 30.2 | 44.8 | 30.2 | 44.4 |
| 10 | 36.5 | 47.7 | 36.5 | 47.3 | 36.5 | 47.6 |
| 20 | 40.1 | 48.1 | 40.1 | 47.9 | 40.1 | 48.0 |
| 30 | 45.5 | 50.0 | 45.5 | 50.5 | 50.5 | 50.3 |

For the SVD algorithm, when the noise is 0, 5, 10, 20, and 30dB, the first 1, 2, 3, 5, and 7 singular values are used to reconstruct the temperature data. For the wavelet transform, two wavelet decompositions are used to filter out the high frequency noise. It can be observed that the U-net performs slightly better than SVD and wavelet transform in terms of PSNR when the Gaussian