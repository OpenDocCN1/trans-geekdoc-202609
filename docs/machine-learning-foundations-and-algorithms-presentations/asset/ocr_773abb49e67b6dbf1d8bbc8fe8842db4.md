# The GAN formulation

![](bbox=[0.183, 0.193, 0.683, 0.503])

+   * The original GAN formulation is the following min-max optimization

$$\min_G \max_D E_X \log D(X) + E_Z \log(1 - D(G(Z)))$$

+   * Objective of $D$: $D(X) = 1$ and $D(G(Z)) = 0$

+   * Objective of $G$: $D(G(Z)) = 1$