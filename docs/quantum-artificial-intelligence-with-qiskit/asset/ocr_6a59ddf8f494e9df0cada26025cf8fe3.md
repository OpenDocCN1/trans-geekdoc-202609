# Amplitude Encoding 229

![](bbox=[0.198, 0.105, 0.801, 0.252])

q_0: Ry(1.4275)
q_1: Ry(1.9106)
q_2: Ry(1.9106)
c: 2/ 0 1

**Figure 16.5** The binary tree level is represented by three qubits, to which a rotation gate is applied. For the qubit 1 we apply the rotation $\theta_0=1.98231$, to the qubit 0 we apply the rotation $\theta_{10}=1.4275$, and to qubit 2 we apply the rotation $\theta_{00}=1.9106$. The value of qubit 1 controls the SWAP operation and the measured tensor product of qubit 1 represents the required distribution of the two qubits representing four states.) (The required distribution of the two qubits representing four states.

of qubit 3 and 5 represents the required distribution of the three qubits representing eight states (see Figure 16.6)

```
from qiskit import QuantumCircuit, QuantumRegister, Aer, execute
from qiskit.visualization import plot_histogram
from qiskit.circuit.library import MCGate
from qiskit.quantum_info import Statevector
from qiskit.circuit.library import RGGate
from math import pi
```

```
qc = QuantumCircuit(7,3)
```

```
qc.ry(1.23096,0)
qc.ry(1.42745,1)
qc.ry(2.0944,2)
qc.ry(1.91063,3)
qc.ry(1.0472,4)
qc.ry(1.91063,5)
qc.ry(1.98231,6)
qc.barrier()
qc.cswap(1,0,2)
qc.cswap(5,4,6)
qc.barrier()
qc.cswap(3,1,5)
qc.cswap(3,2,6)
#Measuring 0 1 3
qc.measure(6,0)
qc.measure(5,1)
qc.measure(3,2)
```

```
simulator = Aer.get_backend('qasm_simulator')
result=execute(qc,shots=10000).result()
```