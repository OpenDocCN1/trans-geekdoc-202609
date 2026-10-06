features in the Breast Cancer Wisconsin dataset (Sect. 2.1.2). Note that extraction of
mological features usually requires segmentation of the object to create the region
of interest. We have already explored clustering for segmentation in Chap. 6.

# 8.1.2 Texture descriptors

Texture descriptors are summary statistics of signal values or image intensities. They
be calculated from the whole dataset, signal segments or image patches, or segmented
 of interest. These descriptors include simple statistical measures, such as mean,
median, variance, interquartile range, minimum, coefficient of
variation, kurtosis, and entropy.

For 2D and 3D images of the powerful techniques to characterize texture is
through the Grey Level Co-occurrence Matrix (GLCM). GLCM expresses voxels
of combinations of discretized intensities (grey levels) of neighboring pixels or voxels
distributed along one of the image directions. Fig. 8 shows an example GLCM calc-
un x and y directions. For each pair of intensities (i,j), we add 1 to the
position (i,j) in the GLCM matrix.

![](bbox=[0.248, 0.463, 0.752, 0.574])

8.2 Grey level co-occurrence measures. Each element of $\phi$ contains the count of neighboring
intensity pairs $(i,j)$ in direction $\phi$. Left: GLCM in x-direction $(\phi = 0$ rad). Right: GLCM in y-direction
($\phi = \pi/2$ rad).

If we normalize the GLCM matrix by the overall number of intensity pairs, it can be
preted as 2D probability distribution $p(i,j)$, we can calculate several
measures that characterize the texture of the image:

+   - **contrast:** $\sum_{i,j=0}^{l-1}(i-j)^2p(i,j)$
- **dissimilarity:** $\sum_{i,j=0}^{l-1}|i-j|p(i,j)$
- **homogeneity:** $\sum_{i,j=0}^{l-1}\frac{1}{1+(i-j)^2}p(i,j)$
- **energy:** $\sqrt{\sum_{i,j=0}^{l-1}p(i,j)^2}$
- **correlation:** $\sum_{i,j=0}^{l-1}\frac{(i-\mu_i)(j-\mu_j)}{\sigma_i\sigma_j}p(i,j)$

where i and j are discretized intensity levels, $l$ is the number of levels, $\mu_i = \sum_{i,j=0}^{l-1}ip(i,j)$,
$\mu_j = \sum_{i,j=0}^{l-1}jp(i,j)$, $\sigma^2 = \sum_{i,j=0}^{l-1}(j-\mu_j)^2p(i,j)$.
GLCM matrix can be calculated using the skimage function greymatrix as follows: