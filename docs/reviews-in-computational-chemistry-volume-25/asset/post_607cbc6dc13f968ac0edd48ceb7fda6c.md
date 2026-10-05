
## 2 Determining the Glass Transition in Polymer Melts

contribution that computer simulations have made to our understanding of different aspects of the polymer glass transition, ranging from thermodynamic to dynamic properties. This part of the review will present our current understanding of glass transitions in polymeric melts based on simulation, experiment, and theory. We will illustrate this understanding based mainly on our own contributions to the field.

In the next section, a short summary of the phenomenology of the glass transition is presented. The following section on models explains the various types of models employed in the simulation of polymer melts, and the ensuing section on simulation methods introduces the algorithms used for such simulations. We will then describe simulation results relating to the thermophysical properties of the polymer glass transition. Finally, the main section of this review will present an overview of the slow-down of relaxation processes in polymer melts upon approaching the glass transition, and in the conclusions, we summarize what we have learned about how to identify the glass transition in polymer melts.

# PHENOMENOLOGY OF THE GLASS TRANSITION

The defining property of a structural glass transition is an increase of the structural relaxation time by more than 14 orders in magnitude without the development of any long-range ordered structure.¹ Both the static structure and the relaxation behavior of the static structure can be accessed by scattering experiments and can be calculated from simulations. The collective structure factor of a polymer melt, where one sums over all scattering centers M in the system

```
S(q) = \frac{1}{M} \sum_{i,j}^{M} (exp[i\vec{q} \cdot (\vec{r}_i - \vec{r}_j)])
```

resembles the structure factor of small molecule liquids (which we have given here a simplified version of neutron structure factor: all scattering lengths have been set to unity).

In Figure 1, we show an example of a melt structure factor taken from a molecular dynamics simulation (which will be described later). The figure shows a first peak (going from left to right), the so-called amorphous halo, which is a measure of the mean interparticle distance in the liquid (polymer melt). Upon lowering the temperature to the glass transition, the amorphous halo shifts to larger momentum transfers as the mean interparticle distance is reduced by thermal expansion. The amorphous halo also increases in height, which indicates smaller fluctuations of the mean interparticle distance, but no new structural features are introduced by this cooling.

# Phenomenology of the Glass Transition3

![](img/fa9d34afc1bcb785fd3792baa6c5c679_34_0.png)

The thermal expansion, however, changes at the glass transition, which is a phenomenon that was first analyzed in a careful study by Kovacs.⁴ In the polymer melt, the thermal expansion coefficient is almost constant, and it is again so in the glass with a smaller value. At the glass transition, there is therefore a break in the dependence of density on temperature that is the foremost thermophysical characteristic of the glass transition.

The decay of the structural correlations measured by the static structure factor can be studied by dynamic scattering techniques. From the simulations, the decay of structural correlations is determined most directly by calculating the coherent intermediate scattering function, which differs from Eq. [1] by a time shift in one of the particle positions as in Eq. [2]:

```
$S(q,t) = \sum_{L_j=1}^{M} \exp[i\vec{q} \cdot (\vec{r}_j(t) - \vec{r}_0(t))]$ [2]
```

The Fourier transform of this quantity, the dynamic structure factor $S(q,\omega)$, is measured directly by experiment. The structural relaxation time, or $\alpha$-relaxation time, of a liquid is generally defined as the time required for the intermediate coherent scattering function at the momentum transfer of the amorphous halo to decay about 30%; i.e., $S(q_{ah},\tau_{\alpha}) = 0.3$.

The temperature dependence of the $\alpha$ time scale exhibits a dramatic slowdown of the structural relaxation upon cooling. This temperature dependence qualitatively agrees with that of the melt viscosity.

# Determining the Glass Transition in Polymer Melts

![](img/fa9d34afc1bcb785fd3792baa6c5c679_35_0.png)

**Figure 2** Sketch of typical temperature dependencies of the viscosity η of glass-forming systems. The visimetric $T_g$ of a material is defined by the viscosity reaching $10^{13}$ Poise. Strong glass formers follow an Arrhenius temperature dependence, while fragile glass formers follow reasonably well a Vogel-Fulcher (VF) law predicting a diverging viscosity at temperature $T_0$.

This macroscopic measure of the relaxation time in the melt serves to define the so-called visimetric transition $T_g$ as the temperature at which the viscosity is $10^{13}$ Poise. This corresponds to a structural relaxation time of approximately 100 s. In Figure 2, we show three typical temperature dependencies of the viscosity in the form of an Angell plot.$5$ The upper curve is an Arrhenius law defining so-called “strong glass formers.” The other curves follow Vogel-Fulcher laws (Eq. [3]) observed for “fragile glass formers,” a category to which many polymeric systems belong, showing a diverging viscosity at some temperature $T_0 < T_g$. Around $T_g$, the relaxation time of fragile glassers increases sharply. The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition). The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to $T_g$ (similar to the behavior of the glass transition).

The definition of $T_g$ is based on the fact that the system falls out of equilibrium on experimental time scales. As a result of this out of equilibrium, one also observes a merged-out step in the heat capacity curve to$T_g$ (similar to the behavior of the glass transition).

Up to this point the characterization of the glass transition is the same for a polymer melt and for a molecular liquid. In a polymer melt, however, one must also know of both structure and the relaxation behavior of a single chain to characterize the system, be it in the melt or the glassy state. Flexible linear macromolecules in the melt adopt a random coil-like configuration; i.e., their square radius of gyration is given by$^{10-12}$ Eq. [4]:

```
$R_g^2 = \frac{C_{\infty}^2 N}{6}$$
```

where $N (N \gg 1)$ is the degree of polymerization and $\ell$ is the length of a segment. The characteristic ratio $C_{\infty}$ describes short-range orientational correlations among subsequent units along the backbone of the polymer chain, and $b = \sqrt{C_{\infty}}$ is the statistical length of the chain. On intermediate scales, the structure of a polymer coil is well described by the Debye function$^{10}$ Eq. [5]:

```
$S_p(q) = \frac{1}{N} \sum_{ij=1}^N (exp[i\vec{q} \cdot (\vec{r}_i - \vec{r}_j)]) = N f_D(q^2 R_g^2)$
```

```
$f_D(x) = \frac{2}{x^2} [\exp(-x) - 1 + x]$
```

where $qb < 1$ is for the momentum transfer and we set all scattering units to unity.

In the dense melt, chains interpenetrate each other. Thus, their diffusive motion is slow even at temperatures far above the glass transition. If the chain length $N$ is smaller than the "entanglement chain length" $N_e$, above which reptation-like behavior sets in$^{2-15}$ the relaxation time describing how long it takes a coil to renew its configuration is given by the Rouse time

```
$$\tau_R = \zeta(T)N^2C_{\infty}\ell^2/(3\pi^2k_BBT)$$
```

where $\zeta(T)$ is the friction coefficient experienced by the segments of the chain in their Brownian motion, $k_B$ is Boltzmann's constant, and $T$ is the temperature.
