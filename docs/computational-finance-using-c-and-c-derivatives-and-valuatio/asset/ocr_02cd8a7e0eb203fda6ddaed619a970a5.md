# 14 CHAPTER | 2 Introduction to Stochastic Processes

and

Therefore, equation (2.5.3) can be rewritten as

```
$d\phi = \frac{\partial \phi}{\partial t}dt + \sum_{i=1}^n \frac{\partial \phi}{\partial X_i}dX_i + 2E\sum_{i=1}^n\sum_{j=1}^n \frac{\partial^2 \phi}{\partial X_i\partial X_j}dX_idX_j, \quad \(2.5.5)$
```

$$\phi = \phi^* - \phi$.$\nNow

```
$E[dX_idX_j] = E[b_ib_jdt dZ_iZ_j] = b_ib_jdt[dZ_iZ_j] = b_ib_j\rho_{ij}dt,$
```

$$\rho_{ij}$ is the correlation coefficient between ith and jit assets.\nUsing these values in (2.5.5), and substituting for $dX_i$ from (2.5.1), we obtain

```
$d\phi = \frac{\partial \phi}{\partial t}dt + \sum_{i=1}^n \frac{\partial \phi}{\partial X_i}(a_it+b_idW_i) + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n b_ib_j\rho_{ij}dt\frac{\partial^2 \phi}{\partial X_i\partial X_j}, \quad \(2.5.6)$
```

This gives Ito's n-dimensional formula

```
$d\phi = [\frac{\partial \phi}{\partial t} + \sum_{i=1}^n a_i\frac{\partial \phi}{\partial X_i} + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n b_ib_j\rho_{ij}\frac{\partial^2 \phi}{\partial X_i\partial X_j}]dt + \sum_{i=1}^n\frac{\partial \phi}{\partial X_i}b_idW_i. \quad \(2.5.7)$
```

In particular, we consider the case $\sigma_I$

```
$dS_i = \mu_iS_idt + \sigma_iS_idW_i, \quad i=1,\dots,n,$
```

where $\mu_i$ is the constant drift of the ith asset, and $\sigma_i$ is the constant volatility of the ith asset, substituting $X_i=S_i, a_i=\mu_iS_i,$ and $b_i=\sigma_iS_i$ into equation (2.5.7)

```
$d\phi = [\frac{\partial \phi}{\partial t} + \sum_{i=1}^n \mu_iS_i\frac{\partial \phi}{\partial S_i} + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \sigma_i\sigma_jS_iS_j\rho_{ij}\frac{\partial^2 \phi}{\partial S_i\partial S_j}]dt + \sum_{i=1}^n\frac{\partial \phi}{\partial S_i}\sigma_iS_idW_i. \quad \(2.5.8)$
```

# 2.6 ITO PRODUCT AND QUOTIENT RULES IN TWO DIMENSIONS

We now derive expressions for the product and quotient of two stochastic processes. In this case, $\phi \to \phi(X_1,X_2),$

```
$dX_1=a_1dt+b_1dW_1 \quad \text{and} \quad dX_2=a_2dt+b_2dW_2.$
```

The two-dimensional version of Ito's lemma will be used:

```
$d\phi = \frac{\partial \phi}{\partial X_1}dX_1 + \frac{\partial \phi}{\partial X_2}dX_2 + \frac{1}{2}\sum_{i=1}^2\sum_{j=1}^2 \frac{\partial^2 \phi}{\partial X_i\partial X_j}dX_idX_j, \quad \(2.6.1)$
```

where we have the fact that

```
$$\frac{\partial \phi}{\partial t} = 0.$
```