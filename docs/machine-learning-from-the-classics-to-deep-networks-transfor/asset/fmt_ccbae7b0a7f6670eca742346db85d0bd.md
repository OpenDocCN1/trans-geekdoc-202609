
$$
\overline{\mathbf{x}} = \frac{1}{N}\sum\limits_{n = 1}^{N}\mathbf{x}_{n}
$$

![Equation](images/B9780443292385000263/si94.png)

*   and `x` denotes the original (not centered) vector.

*   PCA builds upon *global* information spread over *all* the data observations in the set $\mathcal{X}$. Indeed, the main source of information is the sample covariance matrix `XX^T`. Thus, PCA is effective if the covariance matrix provides a sufficiently rich description of the data at hand. For example, this is the case for Gaussian-like distributions. In [41], modifications of the standard approach are suggested in order to deal with data having a clustered nature. Soon, we are going to discuss techniques alternative to PCA in order to overcome this drawback.

*   Computing the SVD of large matrices can be computationally costly and a number of efficient techniques have been proposed (see, e.g., [1,83,194]). In a number of cases in practice, it turns out that `l > N`. Of course, in this case, the sample covariance is not invertible and some of the eigenvalues are zero. In such scenarios, it is preferable to work with an `X^T X` (`N × N`) instead of an `XX^T` (`l × l`) matrix. To this end, the relationships given in Section [6.4](#Chp006_249-291_B9780443292385000123.xhtml), in order to obtain `u[i]` from `v[i]`, can be employed.

*   The treatment of PCA bears a similarity with the Fisher linear discriminant (FLD) method (Chapter [7](#Chp007_293-342_B9780443292385000135.xhtml)). They both rely on the eigenstructure of matrices that, in one way or another, encode (co)variance information. However, note that PCA is an *unsupervised* method, in contrast to FLD, which is a *supervised* one. As a consequence, PCA performs dimensionality reduction so as to preserve data variability (variance) while FLD class separability. [Fig. 20.3](#Chp020_1103-1179_B9780443292385000263.xhtml#f0025) demonstrates the difference in the resulting (hyper)planes.

![Figure 20.3 The case of a two-class task in the two-dimensional space. PCA computes the direction along which the variance is maximally retained after the projections of the data on it. In contrast, FLD computes the line so that the class separability is maximized.](images/B9780443292385000263/gr003.jpg)

[Figure 20.3](#Chp020_1103-1179_B9780443292385000263.xhtml#cf0365) The case of a two-class task in the two-dimensional space. PCA computes the direction along which the variance is maximally retained after the projections of the data on it. In contrast, FLD computes the line so that the class separability is maximized.

*   *Multidimensional scaling* (MDS) is another linear technique used to project in a lower-dimensional space, while respecting certain constraints. Given the set $\mathcal{X} \subset \mathbb{R}^{(l)}$, the goal is to project onto a lower-dimensional space, so that inner products are optimally preserved; that is, the cost

$$
E = \sum\limits_{i}\sum\limits_{j}\left( \mathbf{x}_{i}^{T}\mathbf{x}_{j} - \mathbf{z}_{i}^{T}\mathbf{z}_{j} \right)^{2}
$$

![Equation](images/B9780443292385000263/si100.png)

*   is minimized, where `z_i` is the image of `x_i` and the sum runs over all the training points in $\mathcal{X}$. The problem is similar to PCA and it can be shown that the solution is given by the eigendecomposition of the Gram matrix,^([^(156)](#fn156))

*   More on these issues can be found in [29,60]. As we will soon see in Section [20.9](#Chp020_1103-1179_B9780443292385000263.xhtml#s0145), the main idea behind MDS of preserving the distances is used, in one way or another, in a number of more recently developed nonlinear dimensionality reduction techniques.
