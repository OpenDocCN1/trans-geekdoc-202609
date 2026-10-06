# 6.6 Gradient Methods

**Remark 6.5 (Justification of the Iteration Direction)** Let the objective function $f$ be differentiable, and let $x^{i-1}, x^i \in \mathbb{R}^n$ (with $i \in \mathbb{N}$) be two arbitrary iteration points of Algorithm 6.3. We consider the quasi-Newton equation (6.11). The matrix $B^i$ in the quasi-Newton equation is now chosen in the class of $(n, n)$ diagonal matrices with real entries. For simplicity, we replace the matrix $B^i$ by the diagonal matrix

![](bbox=[0.435, 0.198, 0.562, 0.298])

where $b^{i} := (b_1^i, \dots, b_n^i) \in \mathbb{R}^n$. In this case, the quasi-Newton equation (6.11) can be written componentwise as

```
$b_k^i(x_k^i - x_k^{i-1}) = \frac{\partial f}{\partial x_k}(x^i) - \frac{\partial f}{\partial x_k}(x^{i-1}) \text{ for all } k \in \{1, \dots, n\. \quad (6.16)$
```

If $x_k^i 
eq x_k^{i-1}$ for every $k \in \{1, \dots, n\}$, then we get

```
$b_k^i = \frac{\partial f}{\partial x_k}(x^i) - \frac{\partial f}{\partial x_k}(x^{i-1})}{x_k^i - x_k^{i-1}} \text{ for all } k \in \1, \dots, n\.$
```

This results in the iteration direction

```
$d^i := -(B^i)^{-1} \nabla f(x^i) = - \begin{pmatrix} 1/b_1^i & & \ & \ddots & \ & & 1/b_n^i \end{pmatrix} \nabla f(x^i)$
```

if $b_1^i, \dots, b_n^i 
eq 0$. Under these assumptions, the components of the iteration direction can be simply written as

```
$d_k^i := -\frac{x_k^i - x_k^{i-1}}{\frac{\partial f}{\partial x_k}(x^i) - \frac{\partial f}{\partial x_k}(x^{i-1})} \text{ for all } k \in \{1, \dots, n\.$
```

This matrix-free formula is used in line 9 of Algorithm 6.3. Note that it is important to check that the denominator does not vanish. Thus, for each component of the negative gradient of $f$ at $x^i$, we determine an “individual step size” instead of