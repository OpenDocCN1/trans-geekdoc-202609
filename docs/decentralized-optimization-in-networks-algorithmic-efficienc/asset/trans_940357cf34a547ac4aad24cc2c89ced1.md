

**定义 3.1.** 给定闭凸集 $\Omega_0 \subseteq \mathbb{R}^p$，我们将 $P_{\Omega_0}(x) = \arg\min_{s \in \Omega_0} \|x - s\|$ 指定为投影算子，其中 $x$ 和 $s$ 均属于空间 $\mathbb{R}^p$.

基于定义 3.1，显然对于任意向量对 $\mu$ 和 $v$，下列不等式始终成立：

$$\|P_{\Omega_0}(\mu) - P_{\Omega_0}(v)\| \leq \|\mu - v\|, \qquad \text{(3.4)}$$

并且最优解（记作 $x^*$）被保证满足下列关系：

$$s^* = P_{\Omega_0}(s^* - \eta_0 \nabla f(s^*)), \qquad \text{(3.5)}$$

其中 $s^*$ 表示问题 (3.1) 的最优解 $x^*$ 投影得到的结果，而 $\eta_0$ 表示固定正步长。由此可推出 $s^* = x^*$.

### 3.2.1 与多目标优化的区别与联系

此处需注意问题 (3.1) 与多目标优化问题之间的区别及关联。

- **(i) 区别：** 作为单目标优化问题提出，(3.1) 中的去中心化优化问题旨在最小化同一等式中概述的全局函数，且基于假设 3.1 具有一个唯一最优解（如图 3.1 左侧所示）。与 (3.1) 所述问题相反，多目标优化问题力求同时最小化众多目标函数 $f(x) = (f^1(x), f^2(x), \dots, f^m(x))^\mathrm{T} (\mathbb{R}^p \to \mathbb{R}^m)$ [44–46]。这些问题产生一组称为帕累托最优解的解（如图 3.1 中间所示）。此外，多目标优化问题强调帕累托前沿（如图 3.1 右侧所示），该概念在本工作中未涉及。

- **(ii) 联系：** 如众多研究 [43–46] 所讨论，多目标优化问题可以转化为单目标优化问题，即本文所讨论的问题，亦即问题 (3.1)。例如，目标规划法 [47] 和加权和技术 [48] 已被引入以促进这一转换。此外，从目标函数和局部函数的角度来看，可以将不同的目标函数分配给不同的节点，作为局部函数。随后，决策者的偏好可以通过这些节点之间的拓扑连接来表达 [43,49]。通过采用这种方法，我们可以使用行随机矩阵（表示无向网络）来替代双随机矩阵，从而有效求解多目标优化问题。

总之，值得注意的是，本工作的主要目标是有效解决由 (3.1) 表示的（单目标）去中心化优化问题，该问题在众多工程场景中具有重要意义。但是，需要澄清的是，本工作的重点并不包含多目标优化问题。我们打算在未来的项目中通过一种去中心化优化算法来解决多目标优化问题。

![](img/3cc494b92b35bef197b953dcaa648a44_90_0.png)

## 3.3 算法构建

为了降低随机梯度算法引入的误差（从而提高计算效率），前人学者提出了方差缩减法（VR）[20–22]。为了尽量减少源于各节点间一致性不足而产生的不准确性，过往研究者引入了梯度跟踪法（GT）[50,51]。借助这两种策略，某些学者提出了 GT-VR 算法结构，其以高计算效率和精确的线性收敛速度著称，尤其是在步长足够小时，如 [19] 所示。针对受限于闭凸集的优化问题，[26] 中的研究人员采用了投影算子，设计了一种名为 GT-CDGD 的算法。然而，其计算效率仍有很大提升空间。为提升这一效率，我们将投影算子与方差缩减法相结合，提出了一种新的投影去中心化方差缩减算法（P-DVR），专用于受限去中心化优化问题。节点 i 的迭代过程如下所示，其中 \(\eta > 0\) 表示固定步长：

```
\(x_{k+1}^i = P_{\Omega_0}[\sum_{j=1}^m a^{ij} x_k^j] - \eta y_k^i,\) (3.6a)

\(s_{k+1}^i = P_{\Omega_0}[x_{k+1}^i],\) (3.6b)

\(y_{k+1}^i = \sum_{j=1}^m a^{ij} y_k^j + g^i(s_{k+1}^i) - g^i(s_k^i).\) (3.6c)
```

在算法 1 中，每个节点 \(i\) 维护一个分量梯度表，记为 \(\{ \nabla f^{i,j}(t_k^{i,j}) \}_{j=1}^{n^i}\)，用于计算梯度估计器 \(g^i(s_k^i)\)。这里，\(t_k^{i,j}\) 表示在第 \(k\) 次迭代之前与第 \(j\) 个数据点相关的最新迭代状态，而

```
Algorithm 1 A Projected Decentralized Variance-Reduction Algorithm: for node \( i \in \mathcal{V} \).

1: **Initialization:** Set \( x_0^i = \mathbf{0} \in \mathbb{R}^p \), \( s_0^i = P_{\Omega_0}(x_0^i) \), \( t_0^{i,j} = \mathbf{0} \in \mathbb{R}^p \), \( g^i(s_0^i) = \nabla f(s_0^i) \in \mathbb{R}^p \), \( y_0^i = g^i(s_0^i) \in \mathbb{R}^p \), and \( t_0^i = [\nabla f^{i,1}(s_0^i) \dots \nabla f^{i,n^i}(s_0^i)]^\text{T} \), where \( p \) is the dimension of \( x \).
2: for \( k = 1, 2, \dots \) do
3: Update the state \( x_k^i \) via (3.6a).
4: Compute the auxiliary variable \( s_k^i \) via (3.6b).
5: Choose \( \chi_k^i \) uniformly and randomly from \( \{1, \dots, n^i\} \).
6: Compute the local gradient estimator \( g^i(s_k^i) = \nabla f^{i, \chi_k^i}(s_k^i) - \nabla f^{i, \chi_k^i}(t_k^{i, \chi_k^i}) + \frac{1}{n^i} \sum_{j=1}^{n^i} \nabla f^{i,j}(t_k^{i,j}) \).
7: If \( j = \chi_k^i \), then \( t_k^j = s_k^i \), else \( t_k^j = t_k^{i, \chi_k^i} \).
8: Compute the local gradient tracker \( y_k^i \) via (3.6c).
9: **end for**
```

第 \(k\) 次迭代，而 \(\nabla f^{i,j}(t_k^{i,j})\) 表示相应的最新分量梯度。在节点 \(i\) 上，第 \(\chi_k^i\) 个分量梯度，具体为 \(\nabla f^{i, \chi_k^i}(t_k^{i, \chi_k^i})\)，在每次迭代 \(k\) 中均匀随机地从此梯度表中选取。选取之后，局部梯度估计则由以下公式得出：

```
\( g^i(s_k^i) = \nabla f^{i, \chi_k^i}(s_k^i) - \nabla f^{i, \chi_k^i}(t_k^{i, \chi_k^i}) + \frac{1}{n^i} \sum_{j=1}^{n^i} \nabla f^{i,j}(t_k^{i,j}) \).
```

在计算 \( g^i(s_k^i) \) 之后，梯度表中的所有条目保持不变，只需将第 \(\chi_k^i\) 个条目更新为 \(\nabla f^{i, \chi_k^i}(s_k^i)\)。

> **注释 3.1.** 对于大规模数据应用场景，我们的工作因其提升的计算效率而脱颖而出，这一点在 [26] 中明显缺失。我们在研究中遇到的问题可概括如下： 
> - (i) 达到与现有无约束算法 [19] 可比拟的收敛速度具有挑战性，主要是因为我们引入了投影算子以适应闭凸集约束。 
> - (ii) 我们新算法的理论分析比无约束优化算法更为复杂。这种复杂性源于方差缩减技术的引入，我们采用该技术来提升计算效率。

## 3.4 收敛性分析

为便于分析，我们定义 \( x_k = [x_k^1, \dots, x_k^m]^\text{T} \in \mathbb{R}^{m \times p} \)、\( s_k = [s_k^1, \dots, s_k^m]^\text{T} \in \mathbb{R}^{m \times p} \)、\( y_k = [y_k^1, \dots, y_k^m]^\text{T} \in \mathbb{R}^{m \times p} \)、\( \nabla F(s_k) = [\nabla f^1(s_k^1), \dots, \nabla f^m(s_k^m)]^\text{T} \in \mathbb{R}^{m \times p} \),

$g(s_k) = [g^1(s_k^1), \dots, g^m(s_k^m)]^T \in \mathbb{R}^{m \times p}, \bar{x}_k = \frac{1}{m} \mathbf{1}_m^T x_k \in \mathbb{R}^p, \bar{y}_k = \frac{1}{m} \mathbf{1}_m^T y_k \in \mathbb{R}^p, \nabla \bar{F}(s_k) = \frac{1}{m} \mathbf{1}_m^T \nabla F(s_k) \in \mathbb{R}^p, \bar{s}_k = P_{\Omega_0}(\bar{x}_k) \in \mathbb{R}^p, \Omega = \Omega_0^m, \text{ 且 } P_{\Omega_0}(\bar{x}_k) = \frac{1}{m} \mathbf{1}_m^T P_{\Omega}(\mathbf{1}_m \bar{x}_k) \in \mathbb{R}^p$. P-DVR 算法所涉及迭代步骤的紧凑表示（由表达式 (3.6a)–(3.6c) 给出）如下所示：

$x_{k+1} = P_{\Omega}[Ax_k] - \eta y_k, \quad (3.7a)$
$s_{k+1} = P_{\Omega}[x_{k+1}], \quad (3.7b)$
$y_{k+1} = Ay_k + g(s_{k+1}) - g(s_k). \quad (3.7c)$

给定初始值 $x_0$，基于 (3.7) 中概述的紧凑迭代过程，并考虑到 $A^\infty = \frac{1}{m} \mathbf{1}_m \mathbf{1}_m^T$，可得

$A^\infty x_{k+1} = \bar{x}_{k+1} = \frac{1}{m} \mathbf{1}_m^T P_{\Omega}(Ax_k) - \eta \bar{y}_k, \quad (3.8a)$
$A^\infty y_{k+1} = \bar{y}_{k+1} = \bar{y}_k + \frac{1}{m} \mathbf{1}_m^T g(s_{k+1}) - \frac{1}{m} \mathbf{1}_m^T g(s_k) = \frac{1}{m} \mathbf{1}_m^T g(s_{k+1}) = \bar{g}(s_{k+1}), \quad (3.8b)$
$\mathbb{E}[\bar{y}_{k+1}] = \frac{1}{m} \mathbf{1}_m^T \nabla F(s_{k+1}), \quad (3.8c)$
$\bar{s}_k = P_{\Omega_0}[\bar{x}_k]. \quad (3.8d)$

为了刻画最优解处投影算子的影响，我们基于 (3.5) 引入以下变量，以阐明当决策向量 $x$ 达到 $x^*$ 时 $x^*$ 的特性：

\(\begin{cases} x^* = P_{\Omega_0}(x^*) - \eta \nabla f(P_{\Omega_0}(x^*)), \\ s^* = P_{\Omega_0}(x^*), \\ x^* = s^* - \eta \nabla f(s^*). \end{cases}\)

### 3.4.1 预设引理

为便于分析，我们将引入若干先前工作已验证的预设引理。

**引理 3.1.** [19] 考虑算法 1 产生的迭代序列 $\{v_k\}$，以下关系对 $\forall k \ge 0$ 成立：

\(\mathbb{E}[v_{k+1}] \le (1 - \frac{1}{n_{\max}})\mathbb{E}[v_k] + \frac{2}{n_{\min}}\mathbb{E}[\|x_k - A^\infty x_k\|^2] + \frac{2}{n_{\min}}\mathbb{E}[m\|\bar{x}_k - x^*\|^2],\)

其中 $v_k^i = (1/n^i) \sum_{j=1}^{n^i} \|t_k^{i,j} - x^*\|^2$、$v_k = \sum_{i=1}^{m} v_k^i$、$n_{\max} = \max_{i \in \mathcal{V}} \{n^i\}$，且 $n_{\min} = \min_{i \in \mathcal{V}} \{n^i\}$.

**引理 3.2.** [35] 假设假设 3.1 成立。若 $0 < \eta \le \frac{1}{\beta}$，则有

\(\|u - v - \eta(\nabla f(u) - \nabla f(v))\| \le (1 - \eta \lambda)\|u - v\|.\)

