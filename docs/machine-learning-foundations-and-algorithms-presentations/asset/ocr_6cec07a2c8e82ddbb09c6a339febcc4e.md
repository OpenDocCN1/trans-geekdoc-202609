# Example: polynomial kernel

For $oldsymbol{x} = [x_1, x_2]^T$, let $\phi(oldsymbol{x}) = [x_1^2, \sqrt{2}x_1x_2, x_2^2]$

The kernel is defined by:

```
$k(\boldsymbol{x}, \boldsymbol{x}') = x_1^2x_1'^2 + 2x_1x_2x_1'x_2' + x_2^2x_2'^2$
$= (x_1x_1' + x_2x_2')^2$
$= \langle \boldsymbol{x}, \boldsymbol{x}' \rangle^2$
```

Kernel for polynomials of degree d:

```
$k(\boldsymbol{x}, \boldsymbol{x}') = \langle \boldsymbol{x}, \boldsymbol{x}' \rangle^d$
```