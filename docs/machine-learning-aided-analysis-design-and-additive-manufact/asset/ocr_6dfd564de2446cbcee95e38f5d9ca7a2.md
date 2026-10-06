Then, substituting Eq. (4.16) into Eq. (4.15), the potential energy of the bound-aries can be written as:

```
$U_b = \frac{\pi R}{2} \left\{ k_u^2[U(0)]^2 + k_v^2[V(0)]^2 + k_w^2[W(0)]^2 + k_{\theta}^2\left[\frac{W(0)}{L_{\eta}}\right]^2 \right\\+ \frac{\pi R}{2} \left\{ k_u^2[U(1)]^2 + k_v^2[V(1)]^2 + k_w^2[W(1)]^2 + k_{\theta}^2\left[\frac{W(1)}{L_{\eta}}\right]^2 \right\right}$ (4.22)
```

The Lagrange function of the FG porous cylindrical shell with arbitrary boundary conditions is defined as:

```
$\Pi = T - U_c - U_s$ (4.23)
```

Applying a standard Ritz procedure, minimize II with respect to the unknown coefficients, the expression (4.24) can be obtained:

```
$\frac{\partial \Pi}{\partial a_g}=0, \frac{\partial \Pi}{\partial b_g}=0, \frac{\partial \Pi}{\partial c_g}=1, 2, \dots, NT$ (4.24)
```

So the following eigenvalue equation is generated:

```
$\omega^2 \mathbf{M} - \mathbf{K} - \mathbf{K}_s]\mathbf{q} = \mathbf{0}$ (4.25)
```

where $\mathbf{q} = [\mathbf{a}_g, \mathbf{b}_g, \mathbf{c}_g]^T$ is the Ritz vector given by $\mathbf{a}_g = [a_1, a_2, \dots, a_{NT}]^T, \\mathbf{b}_g = [b_1, b_2, \dots, b_{NT}]^T$, and $\mathbf{c}_g = [c_1, c_2, \dots, c_{NT}]^T$.

The expression for the mass matrix $\mathbf{M}$ is:

```
$\mathbf{M} = \begin{bmatrix} \mathbf{M}_{aa} & \mathbf{M}_{ab} \\ \mathbf{M}_{ac} & \mathbf{M}_{bc} \end{bmatrix}$ (4.26)
```

where

```
$$\mathbf{M}_{aa}(p, q) = \rho_L^{LR} \int_0^1 \psi_p^a(\eta)\psi_q^a(\eta)d\eta$ (4.27)
```

```
$$\mathbf{M}_{ab}(p, q) = \rho_L^{LR} \int_0^1 \psi_p^a(\eta)\psi_q^b(\eta)d\eta$ (4.28)
```

```
$$\mathbf{M}_{bc}(p, q) = \rho_L^{LR} \int_0^1 \psi_p^b(\eta)\psi_q^c(\eta)d\eta$ (4.29)
```