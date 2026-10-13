
**u**[*x*]^(*T*)*Σ̂*[*x**x*]**u**[*x*, *i*] = 0,  **u**[*y*]^(*T*)*Σ̂*[*y**y*]**u**[*y*, *i*] = 0,  *i* = 1, 2, …, *k*.

![Equation](images/B9780443292385000263/si158.png) (20.37)

**u**[*x*]^(*T*)*Σ̂*[*x**y*]**u**[*y*, *i*] = 0,  **u**[*y*]^(*T*)*Σ̂*[*y**x*]**u**[*x*, *i*] = 0,  *i* = 1, 2, …, *k*.

![Equation](images/B9780443292385000263/si159.png) (20.38)

In other words, every new pair of vectors is computed so as to be normalized (Eq. [(20.36)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq46)) and, at the same time, each one is orthogonal (in the generalized sense) to those obtained in the previous iteration steps (Eqs. [(20.37)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq47) and [(20.38)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq48)). Note that this guarantees that the derived canonical variates are uncorrelated to all previously derived ones. This reminds us of the uncorrelatedness property of the principal components in PCA. The only nonzero correlation in CCA, which is maximized at every iteration step, is the one between *z*[*x*, *k*] = **u**[*x*, *k*]^(*T*)**x** and *z*[*y*, *k*] = **u**[*y*, *k*]^(*T*)**y**,  *k* = 1, 2, …, *m*.

![Equation](images/B9780443292385000263/si160.png)
![Equation](images/B9780443292385000263/si161.png)

More on CCA can be found in [6,26]. Extensions of CCA in reproducing kernel Hilbert spaces have also been developed and used (see, for example, [9,89,117] and the references therein). In [89], the kernel CCA is used for content-based image retrieval. The aim is to allow retrieval of images from a text query but without reference to any labeling associated with the image. The task is treated as a cross-modal problem. A probabilistic Bayesian formulation of CCA has been given in [15,113]. A regularized CCA version, using sparsity-based arguments, has been derived in [90]. In [65], a variant of CCA is proposed, named *correlated component analysis*; instead of two directions (subspaces), a common direction is derived for both data sets. The idea behind this method is that the two data sets may not be much different, so a single direction is enough. In this way, the task has fewer free parameters to estimate. Moreover, the constraint on orthogonality is dropped, which in some cases may not be physically justifiable. A Bayesian extension of the method is provided in [147].

## Example 20.3
