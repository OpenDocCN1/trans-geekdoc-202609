
# 制作笔记

有两件事是不应该眼睁睁别人制作的：香肠和法律。

> — 马克·吐温

这本书是由我们两个人在三个不同的国家（爱尔兰、西班牙和瑞士）使用 LaTeX 编写的，地点涵盖了广泛：梅纳斯大学、奥维埃多大学和欧洲核子研究组织（CERN）的办公室；奥维埃多的一间公寓、梅纳斯的大学宿舍、以及日内瓦的一间公寓；体育馆；两个不同医院急诊室的候诊室；海边；山间；汽车后座；某些通勤路线上；几个不同的机场；阿尔梅里亚的一家酒店；可能还有其他我们现在不记得的地点。

如果没有适当的工具和应用程序，这一切是不可能的。主要的工具是 Overleaf (https://www.overleaf.com)，它允许我们在即使相隔数千公里的情况下同时进行协作工作。

为了帮助我们在 LaTeX 中编写公式、绘制电路和格式化代码，我们使用了许多非常有用的包，如 `quantikz`、`physics`、`siunitx` 和 `listings`。为了创建插图，我们使用了 TikZ、Graphviz (https://graphviz.org/) 和 Graphviz Visual Editor (http://magjac.com/graphviz-visual-editor/)。为了编写和运行代码示例，我们同时使用了 Anaconda 和 Google Colab（如附录 D“安装工具”所述）。

它们都是出色的工具，让这本书的编写变成了一种更加愉快和轻松的体验。

# 评估

## 第 1 章，量子计算基础

(1.1) 如果比特位的状态为 $|\sqrt{1/2}|0\rangle + \sqrt{1/2}|1\rangle$，则测量 0 的概率等于 $|\sqrt{1/2}|^2 = 1/2$。

同样，测量 1 的概率也是 1/2。如果比特位的状态为 $\sqrt{1/3}|0\rangle + \sqrt{2/3}|1\rangle$，则测量 0 的概率为 $|\sqrt{1/3}|^2 = 1/3$，测量 1 的概率为 $|\sqrt{2/3}|^2 = 2/3$。

最后，如果比特位状态为 $\sqrt{1/2}|0\rangle - \sqrt{1/2}|1\rangle$，则测量 0 的概率为 $|\sqrt{1/2}|^2 = 1/2$，测量 1 的概率为 $|-\sqrt{1/2}|^2 = 1/2$。

(1.2) $\sqrt{1/2}|0\rangle + \sqrt{1/2}|1\rangle$ 与 $\sqrt{1/3}|0\rangle + \sqrt{2/3}|1\rangle$ 的内积为 $\sqrt{1/2}\sqrt{1/3} + \sqrt{1/2}\sqrt{2/3} = \sqrt{1/6} + \sqrt{1/3}$。

$\sqrt{1/2}|0\rangle + \sqrt{1/2}|1\rangle - \sqrt{1/2}|1\rangle$ 的内积是 [原文错误]。

(1.3) $X$ 的伴共轭是 $X$，且满足 $XX = I$。因此，$X$ 是酉矩阵，其逆为 $X$。$X$ 将 $|a\rangle + |b\rangle$ 映射到 [原文错误]。

(1.4) $H$ 的伴共轭是 $H$，且满足 $HH = I$。因此，$H$ 是酉矩阵，其逆为 $H$。$H$ 将 $|+\rangle$ 和 $|-\rangle$ 映射到 [原文错误]。

(1.5) 同样满足 $Z$ 的伴共轭是 $Z$，且满足 $ZZ = I$。因此，$Z$ 是酉矩阵，其逆为 $Z$。$Z$ 将 $|+\rangle$ 和 $|-\rangle$ 映射到 [原文错误]。

(1.6) 由于 $S^2 = I$，$S$ 是酉矩阵，其逆为 $S$。$T^4 = I$，$T$ 是酉矩阵，其逆为 $T$。

(1.7) 根据 $R_X$ 的定义，$R_X(\pi) = iX$。同样，$R_Y(\pi) = iY$ 和 $R_Z(\pi) = iZ$。

(1.8) 根据 $U(\theta, \phi, \lambda)$ 的定义，$U(\theta, \phi, \lambda) U(\theta, \phi, \lambda)^{\dagger} = I$ 且同样，$U(\theta, \phi, \lambda)^{\dagger} U(\theta, \phi, \lambda) = I$。那么，$U(\theta, \phi, \lambda)$ 是酉矩阵。

类似地，有：

$U(\theta, 0, 0) = \left( \begin{matrix} \cos \frac{\theta}{2} & -\sin \frac{\theta}{2} \\ \sin \frac{\theta}{2} & \cos \frac{\theta}{2} \end{matrix} \right) = R_Y(\theta)$

以及

$U(0, 0, \theta) = \left( \begin{matrix} 1 & 0 \\ 0 & e^{i\theta} \end{matrix} \right) = e^{i\frac{\theta}{2}}R_Z(\theta)$

**(1.9)** 由于 $\theta = 2 \arccos \sqrt{p}$，在测量之前：

$\cos \frac{\theta}{2}|0\rangle + \sin \frac{\theta}{2}|1\rangle = \sqrt{p}|0\rangle + \sqrt{1-p}|1\rangle$。

结果，测量 0 的概率为 $p$，测量 1 的概率为 $1-p$。

**(1.10)** 得到 1 的概率将是 $|a_{10}|^2 + |a_{11}|^2$。在该测量结果下，状态将塌缩为

$$\frac{a_{10}|10\rangle + a_{11}|11\rangle}{\sqrt{|a_{10}|^2 + |a_{11}|^2}}$$

**(1.11)** 有：

$U_1 \otimes U_2(U_1^\dagger \otimes U_2^\dagger) = (U_1U_1^\dagger) \otimes (U_2U_2^\dagger) = I.$。

类似，$(U_1^\dagger \otimes U_2^\dagger)(U_1 \otimes U_2) = I \otimes I$。因此，$U_1 \otimes U_2$ 的逆是 $U_1^\dagger \otimes U_2^\dagger$。

此外，根据矩阵张积的定义，我们得到对于任意矩阵 A 和 B（即使是非酉正的），都有：

$A^{\dagger} \otimes B^{\dagger} = \begin{pmatrix} a_{11}^* & a_{21}^* \\ a_{12}^* & a_{22}^* \end{pmatrix} \otimes \begin{pmatrix} b_{11}^* & b_{21}^* \\ b_{12}^* & b_{22}^* \end{pmatrix} = \begin{pmatrix} a_{11}^*b_{11}^* & a_{11}^*b_{21}^* & a_{21}^*b_{11}^* & a_{21}^*b_{21}^* \\ a_{12}^*b_{11}^* & a_{12}^*b_{21}^* & a_{22}^*b_{11}^* & a_{22}^*b_{21}^* \\ a_{11}^*b_{12}^* & a_{11}^*b_{22}^* & a_{21}^*b_{12}^* & a_{21}^*b_{22}^* \\ a_{12}^*b_{12}^* & a_{12}^*b_{22}^* & a_{22}^*b_{12}^* & a_{22}^*b_{22}^* \end{pmatrix} = (A \otimes B)^{\dagger}$。

**(1.12)** $X \otimes X$ 的矩阵是

$\begin{pmatrix} 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 1 & 0 & 0 & 0 \end{pmatrix}$

$H \otimes I$ 的矩阵是

$\frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 0 & 1 & 0 \\ 0 & 1 & 0 & 1 \\ -1 & 0 & 1 & 0 \\ 0 & -1 & 0 & 1 \end{pmatrix}$

**(1.13)** 在电路

![](img/9fb09d10535597eb51a8f327fe77afc4_617_0.png)

中，状态 $|00\rangle$ 和 $|10\rangle$ 保持不变，而 $|01\rangle$ 和 $|11\rangle$ 映射到彼此。这正是一个 CNOT 门的作用，其控制位是底部比特，目标位是上方比特。

该电路的矩阵

$\begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \end{pmatrix}$

正是一个从底部比特到上方比特的 CNOT 门矩阵。

另一方面，电路

![](img/9fb09d10535597eb51a8f327fe77afc4_618_0.png)

使 $|00\rangle$ 和 $|11\rangle$ 不变，而它将 $|01\rangle$ 和 $|10\rangle$ 映射到彼此。这正是一个 SWAP 门的作用。

或者，电路的矩阵是

$\begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}$

这是 SWAP 门的矩阵。

**(1.14)** 状态 $\sqrt{1/2}(|00\rangle+|01\rangle)$ 是纠缠的。然而 $\frac{1}{2}(|00\rangle+|01\rangle+|10\rangle+|11\rangle)$ 是乘积态，因为它可以写成 $|+\rangle|+\rangle$。

**(1.15)** 如果 $U$ 的矩阵是 $(u_{ij})_{i,j=1}^2$，那么 $|00\rangle$ 和 $|10\rangle$ 被 $CU$ 映射到自身。此外，$|01\rangle$ 被映射到 $|0\rangle(u_{11})$，而 $|11\rangle$ 被映射到 $|1\rangle(u_{22})$。

因此，$CU$ 的矩阵是

$\begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & u_{11} & u_{12} \\ 0 & 0 & u_{21} & u_{22} \end{pmatrix}$

$CU$ 的伴随矩阵是 $CU^\dagger$，且满足 $UC^\dagger = I$。因此，$CU$ 是酉的。

**(1.16)** 等价性直接源于 $H=Z$。

**(1.17)** 我们可以通过以下电路准备 $\sqrt{1/2}(|00\rangle-|11\rangle)$：

![](img/9fb09d10535597eb51a8f327fe77afc4_619_0.png)

我们可以使用电路 ![](img/9fb09d10535597eb51a8f327fe77afc4_619_1.png) 来准备 $\sqrt{1/2}(|10\rangle+|01\rangle)$。

最后，电路 ![](img/9fb09d10535597eb51a8f327fe77afc4_619_2.png) 可以用于得到 $\sqrt{1/2}(|10\rangle-|01\rangle)$。

注意，为了准备这些状态，我们只使用了用于得到原始贝尔态 $\sqrt{1/2}(|00\rangle+|11\rangle)$ 的张积门。例如，我们有 $\sqrt{1/2}(|10\rangle-|01\rangle) = (X \otimes Z)\sqrt{1/2}(|00\rangle+|11\rangle)$，然后 $(X \otimes Z)\sqrt{1/2}(|10\rangle-|01\rangle) = \sqrt{1/2}(|00\rangle+|11\rangle)$。如果 $\sqrt{1/2}(|10\rangle-|01\rangle)$ 是乘积态，那么 $\sqrt{1/2}(|00\rangle+|11\rangle)$ 也将是乘积态。但这是不可能的，我们知道 $\sqrt{1/2}(|00\rangle+|11\rangle)$ 是纠缠的。

**(1.18)** 我们可以通过归纳法证明。我们知道 $n=1$ 时结果成立。现在假设 $n>1$ 时成立，并考虑一个 $n+1$ 个比特的基态 $|\psi\rangle$。如果 $|\psi\rangle = |0\rangle|\psi'\rangle$，那么 $|\psi\rangle$ 的列向量将以 $|\psi'\rangle$ 的列向量开头，并有 $2^n$ 个零。根据归纳假设，$|\psi'\rangle$ 的列向量正是我们感兴趣的形式。因此 $|\psi\rangle$ 也具有这种结构。$|\psi\rangle = |1\rangle|\psi'\rangle$ 的情况也是类似的。另一方面，由于每个 $n$-比特态都可以写成基态的归一化组合，它的向量表示是一个具有 $2^n$ 个坐标的单位向量。

**(1.19)** 如果测量多比特态的第 $j$ 个比特，得到 1 的概率由 $\sum_{l \in f_j} |a_l|^2$ ，其中 $f_j$ 是第 $j$ 位为 1 的数字集。塌缩后的状态将是 $\frac{\sum_{l \in f_j} a_l |l\rangle}{\sqrt{\sum_{l \in f_j} |a_l|^2}}$。

**(1.20)** 当我们测量 $(1/2)|100\rangle + (1/2)|010\rangle + \sqrt{1/2}|001\rangle$ 的第二个比特时，得到 0 的概率为 $\left| \frac{1}{2} \right|^2 + \left| \frac{1}{\sqrt{2}} \right|^2 = \frac{1}{4} + \frac{1}{2} = \frac{3}{4}$。

测量第二个比特并得到 0 的结果将是 $\frac{1}{\sqrt{3}}|100\rangle + \frac{\sqrt{2}}{\sqrt{3}}|001\rangle$。

**(1.21)** 令 $x = x_1 ... x_n$ 和 $y = y_1 ... y_n$，其中 $x_i$ 是 $x$ 的第 $i$ 位。那么 $\langle y|x\rangle = 1$ 当 $x=y$ 时成立，当 $x \neq y$ 时为 0。由此可知 $\{x\rangle\}_{x\in\{0,1\}^n}$ 构成一个基。

## 第 2 章，量子计算中的工具

(2.1) 我们已经在附录 D 安装工具中给出了解决方案。

(2.2) 为了构建图 2.3b 中的电路，你必须执行以下代码：

```python
from qiskit import *
import numpy as np

qc = QuantumCircuit(2)
qc.z(0)
qc.y(1)
qc.cry(np.pi/2, 0, 1)
qc.u(np.pi/4, np.pi, 0, 0)
qc.rz(np.pi/4, 1)
```

如果你想可视化该电路，当然，可以使用 `qc.draw("mpl")`

(2.3) 你可以检查 IBM 对该方法的实现](https://github.com/Qiskit/qiskit-terra/blob/5ccf3a4cb10742ae215b86ee9d13bb05f64f36/qiskit/circuit/quantumcircuit.py#L2205) 并与你自己的进行对比！

他们采取了一些我们没有考虑到的额外步骤，例如在电路中添加屏障（barriers），但你可以忽略这些细节。

(2.4) 你已经在附录 D“安装工具”中得到了解决方案。

(2.5) 我们已经学习了如何在 Qiskit 中构建这些电路。为了在 PennyLane 中构建它们，我们需要运行以下代码：

```python
import pennylane as qml
import numpy as np

dev = qml.device('default_qubit', wires = 2)

@qml.node(dev)
def qircuitA():
    qml.PaulX(wires = 0)
    qml.RX(np.pi/4, wires = 1)
    qml.CNOT(wires = [0,1])
    qml.U3(np.pi/3, 0, np.pi, wires = 0)
    return qml.state()

@qml.node(dev)
def qircB():
    qml.PaulIZ(wires = 0)
    qml.PaulIY(wires = 1)
    qml.CRY(np.pi/2, wires = [0,1])
    qml.U3(np.pi/4, np.pi, wires = 0)
    qml.RZ(np.pi/4, wires = 1)
    return qml.state()
```

如果我们运行这些代码，例如通过执行 `print(qcircB())` 运行 B，我们将得到以下态向量：

```python
tensor([[ 0.          +0.j , -0.35355339+0.85355339j,
          0.          +0.j ,  0.14644661-0.85355339j],
requires_grad=True])
```

另一方面，如果我们用 Qiskit 验证同一个电路，我们将得到对应的输出：
