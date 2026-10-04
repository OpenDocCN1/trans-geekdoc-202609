# Quantum Associative Memory ■ 189

state |0110> by a negative phase and a Grover's rotation

(0.02, 0.02, 0.02, 0.5, 0.02, 0.02, -0.4, 0.02, 0.5, 0.02, 0.02, 0.02, 0.5)^T

all four basis states have nearly equal distribution and the information of the target state |0110> is negative. If we mark the target by a negative phase, the information about it will be like. How can we deal with non-uniform distributions?

# 14.2 Ventura Martinez Trick

Venture and Martinez, proposed a modified version of Grover's search algorithm [114, 115]. As before, from the initial distribution we mark the target state |0110> by a negative phase

> $\frac{1}{2}(0, 0, 0, 1, 0, 0, -1, 0, 1, 0, 0, 0, 0, 1)^T$

and perform a Grover's rotation with the result

> $\frac{1}{8}(-1, -1, -1, -3, -1, -5, -1, -1, -3, -1, -1, -1, -3)^T$

However, now we mark all four states that represent our distribution by a negative phase and perform a Grover's rotation with the result

> $\frac{1}{8}(1, 1, -1, -1, 1, 7, 1, 1, -1, 1, 1, 1, 1, -1)^T$

We mark again all four states that represent our distribution by a negative phase and perform a Grover's rotation

> $(0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0)^T$

with the amplitude indicating the target state. The qiskit circuit (see Figure 14.5) is represented as:

```
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