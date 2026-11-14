of heads and tails. Similarly, for inferring the mean of a Gaussian distribution with known variance we only need to know the empirical mean and number of samples.

Earlier in Section 5.1.8 we motivated the exponential family of distributions as being the ones that are minimal in the sense that they contain no other information than constraints on some statistics of the data. It makes sense then that the statistics used to generate exponential family distributions are sufficient. It also hints at the more remarkable fact of the Pitman-Koopman-Darmois theorem, which says that for any distribution whose domain is fixed, it is only the exponential family that admits sufficient statistics with bounded dimensionality as the number of samples increases [Dia88b].

# 5.3.5 Multivariate mutual information

There are several ways to generalize the idea of mutual information to a set of random variables as we discuss below.

# 5.3.5.1 Total correlation

The simplest way to define multivariate MI is to use the total correlation [Wat60] or multi-information [SV98], defined as

```
\mathbb{TC}(\{X_1, \dots, X_D\}) \triangleq D_{KL} \left( p(x) \| \prod_d p(x_d) \right)
```

```
= \sum_x p(x) \log \frac{p(x)}{\prod_{d=1}^D p(x_d)} = \sum_d \mathbb{H}(x_d) - \mathbb{H}(x)
```

For example, for 3 variables, this becomes

```
\mathbb{TC}(X, Y, Z) = \mathbb{H}(X) + \mathbb{H}(Y) + \mathbb{H}(Z) - \mathbb{H}(X, Y, Z)
```

where H(X, Y, Z) is the joint entropy

```
\mathbb{H}(X, Y, Z) = - \sum_x \sum_y \sum_z p(x, y, z) \log p(x, y, z)
```

One can show that the multi-information is always non-negative, and is zero iff p(x) = \prod_d p(x_d). However, this means the quantity is non-zero even if only a pair of variables interact. For example, if p(X, Y, Z) = p(X, Y)p(Z), then the total correlation will be non-zero, even though there is no 3 way interaction. This motivates the alternative definition in Section 5.3.5.2.

# 5.3.5.2 Interaction information (co-information)

The conditional mutual information can be used to give an inductive definition of the multivariate mutual information (MMI) as follows:

```
\mathbb{I}(X_1; \cdots ; X_D) = \mathbb{I}(X_1; \cdots ; X_{D-1}) - \mathbb{I}(X_1; \cdots ; X_{D-1} | X_D)
```

This is called the multiple mutual information [Yeu91b], or the co-information [Bel03]. This definition is equivalent, up to a sign change, to the interaction information [McG54; Han80; JB03; Bro09].