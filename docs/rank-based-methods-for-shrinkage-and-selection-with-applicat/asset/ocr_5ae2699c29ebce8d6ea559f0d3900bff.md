# 10.4 Some Notation and Separation

Based upon a subset partitioning of S<sub>1</sub>, S<sub>2</sub>, and S<sub>3</sub>, we can also partition the true parameters \(\boldsymbol{\beta}^* = (\boldsymbol{\beta}^{*\top}_1, \boldsymbol{\beta}^{*\top}_2, \boldsymbol{\beta}^{*\top}_3)^\top\), without loss of generality. Some notations are shortened for convenience such as \(\boldsymbol{\beta}^*_{S_k} = \boldsymbol{\beta}^*_k, k=1, 2, 3\). Similar notations are also adopted for other sub-vectors and matrices. For example, using the same partitions, the design matrix \(\boldsymbol{X} = (\boldsymbol{x}_1, ..., \boldsymbol{x}_n)^\top, \boldsymbol{x}_i \in \mathbb{R}^{p_n}, i=1, ..., n\), can be written as \(\boldsymbol{X} = (\boldsymbol{X}_1, \boldsymbol{X}_2, \boldsymbol{X}_3)\). We also write \(\boldsymbol{X} = (\boldsymbol{Z}, \boldsymbol{X}_3)\) with \(\boldsymbol{Z} = (\boldsymbol{X}_1, \boldsymbol{X}_2)\). The row vector of \(\boldsymbol{Z}\) is denoted as \(\boldsymbol{z}_i = (z_{i1}, ..., z_{i(p_{1n}+p_{2n})})\), for \(1 \le i \le n\). We denote \(p_{kn} = |S_k|\) for \(k=1, 2, 3\) and \(p_n = p_{1n} + p_{2n} + p_{3n}\). In this chapter, we allow \(p_n = \sum_{k=1}^3 p_{kn}\) to be very large but restrict \(p_{1n} + p_{2n} \le n\) such that \(\boldsymbol{C}_n = n^{-1} \boldsymbol{Z}^\top \boldsymbol{Z}\) is non-singular. In the limit, we assume \(\boldsymbol{C}_n \to \boldsymbol{C}\), where \(\boldsymbol{C}\) is a positive definite matrix. If \(\boldsymbol{C}_n\) is singular, then a generalized inverse matrix is adopted when needed in computations. Specifically, one can use the Moore-Penrose generalized inverse for uniqueness.

# 10.4.1 Special Matrices

For convenience and to avoid confusion with notation, we provide some special sub-matrices of \(\boldsymbol{C}_n\) and their respective limiting cases as follows.

```
Let
\(C_{nlj} = n^{-1} X_{S_i}^\top X_{S_j}, \quad i, j = 1, 2, \quad C_{nii} = n^{-1} X_{S_i}^\top X_{S_i}, \quad i = 1, 2\)
\(C_{n22:1} = n^{-1} \left( X_{S_2}^\top X_{S_2} - X_{S_2}^\top X_{S_1} (X_{S_1}^\top X_{S_1})^{-1} X_{S_1}^\top X_{S_2} \right)\)
\(C_{n11:2} = n^{-1} \left( X_{S_1}^\top X_{S_1} - X_{S_1}^\top X_{S_2} (X_{S_2}^\top X_{S_2})^{-1} X_{S_2}^\top X_{S_1} \right)\)
\(M_{S_1^c} = I_n - X_{S_1^c} \left( X_{S_1^c}^\top X_{S_1^c} + \gamma_n I_{q_n} \right)^{-1} X_{S_1^c}^\top. \quad (10.4.1)\)
```

Let \(\boldsymbol{U} = (\boldsymbol{X}_{S_2}, \boldsymbol{X}_{S_3})\) be a \(n \times (p_{2n} + p_{3n})\) sub-matrix. Let

```
\(M_{S_1} = I_n - X_{S_1} (X_{S_1}^\top X_{S_1})^{-1} X_{S_1}^\top.\)
```

Then, \(\boldsymbol{U}^\top M_{S_1} \boldsymbol{U}\) is a \((p_n - p_{1n}) \times (p_n - p_{1n})\) dimensional singular matrix with rank \(k_n \ge 0\). We denote \(\xi_{1n} \le ... \le \xi_{k_n n}\) for all \(k_n\) positive eigenvalues of \(\boldsymbol{U}^\top M_{S_1} \boldsymbol{U}\).

Here, we have the limits

```
\(\lim_{n \to \infty} C_{nlj} = C_{lij}, \quad i, j = 1, 2,\)
```