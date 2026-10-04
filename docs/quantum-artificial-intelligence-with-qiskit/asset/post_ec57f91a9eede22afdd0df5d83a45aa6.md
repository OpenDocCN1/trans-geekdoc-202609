
![](img/52faec2d621d75e53089d939bb234a82_73_0.png)

**Figure 3.5** Quantum coin represented by a H gate and the measurement of the qubit represented by M. The value of the measurement is represented by one classical bit c.

of the measured qubits that have to be defined in the circuit, the measured values are stored in conventional bits. In our example of quantum coin, we define by the command `qc = QuantumCircuit(1,1)` a quantum circuit, the first index indicates the number of qubits, the second of conventional bits.

```python
qc = QuantumCircuit(1,1)
qc.h(0)
qc.measure(0,0)
qc.draw()
```

The command `qc.measure(0,0)` indicated that we measure the qubit (the counting begins with zero and not one) and store the result of the measurement in the conventional bit c. The quantum circuit is represented in [Figure 3.5]().

```python
simulator = Aer.get_backend('qasm_simulator')
result = execute(qc, simulator, shots=10).result()
counts = result.get_counts()
print(f"Total count: {counts}")
plot_histogram(counts)
```

The command `result = execute(qc, simulator, shots=10).result()` executes the quantum 10 times, the number of samples (shots) is indicated by the command `qc, simulator, shots=10`. A histogram represents the frequency of the two states 0 and 1 measured by one bit is indicated in the [Figure 3.6]() in relation to the number of shots.

Applying the quantum coin twice

$H \cdot (\frac{1}{\sqrt{2}}|0\rangle + \frac{1}{\sqrt{2}}|1\rangle) = H \cdot \frac{1}{\sqrt{2}}|0\rangle + H \cdot \frac{1}{\sqrt{2}}|1\rangle = |0\rangle$

```python
qc = QuantumCircuit(1,1)
qc.h(0)
qc.h(0)
qc.measure(0,0)
qc.draw()
```

results in the quantum circuit indicated in the [Figure 3.7]() and in the histogram [Figure 3.8]().

![](img/52faec2d621d75e53089d939bb234a82_74_0.png)

**Figure 3.6** Two states 0 and 1 and their frequency of outcome as measured by one. The normalized frequencies are represented as probabilities. (a) The number of samples is 10, the total count are: {'1': 6, '0': 4}. (b) The number of samples is 100, the total count are: {'1': 51, '0': 52}. (c) The number of samples is 1000, the total count are: {'1': 502, '0': 498}. (d) The number of samples is 1000, the total count are: {'1': 5026, '0': 4974}. With growing number of samples, the distribution approaches the true values of Figure 3.3.

## 3.6 MATRIX REPRESENTATION

The Hadamard operator $H_3$ measures 3 qubits $|000\rangle$ representing a basis in a Hilbert space $\mathcal{H}_2^3$

```latex
$$\frac{1}{\sqrt{8}} (|000\rangle + |001\rangle + |010\rangle + |011\rangle + |100\rangle + |101\rangle + |110\rangle + |111\rangle) =
```

![](img/52faec2d621d75e53089d939bb234a82_74_1.png)

**Figure 3.7** Applying quantum coin represented by two $H$ gates and the measurement of the qubit represented by $M$. The value of the measurement is represented by one classical bit $c$.

![](img/52faec2d621d75e53089d939bb234a82_75_0.png)

**Figure 3.8** One generated new states represented by one qubit.

This corresponds to the simple program of three qubits 0, 1, 2 using the state vector simulation

```python
qc = QuantumCircuit(3)
qc.h(0)
qc.h(1)
qc.h(2)
qc.draw()
```

```python
simulator = Aer.get_backend('statevector_simulator')
result=execute(qc,simulator).result()
counts = result.get_counts()
print(f"Total count: {counts}")
plot_histogram(counts)
```

in the quantum circuit in the [Figure 3.9] and in the histogram [Figure 3.10]. We can represent the state vector before the measurement indicating its amplitude values using the build-in LaTeX command (when using editor that supports jupyter)

```python
final_state = execute(qc,simulator).result().get_statevector()
from qiskit.visualization import array_to_latex
array_to_latex(final_state, prefix="\text{state}\} = ")
```

| q_0: | H |
| :--- | :--- |
| q_1: | H |
| q_2: | H |

**Figure 3.9** The Hadamard operator $H_3$ maps 3 qubits $|000\rangle$ representing a basis state in a Hilbert space $\mathcal{H}_{2^3}$. This is represented by three $H$ gates on the qubits numbered 0, 1 and 2.

![](img/52faec2d621d75e53089d939bb234a82_76_0.png)

Figure 3.10 Eight generated states represented by three qubit.

```latex
Statevector = \begin{bmatrix} 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} \end{bmatrix}
```

We can represent the quantum circuit by a matrix with the following commands. We will use NumPy that is in qiskit installation. NumPy is library for Python programming language, adding support for large, multi-dimensional arrays and matrices that are highly related to MATLAB.

```python
import numpy as np
from qiskit.visualization import array_to_latex
from qiskit import assemble

simulator = Aer.get_backend('qasm_simulator')
qc.save_unitary()
result = simulator.run(qc).result()
unitary = result.get_unitary()
print("Size of the unitary matrix:", unitary.shape)
print(array_to_latex(unitary, prefix="\text{Circuit = "))
```

with the output matrix:
Size of the unitary: (8, 8)
$\begin{bmatrix} 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} \\ 1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} \\ 1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} & -1/\sqrt{8} \\ 1/\sqrt{8} & -1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} \\ 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} & -1/\sqrt{8} & -1/\sqrt{8} & -1/\sqrt{8} \\ 1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} \\ 1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} \\ 1/\sqrt{8} & -1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} & 1/\sqrt{8} & 1/\sqrt{8} & -1/\sqrt{8} \end{bmatrix}$

Since the size of the matrix grows exponential, it is not possible to represent quantum circuits with a higher number of qubits by a matrix.

## 3.7 QUANTUM CIRCUITS

The four bit conjunction $x \wedge y \wedge z \wedge v$ requires three quantum Toffoli gates $CCX$ and three additional qubits that are zero. With the input state

$|x\rangle|y\rangle|z\rangle|v\rangle$

First Toffoli gate

$(CCX \cdot |x\rangle|y\rangle) \otimes (I_4 \cdot |z\rangle|v\rangle) = |x\rangle|x \wedge y\rangle|z\rangle|v\rangle$

Second Toffoli gate

$(I_2 \cdot |x\rangle) \otimes (CCX \cdot |x \wedge y\rangle|z\rangle) \otimes (I_2 \cdot |v\rangle) = |x\rangle|x \wedge y\rangle|x \wedge y \wedge z\rangle|v\rangle.$

Third quantum Toffoli gate

$(I_4 \cdot |z\rangle|x \wedge y\rangle|z\rangle) \otimes (CCX \cdot |x \wedge y \wedge z\rangle|v\rangle) = |x\rangle|x \wedge y\rangle|x \wedge y \wedge z\rangle|x \wedge y \wedge z \wedge v\rangle.$

The circuit corresponds to the following unitary mapping

with the result

$|x\rangle|x \wedge y\rangle|x \wedge y \wedge z\rangle|v\rangle|x \wedge y \wedge z \wedge v\rangle$
