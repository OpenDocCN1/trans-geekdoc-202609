
## Introduction to stochastic processes

```
$d\phi = \left( \frac{\partial\phi}{\partial t} + \sum_{i=1}^n a_i\frac{\partial\phi}{\partial X_i} + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n b_{ij}b_j\rho_{ij}\frac{\partial^2\phi}{\partial X_i\partial X_j} \right)dt\+ \sum_{i=1}^n \frac{\partial\phi}{\partial X_i}b_idW_i \quad (2.5.7)
```

if we consider the geometric Brownian motion:
$dS_i = \mu_i S_i dt + \sigma_i S_i dW_i, \quad i = 1,\dots,n$,

where $\mu_i$ is the constant drift of the $i$-th asset and $\sigma_i$ is the constant volatility of the substitution $X_i = S_i, a_i = \mu_i S_i,$ and $b_i = \sigma_i S_i$ into Eq. (2.5.7)
yield:

```
$d\phi = \left( \frac{\partial\phi}{\partial t} + \sum_{i=1}^n \mu_i S_i\frac{\partial\phi}{\partial X_i} + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \sigma_i\sigma_j S_i S_j\rho_{ij}\frac{\partial^2\phi}{\partial X_i\partial X_j} \right)dt\+ \sum_{i=1}^n \frac{\partial\phi}{\partial X_i}\sigma_i S_i dW_i \quad (2.5.8)
```

## 2.6 Ito product and quotient rules in two dimensions

We will now derive expressions for the product and quotient of two stochastic processes. in which $\phi = \phi(X_1, X_2)$, with

```
$dX_1 = a_1 dt + b_1 dW_1 \quad \quad dX_2 = a_2 dt + b_2 dW_2$
```

The following two-dimensional version of Ito's lemma can be used:

```
$d\phi = \frac{\partial\phi}{\partial X_1}dX_1 + \frac{\partial\phi}{\partial X_2}dX_2 + \frac{1}{2}E\sum_{i=1}^2\sum_{j=1}^2 \frac{\partial^2\phi}{\partial X_i\partial X_j}dX_i dX_j \quad (2.6.1)
```

where we have used the fact $\frac{\partial\phi}{\partial t} = 0$.

### 2.6.1 Ito product rule

Here $\phi = \phi(X_1, X_2),$ and the partial derivatives are as follows:

```
$\frac{\partial\phi}{\partial X_1}=X_2, \quad\ \frac{\partial\phi}{\partial X_2}=X_1, \quad\ \frac{\partial^2\phi}{\partial X_1^2}=0, \quad\ \frac{\partial^2\phi}{\partial X_2^2}=0.\n\frac{\partial^2\phi}{\partial X_1\partial X_2}=1$
```

Therefore using Eq. (2.6.1)

```
$d\phi = X_2 dX_1 + X_1 dX_2 + \frac{2E[dX_1dX_2]}{2}
```

and the product rule

$d(X_1X_2) = X_2 dX_1 + X_1 dX_2 + E[dX_1dX_2]$

Brownian motion with one source of randomness

For the special case where $X_1$ is Brownian motion and $X_2$ has no random term we have:

$dX_1 = X_1\mu_1 dt + X_1\sigma_1 dW_1 \quad dX_2 = X_2\mu_2 dt$

Now

$E[dX_1dX_2] = E[(X_1\mu_1 dt + X_1\sigma_1 dW_1)X_2\mu_2 dt] \\ \n = X_1X_2\mu_1\mu_2 dt^2 + X_1X_2\sigma_1\mu_2 dt dW_1 = 0$

where we have ignored terms in $dt$ with order higher than 1, and used $E[dW_1] = 0$.

Therefore Eq. (2.6.2) becomes:

$d(X_1X_2) = X_2 dX_1 + X_1 dX_2$

$d(X_1X_2) = X_2(X_1\mu_1 dt + X_1\sigma_1 dW_1) + X_1\mu_2 dt$

So we obtain:

$d(X_1X_2) = (X_1X_2)(\mu_1 + \mu_2) dt + X_1X_2\sigma_1 dW_1$

### 2.6.2 Ito quotient rule

Here $\phi = \phi(X_1/X_2)$ and the partial derivatives are:

$\frac{\partial\phi}{\partial X_1} = \frac{1}{X_2}, \quad \frac{\partial\phi}{\partial X_2} = -\frac{X_1}{X_2^2}, \quad \frac{\partial^2\phi}{\partial X_1^2} = 0, \quad \frac{\partial^2\phi}{\partial X_2^2} = \frac{2X_1}{X_2^3}, \quad \frac{\partial^2\phi}{\partial X_1\partial X_2} = -\frac{1}{X_2^2}$

Therefore using Eq. (2.6.1)

$d\phi = \frac{\partial\phi}{\partial X_1}dX_1 + \frac{\partial\phi}{\partial X_2}dX_2 + \frac{1}{2}\frac{\partial^2\phi}{\partial X_1^2}dX_1^2 + \frac{1}{2}\frac{\partial^2\phi}{\partial X_2^2}dX_2^2 + \frac{\partial^2\phi}{\partial X_1\partial X_2}dX_1dX_2$

$d\phi = \frac{1}{X_2}dX_1 - \frac{X_1}{X_2^2}dX_2 + \frac{1}{2}\frac{2X_1}{X_2^3}dX_2^2 - \frac{1}{X_2^2}dX_1dX_2$

We obtain the following expression for quotient rule:

$d(\frac{X_1}{X_2}) = \frac{X_1}{X_2}\left[\frac{dX_1}{X_1} - \frac{dX_2}{X_2} + \frac{dX_2^2}{X_2^2} - \frac{dX_1dX_2}{X_1X_2}\right]$

### Brownian motion

Here we have

$dX_1 = X_1\mu_1 dt + X_1\sigma_1 dW_1 \quad \text{and} \quad dX_2 = X_2\mu_2 dt + X_2\sigma_2 dW_2$

or equivalently

$\frac{dX_1}{X_1} = \mu_1 dt + \sigma_1 dW_1 \quad \text{and} \quad \frac{dX_2}{X_2} = \mu_2 dt + \sigma_2 dW_2$

Therefore

$E\left[\frac{dX_2}{X_2}\right)\left(\frac{dX_2}{X_2}\right] = E[(\mu_2 dt + \sigma_2 dW_2)(\mu_2 dt + \sigma_2 dW_2)]$
$= E[\mu_2^2 dt^2] + E[\sigma_2^2(dW_2)^2] + 2E[\sigma_2 dt dW_2]$
$= \mu_2^2 dt^2 + \sigma_2^2 dt + 2\sigma_2 dt dW_2$

which results in

$E\left[\frac{dX_2}{X_2}\right)\left(\frac{dX_2}{X_2}\right] = \sigma_2^2 dt \quad (2.6.5)$

where we have ignored all terms in $dt$ with order higher than 1, and used the fact that $E[dW_2] = 0$.

In a similar manner

$E\left[\frac{dX_1}{X_1}\right]\left(\frac{dX_2}{X_2}\right) = E[(\mu_1 dt + \sigma_1 dW_1)(\mu_2 dt + \sigma_2 dW_2)]$
$= E[\mu_1\mu_2 dt^2] + E[\sigma_1\mu_2 dt] + E[\sigma_2\mu_1 dt dW_2] + E[\sigma_1\sigma_2 dt dW_1]$
$= \mu_1\mu_2 dt^2 + \sigma_1\mu_2 dt E[dW_1] + \sigma_2\mu_1 dt E[dW_2] + \sigma_1\sigma_2 E[dW_1 dW_2]$

which gives

$E\left[\frac{dX_1}{X_1}\right)\left(\frac{dX_2}{X_2}\right) = \sigma_1\sigma_2 dt \quad (2.6.6)$

where we have proceeded as before also using the fact $E[dW_1 dW_2] = \rho_{12} dt$.

Substituting these into Eq. (2.6.4) we have

$d[\frac{X_1}{X_2}] = \frac{X_1}{X_2}\left[\frac{dX_1}{X_1} - \frac{dX_2}{X_2} + \sigma_2^2 dt - \sigma_1\sigma_2\rho_{12} dt\right]$

This yields:

$d(\frac{X_1}{X_2}) = \frac{X_1}{X_2}\left[\mu_1 - \mu_2 + \sigma_2^2 - \sigma_1\sigma_2\rho_{12}\right]dt + \left(\frac{X_1}{X_2}\right)[\sigma_1 dW_1 - \sigma_2 dW_2] \quad (2.6.7)$

Brownian motion with one source of randomness

We have

$dX_1 = X_1\mu_1 dt + X_1\sigma_1 dW_1 \quad dX_2 = X_2\mu_2 dt$

As before

$E\left[\frac{dX_2}{X_2}\right]\left(\frac{dX_2}{X_2}\right) = E[\mu_2^2 dt] \rightarrow 0$

$E\left[\frac{dX_1}{X_1}\right]\left(\frac{dX_2}{X_2}\right) = E[(\mu_1 dt + \sigma_1 dW_1)\mu_2 dt] = E[\mu_1\mu_2 dt^2 + \sigma_1\mu_2 dt dW_1] = \mu_1\mu_2 dt^2 + \sigma_1\mu_2 dt E[dW_1] \rightarrow 0$

Therefore

$d(\frac{X_1}{X_2}) = \frac{X_1}{X_2}\left[\frac{dX_1}{X_1} - \frac{dX_2}{X_2}\right] = \left(\frac{X_1}{X_2}\right)(\mu_1 dt + \sigma_1 dW_1 - \mu_2 dt)$

So the final expression is

$d(\frac{X_1}{X_2}) = \left(\frac{X_1}{X_2}\right)[\mu_1 - \mu_2]dt + \left(\frac{X_1}{X_2}\right)[\sigma_1 dW_1] \quad (2.6.8)$

## 2.7 Ito product in n dimensions

Using Eq. (2.5.7) we will now derive an expression for the product of $n$ stochastic processes. In this case $\phi \rightarrow \prod_{i=1}^n X_i$, and the partial derivatives are as follows:

$\frac{\partial\phi}{\partial X_i} = \phi\frac{dX_i}{X_i} \text{ for } i=1, \dots, n$

$\frac{\partial^2\phi}{\partial X_i^2} = 0 \text{ for } i=1, \dots, n$

$\frac{\partial^2\phi}{\partial X_i\partial X_j} = \frac{\partial^2\phi}{\partial X_j\partial X_i} = \left(\left(\frac{dX_i}{X_i}\right)\left(\frac{dX_j}{X_j}\right)\phi \text{ for } i \neq j, i = 1,\dots,n, j = 1,\dots,n$

$\frac{\partial\phi}{\partial t} = 0$

So substituting it into Eq. (2.5.7) we have

$d\phi = \sum_{i=1}^n \left(\frac{dX_i}{X_i}\right)^2 + \phi E\left[\sum_{i=1}^n \sum_{j=1(i\neq j)}^n \left(\frac{dX_i}{X_i}\right)\left(\frac{dX_j}{X_j}\right)\right]$ $(2.7.1)$

which in fills

$d\left(\prod_{i=1}^n X_i\right) = \left(\prod_{i=1}^n X_i\right) \sum_{i=1}^n \left(\frac{dX_i}{X_i}\right)^2 + \left(\prod_{i=1}^n X_i\right) E\left[\sum_{i=1}^n \sum_{j=1(i\neq j)}^n \left(\frac{dX_i}{X_i}\right)\left(\frac{dX_j}{X_j}\right)\right]$ $(2.7.2)$

## 2.8 The Brownian bridge

Let a Brownian process have $W_{t0}$ at time $t_0$ and $W_{t1}$ at time $t_1$. We want to find the conditional distribution of $W_t$, where $t_0 < t < t_1$. This distribution will be denoted by $P(W_t|W_{t0}, W_{t1})$, to indicate that $W_t$ is conditional on the end values $W_{t0}$ and $W_{t1}$. We write $W_{t0}$ and $W_{t1}$ as

$W_t = W_{t0} + \sqrt{t-t_0}X_t, \quad X_t \sim N(0, 1),$ $(2.8.1)$

$W_t = W_{t1} - \sqrt{t_1-t}Y_t, \quad Y_t \sim N(0, 1)$ $(2.8.2)$

where $X_t$ and $Y_t$ are independent normal variates. Combining Eqs. (2.8.1) and (2.8.2) we have

$W_t = W_{t0} + \sqrt{t-t_0}X_t + \sqrt{t_1-t}Y_t$

which can be re-expressed as

$W_t - W_{t0} = \sqrt{t-t_0}X_t + \sqrt{t_1-t}Y_t$

Using the Brownian motion property (iii) in Section 2.1

$\sqrt{t-t_0}Z_t = \sqrt{t-t_0}X_t + \sqrt{t_1-t}Y_t$

So

$\sqrt{t-t_0}Z_t = \sqrt{t-t_0}X_t + \sqrt{t_1-t}Y_t$
