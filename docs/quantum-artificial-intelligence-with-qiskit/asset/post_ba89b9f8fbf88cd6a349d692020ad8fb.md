
## 4.1.1 Identity Gate – I

qc.id(qubit)

$|0\rangle \rightarrow |0\rangle \quad |1\rangle \rightarrow |1\rangle$

The identity gate defines a quantum gate on one qubit and can be represented by a unitary matrix $I$ in Hilbert space $\mathcal{H}_2$

$I = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$

The identity gate does not perform any operation and does not play any role in qiskit. In matrix notation, it indicates that qubits remain when composing a matrix using the tensor product that represents a quantum circuit.

## 4.1.2 NOT Gate, Pauli X Gate – X

qc.x(qubit)

$|0\rangle \rightarrow |1\rangle \quad |1\rangle \rightarrow |0\rangle$

The NOT gate defines a quantum gate on one qubit and can be represented by a unitary matrix $X$ in Hilbert space $\mathcal{H}_2$

$X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$

The NOT gate is also called the Pauli X-gate.

## 4.1.3 Toffoli Gate – ccX

qc.ccx(control1,control2,target)

| CCX[000] $\rightarrow$ | |000| | CCX[100] $\rightarrow$ | |100| |
| CCX[001] $\rightarrow$ | |001| | CCX[101] $\rightarrow$ | |101| |
| CCX[010] $\rightarrow$ | |010| | CCX[110] $\rightarrow$ | |111| |
| CCX[011] $\rightarrow$ | |011| | CCX[111] $\rightarrow$ | |110| |

Toffoli Gate, ccX CNOT gate, controlled controlled not gate also called ccX CNOT gate – controlled controlled not gate, defines a quantum gate on three qubits and can be represented by a unitary matrix CCX in $\mathcal{H}_s$

```
CCX = \begin{pmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 & 1 \end{pmatrix}
```

The Toffoli gate does not change the first input qubits $x_1$ and $x_2$. The operation is described by the following mapping on three input qubits $x_1, x_2, x_3$

```
$ccX(x_1, x_2, x_3) = (x_1, x_2, (x_1 \wedge x_2) \oplus x_3)$
```

A Toffoli gate performs following operations.

- It computes the AND operation, the ancilla (fixed) bit $x_3$ is set to 0.
$ccX(x_1, x_2, 0) = (x_1, x_2, x_1 \wedge x_2)$

- It computes the XOR operation, the bit $x_1$ is set to 1.
$ccX(1, x_2, x_3) = (1, x_2, x_2 \oplus x_3)$

- It computes the NOT operation on $x_3$.
$ccX(1, 1, x_3) = (1, 1, \neg x_3)$

- It computes the NAND operation, the ancilla (fixed) bit $x_3$ is set to 1.
$ccX(x_1, x_2, 1) = (x_1, x_2, \neg(x_1 \wedge x_2))$

- It computes the FANOUT operation (the value of bit $x_2$ is copied into $x_3$).
$ccX(1, x_2, 0) = (1, x_2, x_2)$

The OR operation follows from the De Morgan's laws

```
$x_1 \vee x_2 = \neg(\neg x_1 \wedge \neg x_2)$
```

Because NAND and FANOUT are together universal, we can implement any reversible quantum circuit using the Toffoli gate.

## Quantum Artificial Intelligence with Qiskit

## 4.1.4 Controlled NOT gate – cX

qc.cx(qubit1, qubit2)

```
$CX|00\rangle = |00\rangle \quad CX|01\rangle = |01\rangle$
$CX|10\rangle = |11\rangle \quad CX|11\rangle = |10\rangle$
```

The controlled not gate defines a quantum gate on two qubits and can be represented by a unitary matrix $CX$ in Hilbert space $\mathcal{H}_4$

```
$CX = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}$.
```

A controlled not gate performs following operations.

- Controlled operation. The second qubit is only flipped in the case that the first qubit is 1. In this case a not operation $X$ on the second qubit is executed.

```
$cX(1,x) = (1, \neg x_1)$
$cX(0,x) = (1, x_1)$
```

- Fan-out operation. For this operation the second qubit has to be 0. In this the value of the first qubit is copied into the second one.

```
$cX(x_1,0) = (x_1, x_1)$
```

## 4.1.5 SWAP Gate – SWAP

qc.swap(qubit1, qubit2)

```
$SWAP|00\rangle = |00\rangle \quad SWAP|01\rangle = |10\rangle$
$SWAP|10\rangle = |01\rangle \quad SWAP|11\rangle = |11\rangle$
```

The SWAP gate defines a quantum gate on two qubits and can be represented by a unitary matrix $SWAP$ in Hilbert space $\mathcal{H}_4$

```
$SWAP = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}$
```

The SWAP gate swaps the two qubits

```
$SWAP(x_1,x_2) = (x_2,x_1)$.
```

## 4.1.6 Controlled SWAP Gate – cS

qc.cswap(control,qubit_1,qubit_2)

```
$CSWAP(000) \rightarrow |000| \quad CSWAP(100) \rightarrow |100|$
$CSWAP(001) \rightarrow |001| \quad CSWAP(101) \rightarrow |110|$
$CSWAP(010) \rightarrow |010| \quad CSWAP(110) \rightarrow |101|$
$CSWAP(011) \rightarrow |011| \quad CSWAP(111) \rightarrow |111|$
```

The Controlled SWAP Gate or Fredkin gate, defines a quantum gate on three qubits and can be represented by a unitary matrix $CSWAP$ in Hilbert space $\mathcal{H}_8$

```
$CSWAP = \begin{pmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \end{pmatrix}$
```

- If control qubit is zero no swap is performed
$CSWAP(0, x_1, x_2) = (0, x_1, x_2)$

- If control qubit is one swap is performed
$CSWAP(1, x_1, x_2) = (1, x_2, x_1)$

## GATES FOR ONE QUBIT

The corresponding quantum gates for one qubit alter the distribution of amplitudes that are represented by complex numbers.

### 4.2 Clifford Gates for One Qubit

The Clifford gates are the elements of the Clifford group generated by three gates: Hadamard, $S$, and CNOT. It is a set of mathematical transformations which affect permutations of the Pauli gates: $X$ gate, $Y$ gate, and $Z$ gate. Quantum circuits that consist of only Clifford gates can be efficiently simulated with a classical computer.

### 4.2.1 Hadamard Gate – H

qc.h(qubit)

```
$H(|0\rangle) \rightarrow \frac{1}{\sqrt{2}}|0\rangle + \frac{1}{\sqrt{2}}|1\rangle \quad H(|1\rangle) \rightarrow \frac{1}{\sqrt{2}}|0\rangle - \frac{1}{\sqrt{2}}|1\rangle$
```

The Hadamard gate defines a quantum gate on one qubit and can be represented by a unitary matrix $H$ in Hilbert space $\mathcal{H}_2$

```
$H = \begin{pmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} \end{pmatrix}$
```

The Hadamard gate is also called Walsh gate. If the system starts in state $|0\rangle$ and undergoes the evolution, the probability of observing 0 or 1 is $|1/\sqrt{2}|^2 = 1/2$. If we do not perform a measurement and repeat the mapping, the probability of observing 0 becomes 1 and observing 1 becomes zero. This is due to the fact, that the amplitudes of $|1\rangle$ cancel each other. This effect is destructive interference.

### 4.2.2 Pauli Y Gate – Y

qc.y(qubit)

```
$Y(|0\rangle) \rightarrow i|1\rangle \quad Y(|1\rangle) \rightarrow i|0\rangle
```

The Pauli $Y$ gate defines a quantum gate on one qubit and can be represented by a unitary matrix $Y$ in Hilbert space $\mathcal{H}_2$

```
$Y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}$
```

### 4.2.3 Pauli Z Gate – Z

qc.z(qubit)

```
$Z(|0\rangle) \rightarrow |0\rangle \quad Z(|1\rangle) \rightarrow -|1\rangle$
```

The Pauli $Z$ gate defines a quantum gate on one qubit and can be represented by a unitary matrix $Z$ in Hilbert space $\mathcal{H}_2$

```
$Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$
```

### 4.2.4 S Gate – S

qc.s(qubit)

```
$S|0\rangle \rightarrow |0\rangle \quad S|1\rangle \rightarrow i|1\rangle$
```

The $S$ gate defines a quantum gate on one qubit and can be represented by a unitary matrix $S$ in Hilbert space $\mathcal{H}_2$

```
$S = \begin{pmatrix} 1 & 0 \\ 0 & i \end{pmatrix}$
```

The $S$ gate is also called the $Z9$ gate.

### 4.2.5 Sdag Gate – $S^\dagger$

qc.sdg(qubit)

```
$S^\dagger|0\rangle \rightarrow |0\rangle \quad S^\dagger|1\rangle \rightarrow -i|1\rangle$
```

The $S^\dagger$ gate defines a quantum gate on one qubit and can be represented by a unitary matrix $S$ in Hilbert space $\mathcal{H}_2$

```
$S^\dagger = \begin{pmatrix} 1 & 0 \\ 0 & -i \end{pmatrix}$
```

Clifford gates together with the $T$ gates are universal quantum gates since they can approximate any desired quantum gate with a small error.

## 4.3 ROTATION GATE

## 4.3.1 T Gate – T

qc.t(qubit)

The $T$ gate corresponds to the parameterized $RZ$ gate with $\theta = \pi/4$.

```
$T|0\rangle \rightarrow |0\rangle \quad T|1\rangle \rightarrow e^{i\pi/4} \cdot |1\rangle = \left(\frac{1}{\sqrt{2}} + \frac{i}{\sqrt{2}}\right) \cdot |1\rangle$
```

The $T$ gate defines a quantum gate on one qubit and can be represented by a unitary matrix $T$ in Hilbert space $\mathcal{H}_2$

```
$T = \begin{pmatrix} 1 & 0 \\ 0 & e^{i\pi/4} \end{pmatrix}$
```

with $T$ gate being the square root of the $S$ gate

```
$S = T^2$
```
