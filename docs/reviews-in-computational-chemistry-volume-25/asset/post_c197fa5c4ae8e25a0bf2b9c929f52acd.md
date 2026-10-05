
## Dynamics in 1,4-Polybutadiene 41

performed MD simulations of cis-1,4-polybutadiene$^{143,144}$ to identify candidates for jump motions in asymmetric double-well potentials. The idea of jumps in double-well potentials had been used earlier to explain quasi-elastic neutron scattering (QENS)$^{145,146}$ on PB. A detailed analysis of mode-coupling connections was performed by Zon and de Leew for a PB-like model$^{147}$ and a PE-like model$^{148}$ and by Lylin et al.$^{149-151}$ for polystyrene. The work by Zon and de Leew, no quantitative comparison with experimental data was possible because of the limits of the force field quality and the short runs performed. In the work of Lylin et al., the simulations extended to several tens of nanoseconds, but there too no quantitative comparison was made with the experiment.

In the works of Lylin et al. and of Zon and de Leew, MCT was to provide a consistent description of the coherent as incoherent scattering functions over a temperature range between $T_c$ and $1.2T_c$. The value of the critical temperature Zon and de Leew obtained for PB was $T_c \sim 162K$, which is about 50 K below the experimental value. Their conclusions agree with those derived for the bead-spring model. The relaxation in polymers is more stretched than in the bead-spring model. This stretching results in a smaller value of the von Schweidler de-coupling exponent ($b=0.46$ for the PE-like model vs. $b=0.75$ for the bead-spring model) as well as for the KWW stretching exponent ($\beta \sim 0.4$ for the PE-like model vs. $\beta \sim \infty$), which are intercalated by the MCT prediction $\beta_q \to b$ for $q \to \infty$. The result for the KWW event for the chemically realistic simulation agrees with typical values in neutron scattering or dielectric experiments. In contrast, the result for the bead-spring model is much larger.

We therefore conclude that differences between bead-spring and chemically realistic models can be attributed to either the differences in packing that we discussed above or the presence of barriers in the dihedral potential in atomic models. To quantify the role of dihedral in polymer melt dynamics, we examine high-temperature relaxation in polymer melts.

There has been extensive effort in recent years to use coordinated experimental and simulation studies of polymer melts to understand the connection between polymer motion and conformational dynamics. Although no experimental method directly measures conformational dynamics, several experimental probes of molecular motion are spatially local or sensitive to local motions. Coordinated simulation and experimental studies of local motion in polymers have been conducted for dielectric relaxation$^{152-158}$ dynamic neutron scattering,$^{157,159-164}$ and NMR spin-lattice relaxation.$17,152,165-168}$ A particularly important outcome of these studies is the improved understanding of the relationship between the probed motions of the polymer chains and the underlying conformational dynamics that leads to observed motions. In the following discussion, we will focus on the information obtained from NMR experiments that have been used to probe local reorientational motion.

## 42 Determining the Glass Transition in Polymer Melts

NMR $^{13}$C spin-lattice relaxation times are sensitive to the reorientational dynamics of $^{13}$C-H vectors. The motion of the attached proton(s) causes fluctuations in the magnetic field at the $^{13}$C nuclei, which results in decay of their magnetization. Although the time scale for the experimentally measured decay of a magnetization of a $^{13}$C nucleus in a polymer melt is typically on the order of seconds, the corresponding decay of the $^{13}$C-H vector autocorrelation function is on the order of nanoseconds, and hence, is amenable to simulation.

The spin-lattice relaxation time $T_1$ can be determined from simulation by using the relationship $^{169}$ of Eq. [70]

$$\frac{1}{nT_1} = K(\omega_H - \omega_C) + 3J(\omega_C) + 6J(\omega_H + \omega_C) [70]$$

where $J(\omega)$ is the spectral density as angular frequency by

$$J(\omega) = \frac{1}{2} \int_{-\infty}^{\infty} P_2(t) \exp\{i\omega t\} [71]$$

Here $n$ is the number of attached protons on a carbon atom and $\omega_H$ and $\omega_C$ resonance frequencies. The constant $K$ assumes an autocorrelation decay of $2.29 \times 10^9$ $s^{-2}$ and $2.42 \times 10^9$ $s^{-2}$ for $sp^3$ and $sp^2$ nuclei, respectively. The orientational autocorrelation function is obtained from the simulation trajectory using the relationship

$$P_2(t) = \frac{1}{2}[||\hat{e}_{CH}(t) \cdot \hat{e}_{CH}(0)||^2] - 1] [72]$$

where $\hat{e}_{CH}(t)$ is the unit vector along a C–H bond at time $t$. Equation [72] is an ensemble average over all carbon atoms with the same chemical environment. Experimentally, $T_1$ values can be determined for $^{13}$C nuclei in various environments because of the different chemical shifts of these nuclei (the resonances one can distinguish in a cis-trans copolymer of polybutadiene are shown in Figure 15).

The chemically realistic simulations we are discussing have been performed using a united atom representation of PB, which leads to the question: How does one actually measure a CH vector reorientation for such a model? The answer to this question is to use the trick discussed in the analysis of the pressure dependence of the melt structure factor of PB. Hydrogen atoms are placed on the backbone carbons by their mechanical equilibrium positions for each structure that has been sampled along the MD trajectory. The CH vector dynamics are shown in Figure 16 is solely from the backbone reorientations of the chain.

![](img/fa9d34afc1bcb785fd3792baa6c5c679_74_0.png)

**Figure 15** Sketch of the local environment along a polybutadiene chain of cis-and-trans conformers. For sp³-hybridized carbon atoms (indicated by the gray spheres), the chemical shift is different when they belong to a cis-monomer than they belong to a trans-monomer. For sp²-hybridized carbon atoms (shown by black spheres) in a cis-monomer, NMR shows a different chemical shift whether they belong to another cis-monomer as a neighbor or a trans-monomer.

## Dynamics in 1,4-Polybutadiene 43

We can see that the different positions along the chain show temperature-dependent relaxation curves. To further analyze these relaxation functions, we may Fourier transform to determine their spectral density, which is best done by

![](img/fa9d34afc1bcb785fd3792baa6c5c679_74_1.png)

**Figure 16** Second Legendre polynomial of the CH vector autocorrelation function for sp³-carbon (dashed lines) and the sp² carbon in a trans-group (dashed-dotted lines) for two different temperatures.

![](img/fa9d34afc1bcb785fd3792baa6c5c679_75_0.png)

**Figure 17** Spin-lattice relaxation times for six resonances along a chain. Trans and cis denote sp³ hybridized carbons in the respective monomer, trans-trans, trans-cis, cis-cis, and cis-trans. They denote sp² hybridized carbons in a trans-group with a trans-group as neighbor, a trans-group with a cis-group as neighbor, and so on. Open bars are for simulation, and filled ones for experiment. Values are shown for 273 K (short bars) and 400 K (longer bars).

enables us to extrapolate to “infinite” time. For this process, we fit the data to the fully superposition of exponential and stretched decay

$P_2(t) = Ae^{-t/\tau_1} + (1-A)e^{-(t/\tau_2)^\beta}$ [73]

As can see in Figure 16, where two fit are included, our ansatz for $P_2(t)$ describe the data well, except for the sub-picosecond vibrationally, however, has a negligible contribution to the spin-lattice relaxation time. From this information, we can then calculate the $T_1$ times for different positions along the chain.

For PB, comparison of $^{13}C$ NMR spin-lattice relaxation times and nuclear enhancement (NOE) values from simulation and experiment over a wide range of melt temperatures revealed excellent agreement.$^{168}$ A comparison between simulation and experiment for two temperatures for different resonances is shown in Figure 17. Comparing the variation in $T_1$ for carbon atoms in different chemical environments with the mean waiting time between conformational transitions for the different types of torsions in PB ($\beta$, cis-allyl and trans-allyl), one concludes that spin-lattice relaxation for a given nucleus cannot be associated with the dynamics of any particular rotation. Instead, the $^{13}C$ relaxation occurs as the result of multiple conformational events involving several neighboring torsions.$^{168}$ However, close correspondence was found for torsional autocorrelation times $\tau_{\text{tor}}$.
