between qubits B' on node 2 and B on node 3) and generate an entangled pair over a longer distance (e.g. between A on node 1 and B on node 3). Key to this mechanism is the notion of entanglement swapping, which we will look into. We will also look into a mechanism to transmit quantum information robustly over longer distances using tree-cluster states. But before all that, we need the idea of Bell State Measurement.

# 6.1.1 Bell States and Bell State Measurement

The four Bell states are \(|\Phi^+\rangle = ((|00\rangle + |11\rangle))/\sqrt{2}\), \(|\Phi^-\rangle = ((|00\rangle - |11\rangle))/\sqrt{2}\), \(|\Psi^+\rangle = ((|01\rangle + |10\rangle))/\sqrt{2}\), and \(|\Psi^-\rangle = ((|01\rangle - |10\rangle))/\sqrt{2}\). Since they are orthogonal, they form a basis, the *Bell basis*. For example, a state \(|\psi\rangle\) written in the basis \(\{|00\rangle, |01\rangle, |10\rangle, |11\rangle\}\):

\(|\psi\rangle = \alpha |00\rangle + \beta |11\rangle + \gamma |01\rangle + \delta |10\rangle\) where \(|\alpha|^2 + |\beta|^2 + |\gamma|^2 + |\delta|^2 = 1\), can be rewritten in the Bell basis as
\(|\psi\rangle = \frac{\alpha + \beta}{\sqrt{2}} |\Phi^+\rangle + \frac{\alpha - \beta}{\sqrt{2}} |\Phi^-\rangle + \frac{\gamma + \delta}{\sqrt{2}} |\Psi^+\rangle + \frac{\gamma - \delta}{\sqrt{2}} |\Psi^-\rangle\)

A Bell state measurement asks which of the Bell states \(|\psi\rangle\) is in.

How can we measure in the Bell basis if we can only measure in the *Z* basis (due to the instruments available, for example)? See Aside.

> Aside: Note that measuring a qubit in the X basis is applying the Hadamard gate first and then measuring in the Z basis in the sense that prob(+1) (or the probability of getting the state |0⟩) in this case is the same as X(+1) when measuring in the X basis.² The Pauli X measurement |ψ⟩ —X— can be implemented as |ψ⟩ —H— X— since prob(+1) are the same in both.
> 
> Similarly, suppose |ψ⟩ is a two-qubit state, and if we want to measure in the Bell basis but only can measure in the basis {|00⟩, |01⟩, |10⟩, |11⟩}, we need a U such that: U |Φ⁺⟩ = |00⟩, U |Φ⁻⟩ = |10⟩, U |Ψ⁺⟩ = |01⟩, and U |Ψ⁻⟩ = |11⟩, and use it as follows (where the |ψ⟩ below is a two-qubit state):
> 
> [Circuit Diagram: |ψ⟩ — U — Z — with measurement symbols]