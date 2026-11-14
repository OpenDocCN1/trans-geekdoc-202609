Let us define \(\hat{\mathbf{Q}}_{X,X} = \mathbf{Q}_{X,X} + \sigma^2 \mathbf{I}_N\), and \(\boldsymbol{\Sigma} = (\sigma^{-2}\mathbf{K}_{Z,X}\mathbf{K}_{X,Z} + \mathbf{K}_{Z,Z})^{-1}\). Then the predictive distribution is

```
\(q_{\text{SOR}}(\mathbf{f}_*|\mathbf{y}) = \mathcal{N}(\mathbf{f}_*|\mathbf{Q}_{*,X}\hat{\mathbf{Q}}_{X,X}^{-1}\mathbf{y}, \mathbf{Q}_{*,*} - \mathbf{Q}_{*,X}\hat{\mathbf{Q}}_{X,X}^{-1}\mathbf{Q}_{X,*})\) (18.122)
```

```
\(=\mathcal{N}(\mathbf{f}_*|\sigma^{-2}\mathbf{K}_{*,Z}\boldsymbol{\Sigma}\mathbf{K}_{Z,X}\mathbf{y}, \mathbf{K}_{*,Z}\boldsymbol{\Sigma}\mathbf{K}_{Z,*})\) (18.123)
```

This is equivalent to the usual one for GPs except we have replaced \(\mathbf{K}_{X,X}\) by \(\mathbf{Q}_{X,X}\). This is equivalent to performing GP inference with the following kernel function

```
\(\mathcal{K}_{\text{SOR}}(\mathbf{x}_i, \mathbf{x}_j) = \mathcal{K}(\mathbf{x}_i, \mathbf{Z}) \mathbf{K}_{Z,Z}^{-1} \mathcal{K}(\mathbf{Z}, \mathbf{x}_j)\) (18.124)
```

The kernel matrix has rank \(M\), so the GP is degenerate. Furthermore, the kernel will be near 0 when \(\mathbf{x}_i\) or \(\mathbf{x}_j\) is far from one of the chosen points \(\mathbf{Z}\), which can result in an underestimate of the predictive variance.

# 18.5.3.2 DTC

One way to overcome the overconfidence of DIC is to only assume \(\hat{\mathbf{Q}}_{X,X} = \mathbf{0}\), but let \(\hat{\mathbf{Q}}_{*,*} = \mathbf{K}_{*,*} - \mathbf{Q}_{*,*}\) be exact. This is called the **deterministic training conditional** or **DTC** method [SWL03].

The corresponding joint prior has the form

```
\(q_{\text{dtc}}(\mathbf{f}_X, \mathbf{f}_*) = \mathcal{N}(\mathbf{0}, \begin{pmatrix} \mathbf{Q}_{X,X} & \mathbf{Q}_{X,*} \\ \mathbf{Q}_{*,X} & \mathbf{K}_{*,*} \end{pmatrix})\) (18.125)
```

Hence the predictive distribution becomes

```
\(q_{\text{dtc}}(\mathbf{f}_*|\mathbf{y}) = \mathcal{N}(\mathbf{f}_*|\mathbf{Q}_{*,X}\hat{\mathbf{Q}}_{X,X}^{-1}\mathbf{y}, \mathbf{K}_{*,*} - \mathbf{Q}_{*,X}\hat{\mathbf{Q}}_{X,X}^{-1}\mathbf{Q}_{X,*})\) (18.126)
```

```
\(=\mathcal{N}(\mathbf{f}_*|\sigma^{-2}\mathbf{K}_{*,Z}\boldsymbol{\Sigma}\mathbf{K}_{Z,X}\mathbf{y}, \mathbf{K}_{*,*} - \mathbf{Q}_{*,*} + \mathbf{K}_{*,Z}\boldsymbol{\Sigma}\mathbf{K}_{Z,*})\) (18.127)
```

The predictive mean is the same as in SOR, but the variance is larger (since \(\mathbf{K}_{*,*} - \mathbf{Q}_{*,*}\) is positive definite) due to the uncertainty of \(\mathbf{f}_*\) given \(\mathbf{f}_Z\).

# 18.5.3.3 FITC

A widely used approximation assumes \(q(f_X|f_Z)\) is fully factorized, i.e,

```
\(q(\mathbf{f}_X|\mathbf{f}_Z) = \prod_{n=1}^N p(f_n|\mathbf{f}_Z) = \mathcal{N}(\mathbf{f}_X|\mathbf{K}_{X,Z}\mathbf{K}_{Z,Z}^{-1}\mathbf{f}_Z, \text{diag}(\mathbf{K}_{X,X} - \mathbf{Q}_{X,X}))\) (18.128)
```

This is called the fully **independent training conditional** or **FITC** assumption, and was first proposed in [SG06a]. This throws away less uncertainty that the SOR and DTC methods, since it does not make any deterministic assumptions about the relationship between \(\mathbf{f}_X\) and \(\mathbf{f}_Z\).

The joint prior has the form

```
\(q_{\text{fitc}}(\mathbf{f}_X, \mathbf{f}_*) = \mathcal{N}(\mathbf{0}, \begin{pmatrix} \mathbf{Q}_{X,X} - \text{diag}(\mathbf{Q}_{X,X} - \mathbf{K}_{X,X}) & \mathbf{Q}_{X,*} \\ \mathbf{Q}_{*,X} & \mathbf{K}_{*,*} \end{pmatrix})\) (18.129)
```