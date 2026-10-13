
Second, the estimate of the true signal is computed as $\widehat{\mathbf{y}} = \Psi\widehat{\mathbf{\theta}}$. In Chapter [20](#Chp020_1103-1179_B9780443292385000263.xhtml), we will study the case where the dictionary is not fixed and known, but is estimated from the data.

*   **Linear inverse problems**: Such problems, which come under the more general umbrella of what is known as *signal restoration*, go one step beyond denoising. Now, the available observations are *distorted* as well as noisy versions of the true signal samples; that is, $\mathbf{y} = H\widetilde{\mathbf{y}} + \mathbf{\eta}$, where *H* is a known linear operator. For example, *H* may correspond to the blurring point spread function of an image, as discussed in Chapter [4](#Chp004_119-175_B978044329238500010X.xhtml). Then, similar to the denoising example, assuming that the original signal samples can be efficiently represented in terms of an overcomplete dictionary, $\widehat{\mathbf{\theta}}$ is estimated, via any sparsity promoting method, using *H*Ψ in place of Ψ in [(9.41)](#Chp009_417-462_B9780443292385000159.xhtml#deq81), and the estimate of the true signal is obtained as $\widehat{\mathbf{y}} = \Psi\widehat{\mathbf{\theta}}$.

*   Besides deblurring, other applications that fall under this formulation include image inpainting, if *H* represents the corresponding sampling mask; inverse-Radon transform in tomography, if *H* comprises the set of parallel projections, and so on. See, for example, [49] for more details on this topic.

In this case study, the image denoising task, based on the sparse and redundant formulation as discussed above, is explored. Our starting point is the 256 × 256 image shown in [Fig. 9.13](#Chp009_417-462_B9780443292385000159.xhtml#f0075)A. In the sequel, the image is corrupted by zero mean Gaussian noise, leading to the noisy version of [Fig. 9.13](#Chp009_417-462_B9780443292385000159.xhtml#f0075)B, corresponding to a peak signal-to-noise ratio (PSNR) equal to 22 dB, which is defined as

```
PSNR = 20 log_10 ( m_I / sqrt(MSE) ),
```
(9.42)

where *m*[*I*] is the maximum pixel value of the image and `MSE = (1/N_p) || I - Ĩ ||_F^2`, where *I* and *Ĩ* are the noisy and original image matrices, *N*[*p*] is equal to the total number of pixels, and the Frobenius norm for matrices has been employed.

![Figure 9.13 Denoising based on sparse and redundant representations.](images/B9780443292385000159/gr014.jpg)

Figure 9.13 Denoising based on sparse and redundant representations.
