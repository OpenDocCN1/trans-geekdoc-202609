
# Atomistic Modeling of Condensed-Phase Reactions 175

![](img/fa9d34afc1bcb785fd3792baa6c5c679_206_0.png)

**9** Diffusion constant for O and H atoms at 2000 K as a function of density. The lines with circles correspond to hydrogen and the lines with squares to oxygen. The solid lines correspond to a liquid (‘L’) initial configuration and the dashed lines to ice VII (‘S’) initial configuration. The inset plot shows the pressure as a function of density at 2000 K, where the triangles correspond to ‘L’ and the Xs to ‘S.’

$10^{-4}$ cm²/s. The diffusion constant remains relatively constant with increasing density, quantitative agreement with the experimental results of Chau et al.$^{72}$ for the ionic conductivity.

In contrast, the diffusion constant drops to zero at 75 GPa (2.6 g/cc) for both ‘L’ and ‘S’ initial configurations. The surprisingly massive hysteresis in the fluid to superionic transition allows us to place the transition point between 70 GPa (2.5 g/cc) and 77 GPa (2.6 g/cc). The small hysteresis most likely caused by the weak O-H bonds at the conditions studied, which have free energy barriers to dissociation with $k_BT$ (see below). Simulations that start from the ‘L’ initial configurations are found to quench to an amorphous solid upon compression to 26 g/cc.

The transition of 75 GPa is much higher than the 30 GPa predicted earlier.$^{65}$ This difference is likely caused by the use of a much smaller basis set (Ry) by Cavazzoni et al. Our results are in disagreement with simple extrapolations of the proton diffusion constant to high temperatures.$^{77}$ Radial distribution functions (RDFs) for the ‘S’ simulations are shown in Figure 10. Analysis of the oxygen–oxygen RDF (not shown) for all over 14 for the first peak, which yields a coordination number of just 12 in high-density bcc lattice in which the first two peaks are broadened by thermal fluctuations. The RDF can be further analyzed by calculating an “average position” RDF in which the position of each oxygen is averaged over the course of the trajectory. The results for

# 176 The Reactivity of Energetic Materials at Extreme Conditions

![](img/fa9d34afc1bcb785fd3792baa6c5c679_207_0.png)

Figure 10 O–H radial distribution function as a function of density at 2000K. At 34 GPa, we find a fluid state. At 75 GPa, we show a “covalent” solid phase. At 115 GPa, we find a “network” phase with symmetric hydrogen bonding. Graphs are offset by 0.5 for clarity.

75–115 GPa indicate the presence of a bcc lattice undergoing large amplitude vibrations, even though RDF in Figure 10 has width similar to that of a liquid or a gas. The RDFs for the amorphous phase (not shown) are similar to those of the solid phase obtained in the “S” simulations.

The O-O and H-H RDFs (not shown) indicate that no O-O or H-H covalent bonds are formed during the simulations at all densities. $g(R_{OH})$ shows a lattice-like structure at 115 GPa, which is consistent with proton diffusion via a hopping mechanism between lattice sites.³⁶ At 34 GPa, the coordination number for the first peak in $g(R_{OH})$ is 2, which indicates molecular H₂O. Between 95 GPa and 115 GPa, however, the coordination number for the first peak in $g(R_{OH})$ becomes four, indicating that water has formed symmetric hydrogen bonds where each oxygen has four nearest-neighbor hydrogens.

Concomitant with a shift of the first minimum of the O–H RDF from 1.30 Å at 34 GPa to 1.70 Å at 115 GPa, we observe a similar structural change in the H-H RDF in which the first peak lengthens from 1.63 Å (close to the result for ambient conditions) to 1.85 Å. These observations bear a strong resemblance to the ice VII to ice X transition in which the covalent O–H bond distance of ice becomes equivalent to the hydrogen bond distance as pressure is increased.³⁸² However, the superionic phase differs from ice X, in that the position of the first peak in $g(R_{OH})$ is not half the distance of the first O–O peak.⁸² We analyze the effect

# Atomistic Modeling of Condensed-Phase Reactions 177

![](img/fa9d34afc1bcb785fd3792baa6c5c679_208_0.png)

Figure 11 $RO_{OH}$ free energy surface at 2000 K. The lines are spaced by a factor of 4 kcal/mol for clarity.

the change in $g(R_{OH})$ below in terms of the molecular speciation in the simulations.

We determined the free energy barrier for dissociation by defining a free energy surface for the oxygen-hydrogen distances, viz. $W(r) = -k_BT \ln [g(R_{OH})]$, where $W(r)$ is the free energy surface (potential of mean force). The results are shown in Figure 11.

The free energy barrier can then be defined as the difference between the first minimum and the second maximum in the free energy surface. The free energy barrier is 11 kcal/mol at 34 GPa and 8 kcal/mol at 115 GPa. The remainder of the results discussed below are for the "S" simulations.

We now analyze the chemical species prevalent in water at these extreme conditions by defining instantaneous species on the O-H bond direction. If distance is not a cut-off value $r_c$ we count the atom pair as being bonded. Determining all bonds in the system gives chemical species at each point in time. Species with lifetimes less than an O-H vibrational period (10 fs) are "transient" and do not represent bonded molecules. The optimal cut-off $r_c$ between bonded and nonbonded species is given by the location of the maximum in the free energy surface.⁸³

Using the free energy maximum to define a bond cut-off provides a clear picture of qualitative trends. As expected from a $g(R_{OH})$, at 34 GPa, the free energy peak is found at 1.30 Å, which is approximately the same value obtained from simulations of ambient water. At 75 GPa, the free energy peak maintains almost the same position but broadens. At 115 GPa, the free energy peak has sharpened again, and the maximum is now 1.70 Å.

# 178 The Reactivity of Energetic Materials at Extreme Conditions

![](img/fa9d34afc1bcb785fd3792baa6c5c679_209_0.png)

**12** Mole fraction of $H_3O^+$ and $OH^-$ at 34–115 GPa and 2000 K. The filled circles correspond to $H_3O^+$ whereas the open circles correspond to $OH^-$.

Given the definition of a bond, we can analyze lifetimes. Quantum mechanical methods can now be applied to systems up to 1000 atoms⁸⁷ this capacity is not only from advances in computer technology but also from improvements in algorithms. Recent developments in reactive classical force fields promise to allow the study of significantly larger systems⁸⁸ Many approximations can also be made to a variety of methods, each of which can address a range of questions based on the inherent accuracy of the method chosen. We now discuss a range of quantum mechanical-based methods that one can use to answer specific questions regarding shock-induced detonation conditions.

Atomistic simulations have been performed on condensed-phase HMX, which is a material that is widely used as an ingredient in various explosives and propellants. A molecular solid at standard state, it has four known

# 179 First Principles Simulations of High Explosives

![](img/fa9d34afc1bcb785fd3792baa6c5c679_210_0.png)

**Figure 13** Snapshots of the simulations at 75 GPa (left) and 115 GPa (right). The temperature for both is 2000 K. At 75 GPa, the water molecules are starting to cluster, and at 115 GPa, a well-defined network has been formed.
