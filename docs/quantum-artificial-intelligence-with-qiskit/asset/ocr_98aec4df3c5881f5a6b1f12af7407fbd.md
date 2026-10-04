# 230 Quantum Artificial Intelligence with Qiskit

# (a)

# (b)

![](bbox=[0.166, 0.135, 0.803, 0.303])

Figure 16.6 ((a)) The binary tree at three is represented by seven qubits, to which a qubit rotation is applied. To the qubit 3 we apply the rotation $	heta_0 = 1.98231$, to the qubit 1 we apply the rotation $	heta_{10} = 1.42745$, and to qubit 5 we apply the rotation $	heta_{00} = 1.9106$. We use the SWAP operation. For level three we add all four rotations, we apply the rotation $	heta_{110} = 1.23096$ to the qubit 0, $	heta_{000} = 2.0944$ to the qubit 2, $	heta_{010} = 1.0472$ to the qubit 4, and $	heta_{000} = 1.98231$ to the qubit 6. The qubit 1 and 5 representing the level 2 control of the two sub-trees. The sub-trees are merged with the results of level one by the controlled SWAP operation controlled by the qubit 3. The measured tensor product of qubit 3 with qubit 5 and 3 represents the required distribution of the three qubits representing eight states. (b) The required distribution of the three qubits representing eight states.

```
counts = result.get_counts()
plot_histogram(counts)
```

The circuits depth is not top-down divide strategy, however we require the same number of qubits as rotation gates and the qubits are entangled during the operation.

# 16.4 QISKIT AMPLITUDE CODING

Qiskit offers through the commands desired_state and initialize(desired_tate, qubits) a possibility to initialize the desired states and use the decompose command to indicate the resulting quantum circuit see Figure 16.7.

```
from qiskit import QuantumCircuit,QuantumRegister, Aer, execute
from qiskit.visualization import plot, plot_histogram
import math
from qiskit import QuantumCircuit
```

```
desired_state = [
math.sqrt(0.03),
math.sqrt(0.07),
math.sqrt(0.15),
```