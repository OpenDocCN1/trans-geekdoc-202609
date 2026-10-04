# 168 Quantum Artificial Intelligence with Qiskit

We describe two possible approaches, a method that was developed by Ventura and Martinez [114, 115] and the method of entanglement of binary patterns vectors with index qubits in superposition.

# 13.2 SUPERPOSITIONS OF BINARY PATTERNS

To generate a superposition of $m$ binary linear independent vectors with dimension $n$ with $n > m$ was proposed by Ventura and Martinez [114, 115] and later specified by [111]. The procedure is based on successfully dividing superposition into processing and memory branches. Each new generated memory branch an input pattern is loaded by step. The method is in the number of stored patterns and their dimension [95].

At the initial step the system is in the basis state with load qubits, memory qubits, and the control qubits $c_1, c_2$.

$|memory; c_2, c_1; load\rangle$

We use the qiskit little endian notation. Note, that the original work used a big endian notation [111] $|register; c_1, c_2, memory\rangle$. The idea is to split this basis step by step using the control register until the required superposition

```
$$\sum_{j=1}^m |memory; c_2, c_1; load\rangle_j$
```

with the memory register in the required superposition

```
$$\sum_{j=1}^m |memory; 0, 0; 0 \cdots 0\rangle_j = \frac{1}{\sqrt{m}} \sum_{j=1}^m |memory_j\rangle \otimes |0, 0; \cdots 0\rangle$
```

also called memory branches.
We make a distinction between a processing branch indicated by the control qubit $c_2$ with the one value ($c_2=1$) and the memory branches in superposition with the control qubit $c_2$ with the zero value ($c_2=0$). The control qubit $c_1=1$ indicates the split of the control $c_2$ by the operator $CS_p$ represented by the unitary gate $U(\theta, \phi, \lambda)$ with $\phi=\pi, \lambda=\pi$, and $\theta=\arcsin(...) \cdot 2$

```
$CS_p = CU(\arcsin(\frac{1}{\sqrt{p}}), 2, \pi, \pi) = \begin{pmatrix} 1 & 0 & 0 & 0 \ 0 & 1 & 0 & 0 \ 0 & 0 & \frac{1}{\sqrt{p}} & \frac{\sqrt{p-1}}{\sqrt{p}} \ 0 & 0 & \frac{-\sqrt{p-1}}{\sqrt{p}} & \frac{1}{\sqrt{p}} \end{pmatrix}$
```

with $CS_p[c_2, c_1]$

```
$CS_p|01\rangle = |01\rangle, CS_p|11\rangle = \frac{1}{\sqrt{p}} |10\rangle + \frac{\sqrt{p-1}}{\sqrt{p}} |11\rangle$
```