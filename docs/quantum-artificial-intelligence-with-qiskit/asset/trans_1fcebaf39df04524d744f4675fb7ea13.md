

# 使用 Qiskit 进行量子量子人工智能

其他实用包的数量。此外，你还可以安装 Visual Studio Code。Visual Studio Code 是一个重新定义的代码编辑器，用于运行 Jupyter 笔记本并能自动识别不同的环境 https://code.visualstudio.com/。你可以在该网站找到 qiskit 的指令：

https://qiskit.org/documentation/getting_started.html。

从那里你可以很好地访问在线教程。

在安装 qiskit 之前，你必须在 Anaconda 或终端中启动提示符。从那里你可以调用 conda。要安装 qiskit，请执行以下命令创建一个名为 qiskit（或任何你喜欢的名称）的环境：

```
conda create -n qiskit python 3
```

你可以使用命令列出所有的环境：

```
conda-env list
```

你通过名称 ENV_NAME 激活 qiskit 环境。然后可以使用命令激活它：

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

我们可以通过以下检查已安装的 qiskit 版本（见图3.1）：

```
import qiskit.tools.jupyter
%qiskit_version_table
%qiskit_copyright
```

## 3.3 后端模拟器函数

Qiskit 通过 Aer 包提供了不同的后端模拟器函数。我们将使用两个模拟器。

- 状态向量模拟器（statevector simulator）对 qiskit 电路执行理想运行，并在应用后返回最终状态向量（所有比特）。电路的状态向量可以表示概率值（新版本中的概率），这些值对应于状态向量与酉矩阵相乘。状态向量模拟器比其他模拟方法需要更长时间和更多的内存，因为状态向量维度随比特数量呈指数级增长，n = 2^m（其中 m 是比特数）。

图 3.1 (a) 在带有 8 Gb 的旧电脑上运行 Qiskit 0.34.2 版本；(b) 在带有 16 Gb 的现代电脑上运行 Qiskit 0.43.0 版本。

- qasm 模拟器的行为类似于当今的实际设备，容易受到退相干引起的噪声影响。它运行计数（count），即电路中必须定义的测量比特的采样。它的尺寸小得多，且不会随着比特数量的增加而呈指数级增长。

## 3.4 兼容性

书中介绍的量子电路主要使用基础量子门的简单量子电路，这些门可以很容易移植到其他软件开发工具包。你可以从 https://github.com/andrezweweigart/qai 下载书中的示例（Jupyter 笔记本）。

Qiskit 软件开发工具包（SDK）正在不断开发，不同版本之间存在变化。程序已经在带有 8 Gb 的旧电脑上运行的 Qiskit 0.34.2 版本以及带有 16 Gb 的现代电脑上运行的 Qiskit 0.43.0 版本上经过测试。关于示例的主要差异是直方图图上的注释。在旧版本中，左侧的直方图注释总是“Probabilities”（概率）。在较新版本中，注释使用了使用的模拟器。statevector 注释用于 qasm 模拟器的“Count”。引入准概率概念是为了对经典统计力学应用量子修正。准概率分布不满足传统概率分布的所有属性，例如，对于由于量子力学干涉而没有经典模型的状态，它可以取负值。然而，正如本书描述的，相应的效应在我们的模拟中并不起任何作用。

## 44 使用 Qiskit 进行量子量子人工智能

另一个差异存在 qiskit 机器学习算法库中。我们将在第 23 章中使用一个示例，那里包含两个用于变分分类器的不同笔记本。

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

启动 Anaconda Navigator 或 Visual Studio Code 编辑器（或任何支持 Jupyter 的编辑器）。新建文件，Jupyter 笔记本，通过缩进环境名称选择正确的通道。Hadamard 矩阵 H 在 qiskit 中通过 Hadamard 门 qc(qubit) 表示，其中 qc 是带有所选名称 qc 的量子电路（你也可以选择其他名称，书中我们使用名称 qc）。量子硬币以基态 |0⟩ 定义：

```
$H|0\rangle = \frac{1}{\sqrt{2}}|0\rangle + \frac{1}{\sqrt{2}}|1\rangle. \quad (3.5)$
```

我们通过以下方式定义一个带有一个比特的量子电路：

```
qc = QuantumCircuit(1)
```

在 qiskit 量子电路中，所有比特都初始化为状态 |0>。Hadamard 门 H 作用于比特零，电路中的比特编号为 0, 1, . . 在我们的电路中只有一个比特。

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

3.5.1 Statevector

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

3.5.2 Qasm Simulator

qasm 模拟器承诺行为类似于当今的实际设备，容易受到退相干引起的噪声影响。它返回计数（count），即测量比特的采样

