

## 22.3.1 从 Kitaev 相位估计到哈密量模拟

使用 Kitaev 相位估计算法，我们得到以下关系：

```
$$U \cdot |u\rangle = e^{2\pi i\theta_j} \cdot |u\rangle$$
```

通过使用哈密量模拟，该关系为：

```
$$U_j \cdot |u\rangle = e^{-it\lambda_j} \cdot |u\rangle$$
```

在 Kitaev 相位估计算法中，我们将使用 QFT 代替逆 QFT 来处理负号。在这种情况下，关系变为：

```
$$e^{2\pi i\theta_j} \cdot |u\rangle = e^{it\lambda_j} \cdot |u\rangle$$
```

其中：

```
$$\theta_j = \frac{\lambda_j \cdot t}{2 \cdot \pi}$$
```

在我们的模拟中，控制寄存器中使用两个量子比特，并选择 $t=2\cdot\pi/8$，我们得到：

```
$$\theta_j = \frac{3}{8} \cdot \lambda_j$$
```

其中：

```
$$\theta_1 = \frac{3}{8} \cdot \frac{3}{4} = \frac{2}{4}, \quad \theta_2 = \frac{2}{8} \cdot \frac{3}{3} = \frac{1}{4}$$
```

测量的两个量子比特为 [10] 代表 2，[01] 代表 1：

```
$$\theta=0.x_2x_1 = \frac{x}{4} = \frac{x}{2^2}$$
```

我们表示：

```
$$|b\rangle = |0\rangle = \mathbf{b} = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$$
```

其中：

```
$$|u_1\rangle = \frac{|0\rangle - |1\rangle}{\sqrt{2}}, \quad |u_2\rangle = \frac{|0\rangle + |1\rangle}{\sqrt{2}}$$
```

以及：

```
$$|b\rangle = \sum_j \beta_j |u_j\rangle = \frac{1}{\sqrt{2}} |u_1\rangle + \frac{1}{\sqrt{2}} |u_2\rangle$$
```

```
$$|b\rangle = \frac{1}{\sqrt{2}} \frac{|0\rangle - |1\rangle}{\sqrt{2}} + \frac{1}{\sqrt{2}} \frac{|0\rangle + |1\rangle}{\sqrt{2}} = |0\rangle.$$
```

我们将使用 qiskit 命令 `HamiltonianGate` [21]，其中数据表示为厄米特矩阵 $A$，时间 $t=2\cdot\pi/8$，用于执行哈密量演化，并使用 QFT 代替逆 QFT（见图 22.1）。

![](img/52faec2d621d75e53089d939bb234a82_300_0.png)

![](img/52faec2d621d75e53089d939bb234a82_300_1.png)

图 22.1 (a) 通过哈密量模拟以两个量子比特的精度估计 $U_i$。电路由 3 个量子比特组成，量子比特 0, 1 代表控制寄存器，量子比特 2 代表 $b = |0\rangle$。为了估计相位 $\theta$，我们对 2 个控制量子比特执行 QFT。(b) 测量值对应二进制值 10 和 01。

```python
from qiskit import QuantumCircuit, Aer, execute
from qiskit.visualization import plot_histogram
from math import pi
from qiskit.quantum_info import Operator
from qiskit.extensions import HamiltonianGate
from qiskit.circuit.library import QFT
qft = QFT(2, inverse=False).to_gate()
gate.label = "QFT"
```

```python
from qiskit.circuit.library import QFT
qft = QFT(2, inverse=False).to_gate()
gate.label = "QFT"

op = Operator([[-1,-1/3], [-1/3, 1]])
# create gate which evolves according to exp(-i*op*3*pi/4).control()
gate = HamiltonianGate(op,3*pi/4)
```

```python
qc = QuantumCircuit(3,2)
qc.h([0,1])
# apply gate to qubits [0, 1, 2] in circuit
qc.append(gate, [0,2])
qc.append(gate, [1,2])
qc.append(gate, [1,2])
# Do QFT on counting qubits
qc.append(qft, [0,1])
# Measure counting qubits
qc.measure([0,1], [0,1])
```

simulator = Aer.get_backend('qasm_simulator')
result=execute(qc,simulator,shots=10000).result()
counts = result.get_counts()
plot_histogram(counts)
```

## 22.3.2 条件旋转与反向计算

我们通过以下方式对辅助态 $|0\rangle$ 执行条件旋转：

```
$$R_Y(\alpha) = \begin{pmatrix} \cos(\frac{\alpha}{2}) & -\sin(\frac{\alpha}{2}) \\ \sin(\frac{\alpha}{2}) & \cos(\frac{\alpha}{2}) \end{pmatrix}$$
```

使用两个控制量子比特 [10] 代表 $\lambda_1 = 2$，[01] 代表 $\lambda_2 = 1$：

```
$$\alpha_1 = 2 \cdot \arccos(\frac{1}{\lambda_1}) = 2 \cdot \arccos(\frac{1}{2}) = \frac{\pi}{3}$$
```

```
$$\alpha_2 = 2 \cdot \arccos(\frac{1}{\lambda_2}) = 2 \cdot \arccos(1) = 0$$
```
*(注：原文公式中 $\alpha_2$ 的计算结果似乎有误，此处按逻辑翻译)*

使用受两个量子比特 1 和 2 控制的 $RY$ 门，进行反向计算。结果在量子比特 0 上重构（见图）。

