Employing the Hamilton's principle as follows:

```
$$\int_{0}^{	au} (\delta U_k - \delta U_s + \delta U_d)dt = 0 \quad (7.17)$
```

where $\delta U_k, \delta U_s,$ and $\delta U_d$ denote kinetic energy, strain energy, and potential energy due to the external force, respectively. The following governing equations of FGGR reinforced beam be obtained as:

```
$$\delta u : \frac{\delta N_s}{\delta x} = I_0 \frac{\partial^2 u_0}{\partial t^2} + I_1 \frac{\partial^2 \psi}{\partial t^2}\\delta w : \frac{\delta Q_s}{\delta x} = -P_x \frac{\partial^2 w_0}{\partial x^2} + \frac{\partial^2 \psi}{\partial t^2}}\delta \psi : \frac{\delta M_s}{\delta x} = -Q_s = I_1 \frac{\partial^2 u_0}{\partial x^2} + I_2 \frac{\partial^2 \psi}{\partial t^2} \quad (7.18)$
```

where $N_s, M_s,$ and $Q_s$ can be expressed as:

```
$N_s = A_{11} \frac{\delta u_0}{\delta x} + B_{11} \frac{\delta \psi}{\delta x}; M_s = B_{11} \frac{\delta u_0}{\delta x} + D_{11} \frac{\delta \psi}{\delta x}; Q_s = ak_{55} (\frac{\delta w_0}{\delta x} + \delta \psi) \quad (7.19)$
```

And stiffness components are calculated by:

```
$A_{11}, B_{11}, D_{11} = \int_{-h/2}^{h/2} \frac{E(z)}{1-\nu(z)^2} dz \quad (1, z, z^2)$\
A_{55} = \int_{-h/2}^{h/2} kG(z)dz \quad (7.20)$
```

and $b$ is the width of the beam and $k$ denotes the shear correction factor and is taken $k=5/6$ in this study. Substituting Eq. (7.18), Eq. (7.19), the governing equation of GPLs reinforced beams can be rewritten as:

```
$A_{11} \frac{\partial^2 u_0}{\partial x^2} + B_{11} \frac{\partial^2 \psi}{\partial x^2} = I_0 \frac{\partial^2 u_0}{\partial t^2} + I_1 \frac{\partial^2 \psi}{\partial t^2}$ak_{55} (\frac{\partial^2 w_0}{\partial x^2} + \frac{\partial^2 \psi}{\partial x^2}) = -P_x \frac{\partial^2 w_0}{\partial x^2} + I_2 \frac{\partial^2 \psi}{\partial t^2}$B_{11} \frac{\partial^2 u_0}{\partial x^2} + D_{11} \frac{\partial^2 \psi}{\partial x^2} - ak_{55} (\frac{\partial^2 w_0}{\partial x^2} + \frac{\partial^2 \psi}{\partial x^2}) = I_1 \frac{\partial^2 u_0}{\partial t^2} + I_2 \frac{\partial^2 \psi}{\partial t^2} \quad (7.21)$
```