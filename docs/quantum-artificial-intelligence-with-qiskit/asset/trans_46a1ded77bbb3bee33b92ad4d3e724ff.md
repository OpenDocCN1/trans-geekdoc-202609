

# 使用 Qiskit 的 80 量子人工智能

![](img/52faec2d621d75e53089d939bb234a82_106_0.png)

**图 5.1** Grover 放大的周期性，y 轴表示解的幅度，x 轴表示旋转次数 $r$。m=8$ 代表 256 个状态。当 $k=1$ 时，最大幅度值为 1；当 $k=8$ 时，最大幅度值为 $0.3535=\frac{1}{\sqrt{8}}$，且周期较小 [121]。

## 5.3.2 电路表示

Grover 放大（对于 $m \geq 2$）基于 $G_m=-Q_z$。该酉算符反转了 $|0\rangle$ 的符号：

$$\Lambda_m \cdot |0\rangle = -|0\rangle$$

对于 $|x\rangle \neq |0\rangle$

$$\Lambda_m \cdot |x\rangle = -|x\rangle$$

然后我们可以写为：

$$G_m=-Q_z=-I_m+2 \cdot P_m=2 \cdot P_m-I_m=(H_m \cdot \Lambda_m \cdot H_m) \quad (5.17)$$

其中



$$H_m \cdot \Lambda_m \cdot H_m=\begin{pmatrix} 1-\frac{2}{n} & \dots & \dots & \dots \\ \dots & \frac{2}{n} & \dots & \frac{2}{n} \\ \dots & \dots & \dots & \dots \\ \dots & \frac{2}{n} & \dots & 1-\frac{2}{n} \end{pmatrix} \quad (5.18)$$

## 5.4 矩阵表示法的 NumPy 示例

在解释如何用量子门表示该算法之前，我们将使用矩阵表示法演示 Grover 放大的原理。我们将使用 *Python* 和作为 *qiskit* 安装部分的 *NumPy* 库。我们将演示 $m=3$ 的示例，这意味着 $8=2^3$ 个不同的状态。首先，我们将通过（张量）克罗内克积操作 $kron$ 对 $H$ 矩阵构建 $H_3$ 矩阵。

```python
import numpy as np
np.set_printoptions(precision=4)
```

# Grover 放大

```python
H=np.matrix([[1, 1], [1, -1]])
H=H*1/np.sqrt(2)
np.view(H)
print("H=\n",H)
```

得到 Hadamard 矩阵

```
H=
[[ 0.7071 -0.7071]
[ 0.7071 -0.7071]]
```

使用克罗内克积操作定义 $H_3$

```
H2=np.kron(H,H)
H3=np.kron(H,H2)
print("H3=\n",H3)
```

```
H3=
[[ 0.3536 0.3536 0.3536 0.3536 0.3536 0.3536 0.3536 0.3536]
[ 0.3536 -0.3536 0.3536 -0.3536 -0.3536 -0.3536 0.3536 -0.3536]
[ 0.3536 -0.3536 0.3536 -0.3536 -0.3536 -0.3536 0.3536 -0.3536]
[ 0.3536 -0.3536 -0.3536 -0.3536 -0.3536 -0.3536 -0.3536 -0.3536]
[ 0.3536 0.3536 0.3536 -0.3536 -0.3536 -0.3536 -0.3536 -0.3536]
[ 0.3536 -0.3536 -0.3536 -0.3536 -0.3536 -0.3536 0.3536 -0.3536]
[ 0.3536 -0.3536 -0.3536 -0.3536 -0.3536 -0.3536 0.3536 -0.3536]
[ 0.3536 -0.3536 -0.3536 -0.3536 -0.3536 -0.3536 0.3536 -0.3536]]
```

然后我们定义 $\Lambda_m$

```
L3=np.matrix([[-1, 0, 0, 0, 0, 0, 0, 0],
[ 0, 1, 0, 0, 0, 0, 0, 0],
[ 0, 0, 1, 0, 0, 0, 0, 0],
[ 0, 0, 0, 1, 0, 0, 0, 0],
[ 0, 0, 0, 0, 1, 0, 0, 0],
[ 0, 0, 0, 0, 0, 1, 0, 0],
[ 0, 0, 0, 0, 0, 0, 1, 0],
[ 0, 0, 0, 0, 0, 0, 0, 1]])
```

and

```
G=-H3+L3
print("G=\n",G)
```

```
G=
[[-0.75 0.25 0.25 0.25 0.25 0.25 0.25 0.25]
[ 0.25 -0.75 0.25 0.25 0.25 0.25 0.25 0.25]
[ 0.25 0.25 -0.75 0.25 0.25 0.25 0.25 0.25]
[ 0.25 0.25 0.25 -0.75 0.25 0.25 0.25 0.25]
[ 0.25 0.25 0.25 0.25 -0.75 0.25 0.25 0.25]
[ 0.25 0.25 0.25 0.25 0.25 -0.75 0.25 0.25]
[ 0.25 0.25 0.25 0.25 0.25 0.25 -0.75 0.25]
[ 0.25 0.25 0.25 0.25 0.25 0.25 0.25 -0.75]]
```

在下一步中，我们表示等分布幅度的态向量并将解标记为负号

```
a=1/np.sqrt(8)
x1=np.array([a,a,a,-a]) # 原文长度不一致
print("x1=\n",x1)
x1=[0.3536 0.3536 0.3536 -0.3536]
```

并在 Grover 放大中执行一步，得到的幅度为

```
x1=G.dot(x1)
print("x1=\n",x1)
x1=[-0.1768 0.1768 0.1768 0.8839 0.1768 0.1768]]
```

以及带有结果幅度的第二次迭代

```
x2=np.array([0.1768, 0.1768, 0.1768, -0.8839, 0.1768, 0.1768]) # 原文长度不一致
x2=G.dot(x2)
print("x2=\n",x2)
x2=[-0.0884 -0.0884 -0.0884 0.9723 -0.0884 -0.0884]] # 注意长度
```

通过两次旋转，我们实现了最大幅度值，对应的概率为 $0.94537 = |0.9723|^2$。第三次旋转后，由于 Grover 放大的周期性，幅度开始缩小（见图 5.1）。

## 5.5 分解

对于 Grover 放大，我们有 $G_m = -(H_m \cdot \Lambda_m \cdot H_m)$。我们如何用量子门分解 $\Lambda_m$ 呢？我们知道对于

$$\frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix} \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix} \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix} = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$$

和

$$\frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix} \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix} = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$$

对于三个量子比特，我们可以相应地定义 $\Lambda_3$：

$X_3 = X \otimes X \otimes X$
$H_0 = I \otimes I \otimes H$
$\Lambda_3 = X_3 \cdot H_0 \cdot CCX \cdot H_0 \cdot X_3$

对于 $\Lambda_3$ 带有负符号，且 $G = -H_3 + L_3$ 我们可以通过以下电路表示

```python
import numpy as np
from qiskit import QuantumCircuit, assemble
from qiskit.visualization import array_to_latex, plot_histogram
from qiskit.aer import Aer

qc = QuantumCircuit(3)
qc.h(0)
qc.h(1)
qc.h(2)
qc.ccx(0, 1, 2)
qc.h(0)
qc.h(1)
qc.h(2)
```

然后得到酉算符

```python
qc.save_unitary()
backend = Aer.get_backend('qasm_simulator')
tobj = assemble(qc, backend)
result = backend.run(tobj).result()
unary = result.data()['unitary']
print(f"Size of unitary: {unary.shape}")
array_to_latex(unary)
```

得到的 $G_3$ 矩阵

```python
G3=np.matrix([[-0.75, 0.25, 0.25, 0.25, 0.25, 0.25, 0.25, 0.25],
[ 0.25, -0.75, 0.25, 0.25, 0.25, 0.25, 0.25, 0.25],
[ 0.25, 0.25, -0.75, 0.25, 0.25, 0.25, 0.25, 0.25],
[ 0.25, 0.25, 0.25, -0.75, 0.25, 0.25, 0.25, 0.25],
[ 0.25, 0.25, 0.25, 0.25, -0.75, 0.25, 0.25, 0.25],
[ 0.25, 0.25, 0.25, 0.25, 0.25, -0.75, 0.25, 0.25],
[ 0.25, 0.25, 0.25, 0.25, 0.25, 0.25, -0.75, 0.25],
[ 0.25, 0.25, 0.25, 0.25, 0.25, 0.25, 0.25, -0.75]])
```

## 5.6 Qiskit 示例

在下一步中，我们将 Grover 放大应用到标记的量子比特态。我们的解对应布尔公式

$-x \wedge y \wedge \neg z$

在该公式下为真，即 $x=0, y=1, z=0$。在这种情况下，由算符函数确定的态为 $o(010)=1$，其解编码为 $(-1)^{(x)}$。

对于算符函数 $T$

$$T \cdot |x\rangle = |o(x) \oplus c\rangle$$

其中

$$H_0 = I \otimes I \otimes I \otimes H$$

$$H_0 \cdot T \cdot H_4 = \frac{1}{\sqrt{8}} \sum_{x \in B^3} (-1)^{o(x)} \cdot |x\rangle$$

函数 $o(x)$ 的值被编码为 $(-1)^{o(x)}$，如图所示（见图 5.2）。

```python
import numpy as np
from qiskit import QuantumCircuit, assemble
from qiskit.visualization import array_to_latex, plot_histogram
from qiskit.aer import Aer

qc = QuantumCircuit(3)
qc.h([0,1,2])
qc.x(2) # 标记
qc.ccx(0,1,2)
qc.x(2)
qc.h([0,1,2])

# 获取酉算符
qc.save_unitary()
backend = Aer.get_backend('qasm_simulator')
tobj = assemble(qc, backend)
result = backend.run(tobj).result()
unary = result.data()['unitary']
print(f"Size of unitary: {unary.shape}")
array_to_latex(unary)
```

