# 50 CHAPTER | 3 Generation of Random Variates

where the vector $X$ contains the $p$ variates, $I_p$ is the unit matrix, and $XX^T$ $I_p$.

Then, using the Cholesky factorization of equation (3.4.4), form

```
$Y = AX$,
```

where $Y$ is a $p$ element vector.
Now since $YY^T = AX(AX)^T = A(XX^T)A^T = AA^T = C$, we have that

```
$Y \sim N(0,C)$.
```

Variates that have nonzero means $\mu_k, k=1, \dots, p$ can be obtained by simply modifying equation (3.4.4) to

```
$Y' = AX + \mu$.
```

where $Y'$ is a $p$ variate vector that is distributed as $N(\mu,C)$, and the $p$ elements of $\mu$ contain the means of the variates $Y'_k, k=1, \dots, p$.
If the matrix $C$ is not positive definite, then we can create a repaired matrix, $\hat{C}$, by using the approach outlined in Section 3.4.2.
We use the decomposition

```
$$\hat{C} = VK(VK)^T$.
```

Under circumstances, the p elements $Y$ and $Y'$ are generated using the following modified versions of equation (3.4.4) and equation (3.4.5):

```
$Y = VKX$ and $Y' = VKX + \mu$.
```

The method for generating variates $Y$ from a given correlation matrix $C_r$ is identical. However, non-positive definite matrices are repaired as $\hat{C}_r = FVK(FVK)^T$, see Section 3.4.2.

To generate correlated normal and lognormal variates is given in Code example 3.4.2.

```
long Quasirandom_Normal_LogNormal_Correlated(long fcall, long seq, long inq, double means[], long n,
	double c[], long tdc, long tolk, long "rank", double work[], long lwk) {
	/* Input parameters:
	*/
	ifif fcall == 1 then it is an initialisation, if fcall == 0 then a continuation call
	if seq == 0 then a Faure sequence, if seq == 1 then a Bieder sequence
	if seq == 2 then a Sobol sequence
	if inorm == 0 then it is a lognormal distribution, if inorm == 1 then a normal distribution
	// number of elements in the required covariance matrix, C
	 the second dimension of the matrix
	// the means of the normal variates
	// the standard deviations of the independent normal variates
	 the tolerance used for calculating the rank of the covariance matrix C
	 the size of the work array, work
	Output parameters:
	// the computed rank of the covariance matrix C
	// the elements[s]
}
```

# Code example 3.2 The functions Quasirandom_Normal_LogNormal_Correlated which generate correlated normal and lognormal variates and correlated quasi-random lognormal variates.