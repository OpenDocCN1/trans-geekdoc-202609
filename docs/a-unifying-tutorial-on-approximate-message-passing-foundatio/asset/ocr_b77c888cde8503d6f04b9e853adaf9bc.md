M = - \log f_{\bar{\varepsilon}} in (4.50) yields a maximum likelihood estimator of \beta; see Dümbgen et al. (2011, Section 3) for a maximum likelihood approach to estimating \beta when f_{\bar{\varepsilon}} is unknown. Other popular choices of M include squared error loss w \mapsto w^2, Huber loss w \mapsto w^2 \mathbb{1}_{\{|w| \le B\}} + (2|w| - B)B \mathbb{1}_{\{|w| > B\}} (for robust regression) with B > 0, and quantile loss w \mapsto \tau w - \mathbb{1}_{\{w < 0\}} (for quantile regression) with \tau \in (0, 1). In a classical setting where the dimension p is fixed, x_1, ..., x_n \overset{\text{iid}}{\sim} P_X on \mathbb{R}^p and \varepsilon_1, ..., \varepsilon_n \overset{\text{iid}}{\sim} P_{\bar{\varepsilon}} on \mathbb{R} for all n, Huber (1964 and 1973) proved that

```
\sqrt{n}(\hat{\beta}^{\text{M}} - \beta) \xrightarrow{d} N_p(0, \Sigma^{\text{M}}) \quad \text{as } n \to \infty, \text{ with}
\Sigma^{\text{M}} := \frac{\int_{\mathbb{R}} (M')^2 dP_{\bar{\varepsilon}}}{(\int_{\mathbb{R}} M'' dP_{\bar{\varepsilon}})^2} \left( \int_{\mathbb{R}^p} x x^\top dP_X \right)^{-1}, \quad (4.51)
```

under appropriate regularity conditions on M and the score function S := M'; see also Huber and Ronchetti (2009) and van der Vaart (1998, Example 5.28). When \bar{\varepsilon} \sim P_{\bar{\varepsilon}} has a differentiable density f_{\bar{\varepsilon}}, it follows from the Cauchy-Schwarz inequality that the variance functional

```
V(S; \bar{\varepsilon}) := \frac{\mathbb{E}(S(\bar{\varepsilon})^2)}{\mathbb{E}(S'(\bar{\varepsilon}))^2} = \frac{\int_{\mathbb{R}} (M')^2 dP_{\bar{\varepsilon}}}{(\int_{\mathbb{R}} M'' dP_{\bar{\varepsilon}})^2} \quad (4.52)
```

that appears in (4.51) is bounded below by the Fisher information I(P_{\bar{\varepsilon}}) := \int_{\mathbb{R}} (f'_{\bar{\varepsilon}}/ f_{\bar{\varepsilon}})^2 dP_{\bar{\varepsilon}}, with equality when M = - \log f_{\bar{\varepsilon}} (in which case the maximum likelihood estimator \hat{\beta}^{\text{M}} is asymptotically efficient).

In contrast to (4.51), Donoho and Montanari (2016) showed that the M-estimator \hat{\beta}^{\text{M}} suffers from variance inflation (and cannot be asymptotically efficient) in high-dimensional regimes where n, p \to \infty with n/p \to \delta \in (1, \infty). AMP machinery plays a pivotal role in the analysis that leads to their main result (stated as Theorem 4.7 below), and as in Section 4.5, we will now present the main steps within the context of the GAMP framework of Sections 4.1 and 4.4.

Observing that the convex optimisation problem in (4.50) is an instance of (4.22) with \ell: (u, v) \mapsto M(u - v) and J \equiv 0 (i.e., no penalty term), we first write down an associated GAMP algorithm (4.53) based on the general construction in Section 4.4. For \eta > 0, define a “smoothed” version of \eta M by

```
M_\eta(z) := \min_{t \in \mathbb{R}} \left\{ \eta M(t) + \frac{1}{2}(t - z)^2 \right\}
```