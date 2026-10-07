Axiomatics, the Social Sciences, and the Gödel Phenomenon: A Toolkit 47

# Beyond arithmetic

# Definition 14.8.

```
$$\Phi^{(\omega)} = \{(x, y) : x \in \Phi^{(y)}\}$$
```

for $x, y \in \omega$.

# Definition 14.9.

```
$$\Phi^{(\omega)}(m) = c_{\Phi^{(\omega)}}(m$
```

where $c_{\Phi^{(\omega)}}(m)$ is obtained in Proposition 13.1.

# Definition 14.10.

```
$$\Phi^{(\omega+1)} = (\Phi^{(\omega)})'$$
```

**Corollary 14.11.** $0^{(\omega+1)}$ is the degree of $\varnothing$.

**Corollary 14.12.** $\theta^{(\omega+1)}(m)$ is the characteristic function of a nonarithmetic subset of $\omega$ of degree $\mathbf{0}^{(\omega+1)}$.$

**Corollary 14.13.** If $T$ is arithmetically sound, then, for

```
$$\beta^{(\omega+1)} = \sigma(G(m_0(\Phi^{(\omega)}))$$
```

```
$G(m_0(\Phi^{(\omega)})) = \int_{-\infty}^{+\infty} \frac{C(m_0(\Phi^{(\omega)}), x)e^{-x^2}}{1 + C(m_0(\Phi^{(\omega)}), x)}dx$
```

```
$C(m_0(\Phi^{(\omega)}), x) = \lambda q(m_0(\Phi^{(\omega)}), x_1, \dots, x_r$.$
```

$N \models \beta^{(\omega+1)} = 0$ but $T \nvdash \beta^{(\omega+1)} = 0$ and $T \nvdash \neg\beta^{(\omega+1)} = 0$.

**Proposition 14.14.** If $T$ is arithmetically sound then, given any nontrivial predicate $P$,

+   (1) *there is a family of terms $\zeta_m \in \mathcal{L}_T$ such that there is no general algorithm to check, for every $m \in \omega$, whether or not $P(\zeta_m)$;*

+   (2) *there is a term $\zeta \in \mathcal{L}_T$ such that $\mathbf{M} \models P(\zeta)$ and $T \nvdash P(\zeta)$ and* (cut off)

+   (3) *neither the $\zeta_m$ nor $\zeta$ are arithmetically expressible.*