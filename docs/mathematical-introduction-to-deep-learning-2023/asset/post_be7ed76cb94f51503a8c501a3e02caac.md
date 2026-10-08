
Proof of Lemma 3.1.4. Observe that (3.1) and (3.6) show that

$$
\begin{aligned}
w_{f}(h) &=\sup \left(\left\{|f(x)-f(y)| \in[0, \infty) : (x, y \in A \text { with } |x-y| \leq h)\right\} \cup\{0\}\right) \\
&\leq \sup \left(\left\{|L| x-y| \in[0, \infty) : (x, y \in A \text { with } |x-y| \leq h)\right\} \cup\{0\}\right) \\
&\leq \sup(\{L h, 0\})=L h
\end{aligned}
$$

(cf. Definition 3.1.1). The proof of Lemma 3.1.4 is thus complete.

## 3.1.2 Linear interpolation of one-dimensional functions

**Definition 3.1.5** (Linear interpolation operator). Let $K \in \mathbb{N}$, $\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}, f_{0}, f_{1}, \ldots, f_{K} \in \mathbb{R}$ satisfy $\mathfrak{f}_{0}<\mathfrak{f}_{1}<\ldots<\mathfrak{f}_{K}$. Then we denote by

$$
\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}: \mathbb{R} \rightarrow \mathbb{R}
$$

the function which satisfies for all $k \in\{1,2, \ldots, K\}, x \in(-\infty, \mathfrak{f}_{0}], y \in[\mathfrak{f}_{k-1}, \mathfrak{f}_{k}], z \in[\mathfrak{f}_{K}, \infty)$ that

$$
\begin{aligned}
&\left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(x)=f_{0}, \quad \left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(z)=f_{K}, \\
&\text { and } \quad \left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(y)=f_{k-1}+\left(\frac{y-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)\left(f_{k}-f_{k-1}\right) .
\end{aligned}
$$

**Lemma 3.1.6** (Elementary properties of the linear interpolation operator). Let $K \in \mathbb{N}$, $\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}, f_{0}, f_{1}, \ldots, f_{K} \in \mathbb{R}$ satisfy $\mathfrak{f}_{0}<\mathfrak{f}_{1}<\ldots<\mathfrak{f}_{K}$. Then

- i) it holds for all $k \in\{0,1, \ldots, K\}$ that

$$
\left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(\mathfrak{f}_{k})=f_{k},
$$

- ii) it holds for all $k \in\{1,2, \ldots, K\}, x \in[\mathfrak{f}_{k-1}, \mathfrak{f}_{k}]$ that

$$
\left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(x)=f_{k-1}+\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)\left(f_{k}-f_{k-1}\right),
$$

and

- iii) it holds for all $k \in\{1,2, \ldots, K\}, x \in[\mathfrak{f}_{k-1}, \mathfrak{f}_{k}]$ that

$$
\left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(x)=\left(\frac{\mathfrak{f}_{k}-x}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right) f_{k-1}+\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right) f_{k} .
$$

(cf. Definition 3.1.5).

Proof of Lemma 3.1.6. Note that (3.11) establishes items i) and ii). Observe that item ii) proves that for all $k \in\{1,2, \ldots, K\}, x \in[\mathfrak{f}_{k-1}, \mathfrak{f}_{k}]$ it holds that

$$
\begin{aligned}
\left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(x) &=\left[\frac{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}-\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)\right] f_{k-1}+\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right) f_{k} \\
&=\left(\frac{\mathfrak{f}_{k}-x}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right) f_{k-1}+\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right) f_{k} .
\end{aligned}
$$

This establishes item iii). The proof of Lemma 3.1.6 is thus complete.

**Proposition 3.1.7** (Approximation and continuity properties for the linear interpolation operator). *Let \(K \in \mathbb{N}\), \(\mathfrak{f}_0, \mathfrak{f}_1, \ldots, \mathfrak{f}_K \in \mathbb{R}\) satisfy \(\mathfrak{f}_0 < \mathfrak{f}_1 < \ldots < \mathfrak{f}_K\) and let \(f : [\mathfrak{f}_0, \mathfrak{f}_K] \rightarrow \mathbb{R}\) be a function. Then*

- *(i) it holds for all \(x, y \in \mathbb{R}\) with \(x \neq y\) that*

$$
\begin{align*}
\left| \left( \mathscr{L}_{\mathfrak{f}_0, \mathfrak{f}_1, \ldots, \mathfrak{f}_K}^{f(\mathfrak{f}_0), f(\mathfrak{f}_1), \ldots, f(\mathfrak{f}_K)} \right)(x) - \left( \mathscr{L}_{\mathfrak{f}_0, \mathfrak{f}_1, \ldots, \mathfrak{f}_K}^{f(\mathfrak{f}_0), f(\mathfrak{f}_1), \ldots, f(\mathfrak{f}_K)} \right)(y) \right| 
&\le \left( \max_{k \in \{1, 2, \ldots, K\}} \left( \frac{w_f(\mathfrak{f}_k - \mathfrak{f}_{k-1})}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) \right) |x - y| \tag{3.16}
\end{align*}
$$

- *and (ii) it holds that*

$$
\sup_{x \in [\mathfrak{f}_0, \mathfrak{f}_k]} \left| \left( \mathscr{L}_{\mathfrak{f}_0, \mathfrak{f}_1, \ldots, \mathfrak{f}_K}^{f(\mathfrak{f}_0), f(\mathfrak{f}_1), \ldots, f(\mathfrak{f}_K)} \right)(x) - f(x) \right| \le w_f \left( \max_{k \in \{1, 2, \ldots, K\}} |\mathfrak{f}_k - \mathfrak{f}_{k-1}| \right) \tag{3.17}
$$

*(cf. Definitions 3.1.1 and 3.1.5).*

*Proof of Proposition 3.1.7. Throughout this proof, let \(L \in [0, \infty)\) satisfy*

$$
L = \max_{k \in \{1, 2, \ldots, K\}} \left( \frac{w_f(\mathfrak{f}_k - \mathfrak{f}_{k-1})}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) \tag{3.18}
$$

and let \(\mathfrak{l} : \mathbb{R} \rightarrow \mathbb{R}\) satisfy for all \(x \in \mathbb{R}\) that

$$
\mathfrak{l}(x) = \left( \mathscr{L}_{\mathfrak{f}_0, \mathfrak{f}_1, \ldots, \mathfrak{f}_K}^{f(\mathfrak{f}_0), f(\mathfrak{f}_1), \ldots, f(\mathfrak{f}_K)} \right)(x) \tag{3.19}
$$

*(cf. Definitions 3.1.1 and 3.1.5). Observe that item **(ii)** in Lemma 3.1.6, item **(iv)** in Lemma 3.1.2, and (3.18) ensure that for all \(k \in \{1, 2, \ldots, K\}\), \(x, y \in [\mathfrak{f}_{k-1}, \mathfrak{f}_k]\) with \(x \neq y\) it holds that*

$$
\begin{align*}
|\mathfrak{l}(x) - \mathfrak{l}(y)| & = \left| \left( \frac{x - \mathfrak{f}_{k-1}}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) \left( f(\mathfrak{f}_k) - f(\mathfrak{f}_{k-1}) \right) - \left( \frac{y - \mathfrak{f}_{k-1}}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) \left( f(\mathfrak{f}_k) - f(\mathfrak{f}_{k-1}) \right) \right| \\
& = \left( \frac{|f(\mathfrak{f}_k) - f(\mathfrak{f}_{k-1})|}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) (x - y) \le \left( \frac{w_f(\mathfrak{f}_k - \mathfrak{f}_{k-1})}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) |x - y| \le L |x - y|. \tag{3.20}
\end{align*}
$$

Furthermore, note that the triangle inequality and item **(i)** in Lemma 3.1.6 imply that for all \(k, l \in \{1, 2, \ldots, K\}\), \(x \in [\mathfrak{f}_{k-1}, \mathfrak{f}_k]\), \(y \in [\mathfrak{f}_{l-1}, \mathfrak{f}_l]\) with \(k < l\) it holds that

$$
\begin{align*}
|\mathfrak{l}(x) - \mathfrak{l}(y)| & \le |\mathfrak{l}(x) - \mathfrak{l}(\mathfrak{f}_k)| + |\mathfrak{l}(\mathfrak{f}_k) - \mathfrak{l}(\mathfrak{f}_{l-1})| + |\mathfrak{l}(\mathfrak{f}_{l-1}) - \mathfrak{l}(y)| \\
& = |\mathfrak{l}(x) - \mathfrak{l}(\mathfrak{f}_k)| + |f(\mathfrak{f}_k) - f(\mathfrak{f}_{l-1})| + |\mathfrak{l}(\mathfrak{f}_{l-1}) - \mathfrak{l}(y)| \\
& \le |\mathfrak{l}(x) - \mathfrak{l}(\mathfrak{f}_k)| + \left( \sum_{j = k + 1}^{l - 1} |f(\mathfrak{f}_j) - f(\mathfrak{f}_{j-1})| \right) + |\mathfrak{l}(\mathfrak{f}_{l-1}) - \mathfrak{l}(y)|. \tag{3.21}
\end{align*}
$$

Item (iv) in Lemma 3.1.2, and (3.18) hence demonstrate that for all $k,l \in \{1,2,\dots,K\}$, $x \in [\mathfrak{f}_{k-1}, \mathfrak{f}_k]$, $y \in [\mathfrak{f}_{l-1}, \mathfrak{f}_l]$ with $k < l$ and $x \ne y$ it holds that

$$
\begin{align}
|\mathfrak{l}(x)-\mathfrak{l}(y)| &\leq |\mathfrak{l}(x)-\mathfrak{l}(\mathfrak{f}_{k})|+\left(\sum_{j=k+1}^{l-1}w_{f}(\mathfrak{f}_{j}-\mathfrak{f}_{j-1})\right)+\left|\mathfrak{l}(\mathfrak{f}_{l-1})-\mathfrak{l}(y)\right| \\
&= |\mathfrak{l}(x)-\mathfrak{l}(\mathfrak{f}_{k})|+\left(\sum_{j=k+1}^{l-1}\left(\frac{w_{f}(\mathfrak{f}_{j}-\mathfrak{f}_{j-1})}{\mathfrak{f}_{j}-\mathfrak{f}_{j-1}}\right)(\mathfrak{f}_{j}-\mathfrak{f}_{j-1})\right)+\left|\mathfrak{l}(\mathfrak{f}_{l-1})-\mathfrak{l}(y)\right| \tag{3.22}\\
&\leq |\mathfrak{l}(x)-\mathfrak{l}(\mathfrak{f}_{k})|+L(\mathfrak{f}_{l-1}-\mathfrak{f}_{k})+|\mathfrak{l}(y)-\mathfrak{l}(\mathfrak{f}_{l-1})|.
\end{align}
$$

This and (3.21) show that for all $k,l \in \{1,2,\dots,K\}$, $x \in [\mathfrak{f}_{k-1}, \mathfrak{f}_k]$, $y \in [\mathfrak{f}_{l-1}, \mathfrak{f}_l]$ with $k < l$ and $x \ne y$ it holds that

$$
|\mathfrak{l}(x)-\mathfrak{l}(y)| \leq L \left( (\mathfrak{f}_{k}-x)+\left(\sum_{j=k+1}^{l-1}(\mathfrak{f}_{j}-\mathfrak{f}_{j-1})\right)+(y-\mathfrak{f}_{l-1}) \right) = L |x-y| \tag{3.23}
$$

Combining this and (3.20) proves that for all $x, y \in [\mathfrak{f}_{0}, \mathfrak{f}_K]$ with $x \ne y$ it holds that

$$
|\mathfrak{l}(x)-\mathfrak{l}(y)| \leq L |x-y|. \tag{3.24}
$$

This, the fact that for all $x, y \in (-\infty, \mathfrak{f}_0]$ with $x \ne y$ it holds that

$$
|\mathfrak{l}(x)-\mathfrak{l}(y)| = 0 \leq L |x-y|, \tag{3.25}
$$

the fact that for all $x, y \in [\mathfrak{f}_K, \infty)$ with $x \ne y$ it holds that

$$
|\mathfrak{l}(x)-\mathfrak{l}(y)| = 0 \leq L |x-y|, \tag{3.26}
$$

and the triangle inequality therefore establish that for all $x, y \in \mathbb{R}$ with $x \ne y$ it holds that

$$
|\mathfrak{l}(x)-\mathfrak{l}(y)| \leq L |x-y|. \tag{3.27}
$$

This proves item (i). Observe that item (iii) in Lemma 3.1.6 ensures that for all $k \in \{1,2,\dots,K\}$, $x \in [\mathfrak{f}_{k-1}, \mathfrak{f}_k]$ it holds that

$$
\begin{align}
|\mathfrak{l}(x)-f(x)| &= \left|\left(\frac{\mathfrak{f}_{k}-x}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)f(\mathfrak{f}_{k-1})+\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)f(\mathfrak{f}_{k})-f(x)\right| \\
&= \left|\left(\frac{\mathfrak{f}_{k}-x}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)(f(\mathfrak{f}_{k-1})-f(x))+\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)(f(\mathfrak{f}_{k})-f(x))\right| \\
&\leq \left(\frac{\mathfrak{f}_{k}-x}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)|f(\mathfrak{f}_{k-1})-f(x)| + \left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)|f(\mathfrak{f}_{k})-f(x)|. \tag{3.28}
\end{align}
$$
