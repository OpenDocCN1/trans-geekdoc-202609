$p(\mathbf{v}) = \langle\mathbf{v}|\mathbf{v}\rangle = \frac{\langle\mathbf{v}|e^{-eta H}|\mathbf{v}\rangle}{\text{Tr}(e^{-eta H})}. \quad (7.7)$

While conceptually powerful, many challenges for QBMs exist. Methods for efficient thermal state preparation are needed to ensure that candidate states can be prepared and are stable enough that sufficient samples can be drawn on noisy hardware. Alternatively, generating samples with classical simulation or emulation, efficient Monte Carlo methods are needed. Finally, understanding the optimization landscape is necessary to build efficient training methods that converge to good solutions under noise, both hardware and stochastic. One example is the use of quantum annealing to navigate rugged optimization landscapes [16].

Nevertheless, QBMs build genuinely quantum generative models, using the formalism of quantum statistical machines to represent and learn complex distributions. Table 7.2 summarizes the conceptual and operational differences between RBMs and quantum counterparts. While RBMs operate with classical binary variables and on energy functions defined over hidden nodes, QBMs operate with quantum states governed by a Hamiltonian and described via thermal density matrices. The table contrasts their respective sampling strategies, expressive capacities, and training challenges, highlighting how quantum models could potentially overcome some of the limitations inherent to classical energy-based approaches. Notably, QBMs are able to exploit quantum coherence and entanglement to model more complex correlations, although this comes at the cost of increased implementation complexity and hardware requirements.

Beyond the framework of energy-based models, QGMs use quantum mechanical properties of superposition, entanglement, and interference to model probability distributions. With parameterized unitary gates, QGMs model generative processes that either sample from, or approximate, complex data distributions. These models

Table 7.2. Comparison of RBMs and QBMs. QBMs generalize RBMs by replacing classical energy functions with quantum Hamiltonians, allowing for enhanced representation power via quantum effects such as superposition and entanglement.

| Feature | Classical RBM | Quantum Boltzmann machine |
| --- | --- | --- |
| Energy function | $E(v, h)$ | Quantum Hamiltonian $H$ |
| State | Binary vector | Quantum density matrix $\rho$ |
| representation | | |
| Sampling | Gibbs sampling/contrastive divergence | Quantum thermal state sampling |
| Expressivity | Limited by architecture | Enhanced by quantum coherence and entanglement |
| Training challenges | Approximate gradient estimation | Intractable partition function, hardware required |