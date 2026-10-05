
## 20 Determining the Glass Transition in Polymer Melts

![](img/fa9d34afc1bcb785fd3792baa6c5c679_51_0.png)

**Figure 5** The upper panel shows the logarithm of the specific volume as a function of temperature for a cooling rate $\Gamma = 52.083 \cdot 10^{-6}$, with error bars from 55 independent cooling runs. The lines are fits with a constant expansion coefficient in the melt (continuous line) and glass phase (dashed line), respectively. The lower panel shows the common fit curve for all cooling rates in the melt and fit in the glass for four cooling rates in the legend.

phenomenology of the glass transition. If one assumes that the break in the observed temperature dependencies occurs when the internal relaxation time is equal to the time scale of the cooling experiment $t_{exp}$, one obtains

```
$t_{exp} = \tau_{\infty} \exp\{E_A / (T_G(\Gamma) - T_0)\}$
```

[27]

## Thermodynamic Properties 21

In a stepwise cooling experiment, $t_{\exp}$ is equal to the time spent at every temperature step

```
$t_{\exp}(\Gamma) = \Delta T/\Gamma$
```

so that one obtains

```
$T_g(\Gamma) = T_0 - E_A/\ln(\Gamma \tau_{\infty}/\Delta T)$
```

Applying this prediction to the cooling rate dependence of a break points in the specific volume curves, one obtains a Vogel-Fulcher temperature of $T_0 = 0.35$ that agrees well with that determined from the temperature dependence of the diffusion constant in this model, which is $T_g^0 = 0.32$.

From these results obtained from MD simulations with a coarse-grained model, the following picture emerges. When one cools down a model system in a computer simulation, the break in the temperature dependence of the specific volume indicates the temperature at which the time scale of internal relaxation processes involved in volume relaxation equals the time scale of the cooling process. In strong formers, where the typical time scales at a high increase in an Arrhenius fashion with an activation energy that is much higher than for the fragile glass formers, this means that the system falls out of equilibrium on the time scales accessible in an MD simulation at temperatures that are much higher than the experimental glass transition temperature and that we obtain a very bad estimate for this temperature. For fragile formers, in contrast, the high-temperature increase of relaxation times is in general slow, thus often allowing the simulations to approach more closely to the experimental $T_g$ before falling out of equilibrium. As a result, glass transition temperatures can be in reasonable agreement with the experimental data. For polymers, where a higher temperature activation energy exists, arising from coupling to conformational rearrangements activated jumps over large dihedral barriers, for example, one anticipates the cooling method to be incapable of locating the experimentally relevant $T_g$ on typical simulation scales.

This reasoning means that we were not really describing a thermodynamic measurement of the glass transition in a polymer melt but instead a macroscopic determination of the temperature dependence of volume-related internal relaxation processes, i.e., a dynamic measurement in the disguise of a thermodynamic measurement.

Let us now turn to a discussion of the relation of the temperature dependence of the polymer melt's configurational entropy with its glass transition and address the famous paradox of the Kauzmann temperature of glass-forming systems.$^{90}$ It had been experimentally that the excess entropy of super-cooled liquids, compared with the crystalline state, seemed

## 22 Determining the Glass Transition in Polymer Melts

vanish when extrapolated to low temperatures. The extrapolated temperature of vanishing excess entropy, the so-called Kaumann temperature $T_K$, is generally in close agreement with the extrapolated Vogel-Fischer temperature $T_0$ derived from the temperature dependence of relaxation times. A theoretical derivation of the Kaumann temperature for polymeric glass formers was given by Gibbs and Di Marzo.$^{91}$ Consider the canonical partition function of K polymers of chain length N in a volume V,

```
$Z = \sum_{E} \Omega(E, K, N, V) \exp(-E/k_BT)$ [30]
```

with $E$ being the internal energy of the system and $\Omega$ the microcanonical partition function (i.e., the total number of sites). For simplicity, a lattice with M sites is considered with

```
$M = \frac{L^3}{8} = (KN + H)$ [31]
```

with $H$ being the number of vacant sites (holes). Equation [31] is valid for a simulation of the glass transition in the bond-fluctuation lattice model where each repeat unit occupies the lattice vertices of a unit cube. The glass transition in this model was studied by employing a Hamiltonian that singled out the bounds of the class, [3,0,0] giving them zero energy$^{92}$

```
$$\mathcal{H} = \begin{cases} 0 & \text{if } \epsilon \in [3,0,0] \\ \epsilon & \text{otherwise} \end{cases} [32]
```

The entropy density $s$ is then

```
$s = (ln \Omega)/M$ [33]
```

In the thermodynamic limit $M \rightarrow \infty$, one can consider $s = s(e, \rho)$, where $e = E/M$ is the internal energy per site and $\rho = KN/M$ is the monomer density. We can do this as a function of temperature because $e$ can be replaced by $T$ via the appropriate Legendre transformation.

Variants of an approximate calculation of the configurational entropy of lattice chains have been developed by Flory,$^{93}$ Gibbs and Di Marzo,$^{91}$ and Milchev.$^{94}$ All three treat it as a product of an intrachain $(\Omega_{intra})$ contribution and an interchain $(\Omega_{inter})$ contribution

```
$$\Omega = \Omega_{intra}\Omega_{inter}$ [34]
```

In Flory's original treatment, $\Omega_{intra}$ accounts for the increase of the chain stiffness when the temperature is lowered. Flory$^{93}$ described this chain stiffening by

## Thermodynamic Properties 23

an energy $\varepsilon$ if two consecutive bonds along a chain are not collinear, whereas no energy is assigned if they are collinear. In essence, this calculation relies on the fact that one has a two-level system for the internal degrees of freedom as was realized in the choice of Hamiltonian in, Eq. [32].

If we denote by $f$ the probability of finding a bond in the excited state, we get for the intramolecular part of the partition function, neglecting volume effects by assuming a nonversal random walk, Eq. [35].

```
$\Omega_{\text{intra}} = \left(\frac{K(N-1)}{f(N-1)}\right)\left(\frac{1}{z}\right)^{(1-f)/K(N-1)}\left(\frac{z-2}{z-1}\right)^{K(N-1)} \quad [35]$
```

where $z$ is an effective coordination number. The last term in this equation is obviously correct for the original Flory model where $z-1$ possibly exist for the next bond, one of which is straight and does not carry energy penalty. For the bond-fluctuation model with the Hamiltonian given by Eq. [32], in 12 bonds does not carry energy penalty. Furthermore, the effective coordination number in the melt is around 12, so again one can assume that one of the $z-1$ neighbor bonds is in the ground state.

The treatments of Flory,$^{93}$ Gibbs and Di Marzo, and Milchev$^{94}$ differ in how they calculate the second factor $\Omega_{\text{inter}}$. This microcanonical partition function describes the number of ways in which the $K$ chains can be put on the lattice,

```
$\Omega_{\text{inter}} = 2^{-K}(1/K!) \prod_{k=0}^{K-1} v_{k+1} \quad [36]$
```

with $v_{k+1}$ being the total number of configurations of the $(k+1)$th chain if there are already $k$ chains on the lattice that can be approximated by

```
$v_{k+1} \approx (M-K)N_{\text{empty}}^{N-1}z(z-1)^{N-2} \quad [37]$
```

Here, $M$ is the number of empty sites after $K$ chains have been placed on the lattice and constitutes the number of potential starting points for the $(k+1)$th chain. The factor $z(z-1)^{N-2}$ represents the number of possibilities to place the remaining $N-1$ monomers of the chain after the first monomer has been placed, forbidding only the immediate back-folding of the walk. The factor $N_{\text{empty}}^{N-1}$ for which the bond-fluctuation model counts the number of empty unit, accounts approximately for the chains being self-avoiding and mutually avoiding as in the three approaches as in Eqs. [38]–[40]:

```
$N_{\text{empty}} = 1 - kN/M \quad (Flory) \quad [38]$
```
