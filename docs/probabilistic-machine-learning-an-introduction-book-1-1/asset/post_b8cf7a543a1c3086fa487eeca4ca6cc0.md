
and another point that is infinitesimally close, namely $x + dx$. We see this interval gets mapped to $(y, y + dy)$. The probability mass in these intervals must be the same, hence $p(x)dx = p(y)dy$, and so $p(y) = p(x)dx/dy$. However, since it does not matter (in terms of probability preservation) whether $dx/dy > 0$ or $dx/dy < 0$, we get

$$p_{y}(y) = p_{x}(x) \left| \frac{dx}{dy} \right|$$

$$ (\mathrm{D}.55) $$

Now consider the general case for any $p_{x}(x)$ and any monotonic function $f: \mathbb{R} \to \mathbb{R}$. Let $g = f^{-1}$, so $y = f(x)$ and $x = g(y)$. If we assume that $f: \mathbb{R} \to \mathbb{R}$ is monotonically increasing we get

$$P_{y}(y) = \operatorname{Pr}(f(X) \leq y) = \operatorname{Pr}(X \leq f^{-1}(y)) = P_{x}(f^{-1}(y)) = P_{x}(g(y))$$

$$ (\mathrm{D}.56) $$

Taking derivatives we get

$$p_{y}(y) \triangleq \frac{d}{dy}P_{y}(y) = \frac{d}{dy}P_{x}(x) = \frac{dx}{dy} \frac{d}{dx}P_{x}(x) = \frac{dx}{dy} p_{x}(x)$$

$$ (\mathrm{D}.57) $$

We can derive a similar expression (but with opposite signs) for the case where $f$ is monotonically decreasing. To handle the general case we take the absolute value to get

$$p_{y}(y) = p_{x}\left(g(y)\right) \left| \frac{d}{dy} g(y) \right|$$

$$ (\mathrm{D}.58) $$

This is called **change of variables** formula.

### D.5.3.2 Change of variables: multivariate case

We can extend the previous results to multivariate distributions as follows. Let $\mathbf{f}$ be an invertible function that maps $\mathbb{R}^{n}$ to $\mathbb{R}^{n}$, with inverse $\mathbf{g}$. Suppose we want to compute the pdf of $\mathbf{y} = \mathbf{f}(\mathbf{x})$. By analogy with the scalar case, we have

$$p_{y}(\mathbf{y}) = p_{x}\left(\mathbf{g}(\mathbf{y})\right) \left| \det\left[\mathbf{J}_{\mathbf{g}}(\mathbf{y})\right] \right|$$

$$ (\mathrm{D}.59) $$

where $\mathbf{J}_{\mathbf{g}} = d\mathbf{g}(\mathbf{y})/d\mathbf{y}$ is the Jacobian of $\mathbf{g}$, and $|\det \mathbf{J}(\mathbf{y})|$ is the absolute value of the determinant of $\mathbf{J}$ evaluated at $\mathbf{y}$. (See Sec. B.3.5 for a discussion of Jacobians.) In Exercise 3.3 you will use this formula to derive the normalization constant for a multivariate Gaussian.

Fig. D.10 illustrates this result in 2d, for the case where $\mathbf{f}(\mathbf{x}) = A\mathbf{x} + \mathbf{b}$, where $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$. We see that the area of the unit square changes by a factor of $\det(A) = ad - bc$, which is the area of the parallelogram.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_849_0.png)

Figure D.10: Illustration of an affine transformation applied to a unit square, f(x) = Ax + b. (a) Here A = I. (b) Here b = 0. From [Jan18]. Used with kind permission of Eric Jang

As another example, consider transforming a density from Cartesian coordinates $\mathbf{x} = (x_1, x_2)$ to polar coordinates $\mathbf{y} = \mathbf{f}(x_1, x_2)$, so $\mathbf{g}(r, \theta) = (r \cos \theta, r \sin \theta)$. Then

$$ \mathbf{J}_{\mathbf{g}} = \begin{pmatrix} \frac{\partial x_1}{\partial r} & \frac{\partial x_1}{\partial \theta} \\ \frac{\partial x_2}{\partial r} & \frac{\partial x_2}{\partial \theta} \end{pmatrix} = \begin{pmatrix} \cos \theta & -r \sin \theta \\ \sin \theta & r \cos \theta \end{pmatrix} \qquad (\mathrm{D}.60) $$

$$ |\det(\mathbf{J}_{\mathbf{g}})| = |r \cos^2 \theta + r \sin^2 \theta| = |r| \qquad (\mathrm{D}.61) $$

Hence

$$ p_{r,\theta}(r,\theta) = p_{x_1,x_2}(r \cos \theta, r \sin \theta) r \qquad (\mathrm{D}.62) $$

To see this geometrically, notice that the area of the shaded patch in Fig. D.11 is given by

$$ \Pr(r \le R \le r + dr, \theta \le \Theta \le \theta + d\theta) = p_{r,\theta}(r,\theta) dr d\theta \qquad (\mathrm{D}.63) $$

In the limit, this is equal to the density at the center of the patch, $p(r,\theta)$, times the size of the patch, $r dr d\theta$. Hence

$$ p_{r,\theta}(r,\theta) dr d\theta = p_{x_1,x_2}(r \cos \theta, r \sin \theta) r dr d\theta \qquad (\mathrm{D}.64) $$

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_850_0.png)

Figure D.11: Change of variables from polar to Cartesian. The area of the shaded patch is r dr dθ. Adapted from Figure 3.16 of [Ric95]

## D.5.4 Moments of a linear transformation

Suppose $\mathbf{f}$ is an affine function, so $\mathbf{y} = A\mathbf{x} + \mathbf{b}$. In this case, we can easily derive the mean and covariance of $\mathbf{y}$ as follows. First, for the mean, we have

$$ \mathbb{E}[\mathbf{y}] = \mathbb{E}[A\mathbf{x} + \mathbf{b}] = A\boldsymbol{\mu} + \mathbf{b} \qquad (\mathrm{D}.65) $$

where $\boldsymbol{\mu} = \mathbb{E}[\mathbf{x}]$. If $f$ is a scalar-valued function, $f(\mathbf{x}) = \mathbf{a}^{\top} \mathbf{x} + b$, the corresponding result is

$$ \mathbb{E}[\mathbf{a}^{\top} \mathbf{x} + b] = \mathbf{a}^{\top} \boldsymbol{\mu} + b \qquad (\mathrm{D}.66) $$

For the covariance, we have

$$ \text{Cov}[\mathbf{y}] = \text{Cov}[A \mathbf{x} + \mathbf{b}] = A \Sigma A^{\top} \qquad (\mathrm{D}.67) $$

where $\Sigma = \text{Cov}[\mathbf{x}]$. We leave the proof of this as an exercise.

As a special case, if $y = \mathbf{a}^{\top} \mathbf{x} + b$, we get

$$ \mathbb{V}[y] = \mathbb{V}[\mathbf{a}^{\top} \mathbf{x} + b] = \mathbf{a}^{\top} \Sigma \mathbf{a} \qquad (\mathrm{D}.68) $$

For example, to compute the variance of the sum of two scalar random variables, we can set $\mathbf{a} = [1, 1]^{\top}$ to get

$$ \mathbb{V}[x_1 + x_2] = \begin{bmatrix} 1 & 1 \end{bmatrix} \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix} \begin{bmatrix} 1 \\ 1 \end{bmatrix} \qquad (\mathrm{D}.69) $$

$$ = \Sigma_{11} + \Sigma_{22} + 2 \Sigma_{12} = \mathbb{V}[x_1] + \mathbb{V}[x_2] + 2 \text{Cov}[x_1, x_2] \qquad (\mathrm{D}.70) $$

Note, however, that although some distributions (such as the Gaussian) are completely characterized by their mean and covariance, in general we must use the techniques described above to derive the full distribution of $\mathbf{y}$.

## D.5.5 The convolution theorem

Let $y = x_1 + x_2$, where $x_1$ and $x_2$ are independent rv's. If these are discrete random variables, we can compute the pmf for the sum as follows:

$$ p(y = j) = \sum_{k} p(x_1 = k) p(x_2 = j - k) \qquad (\mathrm{D}.71) $$

for $j = \dots, -2, -1, 0, 1, 2, \dots$

| - | - | 1 | 2 | 3 | 4 | - | - | |
|---|---|---|---|---|---|---|---|---|
| 7 | 6 | 5 | - | - | - | - | - | $z_0 = x_0 y_0 = 5$ |
| - | 7 | 6 | 5 | - | - | - | - | $z_1 = x_0 y_1 + x_1 y_0 = 16$ |
| - | - | 7 | 6 | 5 | - | - | - | $z_2 = x_0 y_2 + x_1 y_1 + x_2 y_0 = 34$ |
| - | - | - | 7 | 6 | 5 | - | - | $z_3 = x_1 y_2 + x_2 y_1 + x_3 y_0 = 52$ |
| - | - | - | - | 7 | 6 | 5 | - | $z_4 = x_2 y_2 + x_3 y_1 = 45$ |
| - | - | - | - | - | 7 | 6 | 5 | $z_5 = x_3 y_2 = 28$ |

*Figure D.12: Discrete convolution of x = [1,2,3,4] with y = [5,6,7] to yield z = [5,16,34,52,45,28]. In general, $z_n = \sum_{k=-\infty}^{\infty} x_k y_{n-k}$. We see that this operation consists of “flipping” y and then “dragging” it over x, multiplying elementwise, and adding up the results.*

If $x_1$ and $x_2$ have pdf's $p_1(x_1)$ and $p_2(x_2)$, what is the distribution of $y$? The cdf for $y$ is given by

$$ P_y(y^*) = \Pr(y \le y^*) = \int_{-\infty}^{\infty} p_1(x_1) dx_1 \int_{-\infty}^{y^* - x_1} p_2(x_2) dx_2 \qquad (\mathrm{D}.72) $$

where we integrate over the region $R$ defined by $x_1 + x_2 < y^*$. Thus the pdf for $y$ is

$$ p(y) = \left[ \frac{d}{dy^*} P_y(y^*) \right]_{y^*=y} = \int p_1(x_1) p_2(y - x_1) dx_1 \qquad (\mathrm{D}.73) $$

where we used the rule of **differentiating under the integral sign**:

$$ \frac{d}{dx} \int_{a(x)}^{b(x)} f(t) dt = f(b(x)) \frac{db(x)}{dx} - f(a(x)) \frac{da(x)}{dx} \qquad (\mathrm{D}.74) $$

We can write Eq. (D.73) as follows:

$$ p = p_1 \circledast p_2 \qquad (\mathrm{D}.75) $$

where $\circledast$ represents the **convolution** operator. For finite length vectors, the integrals become sums, and convolution can be thought of as a “flip and drag” operation, as illustrated in Fig. D.12. Consequently, Eq. (D.73) is called the **convolution theorem.**

For example, suppose we roll two dice, so $p_1$ and $p_2$ are both the discrete uniform distributions over $\{1,2,\dots,6\}$. Let $y = x_1 + x_2$ be the sum of the dice. We have

$$ p(y = 2) = p(x_1 = 1) p(x_2 = 1) = \frac{1}{6} \frac{1}{6} = \frac{1}{36} \qquad (\mathrm{D}.76) $$

$$ p(y = 3) = p(x_1 = 1) p(x_2 = 2) + p(x_1 = 2) p(x_2 = 1) = \frac{1}{6} \frac{1}{6} + \frac{1}{6} \frac{1}{6} = \frac{2}{36} \qquad (\mathrm{D}.77) $$

$$ \dots \qquad (\mathrm{D}.78) $$

Continuing in this way, we find $p(y = 5) = 4/36$, $p(y = 6) = 5/36$, $p(y = 7) = 6/36$, $p(y = 8) = 5/36$, $p(y = 9) = 4/36$, $p(y = 10) = 3/36$, $p(y = 11) = 2/36$ and $p(y = 12) = 1/36$. The result, of course, is

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_852_0.png)

Figure D.13: Distribution of the sum of two dice rolls, i.e., p(y) where y = x1+x2 and xi ~ Unif({1,2,...,6}). From https://en.wikipedia.org/wiki/Probability_distribution. Used with kind permission of Wikipedia author Tim Stellmach.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_852_1.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_852_2.png)

Figure D.14: The central limit theorem in pictures. We plot a histogram of $\hat{\mu}_N^s = \frac{1}{N} \sum_{n=1}^N x_{ns}$, where $x_{ns} \sim \text{Beta}(1,5)$, for $s = 1 : 10000$. As $N \to \infty$, the distribution tends towards a Gaussian. (a) N = 1. (b) N = 5. Adapted from Figure 2.6 of [Bis06]. Generated by centralLimitDemo.m.

equal to the binomial distribution, $\text{Bin}(y|2,(1/6,\dots,1/6))$. See Fig. D.13 for a plot. We see that the distribution looks like a Gaussian; we explain the reasons for this in Sec. D.5.6.

We can also compute the pdf of the sum of two continuous rv's. For example, in the case of Gaussians, where $x_1 \sim \mathcal{N}(\mu_1,\sigma_1^2)$ and $x_2 \sim \mathcal{N}(\mu_2,\sigma_2^2)$, one can show (Exercise D.9) that if $y = x_1 + x_2$ then

$$ p(y) = \mathcal{N}(x_1|\mu_1,\sigma_1^2) \otimes \mathcal{N}(x_2|\mu_2,\sigma_2^2) = \mathcal{N}(y|\mu_1 + \mu_2,\sigma_1^2 + \sigma_2^2) \qquad (\mathrm{D}.79) $$

Hence the convolution of two Gaussians is a Gaussian.

## D.5.6 Central limit theorem

Now consider $N$ random variables with pdf's (not necessarily Gaussian) $p_n(x)$, each with mean $\mu$ and variance $\sigma^2$. We assume each variable is iid. Let $S_N = \sum_{n=1}^N X_n$ be the sum of the rv's. One
