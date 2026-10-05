# Quotient Rule

For $h(x) = \frac{f(x)}{g(x)}$ where $g(x) \neq 0$, $h(x)$ is differentiable and

```
$h'(x) = \frac{g(x)f'(x) - f(x)g'(x)}{[g(x)]^2}$$
```

This rule works as (bottom (top') - top (bottom'))/(bottom squared)

Example:

```
$h(x) = \frac{x}{x^2+1}\nh'(x) = \frac{(x^2+1) \times (1) - x(2x)}{[x^2+1]^2}}\nh'(x) = \frac{1-x^2}{[x^2+1]^2}$
```

# Chain Rule

For a composition of functions $h(x) = f(g(x))$, $h(x)$ is differentiable and

```
$h'(x) = f'(g(x))g'(x)$
```

This rule works by taking the derivative of the outer function $f(x)$ while keeping the input unchanged, and multiplying by the derivative of the inner function.

Example 1:

```
$h(x) = (2-x)^3\nh'(x) = 3(2-x)^2(-1)$ \(apply power rule to outer)\nh'(x) = -3(2-x)^2$
```

For this problem, it is important to realize that $\frac{d}{dx}(2-x) = -1$.

Example 2:

```
$h(x) = e^{2x}\nh'(x) = e^{2x} \frac{d}{dx}(2x)\nh'(x) = 2e^{2x}$
```