**State evolution:** Starting with \(\mu_1 \in \mathbb{R}\) and \(\sigma_1 \in [0, \infty)\), we inductively define state evolution parameters \(\mu_k \in \mathbb{R}\) and \(\sigma_k \in [0, \infty)\) for \(k \in \mathbb{N}\) by

```
\(\mu_{k+1} := \lambda \mathbb{E}(V g_k(\mu_k V + \sigma_k G)), \quad \sigma_{k}^2 := \mathbb{E}'(g_k(\mu_k V - \sigma_k G)^2). \quad (3.6)\)
```

where \(V \sim \pi\) and \(G \sim N(0,1)\) are independent. Note that since each \(g_k\) is Lipschitz and \(\mathbb{E}(V^2) = \mathbb{E}(G^2) = 1\), we indeed have \(\mu_k \in \mathbb{R}\) and \(\sigma_k \in [0, \infty)\) for all \(k\) by induction: we will see below that these represent the *effective signal strength* and *effective noise level* respectively at iteration \(k\).

**Limiting covariance structure:** We now extend (3.6) by specifying the covariance matrices of the limiting Gaussian distributions in Theorem 3.1 below. Let \(\bar{\Sigma}^{[1]} = \bar{\Sigma}_{1,1} := \sigma_1^2 \ge 0\). For a general \(k \ge 2\), suppose inductively that we have already defined a non-negative definite \(\bar{\Sigma}^{[k-1]} \in \mathbb{R}^{(k-1) \times (k-1)}\) with entries \(\bar{\Sigma}_{ij}^{[k-1]} = \bar{\Sigma}_{i,j}\) for \(1 \le i, j \le k-1\), and then let

```
\(\bar{\Sigma}_{k,\ell} = \bar{\Sigma}_{\ell,k}\)
\(:=\left\{\begin{array}{ll} \mathbb{E}(g_0(\mu_0 V + \sigma_0 U) \cdot g_{k-1}(\mu_{k-1} V + \sigma_{k-1} G_{k-1})) & \text{for } \ell = 1 \\ \mathbb{E}(g_{\ell-1}(\mu_{\ell-1} V + \sigma_{\ell-1} G_{\ell-1}) \cdot g_{k-1}(\mu_{k-1} V + \sigma_{k-1} G_{k-1})) & \text{for } \ell = 2, ..., k, \end{array}\right. \quad (3.7)\)
```

where \((\sigma_1 G_1, \dots, \sigma_{k-1} G_{k-1}) \sim N_{k-1}(0, \bar{\Sigma}^{[k-1]})\) is independent of \((U, V)\) from (M1). Let \(\bar{\Sigma}^k\) be the \(k \times k\) matrix with entries \(\bar{\Sigma}_{ij}^k := \bar{\Sigma}_{i,j}\) for \(1 \le i, j \le k\), so that \(\bar{\Sigma}^{[k-1]}\) is the top-left principal \((k-1) \times (k-1)\) submatrix of \(\bar{\Sigma}^k\). It can be verified as in (2.7) that \(\bar{\Sigma}^k\) is non-negative definite. By induction, \(\sigma_k^2 = \mathbb{E}(g_{k-1}(\mu_{k-1} V + \sigma_{k-1} G)^2) = \bar{\Sigma}_{k,k}\) for all \(k \in \mathbb{N}\), so (3.7) does indeed extend (3.6).

We are now ready to state the main result of this subsection, which for each \(k \in \mathbb{N}\) establishes the 2-Wasserstein (\(d_2\)) limit of the joint empirical distributions of the components of \(v^0, v^1, \dots, v^k, v \in \mathbb{R}^n\) as \(n \to \infty\).

**Theorem 3.1.** Suppose that (M0)-(M2) hold for a sequence of AMP iterations (3.3), where for each \(n \in \mathbb{N}\), the symmetric matrix \(A \equiv A(n)\)