# Chapter 3: One-dimensional ANN approximation results

# **Lemma 3.3.2** (Approximations through ANNs with constant realizations).

Let $L, a \in \mathbb{R}$, $b \in [a, \infty)$, $\xi \in [a, b]$, let $f: [a, b] \rightarrow \mathbb{R}$ satisfy for all $x, y \in [a, b]$ that

```
|f(x) - f(y)| \leq L|x - y|,										(3.79)
```

and let $\mathbf{F} \in \mathbf{N}$ satisfy

```
\mathbf{F} = \mathbf{A}_{1,f(\xi)} \bullet (0 \otimes (\mathbf{i}_1 \bullet \mathbf{A}_{1,-\xi}))						(3.80)
```

(cf. Definitions 1.3.1, 2.1.1, 2.3.1, 2.3.4, and 3.2.1). Then

+   - (i) it holds that $\mathcal{D}(\mathbf{F}) = (1, 1, 1)$,

+   - (ii) it holds that $\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{F}) \in C(\mathbb{R}, \mathbb{R})$,

+   - (iii) it holds for all $x \in \mathbb{R}$ that $((\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{F}))(x) = f(\xi)$,

+   - (iv) it holds that $\sup_{x \in [a,b]}(|(\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{F}))(x) - f(x)| \leq L \max\{\xi - a, b - \xi\}$, and

+   - (v) it holds that $\mathcal{P}(\mathbf{F}) = 4$.

(cf. Definitions 1.2.4 and 1.3.4).

*Proof of Lemma 3.3.2.* Observe that items (i) and (ii) in Lemma 2.3.3, and items (ii) and (iii) in Lemma 3.2.4 establish items (i) and (ii). Note that item (iii) in Lemma 2.3.3 and item (iii) in Lemma 2.3.5 imply that for all $x \in \mathbb{R}$ it holds that

```
\begin{aligned} ((\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{F}))(x) &= ((\mathcal{R}_{\xi}^{\mathbf{N}}(0 \otimes (\mathbf{i}_1 \bullet \mathbf{A}_{1,-\xi}))) (x) + f(\xi) \\
&= 0 \big( (\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{i}_1 \bullet \mathbf{A}_{1,-\xi})(x)) \big) + f(\xi) = f(\xi) \end{aligned}			(3.81)
```

(cf. Definitions 1.2.4 and 1.3.4). This proves item (iii). Observe that (3.81), the fact that $\xi \in [a, b]$, and the assumption that for all $x, y \in [a, b]$ it holds that

```
|f(x) - f(y)| \leq L|x - y|										(3.82)
```

demonstrate that for all $x \in [a, b]$ it holds that

```
|(\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{F}))(x) - f(x)| = |f(\xi) - f(x)| \leq L|x - \xi| \leq L \max\{\xi - a, b - \xi\}.	(3.83)
```

This establishes item (iv). Note that (1.78) and item (i) show that

```
\mathcal{P}(\mathbf{F}) = 1(1+1)+1(1+1) = 4.									(3.84)
```

This proves item (v). The proof of Lemma 3.3.2 is thus complete.