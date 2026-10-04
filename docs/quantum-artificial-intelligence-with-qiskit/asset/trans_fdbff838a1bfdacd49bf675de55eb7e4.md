

## 量子关联记忆 ■ 185

| | | | | | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| q_0 | X | | | | | | | | | | | | |
| q_1 | | X | | | | | | | | | | | |
| q_2 | | | X | | | | | | | | | | |
| q_3 | | | | X | | | | | | | | | |
| q_4 | | | | | X | | | | | | | | |

(a)

![](img/52faec2d621d75e53089d939bb234a82_211_0.png)

图14.2 (a) 对索引比特 3 和 4 的 Grover 放大。(b) 由于量子比特与模式纠缠，我们没有得到正确的的结果。

```python
def store():
    qc = QuantumCircuit(5)
    #First pattern
    qc.ccx(3,4,0)
    qc.ccx(3,4,2)
    qc.barrier()
    #Second pattern
    qc.x(3)
    qc.ccx(3,4,0)
    qc.ccx(3,4,1)
    qc.x(3)
    qc.barrier()
    #Third pattern
    qc.x(4)
    qc.ccx(3,4,0)
    qc.ccx(3,4,1)
    qc.ccx(3,4,2)
    qc.x(4)
    qc.barrier()
    #Fourth pattern
    qc.x(3)
    qc.x(4)
    qc.ccx(3,4,1)
    qc.x(4)
```

# 186 ■ 使用 Qiskit 的量子人工智能

| | 0 | 0 |
|---|---|---|
| q_0: | | |
| q_1: | 1 | |
| q_2: | 2 Store | 2 Store! |
| q_3: | H | 3 | H |
| q_4: | 4 | 4 | H |
| q_5: | X H | X | |

![](img/52faec2d621d75e53089d939bb234a82_2_2..))

14.3 (a) 对索引比特进行 Grover 放大，我们需要取消索引比特与模式的纠缠。对于四个状态，我们只需要一次旋转。(b) 我们通过一个状态测量正确的结果 $index_2 = |01|$。

```python
qc.x(3)
qc.name="Store"
return qc
```

```python
def store_inv():
    qc=store()
    qc_inv=qc.inverse()
    qc_inv.name="StoreInv"
    return qc_inv
```

```python
qc = QuantumCircuit(6)
#0-2 data
#Index
#3-4
qc.h(3)
qc.h(4)
```

```python
#Aux Bit
qc.x(5)
qc.h(5)
```

## 量子关联记忆 ■ 187

```python
qc.barrier()
qc.append(store(),range(5))
qc.barrier()
#Dracle
gate = MCX(3)
qc.append(gate,[0, 1, 2, 5])
qc.barrier()
qc.append(store_inv(),range(5))
qc.barrier()
#Redo Aux Bit
qc.h(5)
qc.barrier()
#Diffuser
qc.h(3,4)
qc.z(3,4)
qc.cz(3,4)
qc.h(3,4)
```

对于四个状态，我们只需要一次旋转。我们通过一个状态测量正确的结果 $index_2 = |10|$（见图14.3 (b)）。与其取消，我们希望对代表模式和索引的五个量子比特应用 Grover 算法。Grover 放大一次旋转后的状态表明某些奇怪的事情正在发生。

## 14.2 量子关联记忆 (QuAM)

在 Ventura 和 Martinez 提出的 QuAM 中，变体 Grover 搜索算法用于确定查询向量 [114, 115, 110] 的答案。为了准备维度为 $n > m$ 的 $m$ 个线性无关向量，Ventura 和 Martinez [114, 115] 提出了一种方法，后由 [111] 简化，准备成本为 $O(n-m)$，需要 $\log_2(m)$ 个单位。查询成本相对于传统计算机的 $O(\sqrt{m})$。为了理解变体 Grover 搜索算法及其结果，我们生成简单的叠加态

$|\psi\rangle = \frac{1}{2}(|1100\rangle + |1001\rangle + |1111\rangle + |0110\rangle)$

以便我们可以跟踪幅度分布
$$\frac{1}{2}(0,0,0,0,1,0,1,0,1,0,1,0,0,1)^T.$$

我们注意到幅度分布不是均匀的，四个量子比特的均匀分布对应于

$$\frac{1}{4}(1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1)^T.$$

这可能是问题的原因吗？

# 188 使用 Qiskit 的量子人工智能

| | | | | | | |
|---|---|---|---|---|---|---|
| q_0: | 0 | | | | | | |
| q_1: | | 1 | | | | | |
| q_2: | | | 2 Store | | | |
| q_3: | | | | 3 | | | |
| q_4: | | | | | 4 | | |
| q_5: | X | | | | | H | |

![](img/52faec2d621d75e53089d939bb234a82_214_0.png)

**图 14.4** (a) 与其取消计算，我们希望对代表模式和索引的五个量子比特应用 Grover 算法。(b) Grover 放大一次旋转后的状态表明某些事情正在发生。

## 14.2.1 非均匀分布

从初始分布开始，我们用负相位标记目标态 $|0110>$：

$$(0,0,0,1,0,0,-1,0,0,0,0)^T$$
并执行 Grover 旋转，结果为：
$$\frac{1}{8}(-1,-1,-1,-3,-1,-1,-1,-3)^T$$
我们再次用负相位标记目标态 $|0110>$ 并执行 Grover 旋转，结果为：
$$(-0.2,-0.2,-0.2,0.3,-0.2,0,2,3)^T$$
代表我们分布的四个状态具有高幅度（为了清晰起见）。用负相位标记目标态 $|0110>$ 并进行 Grover 旋转

$(0.02,0.02,0.02,0.5,0.02,0.02,-0.4,0.02,0.5)^T$
所有基态具有几乎相同的分布。

Ventura 和 Martinez 提出了一种变体 Grover 搜索算法 [114,115]。在此之前，从初始分布，我们用负相位标记目标态 $|0110>$：

$$\frac{1}{2}(0,0,0,1,0,0,-1,0,0,0)^T$$
并执行 Grover 旋转，结果为：
$$\frac{1}{8}(-1,-1,-1,-3,-1,-1,-1,-3)^T$$
然而，现在我们用负相位标记代表我们分布的四个状态并执行 Grover 旋转，结果为：
$$\frac{1}{8}(1,1,-1,-1,1,-1,-1)^T$$
我们再次用负相位标记代表我们分布的四个状态并执行 Grover 旋转，结果为：

$$(0,0,0,0,0)^T$$
指示目标态。qiskit 电路（见图14.5）表示为：

```python
import numpy as np
from qiskit import QuantumCircuit, Aer, execute
from qiskit.quantum_info import Statevector
from qiskit.visualization import plot_histogram
from qiskit.circuit.library import MCGate

qc = QuantumCircuit(5)
#0-1 data
#Index
#2-3
qc.h(2)
qc.h(3)

#Aux Bit
qc.x(4)
qc.h(4)
```

```python
qc.barrier()
#First pattern
qc.ccx(2,3,0)
qc.ccx(2,3,1)
```

```python
qc.barrier()
#Second pattern
qc.x(2)
qc.ccx(2,3,0)
qc.x(2)
```

```python
qc.barrier()
#Third pattern
qc.x(3)
qc.ccx(2,3,1)
qc.x(3)
```

```python
qc.barrier()
#Fourth pattern
qc.x(2)
qc.x(3)
qc.ccx(2,3,1)
```

```python
qc.barrier()
#Oracle
qc.x(0)
qc.x(3)
gate = MCGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(3)
qc.x(0)
qc.barrier()
qc.h(4)
```

```python
# Diffuser 0, 1, 2, 3
qc.barrier()
qc.h([0,1,2,3])
qc.x([0,1,2,3])
qc.h(0)
gate = MCGate(3)
qc.append(gate,[1,2,3,0])
qc.h(0)
qc.x([0,1,2,3])
qc.h([0,1,2,3])
```

```python
#Second rotation
qc.barrier()
```

## 量子关联记忆 ■ 191

```python
qc.h(4)
qc.barrier()

#Oracle Trick
qc.x(0)
qc.x(3)
gate = MCGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(3)
qc.x(0)

qc.x(2)
qc.x(3)
gate = MCGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(3)
qc.x(2)

qc.x(1)
qc.x(2)
gate = MCGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(1)

gate = MCGate(4)
qc.append(gate,[0,1,2,3,4])
qc.barrier()
qc.h(4)
#

# Diffuser 0, 1, 2, 3
qc.barrier()
qc.h([0,1,2,3])
qc.x([0,1,2,3])
qc.h(0)
gate = MCGate(3)
qc.append(gate,[1,2,3,0])
qc.h(0)
qc.x([0,1,2,3])
qc.x([0,1,2,3])

#Third rotation
qc.barrier()
qc.h(4)
qc.barrier()

#Oracle Trick
qc.x(0)
qc.x(3)
gate = MCGate(4)
```

## 192 使用 Qiskit 的量子人工智能

```python
qc.append(gate,[0,1,2,3,4])
qc.x(3)
qc.x(0)

qc.x(2)
qc.x(3)
gate = MCGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(3)
qc.x(2)

qc.x(1)
qc.x(2)
gate = MCGate(4)
qc.append(gate,[0,1,2,3,4])
qc.x(1)

gate = MCGate(4)
qc.append(gate,[0,1,2,3,4])
```

