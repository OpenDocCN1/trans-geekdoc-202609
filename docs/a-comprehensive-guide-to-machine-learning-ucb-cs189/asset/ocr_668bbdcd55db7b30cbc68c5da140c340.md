# 8.3. BOOSTING

```
$arg \min_{\alpha, G} \sum_{i=1}^{n} e^{-y_i F_{m-i}(x_i)} e^{-y_i, \alpha G(x_i)}$
```

The term $w_i^{(m)} := e^{-y_i F_{m-i}(x_i)}$ is a constant with respect to our optimization variables. We can split this out sum into the components which correctly classify points and incorrectly classified points:

```
$$\alpha_{m, G_m} = \arg \min_{\alpha, y=G(x)} e^{-\alpha} \sum_{y \neq G(x)} w_i^{(m)} e^{\alpha} \quad (*)$$\n$\alpha = \arg \min_{\alpha, G} \sum_{y \neq G(x)} w_i^{(m)} e^{-\alpha} \sum_{i=1}^{n} w_i^{(m)} e^{\\alpha}$
```

For a fixed value of $\alpha$, the second term does not depend on $G$. We can then see that the best choice of $G_m(x)$ is the classifier that minimizes the error weights $w_i^{(m)}$.

```
$e_m = \frac{\sum_{y \neq G_m(x)} w_i^{(m)}}{\sum w_i^{(m)}}$
```

Once we have obtained $G_m$, we can solve for $\alpha_m$ by dividing ($*$) by the constant $\sum_{i=1}^{n} w_i^{(m)}$, we obtain

```
$$\alpha_m = \arg \min_{\alpha} (1-e_m) e^{-\alpha} + e_m e^{\alpha}$
```

which has the solution (left as exercise)

```
$$\alpha_m = \frac{1}{2} \ln \left(\\frac{1-e_m}{e_m}\right)$
```

as claimed earlier.

From the optimal $\alpha_m$, we can derive the weights:

```
$w_i^{(m+1)} = \exp(-y_i F_m(x_i))$$\n$= \exp(-y_i [F_{m-1}(x_i) + \alpha_m G_m(x_i)]$\n$= w_i^{(m)} \exp(-y_i G_m(x_i) \alpha_m)$$\n$= w_i^{(m)} \exp(-y_i G_m(x_i) \frac{1}{2} \ln \left(\\frac{1-e_m}{e_m}\right))$$\n$= w_i^{(m)} \exp \left[ln \left(\\frac{1-e_m}{e_m}\right) - \frac{1}{2} y_i G_m(x_i)\right]$\n$= w_i^{(m)} \left(\\frac{1-e_m}{e_m}\right)^{-\frac{1}{2} y_i G_m(x_i)}$
```

We see that the multiplicative factor is $\frac{e_m}{1-e_m}$ when $y_i = G_m(x_i)$ and $\frac{1-e_m}{e_m}$ otherwise. This completes the development of the algorithm.

As a final note about the intuition, we view these updates as pushing towards a solution in some direction until we can no longer improve our performance. More precisely, whenever we