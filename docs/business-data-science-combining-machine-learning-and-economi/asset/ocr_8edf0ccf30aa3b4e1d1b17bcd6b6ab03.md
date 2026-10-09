![](bbox=[0.2, 0.08, 0.5, 0.42])

![](bbox=[0.55, 0.08, 0.86, 0.42])

FIGURE 2.3: Dominick’s OJ prices and sales (move) by brand. Note the use of log scale for both continuous variables.

Recall the logarithm definition,

$$\log(a) = b \Leftrightarrow a = e^{b} . \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (2.6)$$

Here, $e \approx 2.72$ is the natural base. We will always use natural logs. The base $e$ plays a central role in science and modeling of dynamic systems because $ex$ is its own derivative: $dex/dx = ex$. In a linear model for logged response, $\beta$ is added to log(y) for each unit increase in $x$: $$\log(y) = \alpha + \beta x. \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (2.7)$$

The fact that we are working in log space makes this model *multiplicative* in $y$. Recall some basic facts about logs and exponents: $\log(ab) = \log(a) + \log(b)$, $\log(a^{b}) = b \, \log(a)$, and $e^{a+b} = e^{a}e^{b}$. Exponentiate both sides of Equation 2.7: $$y = e^{\alpha}e^{\beta x} . \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (2.8)$$

Considering $x^{*} = x + 1$, we see that