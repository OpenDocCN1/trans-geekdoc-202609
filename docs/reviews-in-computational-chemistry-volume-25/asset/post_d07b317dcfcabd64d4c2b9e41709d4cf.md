
## Magnetic Properties of Atomic Clusters of the Transition Elements

Wan and coworkers$^{48}$ studied the magnetic moments of Ni clusters, taking into account both spin and orbital effects. Wan et al.$^{48}$ used the following TB Hamiltonian

```
$H = \sum_{i\sigma} c_{i\sigma}^{\dagger} C_{i\sigma}^{0+} c_{i\sigma} + \sum_{ij} \sum_{LL L'} c_{i\sigma}^{\dagger} C_{i\sigma}^{L'L+} c_{j\sigma'} + H_{SO} + H_{ee}$

+ \sum_{i} c_{i\sigma}^{\dagger} \Delta_{i\sigma}(n_{i'}) C_{i\sigma}^{0+} c_{i\sigma'} + c_{i\sigma'}^{\dagger} (Z_{l'}) (c_{i\sigma}^{\dagger} c_{i\sigma'} + c_{i\sigma'}^{\dagger} c_{i\sigma})$

+ \sum_{iL\sigma} \Delta_{i\sigma}(n_{i'}) (c_{i\sigma}^{\dagger} C_{i\sigma}^L c_{i\sigma} + c_{i\sigma'}^{\dagger} C_{i\sigma'}^L) [57]$
```

where the meaning of the different symbols is as described in the section of the TB method. $L = (l, m)$ indicates the orbital angular momentum quantum numbers. There are some differences with the Hamiltonian in Eqs. [15] and [16]. The first two terms in Eq. [57] are already included in Eq. [15]. The term $H_{SO}$ is the spin-coupling operator in the usual intra-atomic approximation,

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
$V_{L\sigma,L'\sigma'} = \sum_{L_2L_3} (\{U_{LL_2L_2L_3} n_{i,L_2,L_3,i\sigma} + (U_{LL_2L_3L'} - U_{L_2L_3L_2L_3}) n_{i,L_2,L_3,i\sigma}) \delta_{\sigma\sigma'}$
- U_{LL_2L_3L'} n_{i,L_2,L_3,i\sigma'} \delta_{LL'}\delta_{\sigma\sigma'} - U(n_i - 0.5) \delta_{LL'}\delta_{\sigma\sigma'} + J(n_{i\sigma} - 0.5) \delta_{LL'}\delta_{\sigma\sigma'} [60]$
```

## Measurement and Interpretation of the Magnetic Moments

In this expression, $n_{i,L,\sigma,\sigma'} = \langle c_{i,L,\sigma}^{\dagger}c_{i,L,\sigma'}\rangle$ is the single-site density matrix, $n_{i\sigma}$ is the trace of $n_{i,L,\sigma,\sigma'}$, $\sigma=-\sigma'$, and $n_i = \sum_{\sigma} n_{\sigma}$. The matrix elements $U_{LL_2L'L_3}$ can be determined by two parameters, the average on-site Coulomb repulsion $U$ and the exchange $J$,

```
$U = \frac{1}{(2l+1)^2} \sum_{mm'} U_{mm'} [61]$
```

```
$U-J = \frac{1}{2(2l+1)} \sum_{mm'} (U_{mm'} - U_{mm'}) [62]$
```

This can be seen by expressing $U_{LL_1L_2}$ in terms of spherical harmonics and effective Slater integrals $F^k$ as in Eq. [63]:

```
$\langle m,m'|U|m''\rangle = \sum_{k} a_k(m,m',m'') F^k
```

where $0 \leq k \leq 2l$

```
$a_k(m,m',m'') = \frac{4\pi}{2k+1} \sum_{q}|Y_{kq}|m'\rangle|Y_{kq}|m''\rangle [64]$
```

Because we are dealing with d electrons, $l=2$, and the notation for $U_{LL_1L_2}$ has been simplified to $U_{mm'm''}$ in Eqs. [61] and [62]. The Slater integrals $F^k$, which carry the radial integrations in Eq. [63], are of the type:

```
$F^k(s,t) = \int dr' P_{n,l}(r') P_{n,l}(r) \frac{r^k}{r'^k} [65]$
```

where the symbols $s$ and $t$ refer to two different electrons and $P_{n,l}(r)$ is the product of the distance $r$ from the nucleus and the radial function of the electron $R_{nl}$. The terms $r<r'$ correspond to the smaller (larger). Only $F^0, F^2$, and $F^4$ are required for d electrons, which can be linked to the $U$ and $J$ parameters through the relations $U=F^0$ and $J=(F^2+F^4)/(2l+1)$, whereas the ratio $F^2/F^4$ is a constant $\approx0.625$ for the $3d$ elements. In this formalism, the Stoner parameter, which determines the splitting of the bulk bands,$^{67}$ is $I=|2l+J|/(2l+1)$. Wan et al.$^{48}$ chose $I=1.2$ eV in their cluster calculations, to have consistency with the splitting of the bands of bulk in LSDA calculations. They used a value $U=2.6$ eV, although other values ($U=1.8$ eV, and $U=3.2$ eV) were explored. It is evident that orbital polarization is included in this approach via the orbital-dependent effects from $F^2$ and $F^4$. The orbital polarization differentiates the approach discussed in this section from that embodied in Eqs. [16] and [17].

The fifth term in the Hamiltonian of Eq. [57] is added to account for the electronic spillover at the surface.$^{21}$ One extra orbital with symmetry ($s'$ orbitals) is added to each surface $f$ and located in the vacuum region near the atom. This $s'$ orbital interacts with the $s$ orbital of the same surface atom through the hopping integral $t'_f$ and the occupation of the $s'$ orbitals represents the spill. The hopping integral is parameterized such that $t'_f(Z_i) = V_{sc}\sqrt{Z_{max}-Z_i}$, where $Z_{max}-Z_i$ is the local defect in the atomic coordination ($Z_{max}$); 2 for a fcc solid and $V_{sc}$ is the hopping strength. The last term in Eq. [57], which accounts for the orbital shifts from interlayer Coulomb interactions, is related to the last two terms in Eq. [16].$^{48}$ restricted the orbital shifts to the surface atoms $f$.

The eigenvalue equation corresponding to the Hamiltonian of Eq. [57] can be solved by an iterative procedure for any orientation of the spin magnetization (identified as the $zz$ direction). The self-consistent density matrix is then employed to calculate the local spin and orbital magnetic moments. For instance, the local orbital moments at different atoms are determined from

```
$$\mu_{i,orb} = \sum_{\sigma} \sum_{m=-l}^{l} mn_{im\sigma}d\epsilon \quad\quad [66]$$
```

where $m$ refers to the quantum number. The spin magnetic moment $\hat{\mu}_{spin}$ and the orbital magnetic moment $\hat{\mu}_{orb}$ of the cluster are calculated as a vector average of the atomic moments. The total magnetic moment $\hat{\mu}$ is obtained as the vector sum of $\hat{\mu}_{spin}$ and $\hat{\mu}_{orb}$. The self-consistent solution of the Hamiltonian generates a non-uniform and non-collinear distribution of spin and orbital moments; however, it was found by Wan et al. that nonlocality is very weak in this case. Also, the spin-orbit interaction can generate anisotropy, by a comparison of clusters with spin along the three principal axes revealed small energy differences of less than 0.005 eV/atom. The results reported immediately before correspond to spin orientation along the largest axis.

![img/fa9d34af1bcb785fd3792baa6c5c79_254.png]

**Figure 8** Calculated spin, orbital, and total magnetic moments per atom of Ni clusters. Reproduced with permission from Ref. 48.
