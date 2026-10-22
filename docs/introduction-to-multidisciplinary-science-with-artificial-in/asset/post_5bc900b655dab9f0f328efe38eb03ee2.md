
Hence, we have complete random information. More generally, if the probabilities of the mixed states are equally weighted, we have complete random information. This case is known as *ambiguity of mixtures.*

## Properties of the density matrix.

The density matrix satisfies a number of properties. First, the density matrix is a Hermitian operator: $\rho^\dagger = \rho$ as a result of the fact that the probabilities $p_i$ are real. The consequence of hermiticity of $\rho$ means that all of the eigenvalues of the density matrix are real.

Second, $\mathrm{Tr}(\rho) = 1$, which implies that the probabilities add up to one. Actually $\mathrm{Tr}(\rho)$ is the sum of eigenvalues of $\rho$. These eigenvalues themselves can be thought of as probabilities for different states. The eigenvalues go with the eigenstates (i.e., eigenvectors). Because $\rho$ is a Hermitian matrix, its eigenstates are all mutually orthogonal. As mentioned above, for example, when $\lambda_1 = \lambda_2 = ... = \lambda_n = 1/n$, we have a complete ignorance and a maximal knowledge when we are dealing with a pure state (i.e., $n = 1$ and $p = 1$ hence $\rho = |\psi\rangle\langle\psi|$). In addition, a mixed state can be defined as a density matrix that has more than one nonzero eigenvalue.

Third, the density matrix is positive semi-definite; i.e., if $|\phi\rangle$ is an arbitrary quantum state then

$$\langle\phi|\rho|\phi\rangle = \sum_i p_i |\langle\phi|\psi_i\rangle|^2 \ge 0 \tag{4.105}$$

An equivalent definition of a positive semi-definite operator is one whose eigenvalues are always non-negative.

## Entropy of a quantum system.

In Chapter 2, we introduce the entropy of classical systems. It is given by:

$$S = - \sum_i^n p_i \log p_i \tag{4.106}$$

If only one $p_i$ (i.e., $n = 1$ and $p_1 = 1$) is non-zero, we know exactly the state that the system is in and the entropy (lack of information) is zero; $S = 1 \log 1 = 0$. If there is equal probability $p_1 = p_2 = ... = p_n = 1/n$ then:

$$S = - \sum_{i=1}^n \frac{1}{n} \log(1/n) = \log n = S_{\max} \tag{4.107}$$

where $S_{\max} = \log n$ is the maximum entropy of this system. For a quantum system, entropy is

$$S = -\mathrm{Tr}(\rho \log \rho) \tag{4.108}$$

As for the classical case, if the system is definitely in one state, then $S = 1 \log 1 = 0$. If there is equal probability $1/n$ for the system to be in any of $n$ states and the probability to be in any state other than these $n$ states is zero, then: $S = \log n$. As

![](img/f5b5b8709fc3a81631262f22d3552c5e_507_0.png)

> Figure 4.19. Using the quantum-communications satellite Micius successfully sent entangled photons to two cities in China. Micius beamed photons to Earth, separating them by more than 1200 kilometers. Adapted from https://www.sciencenews.org/article/quantum-satellite-shatters-entanglement-record.

Quantum entanglement process. Let us emphasize that quantum entanglement is the property that the state of one particle determines the state of the other due to the requirement that the conservation laws, a pillar of modern physics and quantum mechanics in particular, must be satisfied. The conservation laws are really the origin of entanglement. The seemingly weird properties come from quantum mechanics. Here we discuss the entanglements of electrons and photons.

## Photon entanglements.

One can create a maximally entangled pair of photons by a process known as down conversion. In this process a single photon of frequency $f$ passes through a suitable nonlinear crystal, which creates two maximally entangled photons over energy, each of frequency $f/2$, at the same time. The process must preserve energy, momentum, and angular momentum (polarization). So these three properties are entangled in the two photons. If the process is energy degenerate, then the two emitted photons, called the signal and idler, have the same energy and the entangled properties are momentum and angular momentum (polarization). Possible choices of nonlinear crystals are noncentrosymmetric nonlinear $\chi^{(2)}$-crystals in Table 3.6, including, usually, beta barium borate (BBO), described in the previous chapter 3 — a $\chi^{(2)}$ medium is a nonlinear crystal in which the second term in a general nonlinear expansion of the polarisability is the dominant nonlinear term. Scattering events on such crystals satisfy the conservation of momentum and energy. Without this type of nonlinear crystal, a single photon will not automatically split into two. Anyway, all photon pairs emitted from the crystal are entangled.

## Electron entanglements

Electron entanglements can occur in many ways, although only a few are really practical. For example, the electrons in a specific electron orbital (shell) are entangled with one another in orbitals on a single atom because the electrons in a specific electron orbital on an atom have strong correlations with each other due to their mutual Coulomb interaction. Electrons in an atom more generally form spin singlet states (4.96), which ensure they are in entangled states. A similar argument will also hold for the spin triplet configuration (4.86), in which case the electrons occupy different orbital states. These entanglements are not very useful because they are local, while in most practical cases we are interested in spatially separable electron pairs.

Another way to entangle electrons is to collide them. The challenge is that electrons do not physically interact, as they cannot get nearer than the Planck length (the Planck length is $10^{-35}$ meters and the Planck time is $10^{-43}$ seconds). Remember that each electron has an electromagnetic field. When two electrons get close to each other, each electron begins to respond to the changes in the electromagnetic field due to the other electron. The closer they are, the stronger the repulsive force between the electrons becomes. As a result, the two electrons never really bounce off each other but they can be near enough to ensure that they entangle.

Let us now consider a practical example. If two separate electrons absorb maximally entangled photons, the electrons become spin-entangled because the polarization of light carries spin information that can be transferred to the electrons. Entanglement occurs in optical cavities. Basically, an optical cavity is made of two very smooth partially reflecting surfaces placed very close to each other and the space between them is a vacuum. The whole apparatus is then cooled to near absolute zero temperature. Two neutral atoms trapped in an optical cavity can then be entangled with each other using an entangled pair of photons. One photon would be absorbed by each atom and the two atoms would then become entangled with each other. Notice we do not use electrons directly, rather, we use atoms.

## Atom entanglements.

Entanglement is not limited to subatomic particles. Atoms, ions, and other massive particles can also become entangled. Such entanglements are generally carried out by an experiment involving an optical cavity—two opposing imperfect mirrors—containing two or more atoms, as illustrated in Figure 4.20. Light is shone into one side of the cavity and allowed to bounce back and forth between the mirrors. Some of the light will eventually escape through the opposite side of the cavity, where it is captured by a detector. The leakage is due to the fact that mirrors here are imperfect—that is, not all the light rays that strike them are reflected back. Atoms will spontaneously emit photons out of the cavity due to the coupling of the atom to the modes of the electromagnetic field of free space on either side, as illustrated in Figure 4.20. One can then monitor changes in the cavity transmission resulting from coupling to atoms falling through the cavity. In optical cavity experiments, spherical mirrors are often used as shown in Figure 4.20. This setup is known as a Fabry-Perot configuration. A cavity is designed to confine light (electromagnetic field) between two reflectors. Atoms or other particles placed between two reflectors interact with the electromagnetic field. Thus an optical cavity is an arrangement of two highly reflective mirrors (either dielectric or metallic) placed parallel to each other at a small distance. This arrangement is widely used as a platform to amplify light-matter interactions. Trapping single atoms in this arrangement with high-quality factor mirrors opens up endless possibilities for the
