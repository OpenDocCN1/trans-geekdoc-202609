$$\hat g = \arg\min_{g'\in\mathcal H}\left[\sum_{i=1}^{n}(g'(X_i)-Y_i)^2 + \lambda\|g'\|_{\mathcal H}^2\right].$$

Then

$$\sum_{i=1}^{n}(\hat g(X_i)-Y_i)^2 \le \sum_{i=1}^{n}(g(x)-Y_i)^2 + \lambda\|g\|_{\mathcal H}^2 \le 5\epsilon^2.$$

Using Theorem 9.2, this implies that there exists $\alpha \in \mathbb{R}^n$ so that

$$\|K_{n\times n}\alpha - Y\|_2^2 \le 5\epsilon^2.$$

Since $\epsilon$ is arbitrary, $K_{n\times n}$ has to be full rank.

# 9.3 Generalization Analysis

In this section, we study the generalization behavior of kernel methods using the Rademacher complexity analysis. In particular, we want to bound the Rademacher complexities of (9.9) and (9.10).

We will consider the feature representation (9.1), with the induced kernel (9.3). We know from Theorem 9.8 that if we define the function class

$$\mathcal{F}(A) = \{f(x) \in \mathcal{H}: \|f\|_{\mathcal H}^2 \le A^2\},$$

then for any feature map that satisfies (9.3), $\mathcal{F}(A)$ can be equivalently written in the linear feature representation form as

$$\mathcal{F}(A) = \{f(x) = \langle w, \psi(x)\rangle: \langle w, w\rangle \le A^2\}. \tag{9.11}$$

That is, kernel methods with RKHS regularization are equivalent to linear model with $L_2$ regularization. In the following, we will use the two representations interchangeably.

**Theorem 9.20** Consider $\mathcal{F}(A)$ defined in (9.11). We have the following bound for its Rademacher complexity:

$$R(\mathcal{F}(A),\mathcal{S}_n) \le A\sqrt{\frac{1}{n^2}\sum_{i=1}^{n}k(X_i,X_i)}.$$

Moreover let $\mathcal{F}=\mathcal{F}(+\infty)$, then

$$R^{h}(\mathcal{F},\mathcal{S}_n) \le \frac{1}{\lambda n^2}\sum_{i=1}^{n}k(X_i,X_i),$$

where in (6.3), we set

$$h(w,\mathcal{S}_n)=h_0(w)=\frac{\lambda}{2}\langle w,w\rangle. \tag{9.12}$$