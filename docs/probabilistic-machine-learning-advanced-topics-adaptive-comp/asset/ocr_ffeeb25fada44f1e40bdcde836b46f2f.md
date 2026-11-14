![](bbox=[0.386, 0.098, 0.626, 0.252])

Figure 28.16: Canonical correlation analysis as a PGM.

# 28.3.4.3 Canonical correlation analysis

We now consider a symmetric unsupervised version of PLS, in which we allow each view to have its own “private” subspace, but there is also a shared subspace. If we have two observed variables, \(x_i\) and \(y_i\), then we have three latent variables, \(z_i^s \in \mathbb{R}^{L_s}\) which is shared, \(z_i^x \in \mathbb{R}^{L_x}\) and \(z_i^y \in \mathbb{R}^{L_y}\) which are private. We can write the model as follows [BJ05]:

```
p(z_i) = \mathcal{N}(z_i^s|\mathbf{0}, \mathbf{I}_{L_s})\mathcal{N}(z_i^x|\mathbf{0}, \mathbf{I}_{L_x})\mathcal{N}(z_i^y|\mathbf{0}, \mathbf{I}_{L_y}) \qquad (28.111)
p(x_i|z_i) = \mathcal{N}(x_i|\mathbf{B}_x z_i^x + \mathbf{W}_x z_i^s + \mu_x, \sigma^2 \mathbf{I}_{D_x}) \qquad (28.112)
p(y_i|z_i) = \mathcal{N}(y_i|\mathbf{B}_y z_i^y + \mathbf{W}_y z_i^s + \mu_y, \sigma^2 \mathbf{I}_{D_y}) \qquad (28.113)
```

See Figure 28.16 The corresponding observed joint distribution has the form

```
p(\mathbf{v}_i|\theta) = \int \mathcal{N}(\mathbf{v}_i|\mathbf{W} z_i + \mu, \sigma^2 \mathbf{I}) \mathcal{N}(z_i|\mathbf{0}, \mathbf{I}) dz_i = \mathcal{N}(\mathbf{v}_i|\mu, \mathbf{W}\mathbf{W}^T + \sigma^2 \mathbf{I}_D) \qquad (28.114)
```

where

```
\mathbf{W} = \begin{pmatrix} \mathbf{W}_x & \mathbf{B}_x & \mathbf{0} \\ \mathbf{W}_y & \mathbf{0} & \mathbf{B}_y \end{pmatrix} \qquad (28.115)
\mathbf{W}\mathbf{W}^T = \begin{pmatrix} \mathbf{W}_x \mathbf{W}_x^T + \mathbf{B}_x \mathbf{B}_x^T & \mathbf{W}_x \mathbf{W}_y^T \\ \mathbf{W}_y \mathbf{W}_x^T & \mathbf{W}_y \mathbf{W}_y^T + \mathbf{B}_y \mathbf{B}_y^T \end{pmatrix} \qquad (28.116)
```

[BJ05] showed that MLE for this model is equivalent to a classical statistical method known as canonical correlation analysis or CCA [Hot36]. However, the PGM perspective allows us to easily generalize to multiple kinds of observations (this is known as generalized CCA [Hor61]) or to nonlinear models (this is known as deep CCA [WLL16; SNM16]), or exponential family CCA [KVK10]. See [Uur+17] for further discussion of CCA and its extensions, and Section 32.2.2.2 for more details.

# 28.3.5 Factor analysis with exponential family likelihoods

So far we have assumed the observed data is real-valued, so \(\mathbf{x}_n \in \mathbb{R}^D\). If we want to model other kinds of data (e.g., binary or categorical), we can simply replace the Gaussian output distribution