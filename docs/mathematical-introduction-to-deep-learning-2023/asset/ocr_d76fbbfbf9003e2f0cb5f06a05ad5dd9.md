**Proposition 3.1.7** (Approximation and continuity properties for the linear interpolation operator). *Let \(K \in \mathbb{N}\), \(\mathfrak{f}_0, \mathfrak{f}_1, \ldots, \mathfrak{f}_K \in \mathbb{R}\) satisfy \(\mathfrak{f}_0 < \mathfrak{f}_1 < \ldots < \mathfrak{f}_K\) and let \(f : [\mathfrak{f}_0, \mathfrak{f}_K] \rightarrow \mathbb{R}\) be a function. Then*

+   * *(i) it holds for all \(x, y \in \mathbb{R}\) with \(x \neq y\) that*

```
$$
\begin{align*}
\left| \left( \mathscr{L}_{\mathfrak{f}_0, \mathfrak{f}_1, \ldots, \mathfrak{f}_K}^{f(\mathfrak{f}_0), f(\mathfrak{f}_1), \ldots, f(\mathfrak{f}_K)} \right)(x) - \left( \mathscr{L}_{\mathfrak{f}_0, \mathfrak{f}_1, \ldots, \mathfrak{f}_K}^{f(\mathfrak{f}_0), f(\mathfrak{f}_1), \ldots, f(\mathfrak{f}_K)} \right)(y) \right| 
&\le \left( \max_{k \in \{1, 2, \ldots, K\}} \left( \frac{w_f(\mathfrak{f}_k - \mathfrak{f}_{k-1})}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) \right) |x - y| \tag{3.16}
\end{align*}
$$
```

+   * *and (ii) it holds that*

```
$$
\sup_{x \in [\mathfrak{f}_0, \mathfrak{f}_k]} \left| \left( \mathscr{L}_{\mathfrak{f}_0, \mathfrak{f}_1, \ldots, \mathfrak{f}_K}^{f(\mathfrak{f}_0), f(\mathfrak{f}_1), \ldots, f(\mathfrak{f}_K)} \right)(x) - f(x) \right| \le w_f \left( \max_{k \in \{1, 2, \ldots, K\}} |\mathfrak{f}_k - \mathfrak{f}_{k-1}| \right) \tag{3.17}
$$
```

*(cf. Definitions 3.1.1 and 3.1.5).*

*Proof of Proposition 3.1.7. Throughout this proof, let \(L \in [0, \infty)\) satisfy*

```
$$
L = \max_{k \in \{1, 2, \ldots, K\}} \left( \frac{w_f(\mathfrak{f}_k - \mathfrak{f}_{k-1})}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) \tag{3.18}
$$
```

and let \(\mathfrak{l} : \mathbb{R} \rightarrow \mathbb{R}\) satisfy for all \(x \in \mathbb{R}\) that

```
$$
\mathfrak{l}(x) = \left( \mathscr{L}_{\mathfrak{f}_0, \mathfrak{f}_1, \ldots, \mathfrak{f}_K}^{f(\mathfrak{f}_0), f(\mathfrak{f}_1), \ldots, f(\mathfrak{f}_K)} \right)(x) \tag{3.19}
$$
```

*(cf. Definitions 3.1.1 and 3.1.5). Observe that item **(ii)** in Lemma 3.1.6, item **(iv)** in Lemma 3.1.2, and (3.18) ensure that for all \(k \in \{1, 2, \ldots, K\}\), \(x, y \in [\mathfrak{f}_{k-1}, \mathfrak{f}_k]\) with \(x \neq y\) it holds that*

```
$$
\begin{align*}
|\mathfrak{l}(x) - \mathfrak{l}(y)| & = \left| \left( \frac{x - \mathfrak{f}_{k-1}}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) \left( f(\mathfrak{f}_k) - f(\mathfrak{f}_{k-1}) \right) - \left( \frac{y - \mathfrak{f}_{k-1}}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) \left( f(\mathfrak{f}_k) - f(\mathfrak{f}_{k-1}) \right) \right| \\
& = \left( \frac{|f(\mathfrak{f}_k) - f(\mathfrak{f}_{k-1})|}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) (x - y) \le \left( \frac{w_f(\mathfrak{f}_k - \mathfrak{f}_{k-1})}{\mathfrak{f}_k - \mathfrak{f}_{k-1}} \right) |x - y| \le L |x - y|. \tag{3.20}
\end{align*}
$$
```

Furthermore, note that the triangle inequality and item **(i)** in Lemma 3.1.6 imply that for all \(k, l \in \{1, 2, \ldots, K\}\), \(x \in [\mathfrak{f}_{k-1}, \mathfrak{f}_k]\), \(y \in [\mathfrak{f}_{l-1}, \mathfrak{f}_l]\) with \(k < l\) it holds that

```
$$
\begin{align*}
|\mathfrak{l}(x) - \mathfrak{l}(y)| & \le |\mathfrak{l}(x) - \mathfrak{l}(\mathfrak{f}_k)| + |\mathfrak{l}(\mathfrak{f}_k) - \mathfrak{l}(\mathfrak{f}_{l-1})| + |\mathfrak{l}(\mathfrak{f}_{l-1}) - \mathfrak{l}(y)| \\
& = |\mathfrak{l}(x) - \mathfrak{l}(\mathfrak{f}_k)| + |f(\mathfrak{f}_k) - f(\mathfrak{f}_{l-1})| + |\mathfrak{l}(\mathfrak{f}_{l-1}) - \mathfrak{l}(y)| \\
& \le |\mathfrak{l}(x) - \mathfrak{l}(\mathfrak{f}_k)| + \left( \sum_{j = k + 1}^{l - 1} |f(\mathfrak{f}_j) - f(\mathfrak{f}_{j-1})| \right) + |\mathfrak{l}(\mathfrak{f}_{l-1}) - \mathfrak{l}(y)|. \tag{3.21}
\end{align*}
$$
```