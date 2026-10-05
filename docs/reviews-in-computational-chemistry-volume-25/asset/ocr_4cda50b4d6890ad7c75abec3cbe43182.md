# Magnetic Properties of Atomic Clusters of the Transition Elements

Wan and coworkers$^{48}$ studied the magnetic moments of Ni clusters, taking into account both spin and orbital effects. Wan et al.$^{48}$ used the following TB Hamiltonian

```
$H = \sum_{i\sigma} c_{i\sigma}^{\dagger} C_{i\sigma}^{0+} c_{i\sigma} + \sum_{ij} \sum_{LL L'} c_{i\sigma}^{\dagger} C_{i\sigma}^{L'L+} c_{j\sigma'} + H_{SO} + H_{ee}$\n\n+ \sum_{i} c_{i\sigma}^{\dagger} \Delta_{i\sigma}(n_{i'}) C_{i\sigma}^{0+} c_{i\sigma'} + c_{i\sigma'}^{\dagger} (Z_{l'}) (c_{i\sigma}^{\dagger} c_{i\sigma'} + c_{i\sigma'}^{\dagger} c_{i\sigma})\n\n+ \sum_{iL\sigma} \Delta_{i\sigma}(n_{i'}) (c_{i\sigma}^{\dagger} C_{i\sigma}^L c_{i\sigma} + c_{i\sigma'}^{\dagger} C_{i\sigma'}^L) [57]$
```

where the meaning of the different symbols is as described in the section of the TB method. $L = (l, m)$ indicates the orbital angular momentum quantum numbers. There are some differences with the Hamiltonian in Eqs. [15] and [16]. The first two terms in Eq. [57] are already included in Eq. [15]. [15]. The term $H_{SO}$ is the spin-coupling operator in the usual intra-atomic approximation,

```
$H_{SO} = \xi \sum_{i,L\sigma,\sigma'} (L\sigma | \bar{L}_i | L'\sigma') c_{i\sigma}^{\dagger} C_{i\sigma'}^{L'L}[58]$
```

where $\xi$ gives the strength of the interaction ($\xi = 0.073$ for $d$ orbitals). The term $H_{ee}$, is to be discussed below, is an intraatomic $d$-$d$ electron-electron interaction. The final two terms in Eq. [57] apply specifically to the surface atoms of the cluster, labeled by the subscripts $l'$. To take into account the electronic spillover over the surface,$^{51}$ an extra orbital, labeled $s'$, is attached to each surface atom $l$.
The intraatomic $d$-$d$ electron-electron interaction includes Coulomb and exchange interactions, and is responsible for orbital and spin polarization. To account for orbital polarization, the idea of the LDA $+U$ method was followed.$^{70}$ A generalized Hartree-Fock approximation including all possible pairings were used to write

```
$H_{ee} = \sum_{i,L\sigma,L'\sigma'} V_{L\sigma,L'\sigma'} c_{i\sigma}^{\dagger} C_{i\sigma'}^{L'L}[59]$
```

where

```
$V_{L\sigma,L'\sigma'} = \sum_{L_2L_3} (\{U_{LL_2L_2L_3} n_{i,L_2,L_3,i\sigma} + (U_{LL_2L_3L'} - U_{L_2L_3L_2L_3}) n_{i,L_2,L_3,i\sigma}) \delta_{\sigma\sigma'}\n- U_{LL_2L_3L'} n_{i,L_2,L_3,i\sigma'} \delta_{LL'}\delta_{\sigma\sigma'} - U(n_i - 0.5) \delta_{LL'}\delta_{\sigma\sigma'} + J(n_{i\sigma} - 0.5) \delta_{LL'}\delta_{\sigma\sigma'} [60]$
```