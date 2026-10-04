
## Quantum Associative Memory ■ 185

| | | | | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|---|------|
| q_0 | X | | | | | | | | | | | |
| q_1 | | X | | | | | | | | | | |
| q_2 | | | X | | | | | | | | | |
| q_3 | | | | X | | | | | | | | |
| q_4 | | | | | X | | | | | | | |

(a)

![](img/52faec2d621d75e53089d939bb234a82_211_0.png)

Figure 14.2 (a) Grover's amplification to the index qubits 3 and 4. (b) Since the qubits are entangled with the patterns we do not get the correct results.

```python
def store():
    qc = QuantumCircuit(5)
    #First pattern
    qc.ccx(3,4,0)
    qc.ccx(3,4,2)
    qc.barrier()
    #Second pattern
    qc.x(3)
    qc.ccx(3,4,0)
    qc.ccx(3,4,1)
    qc.x(3)
    qc.barrier()
    #Third pattern
    qc.x(4)
    qc.ccx(3,4,0)
    qc.ccx(3,4,1)
    qc.ccx(3,4,2)
    qc.x(4)
    qc.barrier()
    #Fourth pattern
    qc.x(3)
    qc.x(4)
    qc.ccx(3,4,1)
    qc.x(4)
```

# 186 ■ Quantum Artificial Intelligence with Qiskit

| | 0 | 0 |
|---|---|---|
| q_0: | | | |
| q_1: | 1 | |
| q_2: | 2 Store | 2 Store! |
| q_3: | H | 3 | H Z H |
| q_4: | 4 | 4 | H Z H |
| q_5: | X H | X | H |

![](img/52faec2d621d75e53089d939bb234a82_212_0.png)

Figure 14.3 (a) For Grover's amplification to the index qubits, we have to un-compute the entanglement of index qubits with the patterns. For the four state we require just one rotation. (b) We measure the correct result represented by one state with the |index_2> = |01|.

```python
qc.x(3)
qc.name="Store"
return qc
```

```python
def store_inv():
    qc=store()
    qc_inv=qc.inverse()
    qc_inv.name="StoreInv"
    return qc_inv
```

```python
qc = QuantumCircuit(6)
#0-2 data
#Index
#3-4
qc.h(3)
qc.h(4)
```

```python
#Aux Bit
qc.x(5)
qc.h(5)
```

## Quantum Associative Memory ■ 187

```python
qc.barrier()
qc.append(store(),range(5))
qc.barrier()
#Dracle
gate = MCXGate(3)
qc.append(gate,[0, 1, 2, 5])
qc.barrier()
qc.append(store_inv(),range(5))
qc.barrier()
#Redo Aux Bit
qc.h(S)
qc.barrier()
#Diffuser
qc.h(3,4)
qc.z(3,4)
qc.cz(3,4)
qc.h(3,4)
```

For the four state we require just one rotation. We measure the correct result represented by one state with $index_2 = |10|$ (see Figure 14.3 (b)). Instead of uncomputing, we would like to apply Grover's algorithm to the five qubits representing the patterns and the indexes. Measuring the states after one rotation of Grover's amplification indicates that something weird is happening.

## 14.2 QUANTUM ASSOCIATIVE MEMORY (QuAM)

In the QuAM as proposed by Ventura and Martinez, a modified version of Grover's search algorithm is applied to determine the answer to a query vector [114, 115, 110]. To prepare superposition of $m$ binary linear independent vectors with dimension $n > m$, a method was proposed by Ventura and Martinez [114, 115] and later simplified by [111], with preparation cost $O(n-m)$ requiring $\log_2(m)$ units. The query costs are $O(n\sqrt{m})$ compared to $O(n\cdot m)$ on a conventional computer. To understand the modified version of Grover's search algorithm and the results we generate simple superposition

> $|psi\rangle = \frac{1}{2}(|1100\rangle + |1001\rangle + |1111\rangle + |0110\rangle)$

so that we can track the amplitude distribution
$$\frac{1}{2}(0,0,0,0,1,0,1,0,1,0,1,0,1,0,0,1)^T.$$

We notice that the amplitude distribution is not uniform, a uniform distribution of amplitudes of four qubits would correspond to

$$\frac{1}{4}(1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1)^T.$$

Could this be the cause of the problem?

# 188 Quantum Artificial Intelligence with Qiskit

| | | | | | | |
|---|---|---|---|---|---|---|
| q_0: | 0 | | | | | | |
| q_1: | | 1 | | | | | |
| q_2: | | | 2 Store | | | | |
| q_3: | | | | 3 | | | |
| q_4: | | | | | 4 | | |
| q_5: | X | | | | | H | |

![](img/52faec2d621d75e53089d939bb234a82_214_0.png)

**Figure 14.4** (a) Instead of un-computing, we would like to apply Grover's algorithm to the five qubits representing the patterns and the indexes. (b) Measuring the states after one rotation of Grover's amplification indicates that something is happening.

## 14.2.1 Non-Uniform Distribution

From the initial distribution we mark the target state |0110> by a negative phase
$$(0,0,0,1,0,0,-1,0,0,0,0)^T$$
and perform Grover's rotation with the result
$$\frac{1}{8}(-1,-1,-1,-3,-1,-1,-1,-3)^T$$
We mark again the target state |0110> by a negative phase and perform Grover's rotation with the result
$$(-0.2,-0.2,-0.2,0.3,-0.2,0.2,0.2,0.3)^T$$
The four states that represent our distribution have high negative values of amplitude (the results are rounded for clarity). After marking the target state |0110> by a negative phase and a Grover's rotation
$(0.02,0.02,0.02,0.5,0.02,0.02,-0.4,0.02,0.5,0.02,0.02,0.02,0.5)^T$
all four basis states have nearly equal distribution.

Ventura and Martinez, proposed a modified version of Grover's search algorithm [114,115]. Before, from the initial distribution we mark the target state |0110> by a negative phase
$$\frac{1}{2}(0,0,0,1,0,0,-1,0,0,0,0)^T$$
and perform Grover's rotation with the result
$$\frac{1}{8}(-1,-1,-1,-3,-1,-1,-1,-3)^T$$
However, now we mark all four states that represent our distribution by a negative phase and perform Grover's rotation with the result
$$\frac{1}{8}(1,1,-1,-1,1,1,-1,-1)^T$$
We mark again all four states that represent our distribution by a negative phase and perform Grover's rotation with the result
$$(0,0,0,0,0,)^T$$
with the amplitude indicating the target state. The qiskit circuit (see Figure 14.5) is represented as:

```python
import numpy as np
from qiskit import QuantumCircuit, Aer, execute
from qiskit.quantum_info import Statevector
from qiskit.visualization import plot_histogram
from qiskit.circuit.library import MCXGate

qc = QuantumCircuit(5)
#0-1 data
#Index
#2-3
qc.h(2)
qc.h(3)

#Aux Bit
qc.x(4)
qc.h(4)
```

```python
qc.barrier()
#First pattern
qc.ccx(2,3,0)
qc.ccx(2,3,1)
```

```python
qc.barrier()
#Second pattern
qc.x(2)
qc.ccx(2,3,0)
qc.x(2)
```

```python
qc.barrier()
#Third pattern
qc.x(3)
qc.ccx(2,3,1)
qc.x(3)
```

```python
qc.barrier()
#Fourth pattern
qc.x(2)
qc.x(3)
qc.ccx(2,3,1)
```

```python
qc.barrier()
#Oracle
qc.x(0)
qc.x(3)
gate = MCXGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(3)
qc.x(0)
qc.barrier()
qc.h(4)
```

```python
# Diffuser 0, 1, 2, 3
qc.barrier()
qc.h([0,1,2,3])
qc.x([0,1,2,3])
qc.h(0)
gate = MCXGate(3)
qc.append(gate,[1,2,3,0])
qc.h(0)
qc.x([0,1,2,3])
qc.h([0,1,2,3])
```

```python
#Second rotation
qc.barrier()
```

## Quantum Associative Memory ■ 191

```python
qc.h(4)
qc.barrier()

#Oracle Trick
qc.x(0)
qc.x(3)
gate = MCXGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(3)
qc.x(0)

qc.x(2)
qc.x(3)
gate = MCXGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(3)
qc.x(2)

qc.x(1)
qc.x(2)
gate = MCXGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(1)

gate = MCXGate(4)
qc.append(gate,[0,1,2,3,4])
qc.barrier()
qc.h(4)
#

# Diffuser 0, 1, 2, 3
qc.barrier()

qc.h([0,1,2,3])
qc.x([0,1,2,3])
qc.h(0)
gate = MCXGate(3)
qc.append(gate,[1,2,3,0])
qc.h(0)
qc.x([0,1,2,3])
qc.x([0,1,2,3])

#Third rotation
qc.barrier()
qc.h(4)
qc.barrier()

#Oracle Trick
qc.x(0)
qc.x(3)
gate = MCXGate(4)
```

## 192 ■ Quantum Artificial Intelligence with Qiskit

```python
qc.append(gate,[0,1,2,3,4])
qc.x(3)
qc.x(0)

qc.x(2)
qc.x(3)
gate = MCXGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(3)
qc.x(2)

qc.x(1)
qc.x(2)
gate = MCXGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(1)

gate = MCXGate(4)
qc.append(gate,[0,1,2,3,4])
qc.barrier()
qc.h(4)
```
