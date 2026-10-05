# Theoretical Background 71

for superlubricity. In general, these mechanisms involve hysteresis and energy dissipation, which prevents the recovery of the energy that was expended sliding. In what we follow, we provide a brief overview of common friction mechanisms.

It has long been recognized that solid friction is intimately connected to hysteresis, as best illustrated by Prandtl⁸ and Tomlinson⁹ In this model, a surface atom of mass $m$ is coupled to its lattice via a harmonic spring of stiffness $k$. The lattice state, which moves at constant velocity $v_0$, is assumed to be located at the origin at time $t=0$. In addition to the interaction with its lattice state, the atom experiences a coupling $V_0\cos(2\pi x/a)$ to the substrate, where $V_0$ has units of energy and reflects the strength of the coupling, $a$ is the lattice constant of the substrate, and $x$ is the current position of the surface atom. Upon the introduction of a viscous damping term that is proportional to velocity $\gamma$, the equation of motion for this is

```
$m\ddot{x} + \gamma\dot{x} = k(v_0 - x) + \frac{2\pi}{a}V_0\sin(2\pi x/a) \quad [1]$
```

If $k$ is very large, i.e., $k$ is greater than the maximum curvature of the potential, $V''_{max} = (2\pi/a)^2V_0$, there will be a unique equilibrium position for the atom of $x_{eq} \approx v_0t$ and the atom will always be close to $x_{eq}$. Consequently, the friction will be linear in $v_0$ for small values of $v_0$.

Things become more interesting once $V''_{max}$ exceeds $k$. Now more than one stable position at certain points in time exists, as shown in Figure 2.

![](bbox=[0.275, 0.575, 0.722, 0.823])

**Figure 2** Illustration of an instability in the Prandtl-Tomlinson model. The sum of the substrate potential and the elastic energy of the spring is shown at various instances in time. The energy difference between the initial and the final point of the thick line will be the dissipated energy when temperature temperature and sliding velocities are very small.