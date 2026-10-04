# Quantum Fourier Transform 253

![](bbox=[0.166, 0.125, 0.801, 0.203])

Figure 19.4 QFT for four qubits.

The circuit for m qubits can be imported from the qiskit library. In our example we compose a circuit of 6 qubits, see Figure 19.5

```
from qiskit.circuit.library import QFT
qc = QuantumCircuit(6)
#qc = qc.compose(QFT(6, inverse=True))
qc = qc.compose(QFT(6))
qc.decompose().draw(fold=200)
```

# 19.3.4 QFT Costs

The first term requires one Hadamard gate, the second requires one Hadamard gate and a controlled phase gate. Each following term requires an additional controlled phase gate. Summing up

> $1 + 2 + 3 + \cdots \cdot (m-1) + m = \frac{m \cdot (m-1)}{2} = O(m^2).$

The costs of a QFT are $O(m^2)$ compared to the cost of $O(2^m \cdot m)$ on a conventional computer, the costs of QFT are exponentially less.

# 19.3.5 QFT

A periodic function can be represented as a superposition of qubits and their values of amplitudes (representing the probabilities). For periodic function the amplitudes representing the frequency of the function have positive whereas all other are zero. By measuring the register with high amplitude values, we can reconstruct the period. In our example we generate a state vector of the DFT

![](bbox=[0.166, 0.727, 0.801, 0.805])

Figure 19.5 QFT for six qubits.