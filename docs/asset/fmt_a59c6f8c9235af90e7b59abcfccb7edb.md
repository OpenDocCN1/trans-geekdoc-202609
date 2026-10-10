
- 满足 $\mathcal{P}(\mathbf{F}) \leq 35 \binom{3d}{4r}^{2d} d^2 \mathbb{1}_{(0, a/4)}(r) + (d+1) \mathbb{1}_{[a/4, \infty)}(r)$，
- 满足 $\|T(\mathbf{F})\|_\infty \leq \max\{1, L, |a|, |b|, 2 \lceil \sup_{x \in [a, b]^d} |f(x)| \rceil\}$，且
- 满足 $\sup_{x \in [a, b]^d} |\mathcal{R}_\Gamma^\mathbf{N}(\mathbf{F})(x) - f(x)| \leq 2 L (b-a) r$（参见定义 1.2.4, 1.3.1, 1.3.4, 1.3.5 和 4.2.6）。

*命题 4.3.7 的证明.* 在整个证明过程中，不失一般性地假设 $r < a/4$（参见引理 4.3.5），设 $\delta : [a, b]^d \times [a, b]^d \to \mathbb{R}$ 对所有 $x, y \in [a, b]^d$ 满足

```
\delta(x, y) := \|x - y\|_1,
```

且设 $K \in \mathbb{N} \cup \{\infty\}$ 满足

```
K = \mathcal{C}^{([a,b]^d,\delta),(b-a)^r}.    (4.109)
```

注意引理 4.3.4 保证了 $K < \infty$。此结论与 (4.82) 确保了存在 $\mathbf{f}_{1}, \mathbf{f}_{2}, \ldots, \mathbf{f}_{K} \in [a,b]^{d}$ 使得

```
\sup _{x \in [a,b]^{d}}\left[\min _{k \in\{1,2, \ldots, K\}} \delta(x, \mathbf{f}_{k})\right] \leq(b-a)^{r}.    (4.110)
```

将此结论与命题 4.3.6 结合，确立了第 (i), (ii), (iii), (iv), (v), (vi), (vii) 和 (viii) 项。因此，命题 4.3.7 的证明完成。

### 命题 4.3.8（具有预设误差容限和显式参数边界的隐式多维 ANN 逼近）

设 $d \in \mathbb{N}$，$L, a \in \mathbb{R}$，$b \in [a, \infty)$，$\varepsilon \in (0,1]$ 且设 $f: [a, b]^{d} \rightarrow \mathbb{R}$ 对所有 $x, y \in [a, b]^{d}$ 满足

```
|f(x)-f(y)| \leq L\|x-y\|_{1}    (4.111)
```

（参见定义 3.3.4）。则存在 $\mathbf{F} \in \mathbf{N}$ 使得

- (i) 满足 $\mathcal{I}(\mathbf{F})=d$，
- (ii) 满足 $\mathcal{O}(\mathbf{F})=1$，
- (iii) 满足 $\mathcal{H}(\mathbf{F}) \leq d\left(\log _{2}\left(\max \left\{\frac{3 d L(b-a)}{2}, 1\right\}+\log _{2}\left(\varepsilon^{-1}\right)\right)+2\right)$，
- (iv) 满足 $\mathbb{D}_{1}(\mathbf{F}) \leq \varepsilon^{-d} d(3 d \max \{L(b-a), 1\})^{d}$，
- (v) 对所有 $i \in\{2,3,4, \ldots\}$，满足 $\mathbb{D}_{i}(\mathbf{F}) \leq \varepsilon^{-d} 3\left(\frac{(3 d L(b-a))^{i}}{2^{i}}+1\right)$，
- (vi) 满足 $\mathcal{P}(\mathbf{F}) \leq \varepsilon^{-2 d} 9\left(3 d \max \{L(b-a), 1\}\right)^{2 d} d^{2}$，
- (vii) 满足 $\|T(\mathbf{F})\|_{\infty} \leq \max \{1, L,|a|,|b|, 2\left[\sup _{x \in [a, b]^{d}}|f(x)|\right]\}$，且
- (viii) 满足 $\sup _{x \in [a, b]^{d}}\left(\mathcal{R} \mathbf{N}(\mathbf{F})(x)-f(x)\right) \leq \varepsilon$

（参见定义 1.2.4, 1.3.1, 1.3.4 和 1.3.5）。

*命题 4.3.8 的证明.* 在整个证明过程中，不失一般性地假设

```
L(b-a) \neq 0.    (4.112)
```

注意 (4.112) 确保了 $L \neq 0$ 且 $a < b$。将此结论与假设对所有 $x, y \in [a, b]^{d}$ 满足

```
|f(x)-f(y)| \leq L\|x-y\|_{1},    (4.113)
```

结合，确保了 $L > 0$。因此命题 4.3.7 确保了存在 $\mathbf{F} \in \mathbf{N}$ 满足

- (I) 满足 $\mathcal{I}(\mathbf{F}) = d$，
- (II) 满足 $\mathcal{O}(\mathbf{F}) = 1$，
- (III) 满足 $\mathcal{H}(\mathbf{F}) \le \big[ d \log_2(\frac{3dL(b-a)}{2\varepsilon}) + 1 \big] \mathbb{I}_{(0,d/4]}(\frac{\varepsilon}{2L(b-a)})$，
- (IV) 满足 $\mathbb{D}_1(\mathbf{F}) \le 2d(\frac{3dL(b-a)}{2\varepsilon})^d \mathbb{I}_{(0,d/4]}(\frac{\varepsilon}{2L(b-a)}) + \mathbb{I}_{(d/4,\infty)}(\frac{\varepsilon}{2L(b-a)})$，
- (V) 对所有 $i \in \{2, 3, 4, \ldots\}$，满足 $\mathbb{D}_i(\mathbf{F}) \le 3 \big[ (\frac{3dL(b-a)}{2\varepsilon})^d \frac{1}{2^{i-1}} \big]$，
- (VI) 满足 $\mathcal{P}(\mathbf{F}) \le 35 (\frac{3dL(b-a)}{2\varepsilon})^{2d} d^2 \mathbb{I}_{(0,d/4)}(\frac{\varepsilon}{2L(b-a)}) + (d+1) \mathbb{I}_{(d/4,\infty)}(\frac{\varepsilon}{2L(b-a)})$，
- (VII) 满足 $\|\mathcal{T}(\mathbf{F})\|_\infty \le \max\{1, L, |a|, |b|, 2 \|\mathrm{s}_{[a,b]^d}\|f(x)\|_\infty \}$，且
- (VIII) 满足 $\sup_{x \in [a,b]^d} |(\mathcal{R}_{\tau}^N(\mathbf{F}))(x) - f(x)| \le \varepsilon$

（参见定义 1.2.4, 1.3.1, 1.3.4, 1.3.5 和 4.2.6）。注意第 **(III)** 项确保了

```
\begin{align*}
\mathcal{H}(\mathbf{F}) \le \big( d \big( \log_2(\frac{3dL(b-a)}{2}) + \log_2(\varepsilon^{-1}) \big) + 2 \big) \mathbb{I}_{(0,d/4)}(\frac{\varepsilon}{2L(b-a)}) \\
\qquad \le d(\max \big\{ \log_2(\frac{3dL(b-a)}{2}), 0 \big\} + \log_2(\varepsilon^{-1})) + 2 . \qquad (4.114)
\end{align*}
```

此外，注意第 **(IV)** 项意味着

```
\begin{align*}
\mathbb{D}_1(\mathbf{F}) \le d (\frac{3d \max\{L(b-a), 1\}}{\varepsilon})^d \mathbb{I}_{(0,d/4)}(\frac{\varepsilon}{2L(b-a)}) + \mathbb{I}_{(d/4,\infty)}(\frac{\varepsilon}{2L(b-a)}) \\
\qquad \le \varepsilon^{-d} d(3d \max\{L(b-a), 1\})^d . \qquad (4.115)
\end{align*}
```

再者，注意第 **(V)** 项确立了对于所有 $i \in \{2, 3, 4, \ldots\}$，都有

```
\mathbb{D}_i(\mathbf{F}) \le 3 \big( \frac{3dL(b-a)}{2\varepsilon} \big)^d \frac{1}{2^{i-1}} + 1 \le \varepsilon^{-d} 3 (\frac{3dL(b-a)}{2\varepsilon})^d + 1 ). \qquad (4.116)
```

另外，注意第 **(VI)** 项确保了

```
\begin{align*}
\mathcal{P}(\mathbf{F}) \le 9 (\frac{3d \max\{L(b-a), 1\}}{\varepsilon})^{2d} d^2 \mathbb{I}_{(0,d/4)}(\frac{\varepsilon}{2L(b-a)}) + (d+1) \mathbb{I}_{(d/4,\infty)}(\frac{\varepsilon}{2L(b-a)}) \\
\qquad \le \varepsilon^{-2d} 9 (3d \max\{L(b-a), 1\})^{2d} d^2 . \qquad (4.117)
\end{align*}
```

将此结论与 (4.114)、(4.115) 和 (4.116) 结合第 **(I)、(II)、(VII)** 和 **(VIII)** 项，确立了第 (i), (ii), (iii), (iv), (v), (vi), (vii) 和 (viii) 项。因此，命题 4.3.8 的证明完成。

### 推论 4.3.9（具有预设误差容限和渐近参数边界的隐式多维 ANN 逼近）

*设* $d \in \mathbb{N}$，$L$, $a \in \mathbb{R}$，$b \in [a, \infty)$ *且设* $f \colon [a, b]^d \to \mathbb{R}$ *对所有* $x, y \in [a, b]^d$ *满足*

```
\left\vert f(x) - f(y)\right\vert \leq L\left\Vert x - y\right\Vert_1 \quad (4.118)
```

*(参见定义* **3.3.4**)。*则存在* $\mathfrak{C} \in \mathbb{R}$ *使得对所有* $\varepsilon \in (0,1]$ *存在* $\mathbf{F} \in \mathbf{N}$ *使得*

```
\mathcal{H}(\mathbf{F}) \leq \mathfrak{C}(\log_2(\varepsilon^{-1}) + 1), \qquad \left\Vert \mathcal{T}(\mathbf{F}) \right\Vert_\infty \leq \max\big\{1, L, \vert a\vert, \vert b\vert, 2\big[\sup_{x \in [a,b]^d}\vert f(x)\vert\big]\big\}, \quad (4.119)
```

```
\mathcal{R}^{\mathbf{N}}_\tau(\mathbf{F}) \in C(\mathbb{R}^d, \mathbb{R}), \quad \sup_{x \in [a,b]^d}\big(\left\vert \mathcal{R}^{\mathbf{N}}_\tau(\mathbf{F})\right)(x) - f(x)\big)\vert \leq \varepsilon, \quad \text{且} \quad \mathcal{P}(\mathbf{F}) \leq \mathfrak{C}\varepsilon^{-2d} \quad (4.120)
```

*(参见定义* **1.2.4, 1.3.1, 1.3.4 和 1.3.5**)。

*推论* **4.3.9 *的证明.* 在整个证明过程中，设* $\mathfrak{C} \in \mathbb{R}$ *满足*

```
\mathfrak{C} = 9\big(3d \, \max\{L(b-a), 1\}\big)^{2d} d^2. \quad (4.121)
```

注意命题 **4.3.8** 中的第 **(i), (ii), (iii), (vi), (vii) 和 (viii)** 项 *以及对于所有* $\varepsilon \in (0,1]$ *都有*

```
d\big(\log_2\big(\max\{\frac{3dL(b-a)}{2}, 1\}\big) + \log_2(\varepsilon^{-1})\big) + 2 \leq d\big(\max\big\{\frac{3dL(b-a)}{2}, 1\big\} + \log_2(\varepsilon^{-1})\big) + 2
\leq d \, \max\{3dL(b-a), 1\} + 2 + d \, \log_2(\varepsilon^{-1})
\leq \mathfrak{C}(\log_2(\varepsilon^{-1}) + 1) \quad (4.122)
```

*这意味着对于每个* $\varepsilon \in (0,1)$ *存在* $\mathbf{F} \in \mathbf{N}$ *使得*

```
\mathcal{H}(\mathbf{F}) \leq \mathfrak{C}(\log_2(\varepsilon^{-1}) + 1), \qquad \left\Vert \mathcal{T}(\mathbf{F}) \right\Vert_\infty \leq \max\big\{1, L, \vert a\vert, \vert b\vert, 2\big[\sup_{x \in [a,b]^d}\vert f(x)\vert\big]\big\}, \quad (4.123)
```

```
\mathcal{R}^{\mathbf{N}}_\tau(\mathbf{F}) \in C(\mathbb{R}^d, \mathbb{R}), \qquad \sup_{x \in [a,b]^d}\big(\left\vert \mathcal{R}^{\mathbf{N}}_\tau(\mathbf{F})\right)(x) - f(x)\big)\vert \leq \varepsilon, \quad \text{且} \quad \mathcal{P}(\mathbf{F}) \leq \mathfrak{C}\varepsilon^{-2d} \quad (4.124)
```

*(参见定义* **1.2.4, 1.3.1, 1.3.4 和 1.3.5**)。*推论* **4.3.9 *的证明至此完成。* $\square$

### 引理 4.3.10（向量范数的显式估计）

*设* $d \in \mathbb{N}$，*$p$、$q \in (0, \infty)$ 满足* $p \leq q$。*则对所有* $x \in \mathbb{R}^d$ *都有*

```
\left\Vert x \right\Vert_p \geq \left\Vert x \right\Vert_q \quad (4.125)
```

*(参见定义* **3.3.4**)。

引理 4.3.10 的证明。在整个证明过程中，不妨假设 $q < \infty$。令 $e_{1}, e_{2}, \ldots, e_{d} \in \mathbb{R}^{d}$ 满足 $e_{1} = (1, 0, \ldots, 0)$，$e_{2} = (0, 1, 0, \ldots, 0)$，$\ldots$，$e_{d} = (0, \ldots, 0, 1)$。令 $r \in \mathbb{R}$ 满足

```
r = p^{-1}q, \quad (4.126)
```

并令 $x = (x_{1}, \ldots, x_{d})$，$y = (y_{1}, \ldots, y_{d}) \in \mathbb{R}^{d}$ 满足对所有 $i \in \{1, 2, \ldots, d\}$ 有

```
y_{i} = |x_{i}|^{p}. \quad (4.127)
```

注意到 (4.127)、事实

```
y = \sum_{i=1}^{d} y_{i} e_{i}, \quad (4.128)
```

以及对所有 $v, w \in \mathbb{R}^{d}$ 均有

```
\|v + w\|_{r} \leq \|v\|_{r} + \|w\|_{r} \quad (4.129)
```

（参见定义 3.3.4）所保证的事实，我们有

```
\begin{align*}
```
