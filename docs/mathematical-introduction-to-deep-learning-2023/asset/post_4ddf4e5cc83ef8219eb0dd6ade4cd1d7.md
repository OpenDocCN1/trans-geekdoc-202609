
# 4.3 ANN approximations results for multi-dimensional functions

## 4.3.1 Constructive ANN approximation results

**Proposition 4.3.1.** *Let $d, K \in \mathbb{N}$, $L \in [0, \infty)$, let $E \subseteq \mathbb{R}^{d}$ be a set, let $\mathbf{f}_{1}, \mathbf{f}_{2}, \ldots, \mathbf{f}_{K} \in E$, let $f: E \rightarrow \mathbb{R}$ satisfy for all $x, y \in E$ that $|f(x) - f(y)| \leq L \|x - y\|_{1}$, and let $\mathbf{y} \in \mathbb{R}^{K}$, $\Phi \in \mathbb{N}$ satisfy $\boldsymbol{\eta} = (f(\mathbf{f}_{1}), f(\mathbf{f}_{2}), \ldots, f(\mathbf{f}_{K}))$ and*

$$\Phi = \mathbb{M}_{K} \bullet \mathbf{A}_{-L1K,n} \bullet \mathbf{P}_{K}\big(\mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{1}}, \mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{2}}, \ldots, \mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{K}}\big) \bullet \mathbb{T}_{d,K} \quad (4.77)$$

*(cf. Definitions 1.3.1, 1.5.5, 2.1.1, 2.2.1, 2.3.1, 2.4.6, 3.3.4, 4.2.1, and 4.2.5). Then*

$$\operatorname{sup}_{x \in E}|(\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(x) - f(x)| \leq 2L \big[\operatorname{sup}_{x \in E}(\min_{k \in \{1, \ldots, K\}} \|x - \mathbf{f}_{k}\|_{1})\big] \quad (4.78)$$

*(cf. Definitions 1.2.4 and 1.3.4).*

*Proof of Proposition 4.3.1. Throughout this proof, let $F: \mathbb{R}^{d} \rightarrow \mathbb{R}$ satisfy for all $x \in \mathbb{R}^{d}$ that*

$$F(x) = \max_{k \in \{1, \ldots, K\}}(f(\mathbf{f}_{k}) - L\|x - \mathbf{f}_{k}\|_{1}). \quad (4.79)$$

Observe that Corollary 4.1.4, (4.79), and the assumption that for all $x, y \in E$ it holds that $|f(x) - f(y)| \leq L\|x - y\|_{1}$ assure that

$$\operatorname{sup}_{x \in E}|F(x) - f(x)| \leq 2L \big[\operatorname{sup}_{x \in E}(\min_{k \in \{1, \ldots, K\}}\|x - \mathbf{f}_{k}\|_{1})\big]. \quad (4.80)$$

Moreover, note that Lemma 4.2.9 ensures that for all $x \in E$ it holds that $F(x) = (\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(x)$. Combining this and (4.80) establishes (4.78). The proof of Proposition 4.3.1 is thus complete.

*Exercise 4.3.1. Prove or disprove the following statement: There exists $\Phi \in \mathbb{N}$ such that $\mathcal{I}(\Phi) = 2$, $\mathcal{O}(\Phi) = 1$, $\mathcal{P}(\Phi) < 20$, and*

$$\sup_{v = (x,y) \in [0,2]^{2}} \big| x^{2} + y^{2} - 2x - 2y + 2 - (\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(v) \big| \leq \frac{3}{8}. \quad (4.81)$$

## 4.3.2 Covering number estimates

**Definition 4.3.2** (Covering numbers). *Let $(E, \delta)$ be a metric space and let $r \in [0, \infty)$. Then we denote by $\mathcal{C}^{(E,\delta),r} \in \mathbb{N}_{0} \cup \{\infty\}$ (we denote by $\mathcal{C}^{E,r} \in \mathbb{N}_{0} \cup \{\infty\}$) the extended real number given by*

$$\mathcal{C}^{(E,\delta),r} = \min \bigg( \big\{n \in \mathbb{N}_{0} \colon \big[\exists A \subseteq E \colon \big[(|A| \leq n) \land (\forall x \in E \colon \exists a \in A \colon \delta_{(a,x)} \leq r)\big]\big] \big\} \cup \{\infty\} \bigg) \quad (4.82)$$

*and we call $\mathcal{C}^{(E,\delta),r}$ the $r$-covering number of $(E, \delta)$ (we call $\mathcal{C}^{E,r}$ the $r$-covering number of $E$).*

**Lemma 4.3.3.** Let $(E,\delta)$ be a metric space and let $r \in [0, \infty]$. Then

$$\mathcal{C}_{(E,\delta), r} = \begin{cases} \emptyset & : X = \emptyset \\ \inf \left( \left\{ n \in \mathbb{N} : \left( \exists x_1, x_2, \dots, x_n \in E : \right. \left. E \subseteq \bigcup_{m=1}^n \{ v \in E : d(x_m, v) \leq r \} \right) \right\} \cup \{ \infty \} \right) & : X \neq \emptyset \end{cases} \tag{4.83}$$

(cf. Definition 4.3.2).

*Proof of Lemma 4.3.3.* Throughout this proof, assume without loss of generality that $E \neq \emptyset$. Observe that Lemma 12.2.4 establishes (4.83). The proof of Lemma 4.3.3 is thus complete. $\Box$

*Exercise 4.3.2.* Prove or disprove the following statement: For every metric space $(X, d)$, every $Y \subseteq X$, and every $r \in [0, \infty]$ it holds that $\mathcal{C}_{(Y, d|_{Y \times Y}), r} \leq \mathcal{C}_{(X, d), r}$.

*Exercise 4.3.3.* Prove or disprove the following statement: For every metric space $(E,\delta)$ it holds that $\mathcal{C}_{(E,\delta), \infty} = 1$.

*Exercise 4.3.4.* Prove or disprove the following statement: For every metric space $(E,\delta)$ and every $r \in [0, \infty)$ with $\mathcal{C}_{(E,\delta), r} < \infty$ it holds that $E$ is bounded. (Note: A metric space $(E,\delta)$ is bounded if and only if there exists $r \in [0, \infty)$ such that it holds for all $x, y \in E$ that $\delta(x, y) \leq r$.)

*Exercise 4.3.5.* Prove or disprove the following statement: For every bounded metric space $(E,\delta)$ and every $r \in [0, \infty)$ it holds that $\mathcal{C}_{(E,\delta), r} < \infty$.

**Lemma 4.3.4.** Let $d \in \mathbb{N}$, $a \in \mathbb{R}$, $b \in (a, \infty)$, $r \in (0, \infty)$ and for every $p \in [1, \infty)$ let $\delta_p : ([a, b]^d \times ([a, b]^d) \to [0, \infty)$ satisfy for all $x, y \in [a, b]^d$ that $\delta_p(x, y) = \| x - y \|_p$ (cf. Definition 3.3.4). Then it holds for all $p \in [1, \infty)$ that

$$\mathcal{C}_{([a,b]^d,\delta_p),r} \leq \left( \frac{d^{1/p}(b-a)}{2r} \right)^d \leq \begin{cases} 1 & : r \geq \frac{d^{1/p}(b-a)}{2} \\ \left( \frac{d(b-a)}{r} \right)^d & : r < \frac{d^{1/p}(b-a)}{2}. \end{cases} \tag{4.84}$$

(cf. Definitions 4.2.6 and 4.3.2).

*Proof of Lemma 4.3.4.* Throughout this proof, let $(\mathfrak{N}_p)_{p \in [1, \infty)} \subseteq \mathbb{N}$ satisfy for all $p \in [1, \infty)$ that

$$\mathfrak{N}_p = \left\lceil \frac{d^{1/p}(b-a)}{2r} \right\rceil, \tag{4.85}$$

for every $N \in \mathbb{N}$, $i \in \{ 1, 2, \dots, N \}$ let $g_{N, i} \in [a, b]$ be given by

$$g_{N, i} = a + \frac{(i-1/2)(b-a)}{N} \tag{4.86}$$

and for every $p \in [1, \infty)$ let $A_p \subseteq [a, b]^d$ be given by

$$A_p = \{g_{\mathfrak{N}_p,1}, g_{\mathfrak{N}_p,2}, \dots, g_{\mathfrak{N}_p,\mathfrak{N}_p}\}^d \tag{4.87}$$

(cf. Definition 4.2.6). Observe that it holds for all $N \in \mathbb{N}$, $i \in \{1, 2, \dots, N\}$, $x \in [a + \frac{(i-1)(b-a)}{N}, g_{N,i}]$ that

$$|x - g_{N,i}| = a + \frac{(i-1/2)(b-a)}{N} - x \leq a + \frac{(i-1/2)(b-a)}{N} - \left(a + \frac{(i-1)(b-a)}{N}\right) = \frac{b-a}{2N}. \tag{4.88}$$

In addition, note that it holds for all $N \in \mathbb{N}$, $i \in \{1, 2, \dots, N\}$, $x \in [g_{N,i}, a + \frac{i(b-a)}{N}]$ that

$$|x - g_{N,i}| = x - \left(a + \frac{(i-1/2)(b-a)}{N}\right) \leq a + \frac{i(b-a)}{N} - \left(a + \frac{(i-1/2)(b-a)}{N}\right) = \frac{b-a}{2N}. \tag{4.89}$$

Combining this with (4.88) implies for all $N \in \mathbb{N}$, $i \in \{1, 2, \dots, N\}$, $x \in [a + \frac{(i-1)(b-a)}{N}, a + \frac{i(b-a)}{N}]$ that $|x - g_{N,i}| \leq \frac{(b-a)}{2N}$. This proves that for every $N \in \mathbb{N}$, $x \in [a, b]$ there exists $y \in \{g_{N,1}, g_{N,2}, \dots, g_{N,N}\}$ such that

$$|x - y| \leq \frac{b-a}{2N}. \tag{4.90}$$

This establishes that for every $p \in [1, \infty)$, $x = (x_1, x_2, \dots, x_d) \in [a, b]^d$ there exists $y = (y_1, y_2, \dots, y_d) \in A_p$ such that

$$\delta_p(x, y) = \|x - y\|_p = \left(\sum_{i=1}^d |x_i - y_i|^p\right)^{1/p} \leq \left(\sum_{i=1}^d \left(\frac{(b-a)}{2\mathfrak{N}_p}\right)^p\right)^{1/p} = \frac{d^{1/p}(b-a)}{2\mathfrak{N}_p} \leq \frac{d^{1/p}(b-a)2^r}{2d^{1/p}(b-a)} = r. \tag{4.91}$$

Combining this with (4.82), (4.87), (4.85), and the fact that $\forall x \in [0, \infty) : [x] \leq \mathbb{1}_{(0,1]}(x) + 2x\mathbb{1}_{[1,\infty)}(x) = \mathbb{1}_{(0,r]}(rx) + 2rx\mathbb{1}_{(r,\infty)}(rx)$ yields that for all $p \in [1, \infty)$ it holds that

$$\mathcal{C}^{([a,b]^d, \delta_p), r} \leq |A_p| = |\mathfrak{N}_p|^d = \left(\left[\frac{d^{1/p}(b-a)}{2r}\right]\right)^d \leq \left(\left[\frac{d(b-a)}{2r}\right]\right)^d$$

$$\begin{aligned} &\leq \left(\mathbb{1}_{(0,r]}\left(\frac{d(b-a)}{2}\right) + \frac{2d(b-a)}{2r}\mathbb{1}_{(r,\infty)}\left(\frac{d(b-a)}{2}\right)\right)^d \\ &= \mathbb{1}_{(0,r]}\left(\frac{d(b-a)}{2}\right) + \left(\frac{d(b-a)}{r}\right)^d \mathbb{1}_{(r,\infty)}\left(\frac{d(b-a)}{2}\right) \end{aligned}$$

(cf. Definition 4.3.2). The proof of Lemma 4.3.4 is thus complete.

## 4.3.3 Convergence rates for the approximation error

**Lemma 4.3.5.** Let $d \in \mathbb{N}$, $L, a \in \mathbb{R}$, $b \in (a, \infty)$, let $f: [a, b]^d \to \mathbb{R}$ satisfy for all $x, y \in [a, b]^d$ that $|f(x) - f(y)| \leq L \|x - y\|_1$, and let $\mathbf{F} = \mathbf{A}_{0, f([a+b)/2, (a+b)/2]^{\times d}} \in \mathbb{R}^{1 \times d} \times \mathbb{R}^1$ (cf. Definitions 2.3.1 and 3.3.4). Then

(i) it holds that $\mathcal{I}(\mathbf{F}) = d$,
