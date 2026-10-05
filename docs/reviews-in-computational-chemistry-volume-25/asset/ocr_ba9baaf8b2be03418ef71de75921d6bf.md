# Determining the Glass Transition in Polymer Melts

quantitatively, the qualitative conclusions drawn from these simulations are often valid, especially when they concern more general polymeric properties. However, even qualitative conclusions pertaining only to a specific polymer or to a class of similar polymers can be problematic derived from simulations employing inaccurate or unvalidated potentials. Various classes of chemical potentials (forces for polymers) can be found in the literature$^{18–23}$ and have been reviewed in this book series$^{24–28}$ We are concerned in this chapter with reproducing the static, thermodynamic, and dynamic (transport and relaxational) properties of non-reactive organic polymers, and for this reason, the potential must represent accurately the molecular geometry, nonbonded interactions, and conformational energetics of the macromolecules of interest.

The classical force represents the potential energy of a polymer chain, made of N atoms coordinates by the set $\{\vec{r}\}$, as a sum of nonbonded interactions and contributions from all bond, valence bend, and dihedral interactions:

```
$V(\{\vec{r}\}) = V^{nb}(\{\vec{r}\}) + V^{pol}(\{\vec{r}\})$$
= V^{nb}(\{\vec{r}\}) + \sum_{bonds} V^{bond}(r_{ij}) + \sum_{bends} V^{bend}(	heta_{ijk}) + \sum_{dihedrals} V^{torsion}(\Phi_{ijkl})$$
[10]$
```

More complicated terms between the different intramolecular degrees of freedom are also employed in some force fields, but we will not consider them in the following. The dihedral term may also include four-center improper torsion or out-of-plane bending interactions that occur at $sp^2$ hybridized carbons.$29}$

The nonbonded interactions consist of a sum of two-body repulsion and dispersion energy between atoms that are often of the Lennard-Jones form in addition to the energy for interactions between fixed partial atomic or ionic charges (Coulomb interaction)

```
$V^{nh}(\{\vec{r}\}) = \sum_{i,j=1}^{M} 4\epsilon \left[\left(\frac{\sigma}{r_{ij}}ight)^{12} - \left(\frac{\sigma}{r_{ij}}ight)^6ight] + \frac{q_iq_j}{4\pi\epsilon_0r_{ij}}$$
[11]$
```

The dispersion interactions are compared with repulsion, but they are longer range, which results in an attractive well with a depth $\epsilon$ at an interatomic separation of $\sigma_{min} = 2^{1/6}\sigma$. The interatomic distance at which the potential is zero is used to define the atomic diameter. In addition to the Lennard-Jones form, the exponential-$6$ form of the dispersion-repulsion interaction,

```
$V^{exp-6}(\{\vec{r}\}) = \sum_{i,j=1}^{M} A_{ij}\exp\{-B_{ij}r_{ij}\} - \frac{C_{ij}}{r_{ij}^6}$$
[12]$
```