
# 38 ■ 使用 Qiskit 进行量子人工智能

在测量过程中的量子坍缩是一种非局部力。非局部相互作用不受光速限制，其强度也不受距离介导。这种安排与爱因斯坦的狭义相对论相冲突，该理论认为没有任何东西运动速度超过光速。这种冲突通过以下事实解决：人们无法使用一个量子比特在两个位置（$A$ 和 $B$）处跨越距离分离，且没有其他通信手段；在 $A$ 处测量量子比特决定了 $B$ 处的结果，但在 $B$ 处的结果是未知的。在 $B$ 处测量是在不知道 $A$ 处结果的情况下进行的随机过程。此外，为了执行隐态，我们需要一个经典通道来将信息映射到正确状态的隐态量子比特。

## 2.8 克隆 (CLONING)

产生任意量子态副本的线性操作是不可能的。我们无法复制状态的未知振幅分布。这在量子计算领域具有深远影响，因为我们无法复用任意量子态。

为了实现这一点，我们定义了一个复制机。我们使用正交空间的一个正交基，例如 `|x_1\rangle`，并定义一个酉变复制算子，将 `|x\rangle \in H_n` 复制为：

$$U_{copy}(|x\rangle, |x_1\rangle) = |x\rangle|x\rangle. \quad (2.38)$$

`U_{copy}` 是否存在？对于基态，`U_{copy}` 是定义的。它可以通过 `CX` 实现，当 `|x_1\rangle = |0\rangle` 和 `|x_2\rangle = |1\rangle`：

$$U_{copy}(|x_1\rangle, |x_1\rangle) = |x_1\rangle|x_1\rangle$, $U_{copy}(|x_2\rangle, |x_1\rangle) = |x_2\rangle|x_2\rangle.$$

如果这处于叠加态中

$$|x\rangle = \frac{|x_1\rangle + |x_2\rangle}{\sqrt{2}}$$

它意味着：

$$U_{copy}(|x\rangle, |x_1\rangle) = |x\rangle|x\rangle = \left(\frac{|x_1\rangle + |x_2\rangle}{\sqrt{2}}\right) \otimes \left(\frac{|x_1\rangle + |x_2\rangle}{\sqrt{2}}\right) = \frac{1}{2} \cdot (|x_1\rangle|x_1\rangle + |x_1\rangle|x_2\rangle + |x_2\rangle|x_1\rangle + |x_2\rangle|x_2\rangle).$$

由于 `U_{copy}` 的线性性质，可以得出：

$$U_{copy}(|x\rangle, |x_1\rangle) = U_{copy}\left(\frac{|x_1\rangle + |x_2\rangle}{\sqrt{2}}, |x_1\rangle\right) =$$

$$U_{copy}(|x\rangle, |x_1\rangle) = U_{copy}\left(\frac{|x_1\rangle|x_1\rangle + |x_2\rangle|x_1\rangle}{\sqrt{2}}\right) =.$$

$$U_{copy}(|x_1\rangle|x_1\rangle) + U_{copy}(|x_2\rangle|x_1\rangle) = \frac{1}{\sqrt{2}} \cdot (|x_1\rangle|x_1\rangle + |x_2\rangle|x_2\rangle)$$

这导致了矛盾。产生任意量子态副本的操作是不可能的，我们无法复制状态的未知振幅分布。例如，我们无法复制未知的量子比特 $\alpha|0\rangle+\beta|1\rangle$。振幅分布由 $\alpha$ 和 $\beta$ 的值决定。

## 2.9 相位反传 (PHASE KICK-BACK)

如果我们将 `CX` 门作为控制量子比特 `|1\rangle` 作用于目标值 $\frac{|0\rangle}{\sqrt{2}}$，我们得到：

$$CX|1\rangle \cdot \left(\frac{|0\rangle}{\sqrt{2}}\right)=|1\rangle \cdot \left(\frac{X|0\rangle - X|1\rangle}{\sqrt{2}}\right)$$
$$CX|1\rangle \cdot \left(\frac{|0\rangle}{\sqrt{2}}\right)=|1\rangle \cdot (-1\right) \cdot \left(\frac{|0\rangle - |1\rangle}{\sqrt{2}}\right)$$
$$CX|1\rangle \cdot \left(\frac{|0\rangle - |1\rangle}{\sqrt{2}}\right)=-|1\rangle \cdot \left(\frac{|0\rangle - |1\rangle}{\sqrt{2}}\right)$$

对于控制量子比特 `|0\rangle`，什么都不做：

$$CX|0\rangle \cdot \left(\frac{|0\rangle - |1\rangle}{\sqrt{2}}\right)=|0\rangle \cdot \left(\frac{|0\rangle - |1\rangle}{\sqrt{2}}\right)$$

我们称该值（相位）被“反传”到了控制寄存器。

## 2.10 量子布尔门 (QUANTUM BOOLEAN GATES)

由 $m$ 位位组成的可逆电路对应于一个表示 $m$ 位位排列的酉映射，它定义了一个单射映射 $\mathbf{B}^m \rightarrow \mathbf{B}^m$。酉排列矩阵可以表示这种酉映射。一种更优雅的方法是将电路映射到布尔门。这种酉映射允许我们通过布尔门的数量来确定电路的复杂度。布尔门包括恒等门 `I`、非门 `X` 和控制门 `CX`。这种输出操作。这些操作可以通过酉门表示。Toffoli 门 `CCX` 是三个量子比特的酉门，可以在 $H_8$ 空间通过矩阵表示：

$$CCX = \begin{pmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \end{pmatrix}$$

# Qiskit

我们描述了如何安装 `qiskit` 并演示了我们将使用的两个后端函数。我们在简单的量子硬币上演示了 `qiskit` 的工作原理。我们指示了通过酉矩阵表示简单的量子电路并获取酉命令。引入了消计算的概念，因为在量子计算中我们无法重置量子比特。Deutsch算法通过调用一次函数确定未知函数 $f: B^1 \rightarrow B^1; f(x) = y$ 是否为常数。Deutsch算法是第一个（1985年）展示量子优势的算法；它证明了在某些设置下量子计算机严格于经典计算机。最后，我们给出一个在真实的量子计算机上运行 Deutsch算法的示例。

## 3.1 开发工具包

`Qiskit` 是一个用于电路和算法层面处理量子计算机的开源开发工具包（SDK）[21]。IBM Quantum, https://quantum-computing.ibm.com/。它提供了创建量子程序并在量子设备或本地模拟器上运行它们的工具。它遵循通用量子计算的量子电路模型，并适用于任何遵循该模型的量子硬件。`Qiskit` 基于 Python，你可以在 https://qiskit.org 获取有关的所有信息。

## 3.2 安装

在安装 `qiskit` 之前，你应该安装 Anaconda，这是一个包含 Jupyter 的科学计算平台 Python 分发版。你也可以安装 Miniconda，这是一个 conda 的免费精简安装程序，仅包含 conda、Python 及其依赖的包，以及一个小的

^1作者感谢在该工作中使用 IBM Quantum 服务。文中的观点仅代表作者，不代表 IBM 或 IBM Quantum 团队的官方政策或立场。

DOI: 10.1201/9781003373404-3

# 使用 Qiskit 进行量子量子人工智能

其他实用包的数量。此外，你还可以安装 Visual Studio Code。Visual Studio Code 是一个重新定义的代码编辑器，用于运行 Jupyter 笔记本并能自动识别不同的环境 https://code.visualstudio.com/。你可以在该网站找到 `qiskit` 的指令：

https://qiskit.org/documentation/getting_started.html。

从那里你可以很好地访问在线教程。

在安装 `qiskit` 之前，你必须在 Anaconda 或终端中启动提示符。从那里你可以调用 `conda`。要安装 `qiskit`，请执行以下命令创建一个名为 `qiskit`（或任何你喜欢的名称）的环境：

```
conda create -n qiskit python 3
```

你可以使用命令列出所有的环境：

```
conda-env list
```

你通过名称 `ENV_NAME` 激活 `qiskit` 环境。然后可以使用命令激活它：

```
conda activate ENV_NAME
```

你通过以下命令开始安装：

```
pip install qiskit
pip install qiskit[visualization]
```

对于较新版本的 macOS：

```
pip install 'qiskit[visualization]'
```

我们可以通过以下检查已安装的 `qiskit` 版本（见图3.1）：

```
import qiskit.tools.jupyter
%qiskit_version_table
%qiskit_copyright
```

## 3.3 后端模拟器函数

`Qiskit` 通过 Aer 包提供了不同的后端模拟器函数。我们将使用两个模拟器。

- 状态向量模拟器（statevector simulator）对 `qiskit` 电路执行理想运行，并在应用后返回最终状态向量（所有比特）。电路的状态向量可以表示概率值（新版本中的概率），这些值对应于状态向量与酉矩阵相乘。状态向量模拟器比其他模拟方法需要更长时间和更多的内存，因为状态向量维度随比特数量呈指数级增长，n = 2^m（其中 m 是比特数）。

图 3.1 (a) 在带有 8 Gb 的旧电脑上运行 Qiskit 0.34.2 版本；(b) 在带有 16 Gb 的现代电脑上运行 Qiskit 0.43.0 版本。

- `qasm` 模拟器的行为类似于当今的实际设备，容易受到退相干引起的噪声影响。它运行计数（count），即电路中必须定义的测量比特的采样。它的尺寸小得多，且不会随着比特数量的增加而呈指数级增长。

## 3.4 兼容性

书中介绍的量子电路主要使用基础量子门的简单量子电路，这些门可以很容易移植到其他软件开发工具包。你可以从 https://github.com/andrezweweigart/qai 下载书中的示例（Jupyter 笔记本）。

`Qiskit` 软件开发工具包（SDK）正在不断开发，不同版本之间存在变化。程序已经在带有 8 Gb 的旧电脑上运行的 Qiskit 0.34.2 版本以及带有 16 Gb 的现代电脑上运行的 Qiskit 0.43.0 版本上经过测试。关于示例的主要差异是直方图图上的注释。在旧版本中，左侧的直方图注释总是“Probabilities”（概率）。在较新版本中，注释使用了使用的模拟器。statevector 注释用于 qasm 模拟器的“Count”。引入准概率概念是为了对经典统计力学应用量子修正。准概率分布不满足传统概率分布的所有属性，例如，对于由于量子力学干涉而没有经典模型的状态，它可以取负值。然而，正如本书描述的，相应的效应在我们的模拟中并不起任何作用。

## 44 使用 Qiskit 进行量子量子人工智能

另一个差异存在 `qiskit` 机器学习算法库中。我们将在第 23 章中使用一个示例，那里包含两个用于变分分类器的不同笔记本。

## 3.5 示例：量子硬币

我们从一个非常简单的示例开始，量子硬币。量子硬币有两个基态 0 和 1 的系统：

```
$|0\rangle = \begin{pmatrix} 1 & 0 \end{pmatrix}, |1\rangle = \begin{pmatrix} 0 & 1 \end{pmatrix}. \quad (3.1)$
```

映射表示为：

```
$|0\rangle \rightarrow \frac{1}{\sqrt{2}}|0\rangle + \frac{1}{\sqrt{2}}|1\rangle. \quad (3.2)$
```

以及

```
$|1\rangle \rightarrow \frac{1}{\sqrt{2}}|0\rangle - \frac{1}{\sqrt{2}}|1\rangle. \quad (3.3)$
```

对应的算符由以下酉矩阵指示：

```
$W = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix} = \frac{1}{\sqrt{2}} \cdot \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}. \quad (3.4)$
```

如果系统从状态 |0⟩ 开始并经历时间演化，观测到 0 或 1 的概率为 $|\frac{1}{\sqrt{2}}|^2=1/2$。如果我们不进行测量并重复映射，观测到 0 的概率变为零，观测到 1 的概率变为一。这是由于 [1] 的幅度相互抵消。这种效应是由于破坏性干涉引起的，且不会出现在概率分布中，因为所有系数是非负实数。

启动 Anaconda Navigator 或 Visual Studio Code 编辑器（或任何支持 Jupyter 的编辑器）。新建文件，Jupyter 笔记本，通过缩进环境名称选择正确的通道。Hadamard 矩阵 H 在 `qiskit` 中通过 Hadamard 门 `qc(qubit)` 表示，其中 `qc` 是带有所选名称 `qc` 的量子电路（你也可以选择其他名称，书中我们使用名称 `qc`）。量子硬币以基态 |0⟩ 定义：

```
$H|0\rangle = \frac{1}{\sqrt{2}}|0\rangle + \frac{1}{\sqrt{2}}|1\rangle. \quad (3.5)$
```

我们通过以下方式定义一个带有一个比特的量子电路：

```
qc = QuantumCircuit(1)
```

在 `qiskit` 量子电路中，所有比特都初始化为状态 |0>。Hadamard 门 H 作用于比特零，电路中的比特编号为 0, 1, . . 在我们的电路中只有一个比特。

Qiskit ■ 45

图 3.2 H 门。

```
qc.h(0)
```

首先我们加载必要的库，然后定义电路并绘制它。

```
from qiskit import QuantumCircuit, Aer, execute
from qiskit.visualization import plot_histogram
qc = QuantumCircuit(1)
qc.h(0)
qc.draw()
```

程序定义为：

```
from qiskit import QuantumCircuit, Aer, execute
from qiskit.visualization import plot_histogram
qc = QuantumCircuit(1)
qc.h(0)
qc.draw()
```

### 3.5.1 Statevector

下一步我们将执行状态向量模拟并在其中绘制结果。

```
simulator = Aer.backend('statevector_simulator')
result = execute(qc,simulator).result()
final_state = result.get_statevector()
from qiskit.visualization import array_to_latex
array_to_latex(final_state, prefix="Statevector = ")
```

如果 Jupyter 没有在 Jupyter 中替换：

> Statevector = \frac{1}{\sqrt{2}} - \frac{1}{\sqrt{2}}

如果我们改变量子电路以使用 NOT 门表示映射，我们将得到不同的幅度：

```
$H \cdot |0\rangle = H \cdot |1\rangle = \frac{1}{\sqrt{2}}|0\rangle - \frac{1}{\sqrt{2}}|1\rangle. \quad (3.6)$
```

### 3.5.2 Qasm Simulator

`qasm` 模拟器承诺行为类似于当今的实际设备，容易受到退相干引起的噪声影响。它返回计数（count），即测量比特的采样

![](img/52faec2d621d75e53089d939bb234a82_73_0.png)

**图 3.5** 由 H 门表示的量子硬币以及由 M 表示的量子比特测量。测量值由一个经典比特 c 表示。

对于电路中必须定义的被测量子比特，测量值存储在传统的比特（conventional bits）中。在我们的量子硬币示例中，我们通过命令 `qc = QuantumCircuit(1,1)` 定义了一个量子电路，第一个索引表示量子比特的数量，第二个表示传统比特的数量。

```python
```
