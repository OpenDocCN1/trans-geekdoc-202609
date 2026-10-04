# 4.1.1 Identity Gate – I

qc.id(qubit)

$|0\rangle ightarrow |0\rangle \quad |1\rangle ightarrow |1\rangle$

The identity gate defines a quantum gate on one qubit and can be represented by a unitary matrix $I$ in Hilbert space $\mathcal{H2$

$I = \begin{pmatrix} 1 & 0 \ 0 & 1 \end{pmatrix}$

The identity gate does not perform any operation and does not play any role in qiskit. In matrix notation, it indicates that qubits remain when composing a matrix using the tensor product that represents a quantum circuit.

# 4.1.2 NOT Gate, Pauli X Gate – X

qc.x(qubit)

$|0\rangle ightarrow |1\rangle \quad |1\rangle ightarrow |0\rangle$

The NOT gate defines a quantum gate on one qubit and can be represented by a unitary matrix $X$ in Hilbert space $\mathcal{H2$

$X = \begin{pmatrix} 0 & 1 \ 1 & 0 \end{pmatrix}$

The NOT gate is also called the Pauli X-gate.

# 4.1.3 Toffoli Gate – ccX

qc.ccx(control1,control2,target)

| CCX[000] $ightarrow$ |000| | CCX[100] $ightarrow$ |100| |
| CCX[001] $ightarrow$ |001| | CCX[101] $ightarrow$ |101| |
| CCX[010] $ightarrow$ |010| | CCX[110] $ightarrow$ |111| |
| CCX[011] $ightarrow$ |011| | CCX[111] $ightarrow$ |110| |