# **Exercise D.3** [Conditional independence iff joint factorizes]

In the text we said $X \perp Y | Z$ iff

```
p(x, y|z) = p(x|z)p(y|z)  
(D.86)
```

for all $x, y, z$ such that $p(z) > 0$. Now prove the following alternative definition: $X \perp Y | Z$ iff there exist functions $g$ and $h$ such that

```
p(x, y|z) = g(x, z)h(y, z)  
(D.87)
```

for all $x, y, z$ such that $p(z) > 0$.

# **Exercise D.4** [Uncorrelated does not imply independent]

Let $X \sim U(-1, 1)$ and $Y = X^2$. Clearly $Y$ is dependent on $X$ (in fact, $Y$ is uniquely determined by $X$). However, show that $\rho(X, Y) = 0$. Hint: if $X \sim U(a, b)$ then $E[X] = (a + b)/2$ and $\mathbb{V}[X] = (b - a)^2/12$.

# **Exercise D.5** [Correlation coefficient is between -1 and +1]

Prove that $-1 \le \rho(X, Y) \le 1$

# **Exercise D.6** [Correlation coefficient for linearly related variables is ±1]

Show that, if $Y = aX + b$ for some parameters $a > 0$ and $b$, then $\rho(X, Y) = 1$. Similarly show that if $a < 0$, then $\rho(X, Y) = -1$.

# **Exercise D.7** [Linear combinations of random variables]

Let **x** be a random vector with mean **m** and covariance matrix $\Sigma$. Let **A** and **B** be matrices.

+   a.  Derive the covariance matrix of **Ax**.
+   
+   b.  Show that tr(**AB**) = tr(**BA**).
+   
+   c.  Derive an expression for $\mathbb{E}\left[\mathbf{X}^{T}\mathbf{A}\mathbf{X}\right]$.

# **Exercise D.8** [Expected value of the minimum of two rv's]

Suppose $X, Y$ are two points sampled independently and uniformly at random from the interval $[0, 1]$. What is the expected location of the leftmost point?

# **Exercise D.9** [Convolution of two Gaussians is a Gaussian]

Show that the convolution of two Gaussians is a Gaussian, i.e.,

```
p(y) = $\mathcal{N}(x_1|\mu_1, \sigma_1^2) * \mathcal{N}(x_2|\mu_2, \sigma_2^2) = \mathcal{N}(y|\mu_1 + \mu_2, \sigma_1^2 + \sigma_2^2)$
(D.88)
```

where $y = x_1 + x_2,\ x_1 \sim \mathcal{N}(\mu_1, \sigma_1^2)$ and $x_2 \sim \mathcal{N}(\mu_2, \sigma_2^2)$.

# **Exercise D.10** [Variance of a sum]

Show that the variance of a sum is

```
$\mathbb{V}[X + Y] = \mathbb{V}[X] + \mathbb{V}[Y] + 2\text{Cov}[X, Y]$,  
(D.89)
```

where $\text{Cov}[X, Y]$ is the covariance between $X$ and $Y$.

# **Exercise D.11** [Deriving the inverse gamma density]

Let $X \sim \text{Ga}(a, b)$, and $Y = 1/X$. Derive the distribution of $Y$.