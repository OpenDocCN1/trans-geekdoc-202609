Apart from the GHZ state, there is a three-qubit (or tripartite) entangled state called the W state of the form:

$|W\rangle = \frac{1}{\sqrt{3}}(|001\rangle + |010\rangle + |100\rangle)$

It has been noted by Dür et al. [2000] that any tripartite entangled state can be converted using Local Operations and Classical Communication (LOCC) (e.g. local gates/operations on each node holding one qubit and classical communications between nodes) into one of two standard forms, the GHZ state or the W state (not both), and that if a state \(|\psi\rangle\) is convertible (via LOCC) into a GHZ state and another state \(|\phi\rangle\) into the W state, then \(|\psi\rangle\) cannot be converted into \(|\phi\rangle\) and conversely. This means that GHZ and W are in this sense two very different kinds of entangled states.

An interesting observation about the W state is that it is more robust to errors than \(|GHZ\rangle\), in the following sense. Suppose we have the W state shared among three qubits, and one of the qubits is measured, say the last qubit, then with probability 1/3 we get \(|1\rangle\) and the other qubits end up in state \(|00\rangle\) (corresponding to \(|001\rangle\)). But with probability 2/3 we get \(|0\rangle\), and the other qubits end up in an entangled state: \(\frac{1}{\sqrt{2}}(|01\rangle + |10\rangle)\) (corresponding to the superposition of \(|010\rangle\) and \(|100\rangle\)). But with the GHZ state, on measuring the last qubit, we get either \(|0\rangle\) or \(|1\rangle\), and no chance of the remaining two qubits being in an entangled state. Hence, three qubits, if sharing a W state and one qubit is measured (or “lost” as a result of some interaction with the environment), there is still a probability of 2/3 that the remaining two qubits share an entangled state (retaining the resource of entanglement), but if sharing a GHZ state and one qubit “lost,” no resource (entanglement) can be retained. This fact might have significance for the quantum network, in terms of robustness.

The generalized \(W_n\) state is of the form:

\(|W_n\rangle = \frac{1}{\sqrt{n}}(|100\dots000\rangle + |010\dots000\rangle + \cdots + |000\dots010\rangle + |000\dots001\rangle)\)

with each label being \(n\)-bit strings. Similar arguments about robustness can be considered for the generalized case, compared to \(|GHZ_n\rangle\).

# 2.4 Teleportation and Superdense Coding

Quantum teleportation was mentioned earlier, and we now provide the mathematical model of this technique of transferring a quantum state from one node to another.

A key resource required for quantum teleportation is entanglement. Consider the problem of transferring a quantum state \(|\psi\rangle = \alpha|0\rangle + \beta|1\rangle\) from one node to