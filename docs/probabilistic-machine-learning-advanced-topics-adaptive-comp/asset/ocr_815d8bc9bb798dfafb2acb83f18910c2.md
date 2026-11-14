This is called **statistical linear regression** or **SLR** [LBS01; AHE07], and ensures that we minimize

```
$\mathcal{L}(\mathbf{A}, \mathbf{b}, \mathbf{\Omega}) = \mathbb{E}_{\mathcal{N}(\mathbf{z}|\boldsymbol{\mu}, \mathbf{\Sigma})} [D_{\text{KL}} (p(\mathbf{y}|\mathbf{z}) \parallel q(\mathbf{y}|\mathbf{z}; \mathbf{A}, \mathbf{b}, \mathbf{\Omega}))]$
```

For the proof, see [GF+15; Kam+22]. Equivalently, one can show that the above parameters minimize the following mean squared error

```
$\mathcal{L}(\mathbf{A}, \mathbf{b}) = \mathbb{E} [(\mathbf{y} - \mathbf{A}\mathbf{x} - \mathbf{b})^\mathsf{T}(\mathbf{y} - \mathbf{A}\mathbf{x} - \mathbf{b})]$
```

with $\mathbf{\Omega}$ given by the residual noise

```
$\mathbf{\Omega} = \mathbb{E} [(\mathbf{y} - \mathbf{A}\mathbf{x} - \mathbf{b})(\mathbf{y} - \mathbf{A}\mathbf{x} - \mathbf{b})^\mathsf{T}]$
```

See [SS23, Sec 9.4] for the proof.

Note that although SLR results in a linear model, it is different than the Taylor series approximation of Section 8.3.1, since the linearization is chosen to be optimal wrt a distribution of points (averaged over $\mathcal{N}(\mathbf{z}|\boldsymbol{\mu}, \mathbf{\Sigma})$), instead of just being optimal at a single point $\boldsymbol{\mu}$.

# 8.5.1.2 Approximating the moments

To implement GGF, we need a way to compute $\hat{\mathbf{y}}$, $\mathbf{S}$ and $\mathbf{C}$. To help with this, we define two functions to compute Gaussian first and second moments:

```
$g_e(\mathbf{f}, \boldsymbol{\mu}, \mathbf{\Sigma}) \triangleq \int \mathbf{f}(\mathbf{z})\mathcal{N}(\mathbf{z}|\boldsymbol{\mu}, \mathbf{\Sigma})d\mathbf{z}$
```

```
$g_e(\mathbf{f}, \mathbf{g}, \boldsymbol{\mu}, \mathbf{\Sigma}) \triangleq \int (\mathbf{f}(\mathbf{z}) - \overline{\mathbf{f}})(\mathbf{g}(\mathbf{z}) - \overline{\mathbf{g}})^\mathsf{T}\mathcal{N}(\mathbf{z}|\boldsymbol{\mu}, \mathbf{\Sigma})d\mathbf{z}$
```

where $\overline{f} = g_e(\mathbf{f}, \boldsymbol{\mu}, \mathbf{\Sigma})$ and $\overline{\mathbf{g}} = g_e(\mathbf{g}, \boldsymbol{\mu}, \mathbf{\Sigma})$. There are several ways to compute these integrals, as we discuss below.

# 8.5.1.3 Approximation based on linearization

The simplest approach to approximating the moments is to linearize the functions $\mathbf{f}$ and $\mathbf{g}$ around $\boldsymbol{\mu}$, which yields the following (see Section 8.3.1):

```
$\hat{\mathbf{f}}(\mathbf{z}) = \boldsymbol{\mu} + \mathbf{F}(\mathbf{z} - \boldsymbol{\mu})$
```

```
$\hat{\mathbf{g}}(\mathbf{z}) = \boldsymbol{\mu} + \mathbf{G}(\mathbf{z} - \boldsymbol{\mu})$
```