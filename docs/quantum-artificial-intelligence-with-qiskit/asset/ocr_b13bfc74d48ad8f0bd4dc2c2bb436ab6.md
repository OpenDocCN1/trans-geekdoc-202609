# 68 Quantum Artificial Intelligence with Qiskit

# 4.2.1.1 Hadamard Gate – H

qc.y(qubit)

```
$H(|0\rangle) ightarrow \frac{1}{\sqrt{2}}|0\rangle + \frac{1}{\sqrt{2}}|1\rangle \quad \quad H(|1\rangle) ightarrow \frac{1}{\sqrt{2}}|0\rangle - \frac{1}{\sqrt{2}}|1\rangle$
```

The Hadamard gate defines a quantum gate on one qubit and can be represented by a unitary matrix $H$ in Hilbert space $\mathcal{H}_2$

```
$H = \begin{pmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \ \frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} \end{pmatrix}$
```

The Hadamard gate is also called Hadamard-Walsh gate. If the system starts in state $|0\rangle$ and undergoes the evolution, the probability of observing 0 or 1 is $|\1/\sqrt{2}|^2 = 1/2$. If we do not prema a measurement and repeat the mapping, the probability of observing 0 becomes 1 and observing 1 becomes zero. This is due to the fact, that the amplitudes of $|1\rangle$ cancel each other. This effect is destructive interference.

# 4.2.2 Pauli Y Gate – Y

qc.y(qubit)

```
$Y(|0\rangle) \rightarrow i|1\rangle \quad \quad Y(|1\rangle) \rightarrow i|0\rangle$
```

The Pauli $Y$ gate defines a quantum gate on one qubit and can be represented by a unitary matrix $Y$ in Hilbert space $\mathcal{H}_2$

```
$Y = \begin{pmatrix} 0 & -i \ i & 0 \end{pmatrix}$
```

# 4.2.3 Pauli Z Gate – Z

qc.z(qubit)

```
$Z(|0\rangle) \rightarrow |0\rangle \quad \quad Z(|1\rangle) \rightarrow -|1\rangle$
```

The Pauli $Z$ gate defines a quantum gate on one qubit and can be represented by a unitary matrix $Y$ in Hilbert space $\mathcal{H}_2$

```
$Z = \begin{pmatrix} 1 & 0 \ 0 & -1 \end{pmatrix}$
```