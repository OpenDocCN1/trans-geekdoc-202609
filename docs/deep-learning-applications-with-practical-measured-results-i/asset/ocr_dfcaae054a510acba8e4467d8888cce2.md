$L_F(\mathbf{x}, \hat{\mathbf{x}}) = \frac{\|\hat{\mathbf{x}} - \mathbf{x}\|_2^2}{\|\mathbf{x}\|_2^2}. \tag{6}$

It is worth noting that the denominator of Equation (6) cannot be zero. However, since x is taken from the natural images instead of artificial generated matrices, it is impossible for x to be a zero matrix.

# 2.3.3. Discrete Wavelet Similarity (DW-SSIM) and DW-SSIM Loss

Inspired by structural similarity (SSIM) [47] and complex-wavelet structure similarity (CW-SSIM) [48], we propose to use two-dimensional discrete wavelet transform (2D-DWT) [49] to analyze the similarity between the recovered image and the original image. The similarity is termed DW-SSIM which stands for discrete-wavelet similarity.

2D-DWT. The 2D-DWT is able to decompose an image into different levels of subbands. The first level is the decomposition of the original image. Each level is composed of four subband images which can be referred to as low–low (LL), low–high (LH), high–low (HL) and high–high (HH). The LL image at each level can be further decomposed into the next level of subbands. The LH image represents the variation along the vertical direction, HL image the horizontal direction, and HH image the diagonal direction [49]. The high-frequency LH, HL, and HH subband images altogether form the details of the original image. As the decomposition level goes higher, the subband images become coarser, thus details of different scales can be analyzed. Figure 4 provides an example of a three-level 2D-DWT decomposition of an image.

![](bbox=[0.35, 0.48, 0.55, 0.64])

(a)

![](bbox=[0.2, 0.68, 0.8, 0.83])

(b)

Figure 4. Illustration of 2D-discrete wavelet transform (DWT) image decomposition. (a) Original image. (b) Three-level decomposition of the image. For clarity, every intermediate low–low (LL) image is put in its place, yet DWT only preserves the LL image of the highest level.

DW-SSIM. We divide the calculation of DW-SSIM between the original image and the recovered image into two stages. The first stage involves figuring out the local DW-SSIM, where a “window” slides through the original image and the recovered image. 2D-DWT is performed on the image patches