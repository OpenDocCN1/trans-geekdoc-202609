# 86 Quantum Artificial Intelligence with Qiskit

![](bbox=[0.166, 0.114, 0.811, 0.206])

Figure 5.3 Quantum oracle indicating marking the state [010] by a minus sign and the Grover's amplification.

```
qc.draw(fold=140)

simulator = Aer.get_backend('statevector_simulator')
final_state = simulator.run(qc).result().get_statevector
```

```
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector") = 

StateVector = [0 0 0 0 0 0 0 0 0.1768 0.1768 0.8839 0.1768 0.1768 0.1768 0.1768 0.1768]
```

In the next step we will perform two rotations using qasmis simulator. We do not minus sign operation

> $G_3 = -H_3 \cdot \Lambda_3 \cdot H_3$

to get the correct result, what changes is the minus sign of over all amplitudes. This has no consequence for the resulting probabilities, so Grover's amplification can be simplified to (see Figures 5.4 and 5.5)

> $G_3 = H_3 \cdot \Lambda_3 \cdot H_3$

```
import numpy as np
from qiskit import QuantumCircuit, Aer, execute
from qiskit.visualization import plot_histogram
from qiskit.circuit.library import MCXGate

qc = QuantumCircuit(4,3)
c.h([0,1,2])
#Preparation of Aux
qc.x(3)
c.h(3)
#Oracle
qc.barrier()
qc.x(0)
qc.x(2)
gate = MCXGate(3)
qc.append(gate, [0, 1, 2, 3])
qc.x(0)
qc.x(2)
```