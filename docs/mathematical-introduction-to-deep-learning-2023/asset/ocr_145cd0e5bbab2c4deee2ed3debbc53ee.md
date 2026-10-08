Proof of Corollary 9.11.3. Observe that Proposition 9.11.2 ensures that there exists $\psi \in \mathbb{R}^{\mathfrak{d}}$ which satisfies that

+   (i) it holds that $\mathcal{L}(\psi) = \mathcal{L}(\vartheta)$,

+   (ii) it holds for all $t \in [0, \infty)$ that $\|\Theta_t - \psi\|_2 < \varepsilon$,

+   (iii) it holds for all $t \in [0, \infty)$ that $0 \le \mathcal{L}(\Theta_t) - \mathcal{L}(\psi) \le \mathfrak{C}^{2}\mathfrak{C}^{2}(\|_{\{0\}}(\mathfrak{c}) + \mathfrak{C}^{2}\mathfrak{c} + \mathfrak{C}^{2\alpha}t)^{-1}$, and

+   (iv) it holds for all $t \in [0, \infty)$ that

```
$$
\begin{aligned}
\|\Theta_t - \psi\|_2 &\le \int_t^\infty \|\mathscr{G}(\mathfrak{S}_s)\|_2 \, \mathrm{d}s \n&\le \mathfrak{C}(1-\alpha)^{-1}[\mathcal{L}(\Theta_t) - \mathcal{L}(\psi)]^{1-\alpha} \\
&\le \mathfrak{C}^{3-2\alpha}\mathfrak{C}^{2-2\alpha}(1-\alpha)^{-1}(\|_{\{0\}}(\mathfrak{c}) + \mathfrak{C}^{2}\mathfrak{c} + \mathfrak{C}^{2\alpha}t)^{\alpha-1}.
\end{aligned}
$$ (9.162)
```

Note that item (iii) and the assumption that $\mathfrak{c} \le 1$ establish that for all $t \in [0, \infty)$ it holds that

```
$$
0 \le \mathcal{L}(\Theta_t) - \mathcal{L}(\psi) \n\le \mathfrak{C}^{2}(\mathfrak{C}^{2}\|_{\{0\}}(\mathfrak{c}) + \mathfrak{c} + \mathfrak{C}^{-2}\mathfrak{C}^{2\alpha}t)^{-1} \n\le (1+\mathfrak{C}^{-2}t)^{-1}.
$$ (9.163)
```

This and item (iv) show that for all $t \in [0, \infty)$ it holds that

```
$$
\begin{aligned}
\|\Theta_t - \psi\|_2 &\le \int_t^\infty \|\mathscr{G}(\mathfrak{S}_s)\|_2 \, \mathrm{d}s \n&\le \mathfrak{C}(1-\alpha)^{-1}[\mathcal{L}(\Theta_t) - \mathcal{L}(\psi)]^{1-\alpha} \\
&\le \mathfrak{C}(1-\alpha)^{-1}(1+\mathfrak{C}^{-2}t)^{\alpha-1}.
\end{aligned}
$$ (9.164)
```

Combining this with item (i), item (ii), and (9.163) proves (9.161). The proof of Corollary 9.11.3 is thus complete.

# 9.11.2 Abstract global convergence results for GF processes

Proposition 9.11.4. Let $\mathfrak{d} \in \mathbb{N}$, $\Theta \in C([0, \infty), \mathbb{R}^{\mathfrak{d}})$, $\mathcal{L} \in C(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$, let $\mathscr{G} : \mathbb{R}^{\mathfrak{d}} \to \mathbb{R}^{\mathfrak{d}}$ be $\mathcal{B}(\mathbb{R}^{\mathfrak{d}})/\mathcal{B}(\mathbb{R}^{\mathfrak{d}})$-measurable, assume that for all $\vartheta \in \mathbb{R}^{\mathfrak{d}}$ there exist $\varepsilon, \mathfrak{C} \in (0, \infty)$, $\alpha \in (0, 1)$ such that for all $\theta \in \mathbb{R}^{\mathfrak{d}}$ with $\|\theta - \vartheta\|_2 < \varepsilon$ it holds that

```
$$
|\mathcal{L}(\theta) - \mathcal{L}(\vartheta)|^{\alpha} \n\le \mathfrak{C}\|\mathscr{G}(\vartheta)\|_2,
$$ (9.165)
```

assume for all $t \in [0, \infty)$ that

```
$$
\mathcal{L}(\Theta_t) = \mathcal{L}(\Theta_0) - \int_0^t \|\mathscr{G}(\mathfrak{S}_s)\|_2^2 \, \mathrm{d}s
\quad \text{and} \quad
\Theta_t = \Theta_0 - \int_0^t \mathscr{G}(\mathfrak{S}_s) \, \mathrm{d}s,
$$ (9.166)
```

and assume $\lim_{t\to\infty}\inf \|\Theta_t\|_2 < \infty$. Then there exist $\vartheta \in \mathbb{R}^{\mathfrak{d}}$, $\mathfrak{C}, \tau, \beta \in (0, \infty)$ such that for all $t \in [\tau, \infty)$ it holds that

```
$$
\|\Theta_t - \vartheta\|_2 \n\le (1+\mathfrak{C}(t-\tau))^{-\beta}
\quad \text{and} \quad
0 \le \mathcal{L}(\Theta_t) - \mathcal{L}(\vartheta) \n\le (1+\mathfrak{C}(t-\tau))^{-1}.
$$ (9.167)
```