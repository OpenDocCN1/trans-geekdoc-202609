where **F** and **G** are the Jacobians of $f$ and $g$. Thus we get the following implementation of the moment functions:

```
$$g_e(\hat{f}, \mu, \Sigma) = \mathbb{E} \left[ \mu + \mathbf{F}(z - \mu) \right] = \mu$$
$$g_c(\hat{f}, \hat{g}, \mu, \Sigma) = \mathbb{E} \left[ (\hat{f}(z) - \overline{f})(\hat{g}(z) - \overline{g})^\top \right]$$
$$= \mathbb{E} \left[ \hat{f}(z)\hat{g}(z)^\top + \overline{f}\overline{g}^\top - \hat{f}(z)\overline{g}^\top - \overline{f}\hat{g}(z)^\top \right]$$
$$= \mathbb{E} \left[ (\mu + \mathbf{F}(z - \mu))(\mu + \mathbf{G}(z - \mu))^\top + \mu\mu^\top - \mu\mu^\top - \mu\mu^\top \right]$$
$$= \mathbb{E} \left[ \mu\mu^\top + \mathbf{F}(z - \mu)(z - \mu)^\top \mathbf{G}^\top + \mathbf{F}(z - \mu)\mu^\top + \mu(z - \mu)^\top \mathbf{G}^\top - \mu\mu^\top \right]$$
$$= \mathbf{F} \mathbb{E} \left[ (z - \mu)(z - \mu)^\top \right] \mathbf{G}^\top = \mathbf{F} \Sigma \mathbf{G}^\top$$
```

Using this inside the GGF is equivalent to the EKF in Section 8.3.2. However, this approach can lead to large errors and sometimes divergence of the filter [IX00; VDMW03].

# 8.5.1.4 Approximation based on Gaussian quadrature

Since we are computing integrals wrt a Gaussian measure, we can use **Gaussian quadrature** methods of the following form:

```
$$\int h(z) \mathcal{N}(z | \mu, \Sigma) dz \approx \sum_{k=1}^K w^k h(z^k)$$
```

for a suitable set of evaluation points $z^k$ (sometimes called **sigma points**) and weights $w^k$. (Note that one-dimensional integrals are called **quadratures**, and multi-dimensional integrals are called **cubatures**.)

One way to compute the sigma points is to use the unscented transform described in Section 8.4.1. Using this inside the GGF is equivalent to the UKF in Section 8.4.2.

Alternatively, we can use **spherical cubature integration**, which gives rise to the **cubature Kalman filter** or **CKF** [AH09]. This turns out (see [SS23, Sec 8.7]) to be a special case of the UKF, with $2n_z + 1$ sigma points, and hyperparameter values of $\alpha = 1$ and $\beta = 0$ (with $\kappa$ left free). A more accurate approximation uses **Gauss-Hermite integration**, which allows the user to select more sigma points. In particular, an order $p$ approximation will be exact for polynomials of order up to $2p - 1$. See [SS23, Sec 8.3] for details, and Figure 8.5(e-f) for an illustration. However, this comes at a price: the number of sigma points is now $p^n$. Using Gauss-Hermite integration for GGF gives rise to the **Gauss-Hermite Kalman filter** or **GHKF** [IX00], also known as the **quadrature Kalman filter** or **QKF** [AHE07].

# 8.5.1.5 Approximation based on Monte Carlo integration

We can also approximate the integrals with Monte Carlo (see Section 11.2). Note, however, that this is not the same as particle filtering (Section 13.2), which approximates the conditional $p(z_t | y_{1:t})$ rather than the joint $p(z_t, y_t | y_{1:t-1})$ (see Section 8.6.1 for discussion of this difference).