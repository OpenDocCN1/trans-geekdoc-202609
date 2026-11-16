| L | W | Mean ± std | Max | L | W | Mean ± std | Max |
|---|---|---|---|---|---|---|---|
| 1.2l | 5d | 37.48 ± 19.0 | 106.21 | 2.2l | 5d | 29.76 ± 15.68 | 78.97 |
| | 10d | 5.06 ± 4.03 | 23.89 | | 10d | 3.75 ± 2.5 | 11.11 |
| | 20d | 3.62 ± 2.28 | 10.96 | | 20d | 1.75 ± 0.82 | 4.06 |
| L | W | Mean ± std | Max |
| 3.2l | 5d | 9.71 ± 5.52 | 27.73 |
| | 10d | 3.28 ± 1.68 | 8.55 |
| | 20d | 1.14 ± 0.51 | 3.05 |

Table 3.1: Mean, standard deviation, and maximum value of the relative error \(\epsilon_{\text{VE}}\) (3.53) in %, computed with ten realizations per combination of length factor \(l\) and width factor \(w\). Table adapted from Stür et al. (2023, Table 1).

# 3.4 Computational investigations

# 3.4.1 Spatial representation of the suspension viscosity through a scalar elongational viscosity

Böhlke and Brüggemann (2001) introduced a simple method to visualize an anisotropic stiffness tensor. We modify this approach to calculate the fiber polymer suspension's resistance to elongational flow in a particular direction via an elongational viscosity \(\eta_{\text{app}}\). In the general non-Newtonian case, we define a direction-dependent, elongational viscosity \(\eta_{\text{app}}\)

```
\(\eta_{\text{app}}(\dot{\gamma}, \mathbf{c}_{\text{F}}, \boldsymbol{d}) = \underline{a}(\boldsymbol{d})^{\mathsf{T}} \overline{\underline{\mathbb{V}}}(\dot{\gamma}, \mathbf{c}_{\text{F}}) \underline{a}(\boldsymbol{d}) \approx \mathbb{V}(\dot{\gamma}, \mathbf{c}_{\text{F}})\cdot(\boldsymbol{d} \otimes \boldsymbol{d} \otimes \boldsymbol{d} \otimes \boldsymbol{d}), \quad (3.54)\)
```

where \(\underline{a}(\boldsymbol{d})\) denotes the components of \(\boldsymbol{d} \otimes \boldsymbol{d}\) in Mandel notation, \(\boldsymbol{d}\) is the elongation direction, and the suspension viscosity \(\overline{\underline{\mathbb{V}}}(\dot{\gamma}, \mathbf{c}_{\text{F}})\) is calculated via equation (3.33) as an approximation of the true suspension viscosity tensor \(\mathbb{V}(\dot{\gamma}, \mathbf{c}_{\text{F}})\). Since the true suspension viscosity tensor \(\mathbb{V}\) has the minor and major symmetries, it is defined by 21 components. As a consequence, the suspension viscosity \(\overline{\underline{\mathbb{V}}}(\dot{\gamma}, \mathbf{c}_{\text{F}})\) can be completely described by a scalar elongational viscosity and a scalar dilatational