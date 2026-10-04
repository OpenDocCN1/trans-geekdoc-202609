# 206 Quantum Artificial Intelligence with Qiskit

```
from qiskit import QuantumCircuit, Aer, execute
from qiskit.quantum_info import Statevector
from qiskit.visualization import plot_histogram
from qiskit.circuit.library import MCXGate
from math import pi
```

```
qc = QuantumCircuit(15)
#0-3 query
#4-7 data
#8-11 count
#Index Pointer
#12-13
#Aux
#14
```

```
#Sleep Phase
#Index Pointer
qc.h(12)
qc.h(13)
qc.barrier()
#1st weights
qc.ccx(12,13,4)
qc.ccx(12,13,7)
qc.barrier()
#2th weights
qc.x(12)
qc.ccx(12,13,4)
qc.x(12)
qc.x(12)
qc.barrier()
#3th weights
qc.x(13)
qc.ccx(12,13,6)
qc.x(13)
qc.barrier()
#4th weights
qc.x(12)
qc.x(13)
qc.ccx(12,13,4)
qc.ccx(12,13,7)
qc.x(12)
qc.x(12)
qc.barrier()
```

```
#Active Phase
#query
qc.x(0)
qc.x(3)
qc.barrier()
qc.ccx(0,4,8)
qc.ccx(1,5,9)
qc.ccx(2,6,10)
```