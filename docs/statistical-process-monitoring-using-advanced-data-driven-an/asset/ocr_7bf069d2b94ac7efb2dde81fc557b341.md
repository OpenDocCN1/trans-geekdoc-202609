where \(\boldsymbol{\alpha} = [\alpha_1, \dots, \alpha_n]\). Mean-centering in the feature space is essential before applying KPCA, which is done as follows:

```
\(\overline{\mathbf{K}}(\mathbf{x}_i, \mathbf{x}_j) = \overline{\Phi}(\mathbf{x}_i)^T \overline{\Phi}(\mathbf{x}_j), \tag{4.20}\)
```

```
\(\overline{\mathbf{K}} = \mathbf{K} - \mathbf{K}\mathbf{1}_n - \mathbf{1}_n\mathbf{K} + \mathbf{1}_n\mathbf{K}\mathbf{1}_n, \tag{4.21}\)
```

where \(\mathbf{1}_n\) is the following matrix:

```
\(\mathbf{1}_n = \frac{1}{n} \begin{pmatrix} 1 & \dots & 1 \\ \vdots & \ddots & \vdots \\ 1 & \dots & 1 \end{pmatrix} \in \mathbb{R}^{n \times n}. \tag{4.22}\)
```

To solve the eigenvalue decomposition problem in Eq. (4.19), KPCA now solves the reformed eigenvalue problem of the centered kernel as [29]

```
\(n\lambda \boldsymbol{\alpha} = \overline{\mathbf{K}} \boldsymbol{\alpha} \tag{4.23}\)
```

for nonzero eigenvalues (\(\lambda \neq 0\)). This is equivalent to applying the conventional PCA in feature space, \(F\). Thereby, performing PCA in \(F\) allows obtaining eigenvectors \(\boldsymbol{\alpha}_1, \dots, \boldsymbol{\alpha}_n\), with \(\lambda_1 \ge \lambda_2 \ge \dots \ge \lambda_n\) as the corresponding eigenvalues.

At last, we can represent the output as

```
\(y_j = \sum_{i=1}^n \alpha_{ij}^k \overline{\mathbf{K}}(\mathbf{x}_j, x), \quad j = 1, \dots, d. \tag{4.24}\)
```

Generally speaking, the performance of the KPCA-based method mainly depends on the selected kernel functions. Numerous kernels are designed in the literature [60], but, to the best of our knowledge, there is no automated way for kernel selection. In the existing techniques, the selection of a kernel function is usually done empirically or experimentally from an ensemble of candidates. Indeed, inappropriate performance could be achieved in the case of a poor kernel choice [61, 62]. Here are some of the most widely used kernel functions in the machine learning literature:

Linear kernel,

```
\(\mathbf{K}(\mathbf{x}_i, \mathbf{x}_j) = \langle \mathbf{x}_i, \mathbf{x}_j \rangle. \tag{4.25}\)
```

Polynomial kernels,

```
\(\mathbf{K}(\mathbf{x}_i, \mathbf{x}_j) = \langle \mathbf{x}_i, \mathbf{x}_j \rangle^d, \quad d \in \mathbb{Z}^+. \tag{4.26}\)
```

Cosine kernels,

```
\(\mathbf{K}(\mathbf{x}_i, \mathbf{x}_j) = \frac{\langle \mathbf{x}_i, \mathbf{x}_j \rangle}{\|\mathbf{x}_i\| \|\mathbf{x}_j\|}. \tag{4.27}\)
```