
# 230 Quantum Artificial Intelligence with Qiskit

# (a)

# (b)

![](img/52faec2d621d75e53089d939bb234a82_256_0.png)

Figure 16.6 ((a)) The binary tree at three is represented by seven qubits, to which a qubit rotation is applied. To the qubit 3 we apply the rotation $\theta_0 = 1.98231$, to the qubit 1 we apply the rotation $\theta_{10} = 1.42745$, and to qubit 5 we apply the rotation $\theta_{00} = 1.9106$. We use the SWAP operation. For level three we add all four rotations, we apply the rotation $\theta_{110} = 1.23096$ to the qubit 0, $\theta_{000} = 2.0944$ to the qubit 2, $\theta_{010} = 1.0472$ to the qubit 4, and $\theta_{000} = 1.98231$ to the qubit 6. The qubit 1 and 5 representing the level 2 control of the two sub-trees. The sub-trees are merged with the results of level one by the controlled SWAP operation controlled by the qubit 3. The measured tensor product of qubit 3 with qubit 5 and 3 represents the required distribution of the three qubits representing eight states. (b) The required distribution of the three qubits representing eight states.

```
counts = result.get_counts()
plot_histogram(counts)
```

The circuits depth is not top-down divide strategy, however we require the same number of qubits as rotation gates and the qubits are entangled during the operation.

# 16.4 QISKIT AMPLITUDE CODING

Qiskit offers through the commands `desired_state` and `initialize(desired_state, qubits)` a possibility to initialize the desired states and use the decompose command to indicate the resulting quantum circuit see Figure 16.7.

```python
from qiskit import QuantumCircuit, QuantumRegister, Aer, execute
from qiskit.visualization import plot, plot_histogram
import math
from qiskit import QuantumCircuit
```

```python
desired_state = [
math.sqrt(0.03),
math.sqrt(0.07),
math.sqrt(0.15),
```

# Amplitude Encoding 231

16.7 Qiskit offers through the commands `desired_state` and `initialize(desired_state, qubits)` a possibility to initialize the desired states and through the decompose command to indicate the resulting quantum circuit. The quantum circuit generating the amplitudes of the superposition $|\psi\rangle$

```python
math.sqrt(0.05),
math.sqrt(0.1),
math.sqrt(0.3),
math.sqrt(0.2),
math.sqrt(0.1),
]
qc = QuantumCircuit(3)
qc.initialize(desired_state, [0,1,2])

qc.decompose().decompose().decompose().decompose().decompose().decompose()
draw(fold=180)
```

```python
simulator = Aer.get_backend('statevector_simulator')
result=execute(qc,simulator).result()
counts = result.get_counts()
print("Total count are:",counts)
plot_histogram(counts)
```

# 16.5 SWAP TEST

We cannot access the amplitudes that represent vectors, but we estimate $\langle x|y\rangle$ using the swap test. Each state represents a normalized vector for the dimension $n$ represented by $m = \log_2 n$ qubits. The quantum $|x\rangle$ and $|y\rangle$ are of length one in the $l_2$ norm,

$||x||_2 = 1, ||y||_2 = 1.$

The additional auxiliary qubit $|0\rangle$ generates

$|0\rangle \otimes |x\rangle|y\rangle = |0, x,y\rangle$

Apply Hadamard on the control qubit $|0\rangle$,

$(H \otimes I \otimes I) \cdot |0,x,y\rangle = \frac{1}{\sqrt{2}} \cdot (|0, x,y\rangle + |1, x,y\rangle) \quad (16.17)$

Apply controlled swap operator on $|x\rangle$ and $|y\rangle$ states that swaps $|x\rangle$ and $|y\rangle$

$|x\rangle \rightarrow |y\rangle|x\rangle$

providing that the control qubit is in state $|1\rangle$ with

$$\frac{1}{\sqrt{2}} \cdot (|0, x, y\rangle + |1, x, y\rangle) \rightarrow \frac{1}{\sqrt{2}} \cdot (|0, x, y\rangle + |1, y, x\rangle) \quad (16.18)$$

We apply another Hadamard gate on the control qubit

$$(H \otimes I_m \otimes I_m) \cdot (\frac{1}{\sqrt{2}} \cdot (|0, x, y\rangle + |1, y, x\rangle)) = \frac{1}{2} \cdot |0\rangle \cdot (|x, y\rangle + |y, x\rangle) + \frac{1}{2} \cdot |1\rangle \cdot (|x, y\rangle - |y, x\rangle) \quad (16.19)$$

The probability of measuring the control qubit in state $|0\rangle$ is given by

$p(0) = |\frac{1}{2} \cdot |0\rangle \cdot (|x, y\rangle + |y, x\rangle) + \frac{1}{2} \cdot |1\rangle \cdot (|x, y\rangle - |y, x\rangle)|^2$
$p(0) = \frac{1}{4} |||x, y\rangle + |y, x\rangle||^2 + \frac{1}{4} |||x, y\rangle - |y, x\rangle||^2$
$p(0) = \frac{1}{2} (1 + \langle x|y\rangle) \quad (16.20)$
$p(1) = \frac{1}{2} (1 - \langle x|y\rangle) \quad (16.21)$

The probability $p(0) = 0.5$ means that the states $|x\rangle$ and $|y\rangle$ are orthogonal, whereas the probability $p(0) = 1$ indicates that the states are identical. We have to perform several measurements to estimate $p(0)$ or $p(1)$. The estimated scalar product is positive and since the vectors are normalized the inner product corresponds to the angle $\varphi$ between the vectors

$0 \le \cos\varphi = \langle x|y\rangle \le 1 \quad (16.23)$

and is usually called the cosine similarity. We can estimate the Euclidean distance as well, since the distance for normalized vectors is constrained to a unit sphere with

$0 \le ||\mathbf{x} - \mathbf{y}||_2 \le \sqrt{2}. \quad (16.24)$

# Amplitude Encoding 233

q_0:
q_1:
q_2:
c: 1/

![](img/52faec2d621d75e53089d939bb234a82_259_0.png)

**Figure 16.8** Qubit 0 represent the vector x and qubit 1 the vector y. After 10000 shots we measure $p(0) = 0.5010$.

# 16.5.1 Example for Two-Dimensional Vectors

$\mathbf{x} = \begin{pmatrix} \sqrt{0.5} \\ \sqrt{0.5} \end{pmatrix}, \quad \mathbf{y} = \begin{pmatrix} \sqrt{0.5} \\ -\sqrt{0.5} \end{pmatrix}$

with

$\langle\mathbf{x}|\mathbf{x}\rangle = ||\mathbf{x}||_2 = 1, \quad \langle\mathbf{y}|\mathbf{y}\rangle = ||\mathbf{y}||_2 = 1.$

and

$\langle\mathbf{x}|\mathbf{y}\rangle = 0$

Qubit 0 represent the vector x and qubit 1 the vector y. After 10000 shots we measure $p(0) = 0.5010$ (see [Figure 16.8](https://example.com/figure-16.8))

$\langle\mathbf{x}|\mathbf{y}\rangle \approx \sqrt{2} \cdot 0.501 - 1 = 0.045.$

Note that the results are probabilistic and they might slightly differ from run to run.

# 16.5.2 Example for Four-Dimensional Vectors

$\mathbf{x} = \begin{pmatrix} \sqrt{0.1} \\ \sqrt{0.2} \\ \sqrt{0.4} \\ \sqrt{0.3} \end{pmatrix}, \quad \mathbf{y} = \begin{pmatrix} 0 \\ 0 \\ \sqrt{0.5} \\ \sqrt{0.5} \end{pmatrix}$.

with

$$\langle x|x\rangle = ||x||_2 = 1, \langle y|y\rangle = ||y||_2 = 1.$$

and

$$\langle x|y\rangle = 0.8345$$

Qubits 0 and 1 represent the vector x and qubits 2 and 3 the vector y

```python
from qiskit import QuantumCircuit, QuantumRegister, Aer, execute
from qiskit.visualization import plot_histogram
from qiskit.circuit.library import RYGate
from qiskit.quantum_info import Statevector
from math import pi

qc = QuantumCircuit(5,1)
qc.h(4)
qc.cry(1.98231, 3, 4)
qc.cry(1.42745, 1, 4)
qc.cry(1.91063, 5, 4)
qc.barrier()
qc.cry(1.23096, 0, 4)
qc.cry(2.0944, 2, 4)
qc.cry(1.0472, 4, 4)
qc.cry(1.98231, 6, 4)
qc.barrier()
qc.cswap(4,0,2)
qc.cswap(4,1,3)
qc.h(4)
qc.measure(4,0)

qc_simulator = Aer.get_backend('qasm_simulator')
result=execute(qc,qc_simulator,shots=10000).result()
counts = result.get_counts()
```

# Amplitude Encoding 235

![](img/52faec2d621d75e53089d939bb234a82_261_0.png)

![](img/52faec2d621d75e53089d939bb234a82_261_1.png)

**Figure 16.9** (a) Qubits 0 and 1 represent the vector **x**, qubits 2 and 3 the vector **y**. (b) after 10000 shots we measure $p(|0|) = 0.8479$.

```python
result=execute(qc_simulator,shots=10000).result()
counts = result.get_counts()
plot_histogram(counts)
```

See Figure 16.9, after 10000 shots we measure $p(|0|) = 0.8479$
