# Quantum Machine Learning

Training proceeds by adjusting $	heta$ to minimize a divergence or distance metric,
total variation distance, or adversarial loss. Depending on the task, QGMs can be
used for:

+   * **Quantum data generation**, i.e. producing quantum states or measurement
statistics;
* **Classical data modeling**, i.e. approximating the distribution of classical data
using a quantum circuit; and
* **Hybrid applications**, where classical and quantum components interact during
training or inference.

# 7.21 Quantum Boltzmann machines

The motivation for Boltzmann machines

Quantum Boltzmann machines (QBMs) [15] extend classical BMs by replacing
classical energy functions with Ising spin Hamiltonians. Instead of modeling
probability distributions directly, QBMs prepare a thermal state in a Hilbert space.
Through projective measurements, samples can be drawn to the density
matrix of the prepared state:

```
$$\rho = \frac{e^{-eta H}}{\text{Tr}(e^{-eta H})} = \sum_i |\psi_i\rangle\langle\psi_i|$
```

Here, $H$ is a Hamiltonian encoding interactions between qubits, $eta$ is the inverse
tperature ($1/k_B T$), and $|\psi_iangle$ represents individual state vectors. The transverse
field Ising model is a well-established system for Boltzmann machines the
Hamiltonian is composed of nearest-neighbor interactions as well as on-site
potentials and external fields,

```
$H_{\text{ISING}} = -\sum_{\langle i,j\rangle}\sigma_i\sigma_j - \sum_i h_i\sigma_i$
```

This system exhibits transitions where individual spins (i.e. neurons or binary
variables) can align or anti-align with nearest neighbors, or can align or anti-align with
t external field. These interactions are controlled by the amplitude and sign of the
individual terms $J_{ij}$, and the on-site potential and external fields ($h_i$) and can result
in long-range coherent patterns or random, frustrated configurations of spins (variables).

Training this model approximates a target distribution by optimizing the
parameters ($J_{ij}, h_i$) of $H_{\text{ISING}}$. The probability of a classical configuration is given
by

> $k_B$ is the Boltzmann constant.