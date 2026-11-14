where \(\mathbf{v}_j\) is the \(j\)’th row of \(\mathbf{V}\), and the prior is factored, so \(p(\mathbf{z}) = \prod_j p_j(z_j)\). We can also replace the sum over \(n\) with an expectation wrt the empirical distribution to get the following objective

```
\(\text{NLL}(\mathbf{V}) = \sum_j \mathbb{E} [G_j(z_j)]\)
```

where \(z_j = \mathbf{v}_j^\text{T}\mathbf{x}\) and \(G_j(z_j) \triangleq -\log p_j(z_j)\). We want to minimize this (nonconvex) objective subject to the constraint that \(\mathbf{V}\) is an orthogonal matrix.

It is straightforward to derive a (projected) gradient descent algorithm to fit this model. (For some JAX code, see https://github.com/tuananhle7/ica). One can also derive a faster algorithm that follows the natural gradient; see e.g., [Mac03, ch 34] for details. However, the most popular method is to use an approximate Newton method, known as **fast ICA** [H000]. This was used to produce Figure 28.32.

# 28.6.4 Alternatives to MLE

In this section, we discuss various alternatives estimators for ICA that have been proposed over the years. We will show that they are equivalent to MLE. However, they bring interesting perspectives to the problem.

# 28.6.4.1 Maximizing non-Gaussianity

An early approach to ICA was to find a matrix \(\mathbf{V}\) such that the distribution \(\mathbf{z} = \mathbf{V}\mathbf{x}\) is as far from Gaussian as possible. (There is a related approach in statistics called **projection pursuit** [FT74].) One measure of non-Gaussianity is kurtosis, but this can be sensitive to outliers. Another measure is the **negentropy**, defined as

```
\(\text{negentropy}(z) \triangleq \mathbb{H} (\mathcal{N}(\mu, \sigma^2)) - \mathbb{H} (z)\)
```

where \(\mu = \mathbb{E}[z]\) and \(\sigma^2 = \mathbb{V}[z]\). Since the Gaussian is the maximum entropy distribution (for a fixed variance), this measure is always non-negative and becomes large for distributions that are highly non-Gaussian.

We can define our objective as maximizing

```
\(J(\mathbf{V}) = \sum_j \text{negentropy}(z_j) = \sum_j \mathbb{H} (\mathcal{N}(\mu_j, \sigma_j^2)) - \mathbb{H} (z_j)\)
```

where \(\mathbf{z} = \mathbf{V}\mathbf{x}\). Since we assume \(\mathbb{E}[\mathbf{z}] = \mathbf{0}\) and \(\text{Cov}[\mathbf{z}] = \mathbf{I}\), the first term is a constant. Hence

```
\(J(\mathbf{V}) = \sum_j - \mathbb{H} (z_j) + \text{const} = \sum_j \mathbb{E} [\log p(z_j)] + \text{const}\)
```

which we see is equal (up to a sign change, and irrelevant constants) to the log-likelihood in Equation (28.151).