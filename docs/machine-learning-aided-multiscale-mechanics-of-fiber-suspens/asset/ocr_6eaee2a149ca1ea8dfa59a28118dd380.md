1987)

```
N = \int_{S^2} n \otimes n \rho(n) \, dS(n), \quad (2.30)
```

as a measure for the fiber orientation state. The tensor N is symmetric, positive semi-definite, and has unit trace, such that

```
N_{ii} = \lambda_1 + \lambda_2 + \lambda_3 = 1, \quad (2.31)
```

where \lambda_1, \lambda_2, \text{and } \lambda_3 denote the eigenvalues of the tensor N. By sorting the eigenvalues

```
\lambda_1 \ge \lambda_2 \ge \lambda_3, \quad (2.32)
```

and considering equation (2.31), the bounds for the largest eigenvalue \lambda_1 are found as

```
1 \ge \lambda_1 \ge \frac{1}{3}. \quad (2.33)
```

Additionally, an upper bound for the eigenvalue \lambda_2 follows from positive semi-definiteness of the tensor N, and a lower bound may be derived by eliminating \lambda_3 from equation (2.32) using equation (2.31), such that

```
\min(\lambda_1, 1 - \lambda_1) \ge \lambda_2 \ge \frac{1 - \lambda_1}{2}. \quad (2.34)
```

Thus, we may parametrize the tensor N by its two eigenvalues \lambda_1 and \lambda_2, and the rotation Q in terms of an eigendecomposition

```
N = Q \, \text{diag}(\lambda_1, \lambda_2, \lambda_3) \, Q^{\text{T}}, \quad (2.35)
```

where the diag operator constructs a second order tensor in the standard basis of \mathbb{R}^3. By objectivity, the results of this thesis generalize to all rotations Q, and for simplicity we choose

```
Q = I. \quad (2.36)
```