# 11 • QCA-Based Encoder Circuit 227

![](bbox=[0.178, 0.076, 0.822, 0.365])

FIGURE 11.15 Potential energy of priority encoder circuit for different states.

![](bbox=[0.178, 0.447, 0.822, 0.603])

FIGURE 11.16 Potential energy of octal to binary encoder.

# 11.10 ENERGY DISSIPATION

The Hamiltonian matrix is used to calculate total energy and power in an array of QCA cells [4,5,17,18]. Hence, energy dissipation of a QCA cell in one clock cycle, $T_{cc} = [-T, T]$ is derived in respect to Hamiltonian and coherence vectors as described in equation 11.3.

```
$E_{diss} = -\frac{h}{2} \int_{-T}^{T} \dot{\Gamma} \cdot \frac{d\vec{\lambda}}{dt} dt = -\frac{h}{2} \left[ \int_{-T}^{T} \dot{\Gamma} \cdot \frac{d\vec{\lambda}}{dt} dt ight] \quad (11.3)$
```

This tool estimates the dissipated energy of whole circuit for each input combinations in various tunneling levels under non-adiabatic switching [19]. The upper bound power dissipation model [19] is shown in equation 11.4.