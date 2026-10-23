
Furthermore, we have

$$|\mathbf{M}|=|\mathbf{M}/\mathbf{H}|\,|\mathbf{H}|=|\mathbf{M}/\mathbf{E}|\,|\mathbf{E}| \tag{C.129}$$

$$|\mathbf{M}/\mathbf{H}|=\frac{|\mathbf{M}/\mathbf{E}|\,|\mathbf{E}|}{|\mathbf{H}|} \tag{C.130}$$

$$|\mathbf{E}-\mathbf{F}\mathbf{H}^{-1}\mathbf{G}|=|\mathbf{H}-\mathbf{G}\mathbf{E}^{-1}\mathbf{F}|\,|\mathbf{H}^{-1}|\,|\mathbf{E}| \tag{C.131}$$

Hence (setting $\mathbf{E}=\mathbf{A}$, $\mathbf{F}=-\mathbf{u}$, $\mathbf{G}=\mathbf{v}^{\top}$, $\mathbf{H}=1$) we have

$$|\mathbf{A}+\mathbf{u}\mathbf{v}^{\top}|=(1+\mathbf{v}^{\top}\mathbf{A}^{-1}\mathbf{u})|\mathbf{A}| \tag{C.132}$$

This is known as the **matrix determinant lemma**.

## C.4 Eigenvalue decomposition (EVD)

In this section, we review some standard material on the **eigenvalue decomposition** or **EVD** of square (real-valued) matrices.

### C.4.1 Basics

Given a square matrix $\mathbf{A}\in\mathbb{R}^{n\times n}$, we say that $\lambda\in\mathbb{R}$ is an **eigenvalue** of $\mathbf{A}$ and $\mathbf{u}\in\mathbb{R}^{n}$ is the corresponding **eigenvector** if

$$\mathbf{A}\mathbf{u}=\lambda\mathbf{u},\quad \mathbf{u}\neq 0. \tag{C.133}$$

Intuitively, this definition means that multiplying $\mathbf{A}$ by the vector $\mathbf{u}$ results in a new vector that points in the same direction as $\mathbf{u}$, but is scaled by a factor $\lambda$. For example, if $\mathbf{A}$ is a rotation matrix, then $\mathbf{u}$ is the axis of rotation and $\lambda=1$.

Note that for any eigenvector $\mathbf{u}\in\mathbb{R}^{n}$, and scalar $c\in\mathbb{R}$,

$$\mathbf{A}(c\mathbf{u})=c\mathbf{A}\mathbf{u}=c\lambda\mathbf{u}=\lambda(c\mathbf{u}) \tag{C.134}$$

Hence $c\mathbf{u}$ is also an eigenvector. For this reason when we talk about “the” eigenvector associated with $\lambda$, we usually assume that the eigenvector is normalized to have length 1 (this still creates some ambiguity, since $\mathbf{u}$ and $-\mathbf{u}$ will both be eigenvectors, but we will have to live with this).

We can rewrite the equation above to state that $(\lambda,\mathbf{x})$ is an eigenvalue-eigenvector pair of $\mathbf{A}$ if

$$(\lambda\mathbf{I}-\mathbf{A})\mathbf{u}=0,\quad \mathbf{u}\neq 0. \tag{C.135}$$

Now $(\lambda\mathbf{I}-\mathbf{A})\mathbf{u}=0$ has a non-zero solution to $\mathbf{u}$ if and only if $(\lambda\mathbf{I}-\mathbf{A})$ has a non-empty nullspace, which is only the case if $(\lambda\mathbf{I}-\mathbf{A})$ is singular, i.e.,

$$\det(\lambda\mathbf{I}-\mathbf{A})=0. \tag{C.136}$$

This is called the **characteristic equation** of $\mathbf{A}$. (See Exercise C.2.) The $n$ solutions of this equation are the $n$ (possibly complex-valued) eigenvalues $\lambda_i$, and $\mathbf{u}_i$ are the corresponding eigenvectors. It is standard to sort the eigenvectors in order of their eigenvalues, with the largest magnitude ones first.

The following are properties of eigenvalues and eigenvectors.

Thus multiplying by any symmetric matrix **A** can be interpreted as multiplying by a rotation matrix **U**ᵀ, a scaling matrix **Λ**, followed by an inverse rotation **U**.

Once we have diagonalized a matrix, it is easy to invert. Since **A** = **UΛU**ᵀ, where **U**ᵀ = **U**⁻¹, we have

$$\mathbf{A}^{-1}=\mathbf{U}\Lambda^{-1}\mathbf{U}^{\mathsf T}=\sum_{i=1}^{d}\frac{1}{\lambda_i}\mathbf{u}_i\mathbf{u}_i^{\mathsf T} \tag{C.144}$$

This corresponds to rotating, unscaling, and then rotating back.

### C.4.3.1 Checking for positive definiteness

We can also use the diagonalization property to show that a symmetric matrix is positive definite iff all its eigenvalues are positive. To see this, note that

$$\mathbf{x}^{\mathsf T}\mathbf{A}\mathbf{x}=\mathbf{x}^{\mathsf T}\mathbf{U}\Lambda\mathbf{U}^{\mathsf T}\mathbf{x}=\mathbf{y}^{\mathsf T}\Lambda\mathbf{y}=\sum_{i=1}^{n}\lambda_i y_i^2 \tag{C.145}$$

where **y** = **U**ᵀ**x**. Because $y_i^2$ is always nonnegative, the sign of this expression depends entirely on the $\lambda_i$'s. If all $\lambda_i>0$, then the matrix is positive definite; if all $\lambda_i\geq 0$, it is positive semidefinite. Likewise, if all $\lambda_i<0$ or $\lambda_i\leq 0$, then **A** is negative definite or negative semidefinite respectively. Finally, if **A** has both positive and negative eigenvalues, it is indefinite.

### C.4.4 Geometry of quadratic forms

A **quadratic form** is a function that can be written as

$$f(\mathbf{x})=\mathbf{x}^{\mathsf T}\mathbf{A}\mathbf{x} \tag{C.146}$$

where **x** ∈ ℝⁿ and **A** is a positive definite, symmetric $n$-by-$n$ matrix. Let **A** = **UΛU**ᵀ be a diagonalization of **A** (see Sec. [C.4.3](#)). Hence we can write

$$f(\mathbf{x})=\mathbf{x}^{\mathsf T}\mathbf{A}\mathbf{x}=\mathbf{x}^{\mathsf T}\mathbf{U}\Lambda\mathbf{U}^{\mathsf T}\mathbf{x}=\mathbf{y}^{\mathsf T}\Lambda\mathbf{y}=\sum_{i=1}^{n}\lambda_i y_i^2 \tag{C.147}$$

where $y_i=\mathbf{x}^{\mathsf T}\mathbf{u}_i$ and $\lambda_i>0$ (since **A** is positive definite). The level sets of $f(\mathbf{x})$ define hyper-ellipsoids. For example, in 2d, we have

$$\lambda_1y_1^2+\lambda_2y_2^2=r \tag{C.148}$$

which is the equation of a 2d ellipse. This is illustrated in Fig. [C.6](#). The eigenvectors determine the orientation of the ellipse, and the eigenvalues determine how elongated it is.

### C.4.5 Standardizing and whitening data

Suppose we have a dataset **X** ∈ ℝᴺˣᴰ. It is common to preprocess the data so that each column has zero mean and unit variance. This is called standardizing the data, as we discussed in Sec. [10.2.8](#).

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_819_0.png)

Figure C.6: Visualization of a level set of the quadratic form $(\mathbf{x} - \boldsymbol{\mu})\top \mathbf{A} (\mathbf{x} - \boldsymbol{\mu})$ in $2d$. The major and minor axes of the ellipse are defined by the first two eigenvectors of $\mathbf{A}$, namely $\mathbf{u}_1$ and $\mathbf{u}_2$. Adapted from Figure 2.7 of [Bis06]. Generated by *gaussEvec.m*.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_819_1.png)

Figure C.7: (a) Height/weight data. (b) Standardized. (c) PCA Whitening. (d) ZCA whitening. Numbers refer to the first 4 datapoints, but there are 73 datapoints in total. Generated by *height_weight_whiten_plot.py*.

Although standardizing forces the variance to be 1, it does not remove correlation between the columns. To do that, we must **whiten** the data. To define this, let the empirical covariance matrix be $\mathbf{\Sigma} = \frac{1}{N} \mathbf{X}^\top \mathbf{X}$, and let $\mathbf{\Sigma} = \mathbf{E} \mathbf{D} \mathbf{E}^\top$ be its diagonalization. Equivalently, let $[\mathbf{U}, \mathbf{S}, \mathbf{V}]$ be the SVD of $\mathbf{X}$ (so $\mathbf{E} = \mathbf{V}$ and $\mathbf{D} = \mathbf{S}^2$, as we discuss in Sec. 20.1.3.3.) Now define

$$\mathbf{W}_{pca} = \mathbf{D}^{-\frac{1}{2}} \mathbf{E}^\top \tag{C.149}$$

This is called the **PCA whitening** matrix. (We discuss PCA in Sec. 20.1.) Let $\mathbf{y} = \mathbf{W}_{pca} \mathbf{x}$ be a transformed vector. We can check that its covariance is white as follows:

$$\text{Cov}[\mathbf{y}] = \mathbf{W} \mathbb{E}[\mathbf{x}\mathbf{x}^\top] \mathbf{W}^\top = \mathbf{W} \mathbf{\Sigma} \mathbf{W}^\top = (\mathbf{D}^{-\frac{1}{2}} \mathbf{E}^\top)(\mathbf{E} \mathbf{D} \mathbf{E}^\top)(\mathbf{E} \mathbf{D}^{-\frac{1}{2}}) = \mathbf{I} \tag{C.150}$$

The whitening matrix is not unique, since any rotation of it, $\mathbf{W} = \mathbf{R} \mathbf{W}_{pca}$, will still maintain the whitening property, i.e., $\mathbf{W}^\top \mathbf{W} = \mathbf{\Sigma}^{-1}$. For example, if we take $\mathbf{R} = \mathbf{E}$, we get

$$\mathbf{W}_{zca} = \mathbf{E} \mathbf{D}^{-\frac{1}{2}} \mathbf{E}^\top = \mathbf{\Sigma}^{-\frac{1}{2}} = \mathbf{V} \mathbf{S}^{-1} \mathbf{V}^\top \tag{C.151}$$

This is called Mahalanobis whitening or ZCA. (ZCA stands for “zero-phase component analysis”, and was introduced in [BS97].) The advantage of ZCA whitening over PCA whitening is that the resulting transformed data is as close as possible to the original data (in the least squares sense) [Amo17]. It is illustrated in Fig. C.7. When applied to images, the ZCA transformed data vectors still look like images. This is useful when the method is used inside a deep learning system [KH09].

### C.4.6 Power method

We now describe a simple iterative method for computing the eigenvector corresponding to the largest eigenvalue of a real, symmetric matrix; this is called the power method. This can be useful when the matrix is very large but sparse. For example, it used by Google’s PageRank to compute the stationary distribution of the transition matrix of the world wide web (a matrix of size about 3 billion!). In Sec. C.4.7, we will see how to use this method to compute subsequent eigenvectors and values.

Let A be a matrix with orthonormal eigenvectors u_i and eigenvalues |λ1| > |λ2| ≥ ⋯ ≥ |λm| ≥ 0, so A = U Λ U^T. Let v0 be an arbitrary vector in the range of A, so A x = v0 for some x. Hence we can write v0 as v0 = U Λ U^T x = a1 u1 + ⋯ + am um (C.152) for some constants a_i. We can now repeatedly multiply v by A and renormalize: v_t ∝ A v_{t-1} (C.153) (We normalize at each iteration for numerical stability.)

Since v_t is a multiple of A^t v0, we have v_t ∝ a1 λ1^t u1 + a2 λ2^t u2 + ⋯ + am λm^t um = λ1^t (a1 u1 + a2 (λ2/λ1) u2 + ⋯ + am (λm/λ1) um) → λ1^t a1 u1 (C.156) since |λk/λ1| < 1 for k > 1 (assuming the eigenvalues are sorted in descending order). So we see that this converges to u1, although not very quickly (the error is reduced by approximately |λ2|/|λ1| at each iteration). The only requirement is that the initial guess satisfy v0^T u1 ≠ 0, which will be true for a random v0 with high probability.

We now discuss how to compute the corresponding eigenvalue, λ1. Define the Rayleigh quotient to be R(A, x) ≜ x^T A x / x^T x (C.157) Hence R(A, u_i) = u_i^T A u_i / u_i^T u_i = λ_i (C.158) Thus we can easily compute λ1 from u1 and A. See power_method_demo.py for some code.
