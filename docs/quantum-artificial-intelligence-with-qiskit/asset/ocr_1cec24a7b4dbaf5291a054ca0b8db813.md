# 8 Puzzle

The n-puzzle is a classical problem for modeling algorithms. For n-puzzle there are $n+1$ different objects: $n$ cells and one empty cell. Each object can be coded by $ho = [\log_2 n+1]$ qubits and a configuration of $n+1$ objects can be represented by a register of $z = p \cdot (n+1) |xangle$. The function $g(x)$ is represented a unitary operator $T$. acts on the $z+1$ qubits with $x \in B^n$ and $c \in B^1$

$T|x,cangle = |x,f(x) \oplus cangle$

We indicate how to extend the 3-puzzle resulting in a non-constant branching factor. We show that the branching factor is reduced by Grover's amplification to the square root of the branching factor and not to the maximal branching factor. Simple experiments of the search of the depth requires 49 qubits. The experiments indicate that the presented methods can be extended to a search of depth, which more qubits are present.

# 10.1 REPRESENTATION

For 8-puzzle, there are nine objects: eight cells and one empty cell. Each object has to be represented by 4 qubits 3 qubits allow only to represent $2^3=8$ different states. The object 1 is represented by 001, 2 is represented by 010, and 3 is represented by 011, and we continue the representation as binary numbers with 8 represented as 1000. We represent the state $x$ by $|xangle$. The state is represented by 36 qubits, $x_0, x_1, x_2, x_3, x_4, x_5, x_6, x_7,...$ see Figure 10.1. The empty cell can move up, down, left or right. The right bound is determined by the position and two bits $r=m_0, m_1$ (qubits 46 and 47) indicating whether the cell should perform move right ($m=0=|00\}$), left ($m=1=|01\}$), up ($m=2=|10\}$) or down ($m=3=|11\}$). There are 36 qubits to represent the state and 9 qubits for the trace, together the auxiliary qubit 49 qubits are represented by

```
qc = QuantumCircuit(49,2)
#State Preparation 0-35
#N3
qc.x(0)
qc.x(1)
```