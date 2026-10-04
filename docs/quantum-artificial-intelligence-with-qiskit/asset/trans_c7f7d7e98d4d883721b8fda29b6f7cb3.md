

# 使用 Qiskit 的 86 量子人工智能

![](img/52faec2d621d75e53089d939bb234a82_112_0.png)

图 5.3 量子门谕（Quantum oracle），用负号标记状态 [010] 并展示了 Grover 放大。

```python
qc.draw(fold=140)

simulator = Aer.get_backend('statevector_simulator')
final_state = simulator.run(qc).result().get_statevector
```

```python
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector") = 

StateVector = [0 0 0 0 0 0 0 0 0.1768 0.1768 0.8839 0.1768 0.1768 0.1768 0.1768 0.1768]
```

在下一步中，我们将使用 qasmis 模拟器执行两次旋转。我们不进行负号操作

> $G_3 = -H_3 \cdot \Lambda_3 \cdot H_3$

为了得到正确的结果，改变的是整体幅的负号。这对于最终概率没有影响，因此 Grover 放大可以简化为（见图 5.4 和 5.5）：

> $G_3 = H_3 \cdot \Lambda_3 \cdot H_3$

```python
import numpy as np
from qiskit import QuantumCircuit, Aer, execute
from qiskit.visualization import plot_histogram
from qiskit.circuit.library import MCXGate

qc = QuantumCircuit(4,3)
qc.h([0,1,2])
# 准备辅助位
qc.x(3)
qc.h(3)
# 谕门
qc.barrier()
qc.x(0)
qc.x(2)
gate = MCXGate(3)
qc.append(gate, [0, 1, 2, 3])
qc.x(0)
qc.x(2)
```

```python
# 扩散器
qc.barrier()
qc.h(3)
qc.barrier()
qc.h([0,1,2])
qc.x([0,1,2])
qc.h(0)
qc.ccx(1,2,0)
qc.h(0)
qc.x([0,1,2])
qc.h([0,1,2])
qc.barrier()
qc.h(3)
# 谕门
qc.barrier()
qc.x(0)
qc.x(2)
gate = MCGate(3)
qc.append(gate, [0, 1, 2, 3])
qc.x(0)
qc.x(2)
qc.barrier()
qc.h(3)
# 扩散器
qc.barrier()
qc.h([0,1,2])
qc.x([0,1,2])
qc.h(0)
qc.ccx(1,2,0)
qc.h(0)
qc.x([0,1,2])
qc.h([0,1,2])
qc.barrier()
qc.measure(0,0)
qc.measure(1,1)
qc.measure(2,2)
qc.draw(fold=90)
```

## 5.7 反计算 (UN-COMPUTATION)

在量子计算中，无法将信息重置为代表初始状态的模式。相反，我们将输出计算回输入。在我们的谕门中

> $T = (X \otimes I \otimes X \otimes I) \cdot MCX \cdot (X \otimes I \otimes X \otimes I)$

```
q_0: ┌──X──X─┐ ┌──H──X──H──X──X─┘
q_1: ┌──H─┘ ┌──X──X─┘
q_2: ┌──X──X─┐ ┌──X──X─┘
q_3: ┌──H─┘ └┴─────────────────┴M─┘
c_0: ┌───────────────────────┐
c_1: ┌───────────────────────┐
c_2: ┌───────────────────────┐
q_0: ┌──X──X─┐ ┌──X──X──X──X──X──M─┘
q_1: ┌──H─┘ ┌──X──X─┘
q_2: ┌──X──X─┐ ┌──X──X──X─┘
q_3: ┌──X─┘ └─────────────────┴M─┘
q_0: ┌───────────────────────┐
q_1: ┌───────────────────────┐
c_2: ┌───────────────────────┐
```

图 5.4 量子谕门，用负号标记状态 [010] 和两次 Grover 放大。

反计算由操作 (X ⊗ I ⊗ X ⊗ I) 表示。我们可能会问，如果不进行反计算并将我们的谕门简单地定义为

> $T = MCX \cdot (X \otimes I \otimes X \otimes I)$

![](img/52faec2d621d75e53089d939bb234a82_112_0.png)

图 5.5 两次 Grover 放大后的直方图。

反计算由操作 (X ⊗ I ⊗ X ⊗ I) 表示。我们可能会问，如果不进行反计算并将我们的谕门简单地定义为

> $T = MCX \cdot (X \otimes I \otimes X \otimes I)$

![](img/52faec2d621d75e53089d939bb234a82_112_0.png)

图 5.5 两次 Grover 放大后的直方图。

## 5.8 针对 M 量比特的泛化

对于 $M$ 个量子比特，我们可以使用 $MCX$ 门来构建谕门。

```python
StateVector = [0 0 0 0 0 0 0 0 0.1768 0.1768 0.8839 0.1768 0.1768 0.1768 0.1768 0.1768]
```

$M=3$ 时的

```python
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector")
```

$M$ 个量子比特，我们可以使用 $MCX$ 门来构建谕门。

```python
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector")
```

$M=4$ 时的

```python
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector")
```

$M$ 个量子比特，我们可以使用 $MCX$ 门来构建谕门。

```python
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector")
```

$M=4$ 时的

```python
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector")
```

$M$ 个量子比特，我们可以使用 $MCX$ 门来构建谕门。

```python
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector")
```

$M=3$ 时的

```python
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector")
```

$M$ 个量子比特，我们可以使用 $MCX$ 门来构建谕门。

```python
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector")
```

$M=4$ 时的

```python
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector")
```

$M$ 个量子比特，我们可以使用 $MCX$ 门来构建谕门。

```python
from qiskit.visualization import array_to_latex
array_to_latex(final_state,max_size=16,prefix="\StateVector")
```

## 6.1 SAT 问题

满足性问题（SAT）是指：是否存在一组变量赋值使得布尔公式为真。SAT 问题由：

- $m$ 个布尔变量：$x_1, x_2, \dots, x_m$；
- 逻辑连接：$\wedge$ (与), $\vee$ (或), $\neg$ (非), $\rightarrow$ (蕴含), $\leftrightarrow$ (当且仅当)；
- 括号。

表 6.1 蕴含 ($\rightarrow$) 的真值表。

| x | y | $x \rightarrow y$ |
|---|---|---|
| 1 | 1 | 1 |
| 1 | 0 | 0 |
| 0 | 1 | 1 |
| 0 | 0 | 1 |

$f_m(x) = (-1)^{\text{m times}}$ ($m$ 次)

$\sum_{x \in \{0,1\}^m} (-1)^{f_m(x)}} |x\rangle$ (5.19)

在前面的例子中，反计算由操作 (X ⊗ I ⊗ X ⊗ I) 表示。我们可能会问，如果不进行反计算并将我们的谕门简单地定义为

> $T = MCX \cdot (X \otimes I \otimes X \otimes I)$

![](img/52faec2d621d75e53089d939bb234a82_112_0.png)

图 5.5 两次 Grover 放大后的直方图。

在前面的例子中，反计算导致了表示初始状态的模式。在这种情况下，其他位纠缠了，见图 5.6。

![](img/52faec2d621d75e53089d939bb234a82_112_0.png)

图 5.6 两次 Grover 放大后的直方图。

## 6.2 SAT 问题与 NP 完全完备

等等，表 6.2 当且仅当 ($\leftrightarrow$) 的真值表。

| x | y | $x \leftrightarrow y$ | XOR |
|---|---|---|---|
| 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 |

否则，我们说该问题是困难的，所需时间随指数增长，无法在传统计算机上在可接受的时间内执行，这类问题被称为 $NP$。

