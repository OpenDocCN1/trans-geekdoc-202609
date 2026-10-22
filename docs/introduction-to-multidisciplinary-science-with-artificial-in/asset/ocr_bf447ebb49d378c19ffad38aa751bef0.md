Table 4.6. Transforms of qubits. The pair, say, (up, up) corresponding spins of (electron 1, electron 2). These τ-matrices are analog to sigma-matrices. σ₁, σ₂, and σ₃ act on electron 1 only and τ₁, τ₂ and τ₃ act on electron 2.

| (up, up) | (up, down) | (down, up) | (down, down) |
|----------|------------|------------|--------------|
| σ₃|uu⟩ = |uu⟩ | σ₃|ud⟩ = |ud⟩ | σ₃|du⟩ = -|du⟩ | σ₃|dd⟩ = -|dd⟩ |
| σ₂|uu⟩ = i|du⟩ | σ₂|ud⟩ = i|dd⟩ | σ₂|du⟩ = -i|uu⟩ | σ₂|dd⟩ = -i|dd⟩ |
| σ₁|uu⟩ = |uu⟩ | σ₁|ud⟩ = |dd⟩ | σ₁|du⟩ = |du⟩ | σ₁|dd⟩ = |dd⟩ |
| τ₃|uu⟩ = |uu⟩ | τ₃|ud⟩ = -|ud⟩ | τ₃|du⟩ = |du⟩ | τ₃|dd⟩ = -|dd⟩ |
| τ₂|uu⟩ = i|ud⟩ | τ₂|ud⟩ = -i|uu⟩ | τ₂|du⟩ = i|dd⟩ | τ₂|dd⟩ = |du⟩ |
| τ₁|uu⟩ = |ud⟩ | τ₁|ud⟩ = |uu⟩ | τ₁|du⟩ = |dd⟩ | τ₁|dd⟩ = |du⟩ |

and α_i are complex numbers. Here is another superposition (i.e., state):

|a'⟩ = 1/√2 |u⟩|u⟩ + 1/√2 |d⟩|d⟩

(4.78)

This state means that, if we measure the spin of the 2-particle system, we have a probability of 1/2 to get |u⟩|u⟩ (e.g., both particles have spin up) and a probability of 1/2 to get |d⟩|d⟩ (e.g., both particles have spin down).

Let us label the spin operators for electron 1 as σ₁, σ₂, and σ₃, as described in (4.68) and electron 2 as τ₁, τ₂, and τ₃. The actions of these operators are shown in Table 4.6.

In general, the dimension of a composite qubit system consisting of N qubits will be 2^N, i.e., the dimension of product spaces grows exponentially. Likewise, a state consisting of N qubits can be written as follows:

|a_N⟩ = α₀ |uu...uu⟩ + α₁ |uu...ud⟩ + ... + α_{N-1} |dd...dd⟩ .

Also note that the superposition principle is still applicable in these cases.

> An operator that measures spin along the direction n = [cosθ, sinθ]^T is given in (4.71). Show that it has eigenvectors |θ₊⟩ = cos(θ/2) |u⟩ + sin(θ/2) |d⟩ and |θ₋⟩ = -sin(θ/2) |u⟩ + cos(θ/2) |d⟩.



As described in the previous subsection, a quantum corresponds to transforming the quantum information (stored in a quantum system) into classical information. Measurement of a qubit, |a⟩, corresponds typically to reading out a classical bit, which is 0 or 1. One of the key features of quantum mechanics is that measurement outcomes are probabilistic. The probability of obtaining |u⟩ after measurement is |⟨u|a⟩|^2 and the probability of obtaining |d⟩ after measurement is |⟨d|a⟩|^2. Now consider a three qubit, |a₃⟩ state, but we only