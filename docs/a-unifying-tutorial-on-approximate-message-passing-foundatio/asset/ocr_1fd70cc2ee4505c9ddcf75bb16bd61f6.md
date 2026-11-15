In summary, the state evolution characterisation of the AMP algorithm (3.3) allows us to choose the functions \(g_k\) in a principled way, depending on the prior information available about the signal \(v\). A poor choice of \((g_k)\) will lead to low effective signal-to-noise ratios \(\rho_k = (\mu_k/\sigma_k)^2\), but the asymptotic convergence results (3.8)-(3.11) will continue to hold provided that the hypotheses of Theorem 3.1 or 3.5 are satisfied.

A key strength of the AMP framework is that it gives us the flexibility to choose non-linear functions \(g_k\), such as the soft-thresholding functions above. Note that the MMSE denoising functions \(g_k^*\) in (3.16) are non-linear except in special cases (such as when \(V\) is Gaussian). Nevertheless, iterations with linear \(g_k\) can sometimes be useful as a theoretical device for obtaining distributional information about spectral estimators, as the following example shows; see also Mondelli and Venkataramanan (2020) and Mondelli et al. (2021).

**Connection with the power method**: Suppose that we initialise (3.3) with \(\hat{v}^0 \equiv \hat{v}^0(n) := \mu_0 v + \xi\), where \(\mu_0 \neq 0\) and \(\xi \equiv \xi(n) \sim N_n(0, I_n)\), and define

```
\(\beta_k := \sqrt{1+\mu_k^2}, \qquad g_k(x) := \frac{x}{\beta_k} \quad \text{for } x \in \mathbb{R},\)

\(\mu_{k+1} := \frac{\lambda}{\sqrt{1+\mu_k^{-2}}} \quad \text{for } k \in \mathbb{N}_0.\)

(3.27)
```

These functions \(g_k\) are constructed in a such a way that the corresponding state evolution formula (3.6) yields \(\sigma_k^2 = 1\) for every \(k\), and parameters \(\mu_k\) that coincide exactly with those defined in (3.27). Observe now that the AMP iteration (3.3) corresponding to (3.27) yields \((\hat{v}^k \equiv \hat{v}^k(n): k \in \mathbb{N})\) satisfying \(\beta_0 \hat{v}^1 = v^1 = A\hat{v}^0\) and

```
\(\left(\beta_k + \frac{1}{\beta_{k-1}}\right)\hat{v}^{k+1} - \frac{1}{\beta_{k-1}}(\hat{v}^{k+1} - \hat{v}^{k-1}) = A\hat{v}^k \quad \text{for } k \in \mathbb{N}.\)

(3.28)
```

The key steps in the theoretical analysis of (3.28) can be summarised as follows:

+   (i) When \(\lambda > 1\), some elementary analysis (e.g., based on the contraction mapping theorem) shows that \(\sqrt{\lambda^2-1}\) is a stable fixed point of the deterministic recursion for \((\mu_k)\) in (3.27), and hence that \(\beta_k \to \lambda\) as \(k \to \infty\).