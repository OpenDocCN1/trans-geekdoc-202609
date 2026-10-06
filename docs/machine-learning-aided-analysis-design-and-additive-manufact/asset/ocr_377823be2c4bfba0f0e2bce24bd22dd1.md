AI-enhanced FE multiscale modeling

# 10.3.2 Bending analysis of FG porous beam

This section examines the static bending behavior of a novel FG porous beam containing a thin low-density layer and bounded by top and bottom high-density porous layers, as depicted in Fig. 10.8, where all the layers are assumed to be perfectly bonded together and made of closed-cell aluminum frames. The relation between layer and beam thicknesses is built on the mid-thickness plane by $h_H$ ($h_H$: high-density layer) = $\frac{1}{2}h$ ($h_L$: low-density layer) = $h$ (total: beam thickness). A Cartesian system $(x, z)$ is built on the mid-thickness plane: $x \in [0, L]$ ($L$ is the beam length), $z \in [-0.h_L, h_H]$, and the beam width is denoted by $b$. The beam deflection is measured under the application of a point load located at the mid-span. The relative densities of each layer are expressed as

```
$\mu = \begin{cases} 13.81\% (\text{high - density layer}) \ 6.92\% (\text{low - density layer}) \end{cases} \quad (10.9)$
```

and the properties of both layers are uncertain with CNN-predicted Young's modulus (based on Eq. (10.5)) written as
Young's modulus of the high-density layer ($\mu = 13.81$, $\alpha_1, eta_1 \in [0, 1]$)

```
$\epsilon_{H}(\alpha_1, \beta_1) = (\epsilon_{H} - \epsilon_{M})\alpha_1 + (\epsilon_{M} - \epsilon_{L})\beta_1 + (\epsilon_{H} - \epsilon_{L})\alpha_1\beta_1 + \epsilon_{H} \quad (10.10)$
```

Young's modulus of the low-density layer ($\mu = 6.92$, $\alpha_2, \beta_2 \in [0, 1]$)

```
$\epsilon_{L}(\alpha_2, \beta_2) = (\epsilon_{L} - \epsilon_{M})\alpha_2 + (\epsilon_{M} - \epsilon_{H})\beta_2 + (\epsilon_{L} - \epsilon_{H})\alpha_2\beta_2 + \epsilon_{L} \quad (10.11)$
```

where $\epsilon_{2H} = 1693.2$ MPa, $\epsilon_{1H} = (1 - 5.92\%)\epsilon_{2H}$, and $\epsilon_{3H} = (1 + 5.92\%)\epsilon_{2H}$. Similarly, $\epsilon_{2L} = 865.9$ MPa, $\epsilon_{1L} = (1 - 5.92\%)\epsilon_{2L}$, and $\epsilon_{3L} = (1 + 5.92\%)\epsilon_{2L}$. That 1693.2 MPa and 865.9 MPa are obtained from the averaged stiffness (Eqs. (10.3)) of RVE sets built with relative density ranges (13.6%–14.02%, mean relative density = 13.81%) and (6.77%–7.08%, mean relative density = 6.92%), respectively, of both which include 100 cases with random probability distributions shown in Fig. 10.8, for examples. Other

![](bbox=[0.2184, 0.5635, 0.7805, 0.8335])

Figure 10.8 Schematic drawing of an FG porous three-layer beam.