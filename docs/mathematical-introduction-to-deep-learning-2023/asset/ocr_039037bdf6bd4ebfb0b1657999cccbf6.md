Proof of Lemma 3.1.4. Observe that (3.1) and (3.6) show that

```
$$\begin{aligned} w_{f}(h) &=\sup \left(\left\{|f(x)-f(y)| \in[0, \infty) : (x, y \in A \text { with } |x-y| \leq h)\right\} \cup\{0\}\right) \\ &\leq \sup \left(\left\{|L| x-y| \in[0, \infty) : (x, y \in A \text { with } |x-y| \leq h)\right\} \cup\{0\}\right) \\ &\leq \sup(\{L h, 0\})=L h \end{aligned} $$
```

(cf. Definition 3.1.1). The proof of Lemma 3.1.4 is thus complete.

# 3.1.2 Linear interpolation of one-dimensional functions

**Definition 3.1.5** (Linear interpolation operator). Let $K \in \mathbb{N}$, $\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}, f_{0}, f_{1}, \ldots, f_{K} \in \mathbb{R}$ satisfy $\mathfrak{f}_{0}<\mathfrak{f}_{1}<\ldots<\mathfrak{f}_{K}$. Then we denote by

```
$$\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}: \mathbb{R} \rightarrow \mathbb{R} $$
```

the function which satisfies for all $k \in\{1,2, \ldots, K\}, x \in(-\infty, \mathfrak{f}_{0}], y \in[\mathfrak{f}_{k-1}, \mathfrak{f}_{k}], z \in[\mathfrak{f}_{K}, \infty)$ that

```
$$\begin{aligned} &\left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(x)=f_{0}, \quad \left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(z)=f_{K}, \\ &\text { and } \quad \left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(y)=f_{k-1}+\left(\frac{y-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)\left(f_{k}-f_{k-1}\right) . \end{aligned} $$
```

**Lemma 3.1.6** (Elementary properties of the linear interpolation operator). Let $K \in \mathbb{N}$, $\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}, f_{0}, f_{1}, \ldots, f_{K} \in \mathbb{R}$ satisfy $\mathfrak{f}_{0}<\mathfrak{f}_{1}<\ldots<\mathfrak{f}_{K}$. Then

+   i) it holds for all $k \in\{0,1, \ldots, K\}$ that

```
$$\left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(\mathfrak{f}_{k})=f_{k}, $$
```

+   ii) it holds for all $k \in\{1,2, \ldots, K\}, x \in[\mathfrak{f}_{k-1}, \mathfrak{f}_{k}]$ that

```
$$\left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(x)=f_{k-1}+\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)\left(f_{k}-f_{k-1}\right), $$
```

and

+   iii) it holds for all $k \in\{1,2, \ldots, K\}, x \in[\mathfrak{f}_{k-1}, \mathfrak{f}_{k}]$ that

```
$$\left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(x)=\left(\frac{\mathfrak{f}_{k}-x}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right) f_{k-1}+\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right) f_{k} . $$
```

(cf. Definition 3.1.5).

Proof of Lemma 3.1.6. Note that (3.11) establishes items i) and ii). Observe that item ii) proves that for all $k \in\{1,2, \ldots, K\}, x \in[\mathfrak{f}_{k-1}, \mathfrak{f}_{k}]$ it holds that

```
$$\begin{aligned} \left(\mathcal{I}_{\mathfrak{f}_{0}, \mathfrak{f}_{1}, \ldots, \mathfrak{f}_{K}}^{f_{0}, f_{1}, \ldots, f_{K}}\right)(x) &=\left[\frac{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}-\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right)\right] f_{k-1}+\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right) f_{k} \\ &=\left(\frac{\mathfrak{f}_{k}-x}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right) f_{k-1}+\left(\frac{x-\mathfrak{f}_{k-1}}{\mathfrak{f}_{k}-\mathfrak{f}_{k-1}}\right) f_{k} . \end{aligned} $$
```

This establishes item iii). The proof of Lemma 3.1.6 is thus complete.