# 4.3.  ANN approximations results for multi-dimensional functions

Moreover, observe that the fact that $\frac{3d}{4r} \geq 3$ implies that

```
\begin{align*} \sum_{i=3}^{\mathcal{L}(\mathbf{F})-1} \binom{3d}{4r}^d \binom{3}{2^{i-2}} \binom{(3d)}{4r} \binom{3}{2^{i-3}} + 1) & \leq \binom{3d}{4r}^{2d} \sum_{i=3}^{\mathcal{L}(\mathbf{F})-1} \binom{3}{2^{i-2}} \binom{3}{2^{i-1}} + 1) \\ &= \binom{3d}{4r}^{2d} \sum_{i=3}^{\mathcal{L}(\mathbf{F})-1} \left[ \binom{9}{2^{2i-5}} + \binom{3}{2^{i-2}} \right] \\ &= \binom{3d}{4r}^{2d} \sum_{i=0}^{\mathcal{L}(\mathbf{F})-4} \left[ \binom{9}{2}(4^{-i}) + \binom{3}{2}(2^{-i}) \right] \\ & \leq \binom{3d}{4r}^{2d} \left( \binom{9}{2} \frac{1}{1-4^{-1}} + \binom{3}{2} \frac{1}{1-2^{-1}} \right) = 9 \binom{3d}{4r}^{2d}. \end{align*}
```

Combining this, (4.104), and (4.105) demonstrates that

```
\mathcal{P}(\mathbf{F}) \leq 26 \binom{3d}{4r}^{2d} d^2 + 9 \binom{3d}{4r}^{2d} \leq 35 \binom{3d}{4r}^{2d} d^2.
```

This establishes item (vi). The proof of Proposition 4.3.6 is thus complete. \qquad $\square$

**Proposition 4.3.7.** Let $d \in \mathbb{N}$, $L, a \in \mathbb{R}$, $b \in (a, \infty)$, $r \in (0, \infty)$ and let $f : [a, b]^d \to \mathbb{R}$ satisfy for all $x, y \in [a, b]^d$ that $|f(x) - f(y)| \leq L \|x - y\|$ (cf. Definition 3.3.4). Then there exists $\mathbf{F} \in \mathbf{N}$ such that

+   - it holds that $\mathcal{I}(\mathbf{F}) = d$,
- it holds that $\mathcal{O}(\mathbf{F}) = 1$,
- it holds that $\mathcal{H}(\mathbf{F}) \leq (\lceil d \log_2 \binom{3d}{4r} \rceil + 1) \mathbb{1}_{(0, a/4)}(r)$,
- it holds that $\mathbb{D}_1(\mathbf{F}) \leq 2d \binom{3d}{4r}^d \mathbb{1}_{(0, a/4)}(r) + \mathbb{1}_{[a/4, \infty)}(r)$,
- it holds for all $i \in \{2, 3, 4, \ldots\}$ that $\mathbb{D}_i(\mathbf{F}) \leq 3 \lceil \binom{3d}{4r}^d \frac{1}{2^{i-1}} \rceil$,
- it holds that $\mathcal{P}(\mathbf{F}) \leq 35 \binom{3d}{4r}^{2d} d^2 \mathbb{1}_{(0, a/4)}(r) + (d+1) \mathbb{1}_{[a/4, \infty)}(r)$,
- it holds that $\|T(\mathbf{F})\|_\infty \leq \max\{1, L, |a|, |b|, 2 \lceil \sup_{x \in [a, b]^d} |f(x)| \rceil\}$, and
- it holds that $\sup_{x \in [a, b]^d} |\mathcal{R}_\Gamma^\mathbf{N}(\mathbf{F})(x) - f(x)| \leq 2 L (b-a) r$ (cf. Definitions 1.2.4, 1.3.1, 1.3.4, 1.3.5, and 4.2.6).

*Proof of Proposition 4.3.7.* Throughout this proof, assume without loss of generality that $r < a/4$ (cf. Lemma 4.3.5), let $\delta : [a, b]^d \times [a, b]^d \to \mathbb{R}$ satisfy for all $x, y \in [a, b]^d$ that

```
\delta(x, y) := \|x - y\|_1,
```