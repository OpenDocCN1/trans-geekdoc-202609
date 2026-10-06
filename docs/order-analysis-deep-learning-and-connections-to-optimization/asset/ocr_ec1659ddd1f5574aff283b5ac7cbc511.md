# 162 7 Deep Learning with Set-Valued Inputs

With Definition 7.3, then we obtain the assertion.

+   (a) $a \leq 0 \leq \overline{a}$.\nNow, we have

```
$$\[a, \overline{a}]\| = sup_{a \in [a, \overline{a}]} |a| = max\{|a|, |\overline{a}|\}\$$
```

from which the assertion follows.

+   (c) $0 \leq a \leq \overline{a}$.\nFinally, we obtain

```
$$\[[a, \overline{a}]\| = sup_{a \in [a, \overline{a}]} |a| = \overline{a} = max\{|a|, |\overline{a}|\}\$$
```

leading to the assertion.

Because of the max term in the equality (7.14), the activation map $\mathcal{F}$ (as a function of the two variables $a$ and $\overline{a}$) is not differentiable everywhere. Non-differentiability exists for all $a$ and $\overline{a}$ with $|a| = |\overline{a}|$. Note that the softfunction $\varrho$ given in Definition 6.2 is differentiable.

**Remark 7.1** Let the function $\eta : \mathbb{R}_{++}^{+} \to \mathbb{R}$ with

```
$$\eta(a, \overline{a}) = max\{|a|, |\overline{a}|\} \text{ for all } a, \overline{a} \in \mathbb{R}_{++}$\$$
```

be. By Proposition 2.14, the function $\eta$ has the directional derivative at arbitrary $(a, \overline{a}) \in \mathbb{R}_{++}^2$.

```
$$\eta'(a, \overline{a})(h) = max_{i \in [a, \overline{a}]} {h_1, h_2} \text{ for all } h = (h_1, h_2) \in \mathbb{R}^2$\$$
```

with the index set

```
$$I(a, \overline{a}) := \{1 | a \in [a, \overline{a}]\} \cup \{2 | |\overline{a}| = \eta(a, \overline{a})\}$\$$
```

Consequently, for intervals $[a, \overline{a}] \in C_{int}(\mathbb{R})$ with $a > 0$, the differentiability of the max term in (7.14) holds.

For the solution of the optimization problem (7.2) in the case of sets in $C_{int}(\mathbb{R})$, we need formulas for the distance functions from Sect. 7.4.

**Theorem 7.4** Let $[a, \overline{a}], [b, \overline{b}] \in C_{int}(\mathbb{R})$ be arbitrarily chosen. Then we will have

+   (a) $d_H([a, \overline{a}], [b, \overline{b}]) = max\{|a-b|, |\overline{a}-\overline{b}|\}\n(b) If $a \leq 0 \leq \overline{a}$ and $b \leq 0 \leq \overline{b}$, then $d_l([a, \overline{a}], [b, \overline{b}]) = max\{|a-b|, |\overline{a}-\overline{b}|\}\n(c) $d_c([a, \overline{a}], [b, \overline{b}]) = max\{|a-b|, |\overline{a}-\overline{b}|\}$.