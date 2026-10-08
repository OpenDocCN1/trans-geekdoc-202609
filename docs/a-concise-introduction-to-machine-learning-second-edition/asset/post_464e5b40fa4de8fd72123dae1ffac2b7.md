
## Dimensionality Reduction

In the previous chapters, the features were taken as given. The kernel trick was introduced through a mapping of the feature space to a higher dimensional space, where the data samples are more easily separable. This higher dimensional space can be viewed as creating new features from the given, combining them in space. Often, the data samples lie in a dimensional set of the feature space. So there is opportunity to go down this dimension.

For example in an 8-bit gray scale image, each pixel has a value between 0 (black) and 255 (white). A standard sized image of 1280 by 720 pixels therefore encoded in 921,600 bytes or approaching one megabyte. In other words, humans are quite well adapted to interpret misprinted information in an image. The Joint Photographic Experts group (JPEG) used this in 1992 to create a standard for lossless image compression.

The image is first divided into $n \times n$ blocks. For the example size above, this results in 14,000 blocks. Instead of storing 64 pixel values for each block, each block is built by overlapping blocks from Figure 7.1 with appropriate weights. Weights are only allowed to have integer values. Many weights will be zero, because few blocks in the image will have high variations, which will have a moderate variation between pixels, some will be mostly one smooth shade of gray. By changing the focus away from the individual pixel to groups of pixels, i.e. few bytes are needed to encode the image.

In mathematical terms, this is a change of basis. When storing the values for each pixel in a block, this is equivalent to using a basis where all values are zero, but one, and the position of this nonzero pixel traverses the block. The weights for this basis are the individual pixel values, and will not be nonzero. The other basis is shown in Figure 7.1. When representing the block in this basis, only a few nonzero weights are necessary.

![](img/c6c76bf52016db7e78a5e30d4766ef81_222_0.png)

Figure 7.1: Discrete Cosine Transform basis of the JPEG standard.

In this chapter, we introduce techniques to find representations of the data samples with different, but fewer features.

## 7.1 Principal Component Analysis

Principal Component Analysis seeks a subspace of a given dimension $K$ of the feature space such that projections of the data samples onto that subspace are spread out as possible. If there is space between groups of data samples, this has advantages when clustering or classifying. This subspace is known as the principal subspace.

Let $D = \{v_1, \dots, v_n\}$ be a set of data samples. We first consider the projection onto a one-dimensional subspace defined by the vector $w$. Just as in the case of linear classification, only the direction of the vector is important, not its length. The length is chosen to be $\|w\| = 1$, so that the projection of the sample $v_n$ is calculated as $w^T v_n$.

The sample mean is given by

```
$$\mu = \frac{1}{N} \sum_{n=1}^N v_n$$
```

while the sample covariance matrix

```
$$\Sigma = \frac{1}{N} \sum_{n=1}^N (v_n - \mu)(v_n - \mu)^T \quad (7.1)$$
```

which is symmetric.

The variance of the projected samples is

```
$$\sum_{n=1}^{N}(\mathbf{w}^T\mathbf{v}_n - \mathbf{w}^T\mu)^2 = \frac{1}{N} \sum_{n=1}^{N} \mathbf{w}^T\mathbf{v}_n\mathbf{v}_n^T\mathbf{w} - 2\mathbf{w}^T\mu\mathbf{w}^T + \mathbf{w}^T\mu\mathbf{w}^T = \mathbf{w}^T[\frac{1}{N} \sum_{n=1}^{N}(\mathbf{v}_n - \mu)(\mathbf{v}_n - \mu)^T]\mathbf{w}$$
```

The objective is to maximize this, because we want the data to be as much stretched as possible, subject to the constraint $\|\mathbf{w}\|^2 = \mathbf{w}^T\mathbf{w} = 1$. The Lagrangian is given by

```
$L(\mathbf{w},\lambda) = \mathbf{w}^T\mathbf{\Sigma} - \lambda(\mathbf{w}^T\mathbf{w} - 1)$
```

A stationary point of $L(\mathbf{w},\lambda)$ is a maximum of the constraint optimization. Using A.2.3 and A.2.2, the derivative of $L(\mathbf{w},\lambda)$ with respect to $\mathbf{w}$ is

```
$$\frac{\partial}{\partial\mathbf{w}}L(\mathbf{w},\lambda) = 2\mathbf{\Sigma}\mathbf{w} - 2\lambda\mathbf{w}$$
```

Setting this to zero, gives

```
$$\mathbf{\Sigma}\mathbf{w} = \lambda\mathbf{w}$$
```

and thus $\mathbf{w}^T\mathbf{w} = 1$, the eigenvalue is

```
$$\lambda = \mathbf{w}^T\mathbf{\Sigma}\mathbf{w}$$
```

which is the variance of the projected data. Then, the data will be as spread out as possible, if $\mathbf{w}$ is chosen to be the eigenvector of $\mathbf{\Sigma}$ with the largest eigenvalue.

Being a covariance matrix, $\mathbf{\Sigma}$ has nonnegative eigenvalues. Since $\mathbf{\Sigma}$ is symmetric, its eigenvectors are orthogonal to each other. Therefore the principal space of dimension $K$, where the projected data has the largest variance, is the subspace spanned by the eigenvectors of the $K$ largest eigenvalues. These are known as principal components.

We illustrate on this MNIST dataset of handwritten digits LeCun et al. (1998) gathered. This dataset contains 60000 of handwritten digits of size $28\times28$. We concentrate on distinguishing between the zeros and ones. Figures 7.2b and 7.2c shows the representations of the same digits using two or three principal components. 7.2b the original digits can be vaguely discerned in most cases, but in 7.2c there seems to be little resemblance to the original digits. Figures 7.2d and 7.2e, however, display the location of samples in the space spanned by two or three principal components, respectively. Note that the sets of zeros and ones are separated. The objective was not the reconstruction of the images, but the separation of digits. To reconstruct the images perfectly would require $28\times28=784$ pixels or components

![](img/c6c76bf52016db7e78a5e30d4766ef81_224_0.png)

Figure 7.2: PCA for two digits.

components would be necessary. Even a reasonably good reconstruction would require more principal components than just two or three, but this was not the aim. Figures 7.3 and 7.4 do the same for three or four digits, respectively. Three digits could be separated using two principal components as 7.3d, but there is some overlap of the datasets. The separation is better with three principal components in 7.3c. Separating four digits is impossible with two principal components as 7.4d illustrates. Going to three dimensions with three principal components is an improvement in 7.4e, but using a further principal component is advisable. Note, that each of the figures 7.2, 7.3 and 7.4 the principal components are different, since including data samples of a further digit changes the covariance matrix $\Sigma$ and the eigenvectors are different for different datasets. In Chapter 5 we have seen how boosting builds strong classifiers from weak ones. PCA can help identify weak classifiers.

![](img/c6c76bf52016db7e78a5e30d4766ef81_225_0.png)

(a) Original.

(b) Reconstruction with two principal components.

(c) Reconstruction with three principal components.

![](img/c6c76bf52016db7e78a5e30d4766ef81_225_1.png)

(d) Sample locations in subspace spanned by two principal components.

(e) Sample locations in subspace spanned by three principal components.

Figure 7.3: PCA for three digits.

Listing 7.1 implements this analysis using grey-scale images while Figures 7.2 to 7.4 were generated by MATLAB on black and white images. Grey-scale already contains information which can be observed when comparing the reconstructions of these different implementations. The original dimension of the feature space is $D=784$, the number of pixels. Let $w_1, \dots, w_D$ be the complete set of orthonormal (orthogonal and of length 1) eigenvectors of $\Sigma$ with corresponding eigenvalues $\lambda_1, \dots, \lambda_D$ sorted by decreasing size of eigenvalue. This is also a basis of the feature space. Each sample $\mathbf{v}_n$ can be expressed in this decomposition into

```
$$\mathbf{v}_n = \sum_{d=1}^D (\mathbf{v}_n^T \mathbf{w}_d) \mathbf{w}_d$$
```
