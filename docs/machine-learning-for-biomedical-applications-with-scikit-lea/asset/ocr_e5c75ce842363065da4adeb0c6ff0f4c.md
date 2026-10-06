(se Fig. 5.11). In this case X = MS is also Gaussian with zero mean and covariance:

$XX^T = (MS)(MS)^T = MSS^TM^T = MM^T.$

Our goal with ICA is to be predict unique sources. However, if the original source signals are Gaussian, we can imagine a situation where we propose a new coefficients matrix M' through a rotation R such that M' = MR. In this case we would observe the effect of a new mixture X' = MS, which, if we are to distinguish the effect of M' from M, would require that the distribution of X' differs from that of X. Unfortunately, in the case of Gaussian variables, this becomes impossible because the covariance of X' is indistinguishable from that of X$^{15}$

$X'^T = M'S^TM'^T = MRRSS^TR^T = MRRMM^T = MM^T.$

Another explanation may be achieved through the central limit theorem, which states that

> "The distribution of a sum of independent random variables tends towards a Gaussian distribution"

In words, a mixed signal will be more Gaussian than that of either of its component signals. We can use this to find the basis of an algorithm to separate the components. What we are looking for is that each source be represented as a linear sum of the mixtures S = A^{-1}X, with coefficients given by the inverse of our mixing matrix. We can therefore try different linear combinations of mixtures, until we find the most non-Gaussian combination. There are many ways to encourage non-Gaussianity, one of the most stable (used by the FastICA algorithm [21]) is to optimize for the negative entropy of the distribution, since

> "a Gaussian variable has the largest entropy among all random variables of equal variance [9]."

Estimates of negative entropy are less sensitive to outliers than standard measures of non-Gaussianity such as Kurtosis and provide a measure which is zero for a Gaussian variable and always nongaussian.

# 5.5.4 Preprocessing for ICA

Regardless of which optimization method is used, a key preprocessing step is the whitening of the mean-centered-covariance matrix. Whitening is related to PCA and works by transforming the original input data X_C into Y, where Cov(Y) = I. This is achieved through SVD of the original covariance matrix Cov(X_C) = C_X =

15 Using the fact that for orthogonal matrices R^T = R^{-1}, such that RR^T = I.