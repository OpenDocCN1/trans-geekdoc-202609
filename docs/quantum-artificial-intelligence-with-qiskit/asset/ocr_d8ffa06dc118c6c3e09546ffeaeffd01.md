Toffoli Gate, ccX CNOT gate, controlled controlled not gate also called ccX CNOT gate – controlled controlled not gate, defines a quantum gate on three qubits and can be represented by a unitary matrix CCX in $\mathcal{H}_s$

```
CCX = \begin{pmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 \ 0 & 1 & 0 & 0 & 0 & 0 & 0 \ 0 & 0 & 1 & 0 & 0 & 0 & 0 \ 0 & 0 & 0 & 1 & 0 & 0 & 0 \ 0 & 0 & 0 & 0 & 1 & 0 & 0 \ 0 & 0 & 0 & 0 & 0 & 1 & 0 \ 0 & 0 & 0 & 0 & 0 & 0 & 1 \end{pmatrix}$
```

The Toffoli gate does not change the first input qubits $x_1$ and $x_2$. The operation is described by the following mapping on three input qubits $x_1, x_2, x_3$

```
$ccX(x_1, x_2, x_3) = (x_1, x_2, (x_1 \wedge x_2) \oplus x_3)$
```

A Toffoli gate performs following operations.

+   - It computes the AND operation, the ancilla (fixed) bit $x_3$ is set to 0.
$ccX(x_1, x_2, 0) = (x_1, x_2, x_1 \wedge x_2)$

+   - It computes the XOR operation, the bit $x_1$ is set to 1.
$ccX(1, x_2, x_3) = (1, x_2, x_2 \oplus x_3)$

+   - It computes the NOT operation on $x_3$.
$ccX(1, 1, x_3) = (1, 1, \neg x_3)$

+   - It computes the NAND operation, the ancilla (fixed) bit $x_3$ is set to 1.
$ccX(x_1, x_2, 1) = (x_1, x_2, \neg(x_1 \wedge x_2))$

+   - It computes the FANOUT operation (the value of bit $x_2$ is copied into $x_3$).
$ccX(1, x_2, 0) = (1, x_2, x_2)$

The OR operation follows from the De Morgan's laws

```
$x_1 \vee x_2 = \neg(\neg x_1 \wedge, \neg x_2)$
```

Because NAND and FANOUT are together universal, we can implement any reversible quantum circuit using the Toffoli gate.