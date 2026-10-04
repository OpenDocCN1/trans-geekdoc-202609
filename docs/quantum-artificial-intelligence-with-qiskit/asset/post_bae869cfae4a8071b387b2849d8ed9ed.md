
## 20.1.1 Example with $T$ Gate

The $T$ gate corresponds to the unitary matrix

```
$T = \begin{pmatrix} 1 & 0 \\ 0 & e^{i\pi/4} \end{pmatrix}
```

With the eigenvector $|1\rangle$ and the eigenvalue $e^{2\pi\theta}$

```
$U \cdot |u\rangle = T|u\rangle = e^{2\pi\theta} \cdot |u\rangle = e^{2\pi\theta} \cdot |1\rangle \quad (20.9)
```

with the phase $\theta=\frac{1}{8}$ since

```
$T|1\rangle = e^{2\pi\theta} = e^{i\pi/4} \cdot |1\rangle = e^{2\pi/4} \cdot |1\rangle$.
```

The phase estimation algorithm will write the phase of $T$ to $m$ qubits in our simple case $m=3$. The value of $m$ determines the precision of the result.

```
$\theta = x_0x_1x_2 = \frac{x}{2^3}$
```

The controlled $T$ gate is represented by the controlled phase gate $CP(\lambda)$ where $\lambda=\pi/4$. The circuit is composed of 4 qubits, qubits 0, 1, 2 represent the 3 qubits in the control register. The qubit 3 represents the eigenvector $|1\rangle$. The control register is mapped into superposition by Hadamard gates and the qubit 4 is initialized to the eigenvector $|1\rangle$ with the NOT gate. The control register controls the unitary operations $T$ applied to the target eigenvector $|1\rangle$ resulting in the Fourier representation of the three control qubits. To estimate the phase $\theta$, we perform the inverse QFT to the 3 control qubits and measure the three qubits and estimate with $\theta$

```
$x = |q_2q_1q_0\rangle$
```

and

```
$\theta = \frac{x}{2^3}$
```

The circuit is represented as (See Figure 20.1)

```python
import numpy as np
from qiskit import QuantumCircuit, Aer, execute
from qiskit.quantum_info import Statevector
from qiskit.visualization import plot_histogram
from qiskit.circuit.library import MCXGate
from math import pi
from qiskit.circuit.library import QFT
qc = QuantumCircuit(4, 3)
qc.h(0)
qc.h(1)
qc.h(2)
qc.x(3)
qc.cp(lambda, control, target)
qc.cp(pi/4, 0, 3)
```

![](img/52faec2d621d75e53089d939bb234a82_284_0.png)

| | | | | | | | |
|---|---|---|---|---|---|---|---|
| q_0 | H | | | | | | |
| q_1 | H | | | | | | |
| q_2 | H | P(n/4) | P(n/4) | P(n/4) | P(n/4) | P(n/4) | |
| q_3 | X | | | | | | | |

![](img/52faec2d621d75e53089d939bb234a82_284_1.png)

![](img/52faec2d621d75e53089d939bb234a82_284_2.png)

**Figure 20.1** (a) Circuit estimating the phase of a T gate with accuracy of three qubits. The circuit is composed of 4 qubits, qubits 0, 1, 2 represent the control register and qubit 3 represents the eigenvector |1>. The control register controls the unitary operations T applied to the target eigenvector |1>. To estimate the phase, we perform the inverse QFT to the 3 control qubits. (b) The measured value corresponds to the binary value 001 equal to one indicating phase $\theta=0.125 = 1/2^3$.

```python
qc.cp(pi/4, 1, 3)
qc.cp(pi/4, 1, 3)
qc.cp(pi/4, 2, 3)
qc.cp(pi/4, 2, 3)
qc.cp(pi/4, 2, 3)
qc.cp(pi/4, 2, 3)
qc.barrier()
qc = qc.compose(QFT(3, inverse=True), [0,1,2])
qc.barrier()
qc.measure(0,0)
qc.measure(1,1)
qc.measure(2,2)
```

```python
simulator = Aer.get_backend('qasm_simulator')
result = execute(qc,simulator,shots=1000).result()
counts = result.get_counts()
plot_histogram(counts)
```

The measured value corresponds to the binary value 001 equal to one indicating phase. The more qubits (m) we use, the higher precision we get. However in this simple example, three control qubits lead to good estimation of the phase $\theta$ $$\theta = \frac{1}{2^3} = \frac{1}{8}$$

## 20.2 QUANTUM COUNTING

Grover's amplification is based on the unitary operator $G_m = 2P_m - I$ in the computational basis with $n^*$ states. (We use notation $n^*$ to indicate the number of qubits used in Grover's amplification and the number of control qubits $m$ do need to be equal.) The probability of seeing one solution should be as close as possible to 1 and the number of iterations. The number of iterations $r$ is the largest integer greater $t$,

```
$r = \lfloor \frac{\pi}{4} \sqrt{\frac{n}{k}} \rfloor$.
```

The value of $r$ depends on the relation of $n$ versus $k$, with $k$ being the number of solutions. We can estimate $k$ by quantum counting. In quantum counting, we simply use the phase estimation algorithm to find an eigenvalue of Grover search. One can represent the state $|t\rangle$ after $t$ Grover's amplification by two subspaces $|solution\rangle$ and $|non\rangle$ representing the solutions and non-solutions with

```
$|t\rangle = \alpha_t |solution\rangle + \beta_t |non\rangle$.
```

Quantum counting algorithm is based on inverse QFT to estimate the sine wave represented by the amplitude $\alpha_t$ or $\beta_t$ after $t$ iterations (see Figure 20.2). After amplification we get

```
$\sqrt{\frac{k}{n}} |solution\rangle + \sqrt{\frac{n-k}{n}} |non\rangle$.
```

![](img/52faec2d621d75e53089d939bb234a82_285_0.png)

**Figure 20.2** The two-dimensional subspace of amplitude and time $t$ represents a periodic curve described by $\alpha_t$ (the dotted curve) and $\beta_t$ (the continuous curve). The x-axis indicates $t$ and the y-axis is the amplitude. The values are $n=256, k=1$, and $1 \le t \le 200$.

## Quantum Artificial Intelligence with Qiskit

with

$$\sin^2 \theta = \frac{k}{n}$$

and

$$\cos^2 \theta = \frac{n-k}{n} = 1 - \frac{k}{n}$$

We can represent the Grover's amplification matrix in the two-dimensional basis $|solution\rangle$ and $|non\rangle$

$G = \begin{pmatrix} \cos(\theta) & -\sin(\theta) \\ \sin(\theta) & \cos(\theta) \end{pmatrix}$

The matrix $G$ has two eigenvectors

$u_1 = \begin{pmatrix} \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} \end{pmatrix}; \quad u_2 = \begin{pmatrix} \frac{1}{\sqrt{2}} \\ \frac{-1}{\sqrt{2}} \end{pmatrix}$

with two eigenvalues $\lambda_1 = e^{2i\theta}$ and $\lambda_2 = e^{-2i\theta}$. The eigenvectors are represented in $|solution\rangle$ and $|non\rangle$ as

$|u_1\rangle = \frac{1}{\sqrt{2}}|solution\rangle + \frac{1}{\sqrt{2}}|non\rangle$

$|u_2\rangle = \frac{1}{\sqrt{2}}|solution\rangle - \frac{1}{\sqrt{2}}|non\rangle$

$|\psi\rangle = e^{i\theta} \cdot \frac{1}{\sqrt{2}}|u_1\rangle + e^{-i\theta} \cdot \frac{1}{\sqrt{2}}|u_2\rangle$

In the original phase estimation algorithm, the required eigenvector is

$U|u\rangle = e^{2i\pi\theta}|u\rangle$

However, we do not need to prepare our register in either of these eigenvectors, the register is actually in a superposition of the Grover's operator

$G|\psi\rangle = G \cdot (e^{i\theta} \cdot \frac{1}{\sqrt{2}}|u_1\rangle + e^{-i\theta} \cdot \frac{1}{\sqrt{2}}|u_2\rangle)$

$G|\psi\rangle = \lambda_1 \cdot (e^{i\theta} \cdot \frac{1}{\sqrt{2}}|u_1\rangle) + \lambda_2 \cdot (e^{-i\theta} \cdot \frac{1}{\sqrt{2}}|u_2\rangle)$

Since our eigenvalues are $\lambda_1 = e^{2i\theta}$ and $\lambda_2 = e^{-2i\theta}$,

$$\theta = \frac{x}{2^m}$$

## 20.2.1 Example

The controlled Grover operator is implemented using the circuit

```python
def grover_operator():
#Grover iteration circuit for oracle 
from qiskit.circuit.library import Diagonal, GroverOperator
oracle = Diagonal([1,1,1,1,1,1,1,1,1,-1,1,-1])
grover_it = GroverOperator(oracle).to_gate()
grover_it.label = "QFT"
return grover_it
```

and we will use the .control() method to create a controlled gate from the Grover operator. The circuit is composed of 5 qubits, qubits 0, 1, 2, 3 represent the 4 qubits in the control register. The qubits 5 to 7 represent the computational basis mapped into superposition by Hadamard gates

```python
import matplotlib.pyplot as plt
import numpy as np
import math
# importing Qiskit
from qiskit QuantumCircuit, Aer, execute
# import basic plot tools
qc = QuantumCircuit(8, 4)

qc.h([0,1,2,3,4,5,6,7])
cgrit = grover_operator().control()

qc.append(cgrit, [0,4,5,6,7])
```
