# 3.3. CANONICAL CORRELATION ANALYSIS

```
$= \sum_{i=1}^{n} ||x_i||^2 - \sum_{i=1}^{n} (x_i^T u)^2 \n\\epsilon_{PCA,Var(u)}$
```

where (*) holds by the Pythagorean theorem

```
$||x - P_u x||^2 + ||P_u x||^2 = ||x||^2$
```

since $x - P_u x \perp P_u x$. Then the first term $\sum_i ||x_i||$ is constant with respect to $u$, we have\n$\arg min_u \epsilon_{PCA,Var(u)} = \arg min \text{ constant} - \epsilon_{PCA,Var(u)}$

Hence minimizing reconstruction error is equivalent to maximizing projected variance.

# 3.3 Canonical Correlation Analysis

The Pearson Correlation $\rho(X,Y)$ is a way to measure how linearly related (in other words, how a linear model captures the relationship between random variables $X$ and $Y$.

```
$$\rho(X,Y) = \frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}$
```

Here are some important facts about:

+   - It is always commutative: $\rho(X,Y) = \rho(Y,X)$

+   - It is always between -1 and 1: $-1 \leq \rho(X,Y) \leq 1$

+   - It is completely invariant to affine transformations: for any $a,b,c,d \in \mathbb{R}$,\n$\rho(aX+b, cY+d) = \frac{Cov(aX+b, cY+d)}{\sqrt{Var(aX+b)Var(cY+d)}}$\n$= \frac{Cov(aX,cY)}{\sqrt{Var(aX)Var(cY)}}$\n$= \frac{a \cdot c \cdot Cov(X,Y)}{\sqrt{a^2 Var(X) \cdot c^2 Var(Y)}}$\n$= \frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}$\n$= \rho(X,Y)$

The correlation is defined in terms of random variables rather than observed data. Assume that $\mathbf{x,y} \in \mathbb{R}^n$ are vectors containing $n$ independent observations of $X$ and $Y$. Recall the law of large numbers, which states that for i.i.d. $X$ with mean $\mu$,

```
$$\sum_{i=1}^n X_i \xrightarrow{a.s.} n\mu \text{ as } n \to \infty$
```

We can use this to justify a sample-based approximation to the mean:

```
$Cov(X,Y) = \mathbb{E}[(X-\mathbb{E}[X])(Y-\mathbb{E}[Y])] \approx \frac{1}{n} \sum_{i=1}^n (x_i-\bar{x})(y_i-\bar{y})$
```