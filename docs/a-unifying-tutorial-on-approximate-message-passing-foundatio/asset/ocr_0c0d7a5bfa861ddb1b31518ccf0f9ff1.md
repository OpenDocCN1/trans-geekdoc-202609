that the hypotheses of Theorem 3.5 are satisfied with \(\lambda > 1\), in which case \(\mu_0 = c\sqrt{1 - \lambda^{-2}}\), \(\sigma_0 = c/\lambda\) and \(\rho_0^* = \lambda^2 - 1\).

Suppose that \(V \sim \pi\) satisfies one of the conditions of Lemma 3.8. Then we have the following:

+   (a) The sequence \((\rho_k^*: k \in \mathbb{N}_0)\) of effective signal-to-noise ratios defined through (3.20) is strictly increasing, and converges to the *smallest* strictly positive fixed point of \(\rho = \lambda^2(1 - \text{mmse}(\rho))\), which we denote by \(\rho_{\text{AMP}}^* \equiv \rho_{\text{AMP}}^*(\lambda) \in (0, \lambda^2]\).

+   (b) For \(k \in \mathbb{N}\) and a (convex, non-negative) loss function \(\psi \in \text{PL}_2(2)\), suppose that \(g_{k,\psi}^*: \mathbb{R} \to \mathbb{R}\) is Lipschitz and attains the infimum in the definition of \(R_{\pi, \psi}(\rho_k^*)\). Then the estimates \(\hat{v}^{k,\psi} \equiv \hat{v}^{k,\psi}(n) := g_{k,\psi}^*(v^{k,\text{B}})\) satisfy (3.23) with equality, i.e., \(n^{-1} \sum_{i=1}^n \psi(\hat{v}_i^{k,\psi}, v_i) \xrightarrow{c} R_{\pi, \psi}(\rho_k^*)\) as \(n \to \infty\), and \(R_{\pi, \psi}(\rho_k^*) \ge R_{\pi, \psi}(\rho_{k+1}^*)\).

+   (c) The Bayes-AMP estimates \(\hat{v}^{k,\text{B}} = g_k^*(v^{k,\text{B}})\) satisfy

\(\text{c-lim}_{n\to\infty} \|\hat{v}^{k,\text{B}} - v\|_n^2 = 1 - \frac{\rho_{k+1}^*}{\lambda^2} \searrow 1 - \frac{\rho_{\text{AMP}}^*(\lambda)}{\lambda^2}\) (3.24)

and \(\text{c-lim}_{n\to\infty} \frac{\langle \hat{v}^{k,\text{B}}, v \rangle_n}{\|\hat{v}^{k,\text{B}}\|_n \|v\|_n} = \frac{\sqrt{\rho_{k+1}^*}}{\lambda} \nearrow \frac{\sqrt{\rho_{\text{AMP}}^*(\lambda)}}{\lambda}\) (3.25)

as \(k \to \infty\).

![](bbox=[0.153, 0.638, 0.946, 0.794])

**Figure 3.1:** “Cobweb diagrams” illustrating the conclusion of Theorem 3.10(a) that \(\rho_k^* \nearrow \rho_{\text{AMP}}^*\) as \(k \to \infty\), under (i) and (ii) respectively with \(\lambda = 1.7\); note that \(1 - \text{mmse}(0) = \mathbb{E}(V)^2\). *Left, non-spectral initialisation:* \(V \sim \pi = \frac{3}{4}\delta_0 + \frac{1}{4}\delta_2\), with \(\mathbb{E}(V) = 1/2 \neq 0\) and \(\mathbb{E}(V^2) = 1\): convergence to \(\rho_{\text{AMP}}^*\) occurs when \(\rho_0^* = 0\). *Right, spectral initialisation:* \(V \sim \pi = \frac{1}{2}\delta_{-1} + \frac{1}{2}\delta_1\), with \(\mathbb{E}(V) = 0\) and \(\mathbb{E}(V^2) = 1\): convergence to \(\rho_{\text{AMP}}^*\) occurs only if \(\rho_0^* > 0\).