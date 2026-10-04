

# Quantummatrix ■ 203

![](img/52faec2d621d75e53089d939bb234a82_229_0.png)

图 15.7. 三个模式 $\mathbf{x}_1 = (1, 0, 0, 1)$；$\mathbf{y}_1 = (1, 0, 0, 1)$；$\mathbf{x}_2 = (1, 0, 0, 0)$；$\mathbf{y}_2 = (0, 1, 0, 0)$ 以及 $\mathbf{x}_3 = (0, 0, 0, 1)$；$\mathbf{y}_3 = (0, 0, 1, 0)$ 相关后四个单元表示的权重矩阵。学习过程与由四个单元表示的学习阶段权重矩阵相同（见图 15.7）。在索引量子比特 $|index_{xj}\rangle$ 与权重向量纠缠后，得到的状态如下，状态 $count_j$ 和 $unit_j$ 由四个量子比特表示，对应四个二进制权重，

```
$|unit_j\rangle = |(w_4w_3w_2w_1)\rangle$
```

（见图 15.8）

```
$\frac{1}{2} \cdot \left( \sum_{j=1}^{4} |index_{xj}\rangle|unit_{j}\rangle \right)$ (15.13)
```

值 $|count_j\rangle$ 是学习矩阵值 $net_j$ 的一元表示。我们引入查询向量 $\mathbf{x}_q = (1, 0, 0, 1)$，

```
$\frac{1}{2} \cdot \left( \sum_{j=1}^{4} |index_{xj}\rangle|unit_{j}\rangle \right) \otimes |query\rangle =$
```

```
$\frac{1}{2} \cdot \left( \sum_{j=1}^{4} |(iz_j)\rangle((c_4c_3c_2c_1))((w_4w_3w_2w_1)) \right) \otimes |1001\rangle$ (15.14)
```

测量量子比特得到的直直方图如图 15.9 所示。在接下来的步骤中，我们描述**激活阶段**（见图 15.10）。为了简单起见，我们将忽略索引量子比特，因为它们在激活阶段并不重要。我们使用处于叠加态的控制位进行量子计数，结果为：

```
$\frac{1}{\sqrt{2}} \cdot (|0\rangle + |1\rangle) \otimes \frac{1}{2} \cdot \left( \sum_{j=1}^{4} |(c_4c_3c_2c_1)_j\rangle[(w_4w_3w_2w_1)_j] \right) \otimes |1001\rangle =
```

# 204 使用 Qiskit 的量子人工智能

![](img/52faec2d621d75e53089d939bb234a82_230_0.png)

图 15.8. 产生睡眠阶段的量子电路。0 到 3 表示向量，量子比特 4 到 7 是关联存储，量子比特 8 到 11 表示计数，量子比特 12 和 13 是索引量子比特，而量子比特 14 是控制量子比特。

```
$$\frac{1}{2\cdot\sqrt{2}} \cdot |0\rangle \left(\sum_{j=1}^{4} (c_{4c_3c_2c_j}) \cdot (w_4w_3w_2w_j)\right) \otimes |1001\rangle +$$
```

```
$$\frac{1}{2\cdot\sqrt{2}} \cdot |1\rangle \left(\sum_{j=1}^{4} (c_{4c_3c_2c_j}) \cdot (w_4w_3w_2w_j)\right) \otimes |1001\rangle \quad (15.15)$$
```

由于向量计数中存在两个 1 且 $count_j \le 2$，应用 $N=2$ 的受控相位操作：

```
$$\frac{1}{2\cdot\sqrt{2}} \cdot |0\rangle \left(\sum_{j=1}^{4} e^{-i\frac{\pi\cdot count_j}{2}} \cdot (c_{4c_3c_2c_j}) \cdot (w_4w_3w_2w_j)\right) \otimes |1001\rangle +$$
```

```
$$\frac{1}{2\cdot\sqrt{2}} \cdot |1\rangle \left(\sum_{j=1}^{4} e^{-i\frac{\pi\cdot count_j}{2}} \cdot (c_{4c_3c_2c_j}) \cdot (w_4w_3w_2w_j)\right) \otimes |1001\rangle \quad (15.16)$$
```

对控制量子比特使用哈达玛门，得到：

```
$$\left(\sum_{j=1}^{4} \frac{1}{2} \cos\left(\frac{\pi\cdot count_j}{2}\right)\right) \cdot |0\rangle \cdot (c_{4c_3c_2c_j}) \cdot (w_4w_3w_2w_j) \otimes |1001\rangle$$
```

```
$$\left(\sum_{j=1}^{4} \frac{1}{2} \sin\left(\frac{\pi\cdot count_j}{2}\right)\right) \cdot |1\rangle \cdot (c_{4c_3c_2c_j}) \cdot (w_4w_3w_2w_j) \otimes |1001\rangle \quad (15.17)$$
```

# 量子矩阵 ■ 205

![](img/52faec2d621d75e53089d939bb234a82_231_0.png)

图 15.9 关联关联存储四个单元的叠加态。量子比特 0 到 3 表示查询向量 $\chi_q = (1, 0, 0, 1)$，量子比特 4 到 7 是关联存储，量子比特 8 到 11 表示计数，量子比特 12 和 13 是索引量子比特，而控制量子比特 14 为零。注意索引量子比特按反序计数的：第一个是 11，第二个是 10，第三个是 01，第四个是 00。

架构由 15 个量子比特描述。量子比特 0 到 3 表示查询向量，4 到 7 是关联存储，8 到 11 表示计数，量子比特 14 是控制量子比特。计数操作通过 cex 门完成（见图 15.8 和 15.10）。

![](img/52faec2d621d75e53089d939bb234a82_231_1.png)

图 15.10 产生激活阶段的量子电路。对量子比特 8 到 11 进行放大。控制量子比特 14。

# 206 使用 Qiskit 的量子人工智能

```python
from qiskit import QuantumCircuit, Aer, execute
from qiskit.quantum_info import Statevector
from qiskit.visualization import plot_histogram
from qiskit.circuit.library import MCXGate
from math import pi
```

```python
qc = QuantumCircuit(15)
#0-3 查询
#4-7 数据
#8-11 计数
#索引指针
#12-13 辅助
#14
```

```python
# 睡眠阶段
#索引指针
qc.h(12)
qc.h(13)
qc.barrier()
# 第一个权重
qc.ccx(12,13,4)
qc.ccx(12,13,7)
qc.barrier()
# 第二个权重
qc.x(12)
qc.ccx(12,13,4)
qc.ccx(12,13,7)
qc.barrier()
# 第三个权重
qc.x(13)
qc.ccx(12,13,6)
qc.barrier()
# 第四个权重
qc.x(12)
qc.x(13)
qc.ccx(12,13,4)
qc.barrier()
```

```python
# 激活阶段
# 查询
qc.x(0)
qc.x(3)
qc.barrier()
qc.ccx(0,4,8)
qc.ccx(1,5,9)
qc.ccx(2,6,10)
```

```python
qc.ccx(3,7)
# 分割
qc.h(14)
qc.barrier()
# 标记
qc.cp(-pi/4,8,14)
qc.cp(-pi/4,9,14)
qc.cp(-pi/4,10,14)
qc.cp(-pi/4,11,14)
qc.barrier()
qc.x(14)
qc.cp(-pi/4,8,14)
qc.cp(-pi/4,9,14)
qc.cp(-pi/4,10,14)
qc.cp(-pi/4,11,14)
qc.barrier()
qc.h(14)
```

```python
simulator = Aer.backend('statevector_simulator')
# 并获取计数
result=execute(qc,simulator).result()
counts = result.get_counts()
plot_histogram(counts)
```

带有查询向量 $x_q = (1, 0, 0, 1)$，由第一个单元后的状态表示的单元 $count=2$，以及两个对应的状态：对于控制 $qubit=1$，值为 $1=\sin(\pi/2)$，测量概率为 $\sin(\pi/2)^2 =0.5$；对于控制 $qubit=0$，值为 $0=\cos(\pi/2)$。第二个单元 $count=1$，两个对应状态：对于控制 $qubit=1$，值为 $1/\sqrt{2}=\sin(\pi/4)$，测量概率为 $\sin(\pi/4)^2=0.5$；对于控制 $qubit=0$，值为 $1/\sqrt{2}=\cos(\pi/4)$。第三个单元 $count=1$，两个对应状态：对于控制 $qubit=1$，值为 $1/\sqrt{2}=\sin(\pi/4)$，测量概率为 $\sin(\pi/4)^2=0.5$；对于控制 $qubit=0$，值为 $1/\sqrt{2}=\cos(\pi/4)$。第四个单元 $count=2$，两个对应状态：对于控制 $qubit=1$，值为 $1=\sin(\pi/2)$，测量概率为 $\sin(\pi/2)^2 =0.5$；对于控制 $qubit=0$，值为 $0=\cos(\pi/2)$。

# 15.4.1 推广

我们推广 $n$ 个单元的描述。在索引量子比特与叠加态纠缠后，得到的状态如下，状态 $count_j$ 和 $unit_j$ 由 $[111]$, $[112]$ 表示，

```
$$\frac{1}{\sqrt{n}} \left( \sum_{j=1}^{n} |index_j\rangle |unit_j\rangle \right) \otimes |query\rangle. \quad (15.18)$$
```

复杂度为 $O(n^2)$。我们应用于控制量子比特（忽略索引量子比特）：

```
$$\frac{1}{\sqrt{2}} (|0\rangle + |1\rangle) \otimes \left( \sum_{j=1}^{n} |count_j\rangle |unit_j\rangle \right) \otimes |query\rangle = $$
$$\frac{1}{\sqrt{2} \cdot n} \cdot |0\rangle \left( \sum_{j=1}^{n} |count_j\rangle |unit_j\rangle \right) \otimes |query\rangle + $$
$$\frac{1}{\sqrt{2} \cdot n} \cdot |1\rangle \left( \sum_{j=1}^{n} |count_j\rangle |unit_j\rangle \right) \otimes |query\rangle \quad (15.19)$$
```

