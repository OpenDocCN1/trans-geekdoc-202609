
# The Reactivity of Energetic Materials at Extreme Conditions

In addition to the intermolecular potential, there is an intramolecular portion of the Helmholtz free energy. Cheetah uses a polyatomic model to account for this portion including electronic, vibrational, and rotational states. Such a model can be expressed conveniently in terms of the heat of formation, standard entropy, and constant-pressure heat capacity of each species.

We now consider how the EOS described above predicts the detonation behavior of condensed explosives. The overdriven shock Hugoniot of an explosive is an appropriate EOS test, because it accesses a wide range of high pressures. Overdriven states lie on the shock Hugoniot at pressures above the C–J point (see Figure 2). The Fried, Howard and Souers^{40} have calculated the Hugoniot of penta-erythritol tetranitrate (PETN) is shown in Figure 3. Fried with the exp-6 model and the JCZS¹ product library. Figure 3 shows that the exp-6 model lies within 1% of the measured data for pressures up to 120 GPa (1.2 Mbar). The JCZS model is accurate to within 1% up to a pressure of 90 GPa, but the exp-6 model is not calibrated to condensed explosives, which agreement is a disagreement with experiment at 120 GPa. This is a strong indicator of the validity of the chemical equilibrium approximation to detonation.

Despite the many successes in the thermochemical modeling of energetic materials, several significant limitations exist. One such limitation is that real systems do not always obtain chemical equilibrium during the relatively short (nanoseconds-microseconds) time scales of detonation. When this occurs, quantities such as energy of detonation and the detonation velocity are commonly predicted to be 10–20% higher than experiment by a thermochemical calculation.

![](img/fa9d34afc1bcb785fd3792baa6c5c679_197_0.png)

Figure 3 The shock Hugoniot of PETN as calculated with exp-6 (solid line) and the JCZS library (dotted line) vs. experiment (error bars).

# Chemical Equilibrium 167

Chemical kinetic modeling is another way to treat detonation. Several well-developed chemical kinetic mechanisms exist for highly studied materials such as hexahydro-1,3,5-trinitrito-1,3,5-s-triazine (RDX) and 1,3,5,7-tetrannitro-1,3,5,7-tetrazayocyclooctane (HMX).⁴² Unfortunately, detailed chemical kinetic mechanisms are not available for high-pressure conditions. Some workers have applied chemical kinetics to detonation processes.¹⁶ The primary difficulty in high-pressure chemical kinetic models is a lack of experimental data on speciation. First principles simulations, discussed below, have the potential to provide chemical kinetic information for fast processes. This information could then conceivably be applied to longer time scales and lower temperatures using high-pressure chemical kinetics.

The possible occurrence of ionized species as detonation products is a further complication that cannot be modeled using the exp-6 representation alone. Recent results on the supersonic behavior of water at high pressures (see discussion below) provide compelling evidence for a high-pressure ionization scenario. These results suggest, for example, that polar and ionic species account for approximately 10% of the (C–J) pressure of PETN. In addition, we note that thermochemical calculations of high explosive formulations—such as F and Cl—typically have substantially higher errors than calculations performed on formulations containing only elements H, C, N, and O. The difficulty in modeling the C–J states of these formations successfully may be from the regime of ionic species.

Bastea, Glasemann, and Fried⁴³ have extended the exp-6 free energy approach to include the explicit thermodynamic contributions arising from dipolar and ionic interactions. The main task of their theory involves calculating the Helmholtz free energy (per particle) of the detonation products—. The theory starts with a mixture of molecular species whose short-range interactions are well described by isotropic, exp-6 potentials. This mixture includes, for example, all molecules commonly encountered as detonation products, such as N₂, H₂O, CO₂, CO, NH₃ and CH₄. As documented previously⁴⁴ a one-fluid representation of this system, where one replaces the different exp-6 interactions between species by a single interaction dependent on both individual interactions and mixture composition, is a very good approximation. Bastea, Glasemann, and Fried therefore, chose this nonpolar and neutral one-component exp-6 fluid to be the reference fluid. If the mixture components possess no charge or permanent dipole moments, the calculation of the corresponding free energy per particle, designated as $f_{exp}-6$, suffices to yield the mixture thermodynamics and all desired detonation properties. This physical model has been used in many thermochemical codes for the calculation of high explosives behavior.

It is worth that at detonation pressures and temperatures the behavior of the exp-6 fluid introduced is dominated by short-range repulsions and is similar to that of a hard repulsive sphere fluid. The variational theory treatment$^{45}$ of the exp-6 thermodynamics employs a reference hard sphere system with an effective, optimal diameter $\sigma_{eff}$ that depends on density and temperature. Bastea, Glasemann, and Pured have shown this connection to the hard sphere fluid by considering first a fluid of equalized hard spheres of diameter $\sigma$ with dipole moments $\mu$. For this simple model of a polar liquid, Stell et al.$^{46,47}$ had previously suggested a Padé approximation for calculating the free energy $f_d$,

$$f_d = f_0 + \Delta f_d$$

$$Delta f_d = \frac{f_2}{1 - f_3/f_2}$$

where $f_0$ corresponds to the simple hard sphere fluid and $f_2$ and $f_3$ are terms (second and third order, respectively) of the perturbation expansion in the dipole-dipole interaction $(\sim \mu^2)$ such that

$$f_d = f_0 + f_2 + f_3 + \dots$$

The first order term $f_1$ can be shown to be identically zero, whereas $f_2$ and $f_3$ have been calculated explicitly.$^{46}$ The resulting thermodynamics can be written in scaled variables as

$$\Delta f_d = \Delta f_d(\rho^*, \beta_d^*)$$

$$\rho^* = \rho\sigma^3$$
$$\beta_d^* = \frac{\mu^2}{k_B T\sigma^3}$$

where $\rho$ is the (number) density and $T$ is the temperature. The same Padé approximation also holds for a mixture of identical hard spheres with different dipole moments $\mu_i^{48,49}$ We note that within this approximation, it is easy to show that the mixture thermodynamics is equivalent to that of a simple hard spheres polar fluid with an effective dipole moment $\mu$ given by

$$\mu^2 = \sum_i x_i\mu_i^2$$

where $x_i = \rho_i/\rho$ is the concentration of particles with dipole moment $\mu_i$.

# Chemical Equilibrium 169

![](img/fa9d34afc1bcb785fd3792baa6c5c679_200_0.png)

**Figure 4** Comparison of pressure results for a model of polar water at $T = 2000$ K: MD simulations (symbols), newly developed theory for polar fluids (lower line) and exp-6 calculations alone (upper line).

We adopt the above combination rule (Eq. [6]) for the general case of exp-6 mixtures that include polar species. Moreover, in this case, we calculate the polar free energy contribution $\Delta f_d$ using the effective hard sphere diameter $\sigma_{eff}$ of the variational theory.

We show a comparison of this procedure with MD simulation results for an exp-6 model of polar water in Figures 4 and 5. Also shown are

![](img/fa9d34afc1bcb785fd3792baa6c5c679_200_1.png)

**Figure 5** Same as Figure 4 for energy.

# 170 The Reactivity of Energetic Materials at Extreme Conditions

exp-6 thermodynamics alone. For both the pressure and the energy, the agreement is very good.

The thermodynamic theory for exp-6 mixtures of polar materials is now implemented in the thermochemical code Cheetah.${52}$ We considered first the major detonation products H₂O, NH₃, CO and HF. The optimal exp-6 parameters and dipole moment values for these species were determined by fitting to a variety of available experimental data. We find, for example, that a dipole moment of 2.2 Debye reproduces very well all available experiments. Incidentally, this value is in very good agreement with values typically used to model supercritical water.${50}$

A comparison of our Cheetah water model predictions with both high-pressure Hugoniot data,$51}$ and low-density (steam at 800 K) experimental data$^{52}$ is presented in Figure 6. The agreement is very good for both calculations of detonation properties. The newly developed equation of state was applied to the calculation of equation of state is the prediction of detonation velocities as a function of initial densities, and we chose for this purpose PETN. The Cheetah results are shown in Figure 7 along with the experimental data.${53}$ The agreement is very good.

Advances in the treatment of detonation mixtures that include explicit polar and ionic contributions. The new formalism places on a solid footing the modeling of polar species, opens the possibility of realistic fluid phase chemical equilibrium calculations (polar—nonpolar phase segregation), extends the validity domain of the EXP6 library,$40}$ and opens the possibility of applications in a wider regime of pressures and temperatures.

![](img/fa9d34afc1bcb785fd3792baa6c5c679_201_0.png)

**Figure 6** Comparison of theory for polar water: experimental data (Hugoniot—circles and steam at $T = 800	ext{ K}$—diamonds) and theory (lines).
