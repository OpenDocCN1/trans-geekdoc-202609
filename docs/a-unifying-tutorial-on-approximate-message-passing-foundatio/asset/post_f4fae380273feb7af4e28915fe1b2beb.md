
## 4.2 Choosing the Functions $f_k, g_k$, and Inference for $\beta$

Asymptotic estimation error: Since the functions $f_k$ in (4.4) are Lipschitz by assumption, it follows as in Corollary 3.2 that in the setting of Theorem 4.2 above, the asymptotic estimation error of $\hat{\beta}^k$ with respect to any loss function $\psi \in \text{PL}_2(r)$ is given by

$$
\frac{1}{p} \sum_{j=1}^p \psi(\hat{\beta}_j^k, \beta_j) \xrightarrow{\mathcal{L}} \mathbb{E}\{\psi(f_k(\mu_k\bar{\beta} + \sigma_k G_k), \bar{\beta})\}
$$ (4.15)

for each $k \in \mathbb{N}$, as $n, p \to \infty$ with $n/p \to \delta$. In particular, taking $\psi(x, y) = |x - y|^q$ for $q \in [1, r]$, we obtain the asymptotic normalised $\ell_q$ error c-$\lim_{p \to \infty} p^{-1} \|\hat{\beta}^k - \beta\|_q = \mathbb{E}\{(f_k(\mu_k\bar{\beta} + \sigma_k G_k) - \bar{\beta})^q\}^{1/q}$.

Bayes-GAMP: If the limiting prior distribution $\pi_{\bar{\beta}}$, the limiting noise distribution $P_{\bar{\varepsilon}}$ and the initial $\Sigma_0 \in \mathbb{R}^{2\times 2}$ are known, then guided by Lemma 3.7, we can proceed as in Section 3.3 and choose $f_k, g_k$ in (4.4) so as to maximise the effective signal-to-noise ratios $\rho_k = (\mu_k/\sigma_k)^2$ and $\rho_{Z,k} := (\mu_{Z,k}/\sigma_{Z,k})^2$ for each $k$.

Specifically, given the matrix $\Sigma \equiv \Sigma_k \in \mathbb{R}^{2\times 2}$ in (4.7) for some $k \in \mathbb{N}_0$, we can obtain $\mu_{Z,k}, \sigma_{Z,k}$ from (4.8); conversely, given $\mu_{Z,k}, \sigma_{Z,k}$, we can recover $\Sigma$ since $\Sigma_{11} = \delta^{-1} \mathbb{E}(\bar{\beta}^2)$ is known, and (4.8) yields $\Sigma_{21} = \Sigma_{11} \mu_{Z,k}$ and $\Sigma_{22} = \sigma_{Z,k}^2 + \Sigma_{11} \mu_{Z,k}^2$. Now take $(Z, Z_k) \sim N_2(0, \Sigma_k)$ to be independent of $\bar{\varepsilon} \sim P_{\bar{\varepsilon}}$, and let $Y = h(Z, \bar{\varepsilon})$, so that $Y$ and $Z_k$ are conditionally independent given $Z$. Based on the joint distribution of $(Z, Z_k, Y)$, let $g_k^*: \mathbb{R}^2 \to \mathbb{R}$ be a measurable function satisfying

$$
g_k^*(Z_k, Y) = \frac{\mathbb{E}(Z | Z_k, Y) - \mathbb{E}(Z | Z_k)}{\text{Var}(Z | Z_k)},
$$ (4.16)

where $\mathbb{E}(Z | Z_k) = m_k Z_k$ with

$$
m_k := \frac{\Sigma_{21}}{\Sigma_{22}} = \frac{\mu_{Z,k}}{\sigma_{Z,k}^2} \text{Var}(Z | Z_k),
$$

$$
\text{Var}(Z | Z_k) = \Sigma_{11} - \frac{\Sigma_{21}^2}{\Sigma_{22}} = \frac{\Sigma_{11} \sigma_{Z,k}^2}{\sigma_{Z,k}^2 + \Sigma_{11} \mu_{Z,k}^2} = \left( \frac{\delta}{\mathbb{E}(\bar{\beta}^2)} + \rho_{Z,k} \right)^{-1}.
$$

Then by (4.6), (4.9) and the Cauchy–Schwarz inequality, we have

$$
\rho_{k+1} = \frac{\mu_{k+1}^2}{\sigma_{k+1}^2} = \frac{\mathbb{E}(g_k^*(Z_k, Y) g_k(Z_k, Y))^2}{\mathbb{E}(g_k(Z_k, Y)^2)} \le \mathbb{E}(g_k^*(Z_k, Y)^2),
$$

with equality when $g_k$ is a (non-zero) scalar multiple of $g_k^*$.

Now given $\mu_k, \sigma_k$ for some $k \in \mathbb{N}$, we wish to find $f_k: \mathbb{R} \rightarrow \mathbb{R}$ such that defining $\Sigma \equiv \Sigma_k$ as in (4.8), the quantity

$$
\rho_{Z,k} = \frac{\mu_{Z,k}^2}{\sigma_{Z,k}^2} = \frac{\Sigma_{21}^2 \Sigma_{11}^{-2}}{\Sigma_{22} - \Sigma_{21}^2 \Sigma_{11}^{-1}} = \left( \frac{\Sigma_{22}}{\Sigma_{21}^2} \Sigma_{11}^2 - \Sigma_{11} \right)^{-1}
$$

is as large as possible. Since $\Sigma_{11} = \delta^{-1} \mathbb{E}(\bar{\beta}^2)$ is fixed, this amounts to maximising

$$
\frac{\Sigma_{21}^2}{\Sigma_{22}} = \frac{\mathbb{E}(\bar{f}_k(\mu_k \bar{\beta} + \sigma_k \bar{G}_k))^2}{\mathbb{E}(f_k(\mu_k \bar{\beta} + \sigma_k \bar{G}_k)^2)}.
$$

Again by the Cauchy–Schwarz inequality (see (3.19) in Section 3.3), this can be done by taking $f_k$ to be any (non-zero) scalar multiple of $f_k^*$ satisfying

$$
f_k^*(\mu_k \bar{\beta} + \sigma_k \bar{G}_k) = \mathbb{E}(\bar{\beta} \mid \mu_k \bar{\beta} + \sigma_k \bar{G}_k), \quad (4.17)
$$

in which case $\Sigma_{21} = \Sigma_{22} < \Sigma_{11}$. An exact expression for $f_k^*$ is given by Tweedie's formula (3.17), and if $\tilde{\beta} \sim \pi_{\bar{\beta}}$ satisfies the conditions of Lemma 3.8, then $f_k^*$ is Lipschitz. As we saw in (3.18), the choice $f_k = f_k^*$ also minimises the asymptotic mean squared error $\mathbb{E}\{(f_k(\mu_k \bar{\beta} + \sigma_k G_k) - \bar{\beta})^2\}$, for given $\mu_k, \sigma_k$; in other words, $f_k^*$ is the Bayes optimal (i.e., MMSE) denoising function.

By recursively defining \(g_k = g_k^*\) (or some scalar multiple thereof) and \(f_{k+1} = f_{k+1}^*\) for \(k \in \mathbb{N}\) using (4.16) and (4.17), together with corresponding sequences \((\mu_k^*, \sigma_k^*, \mu_{Z,k}^*, \sigma_{Z,k}^*: k \in \mathbb{N})\) of state evolution parameters through (4.6)-(4.7), we obtain a _Bayes-GAMP algorithm_ of the form (4.4). A version of this was originally derived by Rangan (2011, Section IV-B) as an approximation to a sum-product loopy belief propagation algorithm. The limiting empirical distributions for the Bayes-GAMP iterates can be obtained from Theorem 4.2, provided that the functions \(f_k^*\) and \(\tilde{g}_k^*: (z, u, v) \mapsto g_k^*(u, h(z, v))\) are all Lipschitz and (G0)-(G5) are satisfied.

Even when $\pi_{\bar{\beta}}$ is not completely known, it can still be possible to tailor the choices of $f_k, g_k$ to wider classes of limiting prior distributions that induce certain types of structure in the signals $\beta$. For instance, if we are told that $\beta \in \mathbb{R}^p$ has at most $sp$ non-zero entries for some $s \in (0, 1)$ and every $p \equiv p_n$, then as in Section 3.3, we can take each $f_k$ to be a soft-thresholding function $\mathrm{S}_{t_k}: u \mapsto \operatorname{sgn}(u)(|u|-t_k)_+$ for some $t_k > 0$. Using an AMP recursion (4.19) of this form (for the linear model in Section 4.3) with appropriately chosen thresholds $t_k$, Bayati and Montanari (2012) derived exact high-dimensional asymptotics for the Lasso estimator; see Section 4.5.

### Spectral initialisation

Under the conditions of Theorem 4.2, it follows from (4.15) and Lemma 4.1 that for each $k \in \mathbb{N}$, the estimates $\hat{\beta}^k$ in the generic GAMP procedure (4.4) satisfy $\langle \hat{\beta}^k, \beta \rangle_p = p^{-1} \sum_{j=1}^p \hat{\beta}_j^k \beta_j \xrightarrow{c} \mathbb{E}(\bar{\beta} f_k(\mu_k \bar{\beta} + \sigma_k G_k)) = \mu_{Z,k} \mathbb{E}(\bar{\beta}^2)$ as $n, p \to \infty$ with $n/p \to \delta$. To ensure that $\mu_{Z,k} \neq 0$ for some $k$, and hence that the corresponding $\hat{\beta}^k$ has non-zero asymptotic empirical correlation with the signal $\beta$, it is sometimes necessary to start with pilot estimators $\hat{\beta}^0 \in \mathbb{R}^p$ that themselves have the property that c-$\lim_{p \to \infty}\langle \hat{\beta}^0, \beta \rangle_p \neq 0$. Indeed, suppose that the limiting random variables in the state evolution recursion (4.6)-(4.7) are such that

$$
\mathbb{E}(\bar{\beta}) = 0 \quad \text{and} \quad \mathbb{E}(Z|Y) = 0 \quad \text{almost surely,} \quad (4.18)
$$

where the latter condition is equivalent to (3.13) in Mondelli and Venkataramanan (2020). Now given estimates $\hat{\beta}^0 \in \mathbb{R}^p$ for which c-$\lim_{n\to\infty}\langle \hat{\beta}^0, \beta \rangle_p = \delta(\Sigma_0)_{21} = 0$, we see from Lemma 4.1 that $\mu_{Z,0} = 0$ and $Z_0$ is independent of $(Z, Y)$, whence $g_0^*(Z_0, Y) = \mathbb{E}(Z|Y)/\text{Var}(Z) = 0$ almost surely in (4.16) and $\mu_1 = \mathbb{E}(g_0^*(Z_0, Y)g_0(Z_0, Y)) = 0$ by (4.9). This means that $\mu_{Z,1} \mathbb{E}(\bar{\beta}^2) = \delta(\Sigma_1)_{21} = \mathbb{E}(\bar{\beta} f_1(\sigma_1 G_1)) = 0$ by the independence of $\bar{\beta}$ and $G_1$. Continuing inductively, we conclude that $\mu_k = \mu_{Z,k} = 0$ for all $k \in \mathbb{N}$, irrespective of the choices of \(g_k, f_{k+1}\) for \(k \in \mathbb{N}_0\), so $\hat{\beta}^k$ is asymptotically uninformative as an estimator of $\beta \in \mathbb{R}^p$ for every $k \in \mathbb{N}_0$.

Thus, while there are some GLMs (such as the linear model in Section 4.3) in which it suffices to take $\hat{\beta}^0 = c \mathbf{1}_p$ for some fixed $c \in \mathbb{R}$, a different initialiser is required when (4.18) holds. We note that the second condition therein is satisfied in the phase retrieval model, where $y_i = h(x_i^\top \beta, \varepsilon_i) = (x_i^\top \beta)^2 + \varepsilon_i$ for $1 \le i \le n$, and more generally in all non-identifiable models of the form (4.1) where $h(z, w) = h(-z, w)$ for all $z, w$ (and hence $Q(\cdot | z) = Q(\cdot | -z)$ in (4.2) for all $z$). Indeed, for such functions $h$, we have $\mathbb{E}(Z|Y) = \mathbb{E}(Z|h(Z, \bar{\varepsilon})) = -\mathbb{E}(Z|h(Z, \bar{\varepsilon}))$ and hence $\mathbb{E}(Z|Y) = 0$ almost surely.
