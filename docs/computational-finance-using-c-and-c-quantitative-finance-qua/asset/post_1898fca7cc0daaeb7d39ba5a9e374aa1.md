
## Appendix C: Standard statistical results

## C.1 The law of large numbers

Let $x_1, x_2, \dots$ be a sequence of independent, identically distributed random variables (IID), each with expected value $\mu$ and variance $\sigma^2$. Define the sequence of averages

$y_n = \sum_{i=1}^n x_i = \frac{x_1 + x_2 + \dots + x_n}{n}, \quad n = 1, 2, \dots$

Then the law of large numbers states that $y_n$ converges to $\mu$ as $n \to \infty$, that is $Var[y_n] \to 0$.

The mean of $y_n$ is:

$E[y_n] = \frac{1}{n}(E[x_1] + E[x_2] + \dots + E[x_n]) = \frac{1}{n}\mu = \mu$

The variance of $y_n$ we have:

$Var[y_n] = Var\left[\frac{\sum_{i=1}^n x_i}{n}\right] = \frac{1}{n^2}Var\left[\sum_{i=1}^n x_i\right] = \frac{1}{n^2}n\sigma^2 = \frac{\sigma^2}{n}$

where we have used the fact that the variance of the sum of independent random variables is the sum of their variances; see Section C.2.

We have therefore shown that $n \to \infty, Var[y_n] \to 0$.

## C.2 The central limit theorem

Let $x_1, x_2, \dots$ be a sequence of independent, identically distributed random variables (IID), each with expected value $\mu$ and variance $\sigma^2$. If we define $u_i = x_i - \mu$ then:

$E[u_i] = E[u] = 0,\quad Var[u_i] = E[u^2] = \sigma^2$

Let

$s_n = \sum_{i=1}^{n} u_i + n\mu$

So

$s_n = \sum_{i=1}^{n} x_i$

We now introduce the normalized value $z_n$, as follows:

$z_n = \frac{s_n - n\mu}{\sqrt{n}} = \frac{1}{\sqrt{n}} \sum_{i=1}^{n} u_i$

The central limit theorem states as $n$ tends to the probability distribution of $z_n$ tends to a normal distribution with zero mean and unit variance; mathematically $z_n \to N(0, 1)$ as $n \to \infty$.

PROOF. From Section C.5, Eq. (C.5.3)

$M_{z_n} = E[\exp(tz_n)] = E\left[ \exp\left[ \frac{t}{\sqrt{n}} \sum_{i=1}^{n} u_i \right] \right]$

and using Eq. (C.5.5)

$M_{z_n} = \left\{ M_u\left( \frac{t}{\sqrt{n}} \right) \right\n$

Equation (C.5.1) yields:

$M_u\left( \frac{t}{\sqrt{n}} \right) \approx 1 + \frac{t}{\sqrt{n}} E[u] + \frac{1}{2} \left( \frac{t}{\sqrt{n}} \right)^2 E[u^2] + \dots$

As $n \to \infty, \frac{t}{\sqrt{n}} \to 0$ and

$M_u\left( \frac{t}{\sqrt{n}} \right) \to 1 + \frac{t}{\sqrt{n}} E[u] + \frac{1}{2} \left( \frac{t}{\sqrt{n}} \right)^2 E[u^2] = 1 + \frac{t^2}{2n}$

Thus

$\left\{ M_{z_n}\left( \frac{t}{\sqrt{n}} \right) \right\}^n = \left( 1 + \frac{t^2}{2n} \right)^n \to 1 + \frac{t^2}{2} \text{ as } n \to \infty$

where we used the fact that $t \ll 1$; see Grimmett and Welsh (1986). We have then shown that as $n \to \infty$

$M_{z_n}(t) \to 1 + \frac{t^2}{2} \to e^{t^2/2}$

However, from Section D.1 the moment generating function $M_z(t)$ for a standard normal distribution $(\mu=0, \sigma^2 = 1)$ is:

$M_z(t) = e^{t^2/2} \text{ where } z \sim N(0, 1)$

Thus we proved that $z_n \to N(0, 1)$ as $n \to \infty$.

## C.3 The variance and covariance of random variables

### C.3.1 Variance

One variable

Let $X$ be a variate from a given distribution, and $Z$ be the following linear function of this variate:

$Z = a + bX$

where $a$ and $b$ are constants. Then

$E[Z] = E[a] + E[bX] = a + bE[X]$

and

$Var[Z] = E[(Z - E[Z])^2]$
$= E[(a + bX - a - bE[X])^2]$
$= E[(bX - bE[X])^2]$
$= E[b^2(X - E[X])^2]$
$= b^2E[(X - E[X])^2]$

Therefore the mean is $a + bE[X]$, and the variance is $Var[X]$.

Two variables

Let $Z = a + b_1X_1 + b_2X_2$, where $a, b_1$ and $b_2$ are constants. Then the mean is $E[Z] = E[a] + E[b_1X_1] + E[b_2X_2] = a + b_1E[X_1] + b_2E[X_2]$. The variance $Var[Z]$ is computed as follows:

$Var[Z] = E[(a + b_1X_1 + b_2X_2 - a - b_1E[X_1] - b_2E[X_2])^2]$
$= E[(b_1(X_1 - E[X_1]) + b_2(X_2 - E[X_2]))^2]$
$= b_1^2E[(X_1 - E[X_1])^2] + b_2^2E[(X_2 - E[X_2])^2] + 2b_1b_2E[(X_1 - E[X_1])(X_2 - E[X_2])]$
$= b_1^2Var[X_1] + b_2^2Var[X_2] + 2b_1b_2Cov[X_1, X_2],$

$Cov[X_1, X_2]$ is the covariance between $X_1$ and $X_2$. If $X_1$ and $X_2$ are independent distributed random variables (IID), $Cov[X_1, X_2] = 0$, and we have:

$Var[Z] = b_1^2Var[X_1] + b_2^2Var[X_2]$

Three variables

Let $Z = a + b_1X_1 + b_2X_2 + b_3X_3$, where $a, b_1, b_2$ and $b_3$ are constants. Then the mean is $E[Z] = E[a] + E[b_1X_1] + E[b_2X_2] + E[b_3X_3] = a + b_1E[X_1] + b_2E[X_2] + b_3E[X_3]$. The variance $Var[Z]$ is computed as follows:

$Var[Z] = E[(a + b_1X_1 + b_2X_2 + b_3X_3 - a - b_1E[X_1] - b_2E[X_2] - b_3E[X_3])^2]$
$= E[(b_1(X_1 - E[X_1]) + b_2(X_2 - E[X_2]) + b_3(X_3 - E[X_3]))^2]$
$= b_1^2E[(X_1 - E[X_1])^2] + b_2^2E[(X_2 - E[X_2])^2] + b_3^2E[(X_3 - E[X_3])^2] + 2b_1b_2E[(X_1 - E[X_1])(X_2 - E[X_2]) + 2b_1b_3E[(X_1 - E[X_1])(X_3 - E[X_3]) + 2b_2b_3E[(X_2 - E[X_2])(X_3 - E[X_3])]$
$= b_1^2Var[X_1] + b_2^2Var[X_2] + b_3^2Var[X_3] + 2b_1b_2Cov[X_1, X_2] + 2b_1b_3Cov[X_1, X_3] + 2b_2b_3Cov[X_2, X_3]$

If $X_1, X_2$ and $X_3$ are IID the covariance terms are zero and the variance is:

$Var[Z] = b_1^2Var[X_1] + b_2^2Var[X_2] + b_3^2Var[X_3]$

Variance of n variables

We will now derive an expression for the sum of $n$ IID random variables.
Let $Z = a + \sum_{i=1}^n b_iX_i$, where $a$ and $b_i, i = 1, \dots, n$, are constants.

Then we have: $E[Z] = E[a] + E[\sum_{i=1}^n b_iX_i] = a + \sum_{i=1}^n b_iE[X_i]$ and

$Var[Z] = E[(a + \sum_{i=1}^n b_iX_i - a - \sum_{i=1}^n b_iE[X_i])^2]$
$= E[\sum_{i=1}^n b_iX_i - \sum_{i=1}^n b_iE[X_i]]^2]$
$= E[\sum_{i=1}^n b_i^2E[(X_i - E[X_i])^2] + \sum_{i=1}^n \sum_{j=1, j \neq i}^n b_ib_jE[(X_i - E[X_i])(X_j - E[X_j])]$

$\sum_{i=1}^n b_i^2 Var[X_i] + \sum_{i=1}^n \sum_{j=1(j\neq i)}^n b_i b_j Cov[X_i, X_j]$

As before all the $X$ variables are IID then the covariance terms are zero, and we have:

$Var[Z] = \sum_{i=1}^n b_i^2 Var[X_i]$

If in addition the $b_i$ terms are one and all the $X$ variable have variance $\sigma^2$ we obtain:

$Var[Z] = \sum_{i=1}^n Var[X_i] = n\sigma^2$

### C.3.2 Covariance

The covariance between two variables $X$ and $Y$ is defined by:

$Cov[X, Y] = E[(X - E[X])(Y - E[Y])]$

By symmetry it can be seen that $Cov[X, Y] = Cov[Y, X]$. Also $Cov(aX, bY) = ab \, Cov(X, Y)$.

Two variables

Let $Z = a + b_1X_1 + b_2X_2$, where $a, b_1$ and $b_2$ are constants.

$Cov[Z, Y] = Cov(a + b_1X_1 + b_2X_2, Y) = b_1Cov(X_1, Y) + b_2Cov(X_2, Y)$

Three variables

Let $Z_1 = a + b_1X_1 + b_2X_2$ and $Z_2 = a + b_1X_1 + b_2X_2 + b_3X_3$, where $a, b_1, b_2$ and $b_3$ are constants.

$Cov[Z_1, Y] = b_1Cov(X_1, Y) + b_2Cov(X_2, Y)$

Four variables

Let $Z_1 = a + b_1X_1 + b_2X_2 + b_3X_3$ and $Z_2 = a + b_1X_1 + b_2X_2 + b_3X_3 + b_4X_4$, where $a, b_1, b_2, b_3$ and $b_4$ are constants.

$Cov[Z_1, Y] = b_1Cov(X_1, Y) + b_2Cov(X_2, Y) + b_3Cov(X_3, Y)$
