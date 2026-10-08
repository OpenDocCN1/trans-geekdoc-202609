# C.4 Conditional mean and covariance of normal distributions

$X = [X_1, X_2]^T$ be distributed as $N_p(\mu, \Sigma)$ with $\mu = [\mu_1, \mu_2]^T$ and $\Sigma = egin{bmatrix} \Sigma_{11} & \Sigma_{12} \ \Sigma_{21} & \Sigma_{22} \end{bmatrix}$ and $|\Sigma_{21}| > 0$.

We will prove that the conditional distribution of $X_1$, given that $X_2 = x_2$, is normal and has:

Mean = $\mu_e s_1 + \Sigma_{12}\Sigma_{22}^{-1}(x_2 - \mu_2)$, and covariance = $\Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21}$.
Let the inverse of $\Sigma$ be $\Sigma^{-1}$, where

```
$$\Sigma^{-1} = \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \ \Sigma_{21} & \Sigma_{22} \end{bmatrix}^{-1} \quad (C.4.1)$
```

So $\Sigma^{-1} = \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \ \Sigma_{21} & \Sigma_{22} \end{bmatrix}^{-1} = \begin{bmatrix} I_q & 0 \ 0 & I_{p-q} \end{bmatrix} \quad (C.4.2)$

Multiplying out these identities yields the following equations:

```
$$\Sigma_{11}\Sigma_{11} + \Sigma_{21}\Sigma_{21} = I_q \quad (C.4.3)$
```

```
$$\Sigma_{21}\Sigma_{11} + \Sigma_{22}\Sigma_{21} = 0 \quad (C.4.4)$
```

```
$$\Sigma_{11}\Sigma_{12} + \Sigma_{21}\Sigma_{22} = 0 \quad (C.4.5)$
```

```
$$\Sigma_{21}\Sigma_{12} + \Sigma_{22}\Sigma_{22} = 0 \quad (C.4.6)$
```

Multiplying Eq. (C.4.5) on the left by $(\Sigma_{11})^{-1}$ and on the right by $\Sigma_{22}^{-1}$ gives:

```
$(\Sigma_{11})^{-1}\Sigma_{12} = -\Sigma_{12}\Sigma_{22}^{-1} \quad (C.4.7)$
```

Multiplying Eq. (C.4.3) on the left by $(\Sigma_{11})^{-1}$ yields

```
$$\Sigma_{11} + (\Sigma_{11})^{-1}\Sigma_{12}\Sigma_{22}^{-1} = I_q \quad (C.4.8)$
```

and substituting for $(\Sigma_{11})^{-1} = \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21}$ from Eq. (C.4.7) into Eq. (C.4.8) gives

```
$(\Sigma_{11})^{-1} = \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21} \quad (C.4.9)$
```

The probability density function of $x$ is:

```
$f(x) = (2\pi)^{-p/2}|\Sigma^{-1}|^{1/2}\exp\left\{\frac{1}{2}(x-\mu)^T\Sigma^{-1}(x-\mu)\right\} $
```

writing $x, \mu$ and $\Sigma^{-1}$ in their partitioned form and gives:

```
$f(x) = (2\pi)^{-p/2}|\Sigma^{-1}|^{1/2}\n\exp\left[-\frac{1}{2}(x_1-\\mu_1)^T\Sigma^{11}(x_1-\\mu_1) + 2(x_1-\\mu_1)^T\Sigma^{12}(x_2-\\mu_2)\n + (x_2-\\mu_2)^T\Sigma^{22}(x_2-\\mu_2)\right] \quad (C.4.10)$
```