# Amplitude Encoding

Amplitude encoding encodes a real or complex value vector of the length one into the amplitudes of a quantum state. We describe the top-down strategy and indicate the algorithm step by step. Then we describe the combining states strategy. Instead of representing the binary tree by multi-control rotation gates, we can use SWAP operators with simple rotation gates. The resulting circuits depth less than top-down divide strategy, however, we require the same number of qubits as the number of rotation gates and the qubits are entangled after the operation.
Then we describe the possibility to initialize the desired states using qiskit commands. We cannot access the amplitudes that represent vectors, but we estimate the value of the scalar product between them using the SWAP test. We give two examples of the

# 16.1 AMPLITUDE ENCODING EXAMPLE

Amplitude encoding encodes data into the amplitudes $\omega_i$ of a quantum state.

```
$|psi\rangle = \sum_{i=1}^{N} \omega_i \cdot |x\rangle \quad (16.1)
```

A complex normalized vector **x** (length one), for example

x = \begin{pmatrix} \sqrt{0.03} \ \sqrt{0.07} \ \sqrt{0.15} \ \sqrt{0.05} \ \sqrt{0.1} \ \sqrt{0.3} \ \sqrt{0.2} \ \sqrt{0.1} \end{pmatrix}

with qiskit little endian ordering $|q_2q_1q_0\rangle$

```
$|psi\rangle = \sqrt{0.03} \cdot |000\rangle + \sqrt{0.07} \cdot |001\rangle + \sqrt{0.15} \cdot |010\rangle + \sqrt{0.05} \cdot |011\rangle + \sqrt{0.1} \cdot |100\rangle + \sqrt{0.3} \cdot |101\rangle + \sqrt{0.2} \cdot |110\rangle + \sqrt{0.1} \cdot |111\rangle$
```