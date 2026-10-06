# Generation of Multivariate Distributions: Correlated Variates | Section | 3.4 49

and using numerical optimization to determine the appropriate $(n-1)/2$ angles. An initial approximation can then be obtained by computing the Cholesky factorization $\hat{C} = \hat{L}\hat{L}^T$ and then calculating the angles to each nonzero element of $\hat{L}^T$.

# Covariance matrix

We will consider the case when a covariance matrix $C$ is supplied which is not positive definite – there is no Cholesky decomposition $C = L^TL$, where $L$ is lower triangular. In these circumstances, a covariance matrix does not require unit diagonal elements, it is possible to repair $C$ using

```
$C^+ = VK(KV)^T$
```

where $V$ and $K$ have the same meanings as before. A better approximation could be obtained via numerical optimization of the elements of the Cholesky decomposition; however; these optimal points are no longer constrained to lie on the $n$-dimensional unit hypersphere.

# 3.4.3 Normal Distribution

Here, we show how to generate a $p$ variate normal distribution with a given mean and covariance matrix. We will denote the variants of the $i$th observation from a $p$ variate zero normal distribution by $Z_i$, that is, we write a sample of $n$ observations as

```
$Z_i \sim N(0,C), \quad i = 1, \dots, n,$
```

$C$ is the $p 	imes p$ covariance matrix. Further $Z_{i,k}$ is used to denote the $k$th element of $Z_i$, which contains the value of the $k$th variate for the $i$th observation. From a computational point of view, we can consider a sample of $n$ observations to be represented by the $n 	imes p$ matrix $Z$. The $i$th row of $Z$ contains the values for $i$th observation, and the $k$th column of the $i$th row, $Z_{i,k}$, contains the value of the $k$th variate for the $i$th observation.

Also, since the distribution has zero mean, the sample covariance matrix is given by $C = Z^TZ$. We can use the fact that if the matrix $C$ is positive definite, a Cholesky factorization exists in which

```
$C = AA^T$
```

where $A$ is lower triangular. We can therefore generate $p$ variates which have a covariance matrix $C$ as follows. First, by (for example) using the Box Muller method described in Section 3.3.1, the independent normal variates

```
$X \sim N(0,I_p),$
```