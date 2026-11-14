where

\(\hat{g} = g + \frac{1}{2} (n_1 \log(2\pi) - \log |\mathbf{K}_{11}| + \mathbf{h}_1^T \mathbf{K}_{11}^{-1} \mathbf{h}_1)\) (2.140)
\(\hat{\mathbf{h}} = \mathbf{h}_2 - \mathbf{K}_{21} \mathbf{K}_{11}^{-1} \mathbf{h}_1\) (2.141)
\(\hat{\mathbf{K}} = \mathbf{K}_{22} - \mathbf{K}_{21} \mathbf{K}_{11}^{-1} \mathbf{K}_{12}\) (2.142)

# 2.3.3.4 Conditioning on evidence

Consider a potential defined on \((\boldsymbol{x}, \boldsymbol{y})\). Suppose we observe the value \(\boldsymbol{y}\). The new potential is given by the following reduced dimensionality object:

```
\(\phi^*(\boldsymbol{x}) = \exp \left[ g + (\boldsymbol{x}^T \boldsymbol{y}^T) \begin{pmatrix} \boldsymbol{h}_X \\ \boldsymbol{h}_Y \end{pmatrix} - \frac{1}{2} (\boldsymbol{x}^T \boldsymbol{y}^T) \begin{pmatrix} \mathbf{K}_{XX} & \mathbf{K}_{XY} \\ \mathbf{K}_{YX} & \mathbf{K}_{YY} \end{pmatrix} \begin{pmatrix} \boldsymbol{x} \\ \boldsymbol{y} \end{pmatrix} \right]\) (2.143)
\(= \exp \left[ \left( g + \boldsymbol{h}_Y^T \boldsymbol{y} - \frac{1}{2} \boldsymbol{y}^T \mathbf{K}_{YY} \boldsymbol{y} \right) + \boldsymbol{x}^T (\boldsymbol{h}_X - \mathbf{K}_{XY} \boldsymbol{y}) - \frac{1}{2} \boldsymbol{x}^T \mathbf{K}_{XX} \boldsymbol{x} \right]\) (2.144)
```

This generalizes the corresponding equation in [Lau92] to the vector-valued case.

# 2.3.3.5 Converting a linear-Gaussian CPD to a canonical potential

Finally we discuss how to create the initial potentials, assuming we start with a directed Gaussian graphical model. In particular, consider a node with a linear-Gaussian conditional probability distribution (CPD):

```
\(p(\boldsymbol{x}|\boldsymbol{u}) = c \exp \left[ -\frac{1}{2} ((\boldsymbol{x} - \boldsymbol{\mu} - \mathbf{B}^T \boldsymbol{u})^T \mathbf{\Sigma}^{-1} (\boldsymbol{x} - \boldsymbol{\mu} - \mathbf{B}^T \boldsymbol{u})) \right]\) (2.145)
\(= \exp \left[ -\frac{1}{2} (\boldsymbol{x} \ \boldsymbol{u}) \begin{pmatrix} \mathbf{\Sigma}^{-1} & -\mathbf{\Sigma}^{-1} \mathbf{B}^T \\ -\mathbf{B} \mathbf{\Sigma}^{-1} & \mathbf{B} \mathbf{\Sigma}^{-1} \mathbf{B}^T \end{pmatrix} \begin{pmatrix} \boldsymbol{x} \\ \boldsymbol{u} \end{pmatrix} \right.\) (2.146)
\(\left. + (\boldsymbol{x} \ \boldsymbol{u}) \begin{pmatrix} \mathbf{\Sigma}^{-1} \boldsymbol{\mu} \\ -\mathbf{B} \mathbf{\Sigma}^{-1} \boldsymbol{\mu} \end{pmatrix} - \frac{1}{2} \boldsymbol{\mu}^T \mathbf{\Sigma}^{-1} \boldsymbol{\mu} + \log c \right]\) (2.147)
```

where \(c = (2\pi)^{-n/2} |\mathbf{\Sigma}|^{-\frac{1}{2}}\). Hence we set the canonical parameters to

```
\(g = -\frac{1}{2} \boldsymbol{\mu}^T \mathbf{\Sigma}^{-1} \boldsymbol{\mu} - \frac{n}{2} \log(2\pi) - \frac{1}{2} \log |\mathbf{\Sigma}|\) (2.148)
\(\boldsymbol{h} = \begin{pmatrix} \mathbf{\Sigma}^{-1} \boldsymbol{\mu} \\ -\mathbf{B} \mathbf{\Sigma}^{-1} \boldsymbol{\mu} \end{pmatrix}\) (2.149)
\(\mathbf{K} = \begin{pmatrix} \mathbf{\Sigma}^{-1} & -\mathbf{\Sigma}^{-1} \mathbf{B}^T \\ -\mathbf{B} \mathbf{\Sigma}^{-1} & \mathbf{B} \mathbf{\Sigma}^{-1} \mathbf{B}^T \end{pmatrix} = \begin{pmatrix} \mathbf{I} \\ -\mathbf{B} \end{pmatrix} \mathbf{\Sigma}^{-1} \begin{pmatrix} \mathbf{I} & -\mathbf{B} \end{pmatrix}\) (2.150)
```

In the special case that \(x\) is a scalar, the corresponding result can be found in [Lau92]. In particular