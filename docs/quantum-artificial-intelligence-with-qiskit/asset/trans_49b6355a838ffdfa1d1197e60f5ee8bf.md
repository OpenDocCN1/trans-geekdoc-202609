

# 230 基于 Qiskit 的量子人工智能

# (a)

# (b)

![](img/52faec2d621d75e53089d939bb234a82_256_0.png)

图 16.6 ((a)) 三层二叉树由七个量子比特表示，并对这些量子比特应用了量子旋转。我们对量子比特 3 应用旋转 $\theta_0 = 1.98231$，对量子比特 1 应用旋转 $\theta_{10} = 1.42745$，对量子比特 5 应用旋转 $\theta_{00} = 1.9106$。我们使用了 SWAP 操作。对于第三层，我们添加了所有的旋转，对量子比特 0 应用旋转 $\theta_{110} = 1.23096$，对量子比特 2 应用旋转 $\theta_{000} = 2.0944$，对量子比特 4 应用旋转 $\theta_{010} = 1.0472$，对量子比特 6 应用旋转 $\theta_{000} = 1.98231$。量子比特 1 和 5 代表两个子树的第 2 层控制。子树通过由量子比特 3 控制的控制 SWAP 操作与第一层的结果合并。量子比特 3 与量子比特 5 和 3 的测量张量积表示代表八种状态的三个量子比特所需的分布。(b) 代表八种状态的三个量子比特所需的分布。

```
counts = result.get_counts()
plot_histogram(counts)
```

电路的深度并不是自顶向下的划分策略，但我们需要与旋转门相同数量的量子比特，且量子比特在操作过程中处于纠缠态。

# 16.4 QISKIT 振幅编码 

Qiskit 通过 `desired_state` 和 `initialize(desired_state, qubits)` 命令提供了初始化所需状态的可能性，并可以使用 `decompose` 命令来指示结果生成的量子电路，见图 16.7。

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

# 振幅编码 231

16.7 Qiskit 通过 `desired_state` 和 `initialize(desired_state, qubits)` 命令提供了初始化所需状态的可能性，并通过 `decompose` 命令来指示结果生成的量子电路。生成叠加态 $|\psi\rangle$ 振幅的量子电路：

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

# 16.5 SWAP 测试

我们无法访问代表向量的振幅，但我们使用交换测试来估计 $\langle x|y\rangle$。每个状态代表由 $m = \log_2 n$ 个量子比特表示的维度 $n$ 的归一化向量。量子 $|x\rangle$ 和 $|y\rangle$ 在 $l_2$ 范数长度为一：

$||x||_2 = 1, ||y||_2 = 1.$

额外的辅助量子比特 $|0\rangle$ 生成：

$|0\rangle \otimes |x\rangle|y\rangle = |0, x,y\rangle$

在控制量子比特 $|0\rangle$ 上应用 Hadamard 门：

$(H \otimes I \otimes I) \cdot |0,x,y\rangle = \frac{1}{\sqrt{2}} \cdot (|0, x,y\rangle + |1, x,y\rangle) \quad (16.17)$

在 $|x\rangle$ 和 $|y\rangle$ 状态上应用控制交换算符，交换 $|x\rangle$ 和 $|y\rangle$：

$|x\rangle \rightarrow |y\rangle|x\rangle$

当控制量子比特处于状态 $|1\rangle$ 时：

$$\frac{1}{\sqrt{2}} \cdot (|0, x, y\rangle + |1, x, y\rangle) \rightarrow \frac{1}{\sqrt{2}} \cdot (|0, x, y\rangle + |1, y, x\rangle) \quad (16.18)$$

我们在控制量子比特上再次应用一个 Hadamard 门：

$$(H \otimes I_m \otimes I_m) \cdot (\frac{1}{\sqrt{2}} \cdot (|0, x, y\rangle + |1, y, x\rangle)) = \frac{1}{2} \cdot |0\rangle \cdot (|x, y\rangle + |y, x\rangle) + \frac{1}{2} \cdot |1\rangle \cdot (|x, y\rangle - |y, x\rangle) \quad (16.19)$$

测量控制量子比特处于状态 $|0\rangle$ 的概率给出：

$p(0) = |\frac{1}{2} \cdot |0\rangle \cdot (|x, y\rangle + |y, x\rangle) + \frac{1}{2} \cdot |1\rangle \cdot (|x, y\rangle - |y, x\rangle)|^2$
$p(0) = \frac{1}{4} |||x, y\rangle + |y, x\rangle||^2 + \frac{1}{4} |||x, y\rangle - |y, x\rangle||^2$
$p(0) = \frac{1}{2} (1 + \langle x|y\rangle) \quad (16.20)$
$p(1) = \frac{1}{2} (1 - \langle x|y\rangle) \quad (16.21)$

当 $p(0) = 0.5$ 时，$|x\rangle$ 和 $|y\rangle$ 正交；而 $p(0) = 1$ 时表示状态是相同的。内积 $\langle x|y\rangle$ 通常被称为向量之间的夹角 $\varphi$。我们也可以估计欧几里得距离，因为向量是归一化的单位球：$||x-y||_2 \le \sqrt{2} \quad (16.22)$

# 振幅编码 233

$q_0:$
$q_1:$
$q_2:$
![](img/52faec2d621d75e53089d939bb234a82_259_0)

图 16.8 量子比特 0 代表向量 $x$，量子比特 1 代表向量 $y$。经过 10000 次测量 $p(0) = 0.5$。

# 16.5.1 二维向量示例

$x = \begin{pmatrix} \sqrt{0.5} \\ \sqrt{0.5} \end{pmatrix}, y = \begin{pmatrix} \sqrt{0.5} \\ -\sqrt{0.5} \end{pmatrix}$

$\langle x|y\rangle = 0$

# 16.5.2 四维向量示例

$x = \begin{pmatrix} \sqrt{0.1} \\ \sqrt{0.2} \\ \sqrt{0.3} \\ \sqrt{0.4} \end{pmatrix}, y = \begin{pmatrix} \sqrt{0.4} \\ \sqrt{0.3} \\ \sqrt{0.2} \\ \sqrt{0.1} \end{pmatrix}$

$\langle x|y\rangle = \sqrt{0.04} + \sqrt{0.06} + \sqrt{0.06} + \sqrt{0.04} = 0.4 + 2\sqrt{0.06} \approx 0.8899$

注意，结果每次运行可能略有不同。

