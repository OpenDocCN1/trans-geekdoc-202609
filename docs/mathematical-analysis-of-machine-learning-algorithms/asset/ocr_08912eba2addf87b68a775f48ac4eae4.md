$\epsilon_n(\mathcal{G},\mathcal{D}) = \mathbb{E}_{\mathcal{S}_n \sim \mathcal{D}^n} \sup_{w \in \Omega}[\phi(w,\mathcal{D}) - \phi(w,\mathcal{S}_n) - h(w,\mathcal{S}_n)]$
$= \mathbb{E}_{\mathcal{S}_n \sim \mathcal{D}^n} \sup_{w \in \Omega}\mathbb{E}_{\mathcal{S}_n' \sim \mathcal{D}^n}\phi(w,\mathcal{S}_n') - \phi(w,\mathcal{S}_n) - h(w,\mathcal{S}_n)]$
$\le \mathbb{E}_{(\mathcal{S}_n,\mathcal{S}_n') \sim \mathcal{D}^{2n}} \sup_{w \in \Omega}[\phi(w,\mathcal{S}_n') - \phi(w,\mathcal{S}_n) - h(w,\mathcal{S}_n)]$
$= \mathbb{E}_{(\mathcal{S}_n,\mathcal{S}_n') \sim \mathcal{D}^{2n}} \sup_{w \in \Omega} [[\phi(w,\mathcal{S}_n') + 0.5h_1(w,\mathcal{S}_n')] - 0.5h(w,\mathcal{S}_n')$
$- [\phi(w,\mathcal{S}_n) + 0.5h_1(w,\mathcal{S}_n)] - 0.5h(w,\mathcal{S}_n)]$
$\stackrel{(a)}{=} \mathbb{E}_{(\mathcal{S}_n,\mathcal{S}_n') \sim \mathcal{D}^{2n}} \mathbb{E}_{\sigma} \sup_{w \in \Omega} \frac{1}{n} \sum_{i=1}^{n} [\sigma_i(\phi(w,Z_i') + 0.5h_1(w,Z_i')) - 0.5h(w,\mathcal{S}_n')$
$- \sigma_i(\phi(w,Z_i) + 0.5h_1(w,Z_i)) - 0.5h(w,\mathcal{S}_n)]$
$\le \mathbb{E}_{(\mathcal{S}_n,\mathcal{S}_n') \sim \mathcal{D}^{2n}} \mathbb{E}_{\sigma} \sup_{w \in \Omega} \frac{1}{n} \sum_{i=1}^{n}[\sigma_i(\phi(w,Z_i') + 0.5h_1(w,Z_i')) - 0.5h(w,\mathcal{S}_n')]$ 
$+ \mathbb{E}_{(\mathcal{S}_n,\mathcal{S}_n') \sim \mathcal{D}^{2n}} \mathbb{E}_{\sigma} \sup_{w \in \Omega} \frac{1}{n} \sum_{i=1}^{n}[-\sigma_i(\phi(w,Z_i) + 0.5h_1(w,Z_i) - 0.5h(w,\mathcal{S}_n)]$
$= \mathbb{E}_{(\mathcal{S}_n,\mathcal{S}_n') \sim \mathcal{D}^{2n}} [R_n^h(\mathcal{G},\mathcal{S}_n) + R_n^h(\mathcal{G},\mathcal{S}_n')] = 2R_n^h(\mathcal{G},\mathcal{D}).$

In this derivation, (a) used the fact that $\sigma_i(\phi(w,Z_i')+0.5h_1(w,Z_i'))-\sigma_i(\phi(w,Z_i)+0.5h_1(w,Z_i))$ and $(\phi(w,Z_i')+0.5h_1(w,Z_i'))-(\phi(w,Z_i)+0.5h_1(w,Z_i))$ have the same distributions.

# **Example 6.15** Using the offset Rademacher complexity estimate for VC class in Example 6.13, we can obtain the following multiplicative form of expected oracle inequality from Theorem 6.14:

$\mathbb{E}_{\mathcal{S}_n}\phi(\hat{w},\mathcal{D}) \le (1+\gamma)\inf_{w\in\Omega}\phi(w,\mathcal{D}) + \epsilon' + \frac{2(1+0.5\gamma)^2 d \ln(en/d)}{\gamma n}.$

This implies an expected generalization of $O(d\ln n/n)$ when $\inf_{w\in\Omega}\phi(w,\mathcal{D})=0$. In comparison, the standard Rademacher complexity leads to a convergence of $O(\sqrt{d\ln n/n})$ in Example 6.5.

# **6.3 Concentration Inequality**

We showed that using Rademacher complexity, we may obtain an oracle inequality in expectation. By using concentration inequality, we can also obtain high-probability uniform convergence and oracle inequality statements.

The simplest concentration inequality is a generalization of the additive Chernoff bound, due to McDiarmid (1989).

# **Theorem 6.16 (McDiarmid’s Inequality)** Consider $n$ independent random variables $X_1,\dots,X_n$, and a real-valued function $f(X_1,\dots,X_n)$ that satisfies the following inequality: