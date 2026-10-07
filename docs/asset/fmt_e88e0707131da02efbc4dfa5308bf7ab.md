
如果我们将 $U^w$ 应用于 $|u\rangle$，得到：

```math
$U^w|u\rangle = U^{w-1}\cdot(e^{2\pi i\theta}|u\rangle) = (e^{2\pi i\theta})^w \cdot |u\rangle = e^{2\pi i\theta w}|u\rangle. \quad (20.2)$
```

然而，我们不会获得任何信息，因为 $|u\rangle$ 是等效状态，在执行测量时它们表示相同的状态。我们不使用酉算符 $U^w$，而是使用控制 $U^w$ 算符。如果控制是目标比特，$CU^w$ 是可逆的，并定义了到量子比特的注入映射

```math
$CU^w|0\rangle = |0\rangle, CU^w|1\rangle = (e^{2\pi i\theta})^w \cdot |u\rangle.$
```

QFT 表示为单量子比特操作的张量积。QFT 可以分解为 $m$ 个单量子比特操作的张量积，

```math
$|y\rangle = F_m \cdot |x\rangle = \frac{1}{\sqrt{2^m}} \sum_{y \in B^m} e^{2\pi i \cdot y \cdot x} \cdot |y\rangle = \frac{1}{\sqrt{2^m}} \left(|0\rangle + e^{2\pi i \cdot x_1}|1\rangle\right) \otimes \left(|0\rangle + e^{2\pi i \cdot x_2}|1\rangle\right) \otimes \left(|0\rangle + e^{2\pi i \cdot x_3}|1\rangle\right).$
```如果设置 $\theta=0.x_m \cdots x_1$，我们可以重写方程

```math
$|y\rangle = F_m \cdot |x\rangle = \frac{1}{\sqrt{2^m}} \sum_{y \in B^m} e^{2\pi i \cdot y \cdot x} \cdot |y\rangle = \frac{1}{\sqrt{2^m}} \left(|0\rangle + e^{2\pi i \cdot x_1}|1\rangle\right) \otimes \left(|0\rangle + e^{2\pi i \cdot x_2}|1\rangle\right) \otimes \left(|0\rangle + e^{2\pi i \cdot x_3}|1\rangle\right).$
```

对于 $m$ 个量子比特，以以下方式定义 $CU_{j+1}$。对于 $j \in \{0, 1, 2, \cdots, m-1\}$，控制比特 $j+1$ 应用于目标比特 $|u\rangle$，否则不是。算法的第一步是构建

```math
$|0^{\otimes m}\rangle|u\rangle$
```

其中 $|u\rangle$ 是酉算符的特征向量。

## 20.1.1 $T$ 门的示例

$T$ 门对应于酉矩阵

```
$T = \begin{pmatrix} 1 & 0 \\ 0 & e^{i\pi/4} \end{pmatrix}
```

对于特征向量 $|1\rangle$ 和特征值 $e^{2\pi\theta}$

```
$U \cdot |u\rangle = T|u\rangle = e^{2\pi\theta} \cdot |u\rangle = e^{2\pi\theta} \cdot |1\rangle \quad (20.9)$
```

相位 $\theta=\frac{1}{8}$ 是因为

```
$T|1\rangle = e^{2\pi\theta} = e^{i\pi/4} \cdot |1\rangle = e^{2\pi/4} \cdot |1\rangle$.
```

相位估计算法将 $T$ 的相位写入 $m$ 个量子比特中，在我们简单的例子中 $m=3$。$m$ 的值决定了结果的精度。

```
$\theta = x_0x_1x_2 = \frac{x}{2^3}$
```

受控 $T$ 门由受控相位门 $CP(\lambda)$ 表示，其中 $\lambda=\pi/4$。电路由 4 个量子比特组成，量子比特 0, 1, 2 代表控制寄存器中的 3 个量子比特。量子比特 3 代表特征向量 $|1\rangle$。控制寄存器通过 Hadamard 门映射为叠加态，量子比特 4 通过 NOT 门初始化为特征向量 $|1\rangle$。控制寄存器控制应用于目标特征向量 $|1\rangle$ 的酉操作 $T$，从而得到三个控制量子比特的傅里叶表示。为了估计相位 $\theta$，我们对 3 个控制量子比特执行逆量子傅里叶变换 (QFT)，并测量这三个量子比特以估计出 $\theta$

```
$x = |q_2q_1q_0\rangle$
```

和

```
$\theta = \frac{x}{2^3}$
```

电路所示（见图 20.1）

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

| | | | | | | | | |

|---|---|---|---|---|---|---|---|

| q_0 | H | | | | | | | |

| q_1 | H | | | | | | | |

| q_2 | H | P(n/4) | P(n/4) | P(n/4) | P(n/4) | P(n/4) | | |

| q_3 | X | | | | | | | | |

![](img/52faec2d621d75e53089d939bb234a82_284_1.png)

![](img/52faec2d621d75e53089d939bb234a82_284_2.png)

**图 20.1** (a) 使用三个量子比特精度估计 T 门相位的电路。电路由 4个量子比特组成，量子比特 0, 1, 2 代表控制寄存器，量子比特 3 代表特征向量 |1>。控制寄存器控制应用于目标特征向量 |1> 的酉操作 T。为了估计相位，我们对三个控制量子比特执行逆 QFT。(b) 测量值对应于二进制值 001，等于1，表示相位 $\theta=0.125 = 1/2^3$。

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

测量值对应于二进制值 001，等于1，表示相位。我们使用的量子比特 (m) 越多，精度越高。但在在这个简单的示例中，三个控制量子比特对相位 $\theta$ 得到了良好的估计 $$\theta = \frac{1}{2^3} = \frac{1}{8}$$

## 量子计数 (QUANTUM COUNTING)

Grover 放大基于酉操作 $G$，在 $n$ 个状态中 $|solution\rangle$ 和 $|non\rangle$ 之间。相位 $\theta$ 

```python
qc.append(crit, [3,4,5,6,7])
qc.append(crit, [3,4,5,6,7])
qc.append(crit, [3,4,5,6,7])
qc.append(crit, [3,4,5,6,7])
qc.append(crit, [3,4,5,6,7])
qc.append(crit, [3,4,5,6,7])
# 对计数比特进行逆量子FT变换
qc.append(qft_dagger, [0,1,2,3])
# 测量计数比特
qc.measure([0,1,2,3], [0,1,2,3])
```

simulator = Aer.get_backend('qasm_simulator')

result = execute(qc,simulator, shots=1000).result()

counts = result.get_counts()

plot_histogram(counts)

```

最大测量值对应于二进制值 0011（十进制 3）或 1101（十进制 13），参见[图 20.3 (b)](fig203)。相位为 $\theta_1 = \frac{7}{16}$ 或 $\theta_2 = \frac{13}{16}$，对应于两个特征值 $\lambda_1 = e^{i\theta}$ 或 $\lambda_2 = e^{-i\theta}$，具有正相位和负相位，且

$$\sin^2(\theta) = \sin^2(-\theta)$$

$$k = 4.9 \approx \sin^2\left(\frac{\pi \cdot 3}{16}\right) \cdot 16 = \sin^2\left(\frac{\pi \cdot 13}{16}\right) \cdot 16.$$

具有近似正确的答案：

我们使用的控制比特（$m$）越多，获得的精度就越高。在我们的示例中，四个控制比特只能对相位 $\theta$ 进行近似估计。例如，如果标记在 16 个状态中找到了 5 个解（$k=5$），我们测量到的完全相同的最大值 0011（十进制 3）或 1101（十进制 13）。需要更多的控制比特来获得更精确的计数。识别相位 $\theta_1$ 和 $\theta_2$ 的两个最大值的计数将会更高，而其他状态的计数将接近零。

![](img/52faec2d621d75e53089d939bb234a82_289_0.png)

![](img/52faec2d621d75e53089d939bb234a82_289_1.png)

**图 20.3** (a) 使用电路库实现了受控 Grover 算子，其门在 16 个状态中具有 4 个解（$k=4$）（$m^*=4$）。该电路由 8 个比特组成，比特 0, 1, 2, 3 代表控制寄存器中的 4 个比特。比特 5 到 7 代表表示 16 个状态的计算基中的四个 个比特。所有比特都通过 Hadamard 门映射到叠加态。控制寄存器控制酉算符 $G$，产生三个控制比特的傅里叶基表示。为了估计相位 $\theta$，我们对这 4 个控制比特执行逆 QFT 并测量这 4 个比特。(b) 最大测量值对应于二进制值 0011（十进制 3）或 1101（十进制 13），指示相位 $\theta_1 = \pi \cdot 3/16$ 或 $\theta_2 = \pi \cdot 13/16$。

# 量子感知机

经典感知机描述了一种监督学习算法，它只考虑线性可分的问题，在这种问题中组可以通过超平面分开。量子感知机通常不包含学习，而是高效地计算 $net$ 的输出。量子感知机可以基于叠加态作为更大系统的构建块，并行处理任意数量的输入。我们展示一个双比特的简单示例：

# 1.1 使用 Kitaev 算法进行计数

量子感知机通过受控相位门在 $m$ 个比特中写入 $net$ 的相位估计。

$\lambda = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$

```

带有 $\theta$ 的特征值

$$net = \frac{\theta}{2^{m}}$$

```

$$net = \frac{\theta}{2^{m}}$$

```

Kitaev 相位估计算法通过 $m$ 个比特在控制寄存器中写入 $net$ 的相位。

```

$$net \cdot \dots \cdot x_2$$

```

# 2.2 量子感知机

# HHL

线性方程组的量子算法是预计比其经典算法提供加速的主要基础算法之一。为了纪念它的发明者 Aram Harrow、Avinatan Hassidim 和 Seth Lloyd，它被命名为 HHL。它将成为任何量子机器学习算法中最有子程序之一，因为几乎所有的机器学习都使用了某种形式的线性方程组。例如，在支持向量机和量子支持向量机中，通过拉格朗日乘子的最优值来使目标函数最大化是基于求解线性方程的。我们将描述 HHL 算法，使用 qiskit 哈密顿量逐步给出一个示例，并指明算法的限制条件。

## 22.1 线性方程组的量子算法

我们在许多不同领域的现实应用中都能看到方程组。对于一个可逆的复矩阵 $n \times n$ $A$ 和一个复向量 $\mathbf{b}$

$$A \cdot \mathbf{x} = \mathbf{b}$$

我们想要找到 $\mathbf{x}$。如果 $A^* = A$（对于实数矩阵 $A^T = A$），则 $A$ 可以由线性谱分解表示：

$$A = \lambda_1 \cdot |u_1\rangle\langle u_1| + \lambda_2 \cdot |u_2\rangle\langle u_2| + \cdots + \lambda_n \cdot |u_n\rangle\langle u_n|$$

以及

$$A^{-1} = \frac{1}{\lambda_1} |u_1\rangle\langle u_1| + \frac{1}{\lambda_2} |u_2\rangle\langle u_2| + \cdots + \frac{1}{\lambda_n} |u_n\rangle\langle u_n|$$

得出：

$$A^{-1} \cdot |u_j\rangle = \frac{1}{\lambda_j} |u_j\rangle$$

将 $|b\rangle$ 写为 $A$ 特征向量的线性组合：

$$|b\rangle = \sum_{j} |u_j\rangle\langle u_j|b\rangle$$

导致：

$$A \cdot |b\rangle = \sum_{j} \lambda_j |u_j\rangle \langle u_j|b\rangle \quad (22.6)$$

以及

$$|x\rangle = A^{-1} \cdot |b\rangle = \sum_{j} \lambda_j^{-1} |u_j\rangle \langle u_j|b\rangle \quad (22.7)$$

我们如何有效地估计特征值呢？当我们知道对于厄米特矩阵 $A$，$e^{-tA}$ 等于：

$$U = e^{tA} = e^{t\lambda_1} |u_1\rangle \langle u_1| + e^{t\lambda_2} |u_2\rangle \langle u_2| + \cdots + e^{t\lambda_n} \cdot |u_n\rangle \langle u_n| \quad (22.8)$$

以及

$$U^* = U^{-1} = e^{-tA} = e^{-t\lambda_1} |u_1\rangle \langle u_1| + e^{-t\lambda_2} |u_2\rangle \langle u_2| + \cdots + e^{-t\lambda_n} \cdot |u_n\rangle \langle u_n| \quad (22.9)$$

满足

$$U \cdot U^* = I$$

使用 Kitaev 相位算法，我们就可以估计未知的特征值 $e^{2\pi i}$。如果我们将 $U$ 应用于 $|u_j\rangle$，我们得到：

$$U \cdot |u_j\rangle = e^{2\pi i} |u_j\rangle = e^{i\lambda_j} |u_j\rangle \quad (22.10)$$

我们不需要对 $A$ 的特征向量和特征值为分解，因为这会导致循环问题。

## 2.2 算法

注意我们可以：

- 这种表示类似于演化算符 $U_t = e^{-itH}$，其中 $t=1$ 且 $A=H$ 是哈密顿算子。在量子计算机上实现给定的哈密顿演化的过程被称为哈密顿模拟。如果哈密顿矩阵 $H$ 是稀疏的，则可以高效实现哈密顿模拟。

- 我们不需要知道 $U$ 的特征向量 $|u_j\rangle$。因为量子态 $|b\rangle$ 可以分解为正交基：

$$|b\rangle = \sum_{j} |u_j\rangle\langle u_j|b\rangle \quad (22.11)$$

### 2.2.1 哈密顿模拟

在量子计算机上实现给定的哈密顿演化的过程被称为哈密顿模拟。

$$|x(t)\rangle = e^{-itH} \cdot |x(0)\rangle = U_t \cdot |x(0)\rangle \quad (22.12)$$

挑战在于矩阵指数的应用是昂贵的。寻找可靠且准确的计算矩阵指数的方法非常困难，这仍然是目前的研究课题。
