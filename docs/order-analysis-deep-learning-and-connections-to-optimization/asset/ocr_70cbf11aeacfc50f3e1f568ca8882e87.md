Assumption 3.2 $\tilde{S}$ be a nonempty subset of real linear space $X$. Let $Y := \mathbb{R}^m$ (for some $m \in \mathbb{N}$), $C := \mathbb{R}^m_+$, and $g := (g_1, \dots, g_m): \tilde{S} \to \mathbb{R}^m$ be given. Let $f: \tilde{S} \to \mathbb{R}$ be a given functional, let the constraint set

```
$S := \{x \in \tilde{S} \mid g_k(x) \leq 0 \text{ for all } k \in \{1, \dots, m\}$
```

be nonempty.

Theorem 3.2 ([35, Theorem 3.14]) Let Assumption 3.2 be satisfied, and let $\bar{x} \in S$ be a feasible point. Let

```
$I(\bar{x}) := \{k \in \{1, \dots, m\} \mid g_k(\bar{x}) = 0\}$
```

denote the index set of "active" inequality constraints, and let

```
$J(\bar{x}) := \{k \in \{1, \dots, m\} \setminus I(\bar{x}) \mid g_k(x) \leq g_k(\bar{x}) \text{ for all } x \in S\}$ (3.8)
```

denote the index set of "nearly active" inequality constraints. There exist nonnegative real numbers $\alpha_k, \beta_k (in I(\ar{x})), \gamma_k (in J(\\bar{x})),$ where at least one of them is nonzero, and linear functionals $\ell_0 \in \partial_- f(\barbar{x}), \ell_k \in \partial_- g_k(\barbar{x}) (k \in I(\ar{x})), \ell_k \in \partial_- g_k(\barbar{x}) (k \in J(\\bar{x}))$ so that

```
$\alpha \ell_0 + \sum_{k \in I(\ar{x})} \beta_k \ell_k + \sum_{k \in J(\barbar{x})} \gamma_k \ell_k = 0_{\bar{x}}.$ (3.9)
```

Then the vector $\bar{x}$ is a unique minimal solution of the optimization problem $
min_{x \in S} f(x).

Proof Let the given assumptions be satisfied. With the equality (3.9), we then obtain for an arbitrary $x \in \tilde{S}$ with $\bar{x} \neq \bar{x}$

```
$\max {f(x) - f(\barbar{x}), g_1(x), \dots, g_m(x), (g_k(x) - g_k(\barbar{x}))_{k \in J(\\bar{x})}\n\\==\\bar{x)}\}$
```

```
$= \frac{1}{\alpha + \sum_{k \in I(\\bar{x})} \beta_k + \sum_{k \in J(\\bar{x})} \gamma_k} \left( \alpha \ell_0(x) + \sum_{k \in I(\\bar{x})} \beta_k \ell_k(x) + \sum_{k \in J(\\bar{x})} \gamma_k \ell_k(x) \right)\n\\==\\\\delta > 0$
```

```
$\geq \delta \left( \alpha(f(x) - f(\\barbar{x})) + \sum_{k \in I(\\barbar{x})} \beta_k g_k(x) + \sum_{k \in J(\\barbar{x})} \gamma_k (g_k(x) - g_k(\\barbar{x})) \right)$
```

```
$> \delta \left( \alpha \ell_0(x - \barbar{x}) + \sum_{k \in I(\\barbar{x})} \beta_k [g_k(\\barbar{x}) + \ell_k(x - \barbar{x})] + \sum_{k \in J(\\barbar{x})} \gamma_k \ell_k(x - \barbar{x}) \right)$
```