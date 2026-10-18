
Also, letting `H := W̃`, we observe that `tr(W⊥XX⊥W) = tr(H⊥XX⊥H)` and `H⊥H = I_k`.

From ([9.4](#c09.xhtml#c09-disp-0018)), we see that `H` is composed of the eigenvectors of `XX⊥`, as `(XX⊥)H = H D̃`. Hence, the trace in ([9.2](#c09.xhtml#c09-disp-0015)) can be maximized by picking the `k` largest eigenvalues and then summing them up. From [Appendix \*9.A.1](#c09.xhtml#c09-sec-0017), we construct `H = (h_1, ..., h_k)`, where `h_j` is the unit eigenvector corresponding to the `j`‐th largest eigenvalue of `XX⊥`. In summary, we can now conclude with the following pseudo‐code for the PCA algorithm.

## 9.5 FACTOR MODELS VIA PCA

In finance, a reasonable model should provide effective and interpretable predictions with a tractable performance. Factor models are among those most commonly used in practice. Indeed, factor models play an important role in finance: for instance, they provide a decomposition to assist with portfolio hedging; see [Section 9.7](#c09.xhtml#c09-sec-0008). A `p`‐dimensional random vector `x_t` is said to follow an `m`‐linear factor model* if

[(9.5)](#c09.xhtml#R_c09-disp-0019)`x_t = a + B f_t + ε_t, t = 0, 1, 2, ..., n,`
