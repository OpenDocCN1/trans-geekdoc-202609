
# Entropy 147

with a much higher temperature $T_0$. This calculation can be done by performing an isothermal integration over a reversible path from the ideal gas state,

```
$S(T_0, \rho) = S^{ideal}(T_0, \rho) + \frac{E(T_0, \rho)}{T_0} + Nk_B \int_{0}^{\rho} \frac{P(T_0, \rho')}{\rho'^2 T_0} d\rho'$ [11]$
```

where $E(T_0, \rho)$ is the energy of the fluid at the reference state and $P(T_0, \rho)$ is the fluid pressure at density $\rho$ and reference temperature $T_0$. The exact expression for ideal gas contribution to the entropy $S^{ideal}$ is in analytical form. Moreover, both $E(T_0, \rho)$ and $P(T_0, \rho')$ can be computed using standard molecular simulation techniques for equilibrium fluids, such as Monte Carlo or molecular dynamics.$13-17}$ The data collected for $P(T_0, \rho')$ along the isotherm can then be fitted numerically to an analytical equation to facilitate the integration. A key issue to keep in mind is that the chosen reference temperature $T_0$ should be high enough to avoid crossing a liquid-gas phase boundary along the isothermal integration path.$23$ The total entropy $\mathcal{S}$ at any other temperature of interest $T$ is then obtained by thermodynamic integration

```
$S(T_0, \rho) = S(T_0, \rho) + \int_{T_0}^{T} \frac{dT'}{T'} \left( \frac{\partial E(T', \rho)}{\partial T'} \right)_{\rho}$ [12]$
```

where the derivative in the integrand is also typically obtained by fitting a series of temperature-dependent molecular simulation data to a simple analytical equation$^{101}$

At low temperature, however, prohibitively long equilibration and production simulations would be required if standard Monte Carlo and/or molecular dynamics algorithms were used to calculate the necessary thermodynamic properties. Here, one should invoke instead of the powerful simulation methods designed for equilibrating systems with large energy barriers (but not limited to) parallel threading,$105,$ the cluster pivot algorithm of Santen and Krauth,$104,$ the swap Monte Carlo algorithm by Grigera and Parisi,$105,$ and “density-of-states” algorithms$^{106-110}$ The comparative performance of these methods has been examined recently, and a discussion of the results can be found elsewhere.$111,112$ Alternatively, one can invoke an approximate scaling relation introduced earlier by Rosenfeld and Tarazona$^{113}$ to extrapolate high-temperature behavior down to the deeply super-cooled liquid region$^{22,101,114-116}$ in large part, because of its simplicity and its reasonable accuracy.

# Computing Free Volume, Structural Order

The next step when computing configurational entropy is to calculate the vibrational contribution to the entropy $S_{vib}$. The most commonly employed technique to accomplish this calculation is to assume that the configuration point of the liquid executes harmonic vibrations around its inherent structures (i.e., $S_{vib} \approx S_{harm}$), which is a description that can be expected to be accurate at low temperatures. The quantity $S_{harm}$ for a given basin is then computed as

```
$S_{harm} = k_B \sum_{i=1}^{3N-3} [1 - \log(h\omega_i/k_BT)]$ \eqno [13]
```

where $h$ is Planck's constant. The $\omega_i$ are the intra-vibrational eigenfrequencies, which are the square roots of the Hessian matrix$^{117}$ evaluated at the inherent structure of the basin. To complete this analysis, the right hand of Eq. [13] needs to be averaged over a representative set of inherent structures obtained from each equilibrium state. The inherent structure configurations are determined by mapping equilibrium configurations at the temperature and density of interest to their associated local potential minima using, e.g., a conjugate gradient algorithm or an alternative optimization route for large-scale problems (see, for example, Ref. 118). In practice, good statistics for this calculation can usually be obtained when using 1000 inherent structures per state.$^{23}$ A comparison of the properties of inherent structures recovered by different minimization routines has been published.$^{119}$

The harmonic approximation discussed above works well for liquids in their super-cooled state, but it is not sufficient for estimating $S_{vib}$ in the case of strong-forming liquids like water or silica.$^{91,92}$ For these fluids, anharmonic contribution $S_{anh}$ where $S_{vib} = S_{harm} + S_{anh}$ is important and is normally computed by calculating approximately the anharmonic part of the energy $E_{anh}$, where $E_{vib} = E_{harm} + E_{anh}$. The anharmonic contribution to the energy is determined by subtracting the average inherent structure energy $E_{IS}$ and the harmonic contributions, $E_{harm} = (3N-3)k_BT/2$. From the total energy $E_{tot} = E_{IS} - E_{anh}$ and then integrating the isothermal temperature derivative of $E_{anh}$, from $T=0$ to the temperature of interest as in Eq.[12]. In practice, the computed variation of $E_{anh}$ with temperature can be approximately fitted to a polynomial having both zero value and slope at $T=0.$^{91}$ This analysis implicitly assumes that the basin shapes on the PEL do not change acceptably with inherent structure energy (i.e., with basin "elevation"). Finally, the required configurational entropy is obtained by difference,

```
$S_C = S - S_{harm} - S_{anh}$ \eqno [14]
```

Examples of this type of calculation are reported in Ref. 91–94 and 101–102. We present below representative results for a few network-forming liquids that are known to display anomalous thermodynamic and dynamic behavior. 91,92

# TESTING THE ADAM–GIBBS RELATIONSHIP

One of the most convincing tests of the AG relationship appeared in the work of Scala et al.^92 for the SPC/E model of water,37 which is known to reproduce many of water’s distinctive properties in its super-cooled state qualitatively. In this study, the dynamical quantity used to correlate with the configurational entry was the self-diffusivity D. Scala et al. computed D via molecular dynamics simulations. The authors calculated the various contributions to the liquid entropy using the methods described above for a wide range of temperature and density [shown in Figure 12(a–c)].

![](img/fa9d34afc1bcb785fd3792baa6c5c679_180_0.png)

**Figure 12 (a–d)** The total liquid entropy $S$ (Eq. [12]), the vibrational entropy, $S_{vib} = S_{sharm} + S_{anth}$, the configurational entropy, $S_C \equiv S_{conf}$ (Eq. [14]), and diffusivity $D$ as a function of density for the SPC/E water model. The temperatures from top to bottom are $T = 300, 260, 240, 230, 220, 210 K. Reprinted with permission from Ref. 92.

# Computing Free Volume, Structural Order

![](img/fa9d34afc1bcb785fd3792baa6c5c679_181_0.png)

**Figure 13** Self-diffusivity $D$ versus configurational entropy, $S_C \equiv S_{conf}$, for the SPC/E water model at density $\rho$. The lines are fits to AG form given by Eq. [10] with $\tau_R \propto 1/D$. Reprinted with permission from Ref. 92.

The behavior of self-diffusivity for these state points is displayed in Figure 2(d). It is clearly visible that the non-monotonic dependence of $D$ on density $\rho$ is directly reflected by the configurational contribution to the entropy. In fact, the quantitative relationship between $D$ and $S_C$ predicted by Eq. [10] (i.e., the AG relationship) holds remarkably well for SPC/E water over this wide range of thermodynamic conditions, as is shown in Figure 13.

An investigation by Saika-Voyd, Poole, and Sciortino⁹⁹⁰ provides another convincing example of a network-forming liquid that obeys the AG relationship (in this case, silica using the BKS model¹²⁰⁰). Again, the authors compared the behavior of the temperature- and density-dependent self-diffusivity, which they computed via molecular dynamics simulations, to the entropy, obtained by the methods discussed earlier in this text. The BKS silica model represents a particularly interesting case because [text continues]... This type of fragile-to-strong transition for dynamics is discussed in more detail in Ref. 121. The AG relation holds again to a very good approximation as shown in Figure 14.
