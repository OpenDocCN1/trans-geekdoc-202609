# Ito Product in n Dimensions Section | 2.7 17

This yields

```
$d\left(\frac{X_1}{X_2}ight) = \left(\frac{X_1}{X_2}ight)^2 \left[\mu_1 - \mu_2 + \sigma_2^2 - \sigma_1\sigma_2ho_{12}ight]dt + \left(\frac{X_1}{X_2}ight)\{\sigma_1 dW_1 - \sigma_2 dW_2\} \. (2.6.7)$
```

( Brownian motion with one source of randomness

We have

```
$dX_1 = X_1\mu_1 dt + \sigma_1 X_1 dW_1 \quad dX_2 = X_2\mu_2 dt.$
```

As before

```
$E\left[\left(\frac{dX_1}{X_2}ight)\left(\frac{dX_2}{X_2}ight)\right] = E\left[\mu_2^2 dt^2\right] \to 0
```

```
$E\left[\left(\frac{dX_1}{X_1}ight)\left(\frac{dX_2}{X_2}ight)\right] = E\left[(\mu_1 dt + \sigma_1 dW_1)\mu_2 dt\right]$
```

```
$= E\left[\mu_1\mu_2 dt^2 + \sigma_1\sigma_2 dtW_1 dW_2\right]$
```

```
$= \mu_1\mu_2 dt^2 + \sigma_1\sigma_2 dt^2 E[dW] \to 0.$
```

Therefore,

```
$d\left(\frac{X_1}{X_2}\right) = \left(\frac{X_1}{X_2}\right)\left(\frac{dX_1}{X_1} - \frac{dX_2}{X_2}\right)$
```

```
$= \left(\frac{X_1}{X_2}\right)\{\mu_1 dt + \sigma_1 dW_1 - \mu_2 dt\}.$
```

So, the final expression is

```
$d\left(\frac{X_1}{X_2}\right) = \left(\frac{X_1}{X_2}\right)^2 \left\{\mu_1 - \mu_2\right\}dt + \left(\frac{X_1}{X_2}\right)\{\sigma_1 dW_1\. (2.6.8)$
```

# 2.7 ITO PRODUCT IN n DIMENSIONS

Using (2.5.7) we will derive an expression for the product of $n$ stochastic processes. In this case, $\phi = \prod_{i=1}^n X_i$, and the partial derivatives are as follows:

```
$$\frac{\partial \phi}{\partial X_i} = \phi \frac{1}{X_i}, \quad \text{for } i=1,...,n,$
```

```
$$\frac{\partial^2 \phi}{\partial X_i^2} = 0, \quad \text{for } i=1,...,n,$
```

```
$$\frac{\partial^2 \phi}{\partial X_i \partial X_j} = \phi \left(\frac{1}{X_i}\right)\left(\frac{1}{X_j}\right), \quad \text{for } i \neq j, i=1,...,n,j=1,...,n,$
```

```
$$\frac{\partial \phi}{\partial t} = 0.$
```

So substituting into (2.5.7), we have

```
$d\phi = \phi \sum_{i=1}^n \left(\frac{dX_i}{X_i}\right)^2 + \phi E \left[\sum_{i=1}^n \sum_{j=1(i\neq j)}^n \left(\frac{dX_i}{X_i}\right)\left(\frac{dX_j}{X_j}\right)\right] \. (2.7.1)$
```