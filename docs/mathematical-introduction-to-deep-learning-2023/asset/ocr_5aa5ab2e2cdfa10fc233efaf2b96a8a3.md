**Corollary 9.6.2** (Quantitative standard **KL** inequalities for non-constant one-dimensional polynomials). *Let* $\xi \in \mathbb{R}$, $N \in \mathbb{N}$, $p \in C^{\infty}(\mathbb{R}, \mathbb{R})$ *satisfy for all* $x \in \mathbb{R}$ *that* $p^{(N+1)}(x) = 0$, *let* $\beta_0, \beta_1, \ldots, \beta_N \in \mathbb{R}$ *satisfy for all* $n \in \{0, 1, \ldots, N\}$ *that* $\beta_n = \frac{p^{(n)}(\xi)}{n!}$, *and let* $m \in \{1, 2, \ldots, N\}$, $\alpha \in [0, 1]$, $c, \varepsilon \in \mathbb{R}$ *satisfy*

$$|\beta_m| > 0 = \sum_{n=1}^{m-1}|\beta_n|, \qquad \alpha \geq 1-m^{-1}, \qquad c = 2\Big[\sum_{n=1}^{N}\frac{|\beta_n|^{\alpha}}{|\beta_m \boldsymbol{m}|}\Big],$$  $$(9.47)$$

*and* $\varepsilon = \frac{1}{2}[\sum_{n=1}^{N}\frac{|\beta_n|^m|}{|\beta_m \boldsymbol{m}|}]^{-1}$. *Then it holds for all* $x \in [\xi - \varepsilon, \xi + \varepsilon]$ *that*

$$|p(x) - p(\xi)|^{\alpha} \leq c |p'(x)|. \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad (9.48)$$

*Proof of Corollary* **9.6.2**. *Note that Corollary* **9.6.1** *ensures that for all* $x \in \mathbb{R}$ *it holds that*

$$p(x) - p(\xi) = \sum_{n=1}^{N}\beta_n(x-\xi)^n. \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad (9.49)$$

Hence, we obtain for all $x \in \mathbb{R}$ that

$$p'(x) = \sum_{n=1}^{N}\beta_n n (x-\xi)^{n-1} \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad (9.50)$$

Therefore, we obtain for all $x \in \mathbb{R}$ that

$$p(x)-p(\xi) = \sum_{n=m}^{N}\beta_n(x-\xi)^n \quad \text{ and } \quad p'(x) = \sum_{n=m}^{N}\beta_n n (x-\xi)^{n-1}. \quad (9.51)$$

Hence, we obtain for all $x \in \mathbb{R}$ that

$$|p(x)-p(\xi)|^{\alpha} \leq \sum_{n=m}^{N}\big(|\beta_n|^{\alpha}|x-\xi|^{n\alpha}\big). \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad (9.52)$$

The fact that for all $n \in \{\boldsymbol{m}, \boldsymbol{m}+1, \ldots, N\}$, $x \in \mathbb{R}$ with $|x - \xi| \leq 1$ it holds that $|x - \xi|^{n\alpha} \leq |x - \xi|^{n(1-m^{-1})} \leq |x - \xi|^{\alpha(1-m^{-1})} = |x - \xi|^{m-1}$ therefore implies that for all $x \in \mathbb{R}$ with $|x - \xi| \leq 1$ it holds that

$$\begin{aligned} |p(x) - p(\xi)|^{\alpha} &\leq \sum_{n=m}^{N}|\beta_n|^{\alpha}|x-\xi|^{n\alpha} \leq \sum_{n=m}^{N}|\beta_n|^{\alpha}|x-\xi|^{m-1} \\ &= |x-\xi|^{m-1}\Big[\sum_{n=m}^{N}|\beta_n|^{\alpha}\Big] = |x-\xi|^{m-1}\Big[\sum_{n=1}^{N}|\beta_n|^{\alpha}\Big]. \end{aligned} \quad (9.53)$$

Hence, we obtain for all $x \in \mathbb{R}$ with $|x - \xi| \leq 1$ that

$$|p(x) - p(\xi)|^{\alpha} \leq |x - \xi|^{m-1}\Big[\sum_{n=1}^{N}|\beta_n|^{\alpha}\Big] = \frac{\varepsilon}{2}|x - \xi|^{m-1}|\beta_m \boldsymbol{m}|. \qquad \qquad \qquad (9.54)$$

Furthermore, observe that (9.51) ensures that for all $x \in \mathbb{R}$ with $|x - \xi| \leq 1$ it holds that

$$\begin{aligned} |p'(x)| & = \Big|\sum_{n=m}^{N}\beta_n n (x - \xi)^{n-1}\Big| \geq \Big|\sum_{n=m}^{N}\beta_n \boldsymbol{m}| |x - \xi|^{m-1} - \Big[\sum_{n=m+1}^{N}\beta_n n (x - \xi)^{n-1}\Big] \Big| \\ &\geq \Big|\Big[\sum_{n=m}^{N}|\beta_m \boldsymbol{m}| |x - \xi|^{m-1}\Big] - \Big[\sum_{n=m+1}^{N}|\beta_n n| |x - \xi|^{m-1}\Big] \Big| \quad \quad (9.55) \\ &= |x - \xi|^{m-1}\Big|\sum_{n=m}^{N}\beta_n \boldsymbol{m}\Big| - |x - \xi|^{m-1}\Big[\sum_{n=m+1}^{N}|\beta_n n|\Big]. \end{aligned}$$