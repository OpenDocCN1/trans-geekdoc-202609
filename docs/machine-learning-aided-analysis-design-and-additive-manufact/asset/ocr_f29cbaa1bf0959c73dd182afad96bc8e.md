Free and forced vibrations of functionally graded porous shallow shells on elastic foundation

Substituting Eqs. (5.6) and (5.8) into Eq. (5.10), it can be obtained

```
$$\begin{aligned} N_x &= A_{11}z_s^0 + A_{12}z_s^2 + B_{11}\kappa_x + B_{12}\kappa_y \ N_y &= A_{21}z_s^0 + A_{22}z_s^2 + B_{21}\kappa_x + B_{22}\kappa_y \ N_{xy} &= A_{66} + B_{66}\kappa_{xy}, M_{xy} = D_{66}\kappa_{xy} + D_{66}\gamma^0 \ M_x &= B_{11}z_s^0 + B_{12}z_s^2 + D_{11}\kappa_x + D_{12}\kappa_y \ M_y &= B_{21}z_s^0 + B_{22}z_s^2 + D_{21}\kappa_x + D_{22}\kappa_y \ Q_s &= C_{66}\gamma_s, Q_z &= C_{66}\gamma^0 \end{aligned}$ (5.11)
```

where $\kappa$ is the shear correction factor and its value is 5/6. $A_{ij}, D_{ij}$ ($i,j=1, 2$) are the extensensional, and extensensional-bending coefficients, and their values can be computed by the following expressions:

```
$A_{ij} = \int_{-h/2}^{h/2} Q_{ij}dz, D_{ij} = \int_{-h/2}^{h/2} z^2 Q_{ij}dz$ (5.12)
```

The strain potential energy $U_s$ of FGP shallow shell can be articulated as

```
$U_s = \frac{1}{2} \int_0^h \left( N_x\varepsilon_x + N_y\varepsilon_y + N_{xy}\varepsilon_{xy} + M_x\kappa_x + M_y\kappa_y + M_{xy}\kappa_{xy} + Q_s\gamma_s + Q_z\gamma^0 \right) dz$ (5.13)
```

The kinetic energy $T$ of FGP shallow shell can be expressed as:

```
$T = \frac{1}{2} \int_0^h \left( \left(\frac{\partial\dot{w}}{\partial z}\right)^2 + \left(\frac{\partial\dot{\varphi}_x}{\partial z}\right)^2 + \left(\frac{\partial\dot{\varphi}_y}{\partial z}\right)^2 \right) + 2I_1 \left( \dot{w}\left(\frac{\partial\dot{\varphi}_x}{\partial z}\right) + \dot{\varphi}_x\frac{\partial\dot{w}}{\partial z} + \dot{\varphi}_y\left(\frac{\partial\dot{w}}{\partial z}\right) \right) dz$ (5.14)
```

with the inertia terms are:

```
$I_0 = \int_{-h/2}^{h/2} \rho dz, I_1 = \int_{-h/2}^{h/2} \rho z^2 dz$ (5.15)
```

In order to satisfy any boundary conditions, the virtual spring technique is introduced in this chapter to simulate the force vector at the boundary through three sets of linear displacement springs $k_j(i=u,v,w,j=a_0,a_1)$ and two sets of rotary springs $s_k(i=x,y,j=b_0,b_1)$, as shown in Fig. 5.3A. The simulation can then be