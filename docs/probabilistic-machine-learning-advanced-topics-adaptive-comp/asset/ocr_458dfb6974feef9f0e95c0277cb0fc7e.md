# subset-of-data approach.

The key question is: how should we choose the subset? The simplest approach is to pick random examples (this method was recently analyzed in [HIY19]). However, intuitively it makes more sense to try to pick a subset that in some sense “covers” the original data, so it contains approximately the same information (up to some tolerance) without the redundancy. Clustering algorithms are one heuristic approach, but we can also use coreset methods, which can probably find such an information-preserving subset (see e.g., [Hug+19] for an application of this idea to GPs).

# 18.5.1.1 Informative vector machine

Clustering and coreset methods are unsupervised, in that they only look at the features \(\boldsymbol{x}_i\) and not the labels \(y_i\), which can be suboptimal. The informative vector machine [HLS03] uses a greedy strategy to iteratively add the labeled example \((\boldsymbol{x}_j, y_j)\) that maximally reduces the entropy of the function’s posterior, \(\Delta_j = \mathbb{H}(p(f_j)) - \mathbb{H}(p^\text{new}(f_j))\), where \(p^\text{new}(f_j)\) is the posterior of \(f\) at \(\boldsymbol{x}_j\) after conditioning on \(y_j\). (This is very similar to active learning.) To compute \(\Delta_j\), let \(p(f_j) = \mathcal{N}(\mu_j, v_j)\), and \(p(f_j|y_j) \propto p(f_j)\mathcal{N}(y_j|f_j, \sigma^2) = \mathcal{N}(f_j|\mu_j^\text{new}, v_j^\text{new})\), where \((v_j^\text{new})^{-1} = v_j^{-1}+\sigma^{-2}\). Since \(\mathbb{H}(\mathcal{N}(\mu, v)) = \log(2\pi ev)/2\), we have \(\Delta_j = 0.5 \log(1+v_j/\sigma^2)\). Since this is a monotonic function of \(v_j\), we can maximize it by choosing the site with the largest variance. (In fact, entropy is a submodular function, so we can use submodular optimization algorithms to improve on the IVM, as shown in [Kra+08].)

# 18.5.1.2 Discussion

The main problem with the subset of data approach is that it ignores some of the data, which can reduce predictive accuracy and increase uncertainty about the true function. Fortunately there are other scalable methods that avoid this problem, essentially by approximately representing (or compressing) the training data, as we discuss below.

# 18.5.2 Nyström approximation

Suppose we had a rank \(M\) approximation to the \(N \times N\) matrix gram matrix of the following form:

```
\(\mathbf{K}_{X,X} \approx \mathbf{U}\Lambda\mathbf{U}^\top\) (18.106)
```

where \(\Lambda\) is a diagonal matrix of the \(M\) leading eigenvalues, and \(\mathbf{U}\) is the matrix of the corresponding \(M\) eigenvectors, each of size \(N\). In this case, we can use the matrix inversion lemma to write

```
\(\mathbf{K}_\sigma^{-1} = (\mathbf{K}_{X,X} + \sigma^2\mathbf{I}_N)^{-1} \approx \sigma^{-2}\mathbf{I}_N + \sigma^{-2}\mathbf{U}(\sigma^2\Lambda^{-1} + \mathbf{U}^\top\mathbf{U})^{-1}\mathbf{U}^\top\) (18.107)
```

which takes \(O(NM^2)\) time. Similarly, one can show (using the Sylvester determinant lemma) that

```
\(|\mathbf{K}_\sigma| \approx |\Lambda||\sigma^2\Lambda^{-1} + \mathbf{U}^\top\mathbf{U}|\) (18.108)
```

which also takes \(O(NM^2)\) time. Unfortunately, directly computing such an eigendecomposition takes \(O(N^3)\) time, which does not help. However, suppose we pick a subset \(Z\) of \(M < N\) points. We can partition the Gram matrix as