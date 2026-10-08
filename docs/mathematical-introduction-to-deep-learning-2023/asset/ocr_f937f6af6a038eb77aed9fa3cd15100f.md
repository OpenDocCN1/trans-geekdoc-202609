# 4.3 ANN approximations results for multi-dimensional functions

# 4.3.1 Constructive ANN approximation results

**Proposition 4.3.1.** *Let $d, K \in \mathbb{N}$, $L \in [0, \infty)$, let $E \subseteq \mathbb{R}^{d}$ be a set, let $\mathbf{f}_{1}, \mathbf{f}_{2}, \ldots, \mathbf{f}_{K} \in E$, let $f: E \rightarrow \mathbb{R}$ satisfy for all $x, y \in E$ that $|f(x) - f(y)| \leq L \|x - y\|_{1}$, and let $\mathbf{y} \in \mathbb{R}^{K}$, $\Phi \in \mathbb{N}$ satisfy $\boldsymbol{\eta} = (f(\mathbf{f}_{1}), f(\mathbf{f}_{2}), \ldots, f(\mathbf{f}_{K}))$ and*

```
$$\Phi = \mathbb{M}_{K} \bullet \mathbf{A}_{-L1K,n} \bullet \mathbf{P}_{K}\big(\mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{1}}, \mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{2}}, \ldots, \mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{K}}\big) \bullet \mathbb{T}_{d,K} \quad (4.77)$$
```

*(cf. Definitions 1.3.1, 1.5.5, 2.1.1, 2.2.1, 2.3.1, 2.4.6, 3.3.4, 4.2.1, and 4.2.5). Then*

```
$$\operatorname{sup}_{x \in E}|(\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(x) - f(x)| \leq 2L \big[\operatorname{sup}_{x \in E}(\min_{k \in \{1, \ldots, K\}} \|x - \mathbf{f}_{k}\|_{1})\big] \quad (4.78)$$
```

*(cf. Definitions 1.2.4 and 1.3.4).*

*Proof of Proposition 4.3.1. Throughout this proof, let $F: \mathbb{R}^{d} \rightarrow \mathbb{R}$ satisfy for all $x \in \mathbb{R}^{d}$ that*

```
$$F(x) = \max_{k \in \{1, \ldots, K\}}(f(\mathbf{f}_{k}) - L\|x - \mathbf{f}_{k}\|_{1}). \quad (4.79)$$
```

Observe that Corollary 4.1.4, (4.79), and the assumption that for all $x, y \in E$ it holds that $|f(x) - f(y)| \leq L\|x - y\|_{1}$ assure that

```
$$\operatorname{sup}_{x \in E}|F(x) - f(x)| \leq 2L \big[\operatorname{sup}_{x \in E}(\min_{k \in \{1, \ldots, K\}}\|x - \mathbf{f}_{k}\|_{1})\big]. \quad (4.80)$$
```

Moreover, note that Lemma 4.2.9 ensures that for all $x \in E$ it holds that $F(x) = (\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(x)$. Combining this and (4.80) establishes (4.78). The proof of Proposition 4.3.1 is thus complete.

*Exercise 4.3.1. Prove or disprove the following statement: There exists $\Phi \in \mathbb{N}$ such that $\mathcal{I}(\Phi) = 2$, $\mathcal{O}(\Phi) = 1$, $\mathcal{P}(\Phi) < 20$, and*

```
$$\sup_{v = (x,y) \in [0,2]^{2}} \big| x^{2} + y^{2} - 2x - 2y + 2 - (\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(v) \big| \leq \frac{3}{8}. \quad (4.81)$$
```

# 4.3.2 Covering number estimates

**Definition 4.3.2** (Covering numbers). *Let $(E, \delta)$ be a metric space and let $r \in [0, \infty)$. Then we denote by $\mathcal{C}^{(E,\delta),r} \in \mathbb{N}_{0} \cup \{\infty\}$ (we denote by $\mathcal{C}^{E,r} \in \mathbb{N}_{0} \cup \{\infty\}$) the extended real number given by*

```
$$\mathcal{C}^{(E,\delta),r} = \min \bigg( \big\{n \in \mathbb{N}_{0} \colon \big[\exists A \subseteq E \colon \big[(|A| \leq n) \land (\forall x \in E \colon \exists a \in A \colon \delta_{(a,x)} \leq r)\big]\big] \big\} \cup \{\infty\} \bigg) \quad (4.82)$$
```

*and we call $\mathcal{C}^{(E,\delta),r}$ the $r$-covering number of $(E, \delta)$ (we call $\mathcal{C}^{E,r}$ the $r$-covering number of $E$).*