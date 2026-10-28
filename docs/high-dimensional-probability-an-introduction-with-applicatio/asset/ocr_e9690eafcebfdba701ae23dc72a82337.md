— a version of matrix Bernstein inequality (5.17) for unbounded random matrices. Let $Z_1,\ldots,Z_N$ be independent $n\times n$ positive semidefinite random matrices. Show that

$$S := \sum_{i=1}^{N} Z_i \quad\text{satisfies}\quad \mathbb{E}\|S-\mathbb{E}S\| \le C\left(\sqrt{\|\mathbb{E}S\|\cdot L}+L\right)$$

where $L=\log(n)\,\mathbb{E}\max_i\|Z_i\|$.

6.34 (Covariance estimation for unbounded distributions) Let’s relax the boundedness assumption (5.20) in the general covariance estimation result (5.27). Let $X$ be a random vector in $\mathbb{R}^n$ with $\Sigma=\mathbb{E}XX^{\mathsf T}$. Assume that for some $K\ge 1$,

$$\mathbb{E}\max_{i\le m}\|X\|^2 \le K^2\,\mathbb{E}\|X\|^2.$$

Let $X_1,\ldots,X_m$ be i.i.d. copies of $X$, and $\Sigma_m=\frac{1}{m}\sum_{i=1}^{m}X_iX_i^{\mathsf T}$. Prove that

$$\mathbb{E}\|\Sigma_m-\Sigma\| \le C\left(\sqrt{\frac{K^2r\log n}{m}}+\frac{K^2r\log n}{m}\right)\|\Sigma\|.$$

where $r=\operatorname{tr}(\Sigma)/\|\Sigma\|$ is the effective rank of $\Sigma$.

6.35 Let $z_1,\ldots,z_N$ be any vectors in a normed space, let $a=(a_1,\ldots,a_N)\in\mathbb{R}^N$, and let $\varepsilon_1,\ldots,\varepsilon_N$ be independent Rademacher random variables. Show that the following function is convex:

$$f(a):=\mathbb{E}\left\|\sum_{i=1}^{N}a_i\varepsilon_i z_i\right\|.$$

6.36 (Contraction principle for general distributions) Let’s prove the following generalization of Theorem 6.6.1. Let $a=(a_1,\ldots,a_n)\in\mathbb{R}^n$, and let $X_1,\ldots,X_N$ be independent, mean-zero random vectors taking values in a normed space. Show that

$$\mathbb{E}\left\|\sum_{i=1}^{N}a_iX_i\right\|\le 4\|a\|_\infty\cdot\mathbb{E}\left\|\sum_{i=1}^{N}X_i\right\|.$$

6.37 (Logarithmic factor is unavoidable in Gaussian symmetrization) Show that, in general, the factor $\sqrt{\log N}$ in Lemma 6.6.2 is optimal.

6.38 (Contraction and symmetrization for functions of norms) Let $F:\mathbb{R}_+\to\mathbb{R}$ be a convex increasing function. Generalize contraction (Theorem 6.6.1) and Gaussian symmetrization (Lemma 6.6.2) by replacing the norm $\|\cdot\|$ with $F(\|\cdot\|)$ throughout.