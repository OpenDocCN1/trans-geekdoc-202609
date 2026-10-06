The free vibration problem can be considered as a subset solution for Eq. (12.5), by assuming a harmonic vibration as:

```
u(t) = \Phi e^{i\omega t} \quad (12.8)
```

where $\omega$ is the natural frequency (rad/s) of FGP plate; $\Phi$ is the normal mode. Substituting Eq. (12.8) into Eq. (12.5), the generalized eigenvalue problem can be formulated as:

```
K\Phi = \lambda M\Phi \quad (12.9)
```

where $\lambda$ is the eigenvalue, $\Phi$ is the corresponding eigenvector. The fundamental frequency of FGP plate is based on the lowest eigenvalue acquired.

# 12.3.2 Stochastic vibration analysis of functionally graded porous plate

For the randomness involved structural system, the stochastic parameters of material properties would be random and changed to $E(\theta), G(\theta), \rho(\theta)$ for the FGP plate, where $	heta\in\Omega$ is the random event. The global mass, stiffness matrices, and governing equation of free vibration analysis for the FGP plate can be transformed into stochastic format, which can be represented as:

```
M(\theta)\ddot{u}(\theta) + K(\theta)\mathbf{u}(\theta) = 0 \quad (12.10)
```

where $M(\theta), K(	heta), \dot{u}(\theta), \ddot{u}(\theta)$ are the stochastic formats of global mass, stiffness matrices, acceleration and deformation vectors. It should be noticed that, effected by the random properties $\rho(\theta), E(\theta)$ of FGP plate, the elemental mass matrix and stiffness matrix are also transformed into

```
M(\theta) = \sum_{r} M^r(\theta), \quad K(\theta) = \sum_{r} K^r(\theta) \quad (12.11)
```

```
M'(\theta) = \int_{v_r} \rho(\theta)N^T dV, \quad K'(\theta) = \int_{v_r} B^T D(\theta) dBV \quad (12.12)
```

where $M'(\theta)$ and $K'(\theta)$ are the stochastic formats of elemental mass and stiffness matrix, $D(\theta)$ is the stochastic elasticity stiffness matrix, which are affected by the random values of density and Young's modulus of the FGP plate.

For the solutions of uncertain free vibration analysis of the FGP plate, the stochastic eigenvalue problem in Eq. (12.9) can be reformulated as:

```
K(\theta)\Phi(\theta) = \lambda(\theta)M(\theta)\Phi(\theta) \quad (12.13)
```