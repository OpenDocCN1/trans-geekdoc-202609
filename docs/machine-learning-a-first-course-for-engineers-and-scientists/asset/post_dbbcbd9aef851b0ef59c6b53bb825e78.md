
[content]
## 10.4 Representation learning and dimensionality reduction

**Learn the PCA model**
**Data:** Training data $\mathcal{T} = \{\mathbf{x}_i\}_{i=1}^n$
**Result:** Principal axes $\mathbf{V}$ and scores $\mathbf{Z}_0$

1. Compute the mean vector $\bar{\mathbf{x}} = \frac{1}{n}\sum_{i=1}^n \mathbf{x}_i$
2. Center the data, $\mathbf{x}_{0,i} = \mathbf{x}_i - \bar{\mathbf{x}}$, for $i=1, \dots, n$
3. Construct the data matrix $\mathbf{X}_0$ according to (10.36)
4. Perform SVD on $\mathbf{X}_0$ to obtain the factorization $\mathbf{X}_0 = \mathbf{U\Sigma\mathbf{V}^T$
5. Compute principal components $\mathbf{Z}_0 = \mathbf{U\Sigma}$

## Method 10.5: Principal component analysis

This section details the derivation of PCA. We summarize the procedure in Method 10.5. It is interesting to note that the algorithm allows down to simply SVD to the centered data matrix $\mathbf{X}_0$, and this operation is independent of the choice of $q$. Here, in contrast with nonlinear autoencoders$^{15}$ we do not have to decide on the $q$ of latent representation beforehand. Instead, we decide for all possible values of $q$ from a simple SVD factorization. In fact, the orthogonal matrix $\mathbf{V}$ corresponds to a change-of-basis in $\mathbb{R}^p$. By defining a transformed matrix

$$\mathbf{Z}_0 = \frac{\mathbf{X}_0\mathbf{V}}{\sqrt{np}}_{n \times p} \quad (10.44)$$

we have not lost any information in this transformation since $\mathbf{V}$ is invertible.

The columns of $\mathbf{V}$ represent the basis vectors of the new basis. From ordered in terms of importance, that is, the auto-encoder of dimension $q$ is given by the first $q$ columns, or basis vectors. We refer to these as the *principal axes* of $\mathbf{X}_0$, for arbitrary dimension $q < p$, meaning we can obtain the best low-dimensional representation of $q$ by simply picking the first $q$ columns of the transformed data matrix $\mathbf{Z}_0$. The coordinates of the data in this reduced space are the values in $\mathbf{Z}_0$, which are entered as the principal components (or scores). We also observe that we can obtain the principal components directly from the SVD since $\mathbf{Z}_0 = \mathbf{X}_0\mathbf{V} = \mathbf{U\Sigma\mathbf{V}^T}\mathbf{V} = \mathbf{U\Sigma}$. We illustrate the PCA method in Figure 10.11 (left and right panel).

> Time limit 10.2: We have defined the principal components in terms of the centered data. However, we can also compute the non-principal components in the same way as $\mathbf{Z}' = \mathbf{ZV}$ (note that $\mathbf{Z}$ is still computed from the SVD of the centered data matrix). How is $Z$ related to $\mathbf{Z}_0$? How does this relate to the encoder mapping $\mathbf{z} = \mathbf{w}(\mathbf{x})$ that we derive later from?

At the beginning of this section we note that tight link between PCA and the covariance of the data. Indeed, an intuitive view of PCA is that it finds the directions in $\mathbb{R}^p$ along which the data vary. Specifically, the first principal axis is the direction with the largest variance. The second principal axis is the direction with the second largest variance, under the constraint that it should be orthogonal to the first axis and so on. This can be seen in Figure 10.11 where the principal axes are aligned with the directions of largest variance of the data.

To formalize this, note the (sample) variance of data is given by

$$\frac{1}{n}\sum_{i=1}^n(\mathbf{x}_i-\bar{\mathbf{x}})^T(\mathbf{x}_i-\bar{\mathbf{x}}) = \frac{1}{n}\mathbf{X}_0^T\mathbf{X}_0 = \frac{1}{n}\mathbf{U\Sigma^2\mathbf{U}^T} = \frac{1}{n}\mathbf{V\Lambda\mathbf{V}^T \quad (10.45)$$

14. In the sense of minimizing the Frobenius norm of the result.
15. This refers to the nonlinear auto-encoder used. There are extensions to auto-encoders enabling a suitable value for $q$ on the fly.

This material will be published by Cambridge University. This pre-publication is free to view and download for personal use only. Not for re-publication, re-sale or in derivative works. Andrew Lindsay, Nicholas Wahlstrom, Frederik Linde, and Thomas B. Schön. 2021.

## Generative models and learning from unlabeled data

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_231_0.png)

**Figure 10.11:** An illustration of PCA in $\mathbb{R}^2$. In the left panel some $\{x_i\}_{i=1}^n$ is shown. The middle panel shows the first (red) and second (green) principal axes. These vectors are given by the first and second column of $V$, respectively. The plot also shows the data points projected on the first principal axis (pink), which are the same as the reconstructed data points obtained by a linear auto-encoder with $q=1$ latent dimensions. The right panel shows an ellipse fitted to the covariance matrix $\frac{1}{n}XX^T$ of the data. The principal axes of the ellipse are the ones from the middle panel, but the width of the ellipse along each axis is scaled by the standard deviation in the corresponding direction. This illustrates that PCA finds an axis near $R^P$ which is rotated to align with the covariance of the data.

where $A = p \times p$ diagonal matrix with the values $\Lambda = rr^2/n$ on the diagonal. This can be recognized as an eigenvalue decomposition of the covariance matrix. Consequently, the principal axes (columns of $Y$) are the same as the eigenvectors of the covariance matrix. Furthermore, the eigenvalues are given by the squared singular values, normalized $n$. The principal axes of the ellipse are the ones from the middle panel, but the width of the ellipse along each axis is scaled by the standard deviation in the corresponding direction. This illustrates that PCA finds an axis near $R^P$ which is rotated to align with the covariance of the data.

As a final comment, we note that it often can be a good idea to standardize the data before applying PCA, in particular if the different $x_j, j=1, \dots, p$ have very different scales. Otherwise the principal directions can be heavily biased towards certain variables simply because they are expressed in a unit with dominant scale. Thus, what is most appropriate needs to be decided on a case-by-case basis.

## 10.5 Further reading

Many textbooks on machine learning contains methods and methods for unsupervised learning, including Bishop (2006), Hastie et al. (2009, Chapter 14) and Murthy (2012). A longer discussion on the GMM, and its $k$-means is found in Bishop (2006, Chapter 9). For more discussion on the fundamental choice between generative and discriminative models, see Bishop and Lassner (2007), Liang and Jordan (2008), Ng and Jordan (2001), and Wang and Tuttering (2008) and also the text by Jebara (2004).

## 10.5 Further reading

The book by Goodfellow, Bengio, et al. (2016) has more in-depth discussions about deep generative models (Chapter 20), auto-encoders (Chapter 14) and other approaches for representation learning (Chapter 15). Generative adversarial networks were introduced by Goodfellow, Pouget-Abadie, et al. (2014) and are reviewed by, among others, Creswell et al. (2018). Kobyzev et al. (2020) provide an overview of normalizing flows.

Among the deep generative models that we have not discussed in this chapter, perhaps most famous is the variational autoencoder (Diederik P. Kingma and Welling Diederik P. Kingma and Welling 2014, 19. Rezende et al. 2014) which provides a way of connecting deep generative models with auto-encoders. This model has also been used for semi-supervised learning (Diederik P. Kingma, Rezende, et al. 2014) in a way which is similar to how we used the GMM in the semi-supervised setting.
[/content]
