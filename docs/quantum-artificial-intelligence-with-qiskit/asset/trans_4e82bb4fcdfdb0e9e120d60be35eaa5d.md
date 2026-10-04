

```python
from qiskit import QuantumCircuit,QuantumRegister, execute
from qiskit.visualization import plot_histogram
from qiskit.quantum_info import Statevector
```

```python
x = QuantumRegister(1, 'x')
y = QuantumRegister(1, 'y')
z = QuantumRegister(1, 'z')
v = QuantumRegister(1, 'v')
aux = QuantumRegister(2, 'aux')
r = QuantumRegister(1, 'result')
qc = QuantumCircuit(x,y,z,v,aux,r)
qc.x(x)
qc.x(y)
qc.x(z)
qc.x(v)
qc.barrier()
qc.ccx(x,y,aux[0])
qc.ccx(aux[0],z,aux[1])
qc.ccx(aux[1],z,r)
```

```python
simulator = Aer.get_backend('statevector_simulator')
result=execute(qc,simulator).result()
counts = result.get_counts()
print("ncount are:", counts)
plot_histogram(counts)
```

量子电路如图 3.11 所示，状态向量“测量”后的结果如图 3.12 所示。

## 3.7 反计算 (Uncomputing)

量子比特 `aux0=1, aux1=1` 通常不需要进一步计算，因为结果已经表示在输出比特 `result` 中。然而，无法将它们重置为零，相反，它们与输出比特纠缠在一起。对于矩阵 $CCX^{-1} = CCX$，我们重新计算确定结果的第一个和第二个 Toffoli 门。步骤如 `qc.barrier()` 之后的列表所示的反操作。

```python
qc.barrier()
qc.ccx(x,y,aux[0])
qc.ccx(aux[0],z,aux[1])
qc.ccx(aux[1],z,r)
# 对辅助寄存器进行反计算
qc.ccx(aux[0],z,aux[1])
qc.ccx(x,y,aux[0])
```

如图 3.13 所示，状态向量“测量”后的结果如图 3.14 所示。

![](img/52faec2d621d75e53089d939bb234a82_79_0.png)

**图 3.11** 我们使用 X 门将量子比特 x, y, z, v 初始化为 1。初始化后，我们使用 `qc.barrier()` 将电路中的表示隔离开来。它不是一个门，可以防止在计算期间合并门操作。我们随后使用了三个量子 Toffoli 门（也称为 ccX 门，即双受控非门），其结果表示在量子比特 r 中。

### 3.7.2 通用多控 X 门

另一种方法可以使用 `MCXGate(a)` 命令，而无需定义辅助寄存器。`MCXGate(n)` 门是一个由 $n$ 个量子比特控制的通用多控 X 门，在本例中由量子比特 x, y, z, v, r 控制。

```python
from qiskit.circuit.library import MCXGate
x = QuantumRegister(1, 'x')
y = QuantumRegister(1, 'y')
z = QuantumRegister(1, 'z')
```

![](img/52faec2d621d75e53089d939bb234a82_79_1.png)

**图 3.12** 状态向量“测量”后，量子比特的值为 x = 1, y = 1, z = 1, v = 1, aux_0 = 1, aux_1 = 1 且 result = 1。总计数为：{'1111111': 1.0}，表示概率为1。

| x: | X |
|---|---|
| y: | X |
| z: | X |
| v: | X |
| aux_0: | |
| aux_1: | |
| result:| | |

图 3.13 因为 $CCX^{-1} = CCX$，所以在确定结果后重新计算了第一个和第二个量子 Toffoli 门 ccX。

```python
v = QuantumRegister(1, 'v')
r = QuantumRegister(1, 'result')
qc = QuantumCircuit(x,y,z,v,r)
qc.barrier()
```

```python
gate = MCXGate(4)
qc.append(gate,[x,y,z,v,r])
qc.draw()
```

如图 3.15 所示。

![](img/52faec2d621d75e53089d939bb234a82_80_0.png)

图 3.14 状态向量“测量”后，量子比特的值为 x=1, y=1, z=1, v=1, aux_0=0, aux_1=0 且 result=1。总计数（按逆序排列）：{'1001111': 1.0}，1.0 表示状态 [1001111] 的概率为一。总计数为：{'1001111': 1.0}

![](img/52faec2d621d75e53089d939bb234a82_81_0.png)

**图 3.15** 可以使用命令 $MCXGate(4)$ 而无需定义辅助寄存器。

### 3.7.3 OR 操作

OR 操作根据德·摩根定律通过酉变换映射表示：

$x_1 \vee x_2 = \neg(x_1 \wedge \neg x_2)$
$((I_2 \otimes X) \cdot CCX \cdot (X \otimes X \otimes I_1)) \cdot [xy0] = xy(x \vee y)$

```python
x = QuantumRegister(1, 'x')
y = QuantumRegister(1, 'y')
r = QuantumRegister(1, 'result')
qc = QuantumCircuit(x,y,r)
# 准备
qc.x(x)
qc.x(y)
qc.barrier()
# 根据德·摩根定律进行 OR 操作
qc.x(x)
qc.x(y)
qc.x(r)
qc.ccx(x,y,r)
qc.draw()
```

得到图 3.16 所示的量子电路。对于每个量子布尔 AND 操作，简单的实现需要一个辅助（ancilla）位。通过反转前面的步骤，这些比特可以用于进一步计算。电路的复杂度对应量子门的数量。

### 3.8 DEUTSCH 算法

Deutsch 算法 [26] 利用了由 Hadamard 门生成的量子比特叠加态，它比任何经典算法都强大。它用于判断 $f(x)$ 是否为常数。

![](img/52faec2d621d75e53089d939bb234a82_82_0.png)

**图 3.16** OR 操作根据德·摩根定律 $x_1 \vee x_2 = \neg(x_1 \wedge \neg x_2)$ 由酉映射表示。对于一个未知函数 $f : B^1 \to B^1$，通过调用函数来判断单比特的 $f(x)$ 是否为常数。常数函数 $f(0) = f(1)$。

