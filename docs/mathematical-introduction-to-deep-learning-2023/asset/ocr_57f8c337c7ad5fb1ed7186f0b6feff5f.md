# Contents

The optimization problem of computing approximate minimizers of the function $\mathfrak{L}$ is not suitable for discrete numerical computations on a computer as the function $\mathfrak{L}$ is defined on the infinite dimensional vector space $C(\mathbb{R}^{d}, \mathbb{R})$.

To overcome this we introduce a spatially discretized version of this optimization problem. More specifically, let $\mathfrak{d} \in \mathbb{N}$, let $\psi = (\psi_{\theta})_{\theta \in \mathbb{R}^{\mathfrak{d}}} : \mathbb{R}^{\mathfrak{d}} \to C(\mathbb{R}^{d}, \mathbb{R})$ be a function, and let $\mathcal{L} : \mathbb{R}^{\mathfrak{d}} \to [0, \infty)$ satisfy

```
$\mathcal{L} = \mathfrak{L} \circ \psi.$
```

We think of the set

```
$\{\psi_{\theta} : \theta \in \mathbb{R}^{\mathfrak{d}}\} \subseteq C(\mathbb{R}^{d}, \mathbb{R})$ 
(6)
```

as a parametrized set of functions which we employ to approximate the infinite dimensional vector space $C(\mathbb{R}^{d}, \mathbb{R})$ and we think of the function

```
$\mathbb{R}^{\mathfrak{d}} \ni \theta \mapsto \psi_{\theta} \in C(\mathbb{R}^{d}, \mathbb{R})$ 
(7)
```

as the parametrization function associated to this set. For example, in the case $d = 1$ one could think of (7) as the parametrization function associated to polynomials in the sense that for all $\theta = (\theta_{1}, \dots, \theta_{\mathfrak{d}}) \in \mathbb{R}^{\mathfrak{d}}$, $x \in \mathbb{R}$ it holds that

```
$\psi_{\theta}(x) = \sum_{k=0}^{\mathfrak{d}-1} \theta_{k+1} x^{k}$ 
(8)
```

or one could think of (7) as the parametrization associated to trigonometric polynomials. However, in the context of *deep supervised learning* one neither chooses (7) as parametrization of polynomials nor as parametrization of trigonometric polynomials, but instead one chooses (7) as a parametrization associated to *deep ANN s*. In Chapter 1 in Part I we present different types of such deep ANN parametrization functions in all mathematical details.

Taking the set in (6) and its parametrization function in (7) into account, we then intend to compute approximate minimizers of the function $\mathfrak{L}$ restricted to the set $\{\psi_{\theta} : \theta \in \mathbb{R}^{\mathfrak{d}}\}$, that is, we consider the optimization problem of computing approximate minimizers of the function

```
$\{\psi_{\theta} : \theta \in \mathbb{R}^{\mathfrak{d}}\} \ni \phi \mapsto \mathfrak{L}(\phi) = \frac{1}{M} \left[ \sum_{m=1}^{M} \left|\phi(x_{m}) - y_{m}\right|^{2} \right] \in [0, \infty).$ 
(9)
```

Employing the parametrization function in (7), one can also reformulate the optimization problem in (9) as the optimization problem of computing approximate minimizers of the function

```
$\mathbb{R}^{\mathfrak{d}} \ni \theta \mapsto \mathcal{L}(\theta) = \mathfrak{L}(\psi_{\theta}) = \frac{1}{M} \left[ \sum_{m=1}^{M} \left|\psi_{\theta}(x_{m}) - y_{m}\right|^{2} \right] \in [0, \infty)$ 
(10)
```