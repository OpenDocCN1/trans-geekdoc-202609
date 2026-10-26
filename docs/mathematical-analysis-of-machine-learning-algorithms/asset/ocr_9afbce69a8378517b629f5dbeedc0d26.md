Let $d = \ln |A_0^{-1} A_T|$. We obtain

$$\sum_{t=1}^T |f_t(x_t, a_t) - f_*(x_t, a_t)|$$
$$\le \sqrt{\sum_{t=1}^T \|w_t - w_*\|_{A_{t-1}}^2 \sqrt{2\ln|A_0^{-1}A_T|} + 2\ln|A_0^{-1}A_T|}$$
$$\le \sqrt{4d\sum_{t=1}^T \|w_t - w_*\|_{A_{t-1}}^2 + 8d^2}$$
$$= \sqrt{4d\sum_{t=1}^T \left[\lambda T\|w_t - w_*\|_{\mathcal{H}}^2 + 2d/T + \sum_{s=1}^{t-1} |f_t(x_s,a_s)-f_*(x_s,a_s)|^2 \right] }.$$

This implies the second desired bound. The proof of the first bound is left as an exercise. □

# **Example 17.21**

If $\mathcal{F} \subset \mathcal{H} = \{w^\top \psi(x,a): w \in \mathbb{R}^d\}$ can be embedded into a $d$-dimensional linear function class for a finite $d$, then we have the following bound from Proposition 17.20 and Proposition 15.8:

$$\text{EC}(1,\mathcal{F},T) \le 2d\ln(1 + T(BB')^2/d).$$

Since Theorem 5.3 implies that the covering number of $\mathcal{F}$ is also $\tilde{O}(d)$, we can obtain the following regret bound from Theorem 17.19:

$$\sum_{t=2}^T [f_*(x_t) - f_*(x_t, a_t)] = \tilde{O}(d\sqrt{T}),$$

which is consistent with that of Theorem 17.11. One may also use Proposition 15.8 to obtain bounds for nonparametric models such as RKHS induced by RBF kernels (also see Example 15.10).

We note that unlike Algorithm 17.2, Algorithm 17.4 does not use the feature representation $\psi(x,a)$ explicitly. That is, Algorithm 17.4 allows a nonlinear function class that may be embedded in an RKHS with unknown feature $\psi(x,a)$. Therefore the algorithm is more flexible. Moreover, if we consider a function class $\mathcal{F}$ that can be represented as a function in RKHS $\mathcal{H}$, it may be a small subset of $\mathcal{H}$, which has a small covering number. This can also reduce the overall complexity.

In the literature, one often employs a slightly different concept called *eluder dimension*, which is defined in (17.22). We note that Definition 17.17 is more general because it can be shown that a small eluder dimension implies a small eluder coefficient (also see Dann et al., 2021). We leave it as an exercise.