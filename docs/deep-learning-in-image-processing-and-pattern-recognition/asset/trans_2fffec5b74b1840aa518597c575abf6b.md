

其中 $v_k$ 和 $i$ 是线性相关系数。

结合公式 (13) 和 (15)，我们可以得到：

$$\mu_k \sum_{i=1}^{N} v_{k,i} K_{k,i} = \frac{1}{N-1} \sum_{i=1}^{N} v_{k,i} \sum_{j=1}^{N} K_{k,j} K_{j,i}$$

进一步简化结果为：

$$\lambda_k v_k = K v_k$$

其中 $\lambda_k = (N-1)\mu_{k}$，$K \in \mathbb{R}^{N \times N}$ 是核矩阵，其特征值为 $\lambda_1 \geq \lambda_2 \geq \cdots \geq \lambda_N$，对应的特征向量为 $v_1, v_2, \cdots, v_N$。在特征空间 $H$ 中，方程 (15) 中协方差矩阵 $Q$ 的特征向量 $V_k$ 构成矩阵 $\hat{V}_f = [V_1 \quad V_2 \quad \cdots \quad V_f \quad V_{f+1} \quad \cdots \quad V_N]$。选取一个主元（PC），则得到主元空间中的 $\hat{V}_f = [V_1 \quad V_2 \quad \cdots \quad V_f] \in \mathbb{R}^{N \times f}$，因为特征向量 $V_k$ 需满足特征空间 $H$ 中的归一化约束，即 $\langle V_k, V_k \rangle = 1$。因此，核矩阵 $K$ 的特征向量 $v_1, v_2, \cdots, v_N$ 可以表示为：

$$\langle v_k, v_k \rangle = \frac{\langle V_k, V_k \rangle}{\lambda_k}$$

取 $\frac{1}{\sqrt{\lambda_k}}$ 的范数作为特征向量，因此我们有：

$$v_k = \frac{1}{\sqrt{\lambda_k}} v^k$$

特征空间 $H$ 中的 $\hat{V}_f$ 表示为：

$$\hat{V}_f = \left[ \frac{1}{\sqrt{\lambda_1}} X^{T} v^1 \right] = X^T \hat{V} \Lambda^{-1/2}$$

其中 $\Lambda = diag(\lambda_1, \lambda_2, \cdots, \lambda_f)$；$\hat{V} = [v^1 \quad v^2 \quad \cdots \quad v^f]$；$X = [\phi(x_1) \quad \phi(x_2) \quad \cdots \quad \phi(x_N)]^T$。

## 5. SVM 基本理论

SVM 能够提供良好的泛化性能，并已被广泛应用于小样本分类 [15]。作为故障定位领域中的经典非线性问题，SVM 无法在原样本空间中找到分类超平面，因此有必要引入核函数 $K(x_i, x_j)$ 映射到线性可分的高维空间。本文使用高斯核函数进行映射变换，其表达式如下：

$$K(x_i, x_j) = \exp\left(-\gamma \| x_i - x_j \|^2\right)$$

其中 $\| x_i - x_j \|^2$ 是 $x_i$ 和 $x_j$ 之间距离的平方，$\gamma$ 是核函数本身的超参数。优化问题定义为：

$$\min_{\omega, b, \xi} \frac{1}{2} \|\omega\|^2 + c \sum_{i=1}^{N} \xi_i$$

约束条件为 $\begin{cases} y_i (\omega^T \phi(x_i)) \geq 1 - \xi_i, & i = 1, 2, \cdots N \\ \xi_i \geq 0, & i = 1, 2, \cdots N \end{cases}$

其中 $\xi_i$ 是松弛变量，$c$ 是惩罚因子，$x_i$ 是第 $i$ 个输入样本，$y_i$ 是样本类型。

引入拉格朗日惩罚因子 $\alpha$，最终得到软间隔高斯核 SVM 的对偶形式如下：

$$\min_{\alpha} \frac{1}{2} \sum_{i=1}^{N} \sum_{j=1}^{N} \alpha_{i} \alpha_{j} y_{i} y_{j} \exp \left(-\gamma\left\|x_{i}-x_{j}\right\|^{2}\right)-\sum_{i=1}^{N} \alpha_{i} \quad \text{(24)}$$

约束条件为 $\begin{cases} 0 \leq \alpha_{i} \leq c, & i=1,2, \cdots N \\ \sum_{i=1}^{N} \alpha_{i} y_{i}=0 \end{cases}$

## 6. 实验与仿真

基于 VMD-MMFD 的方法用于故障电路的特征提取和故障诊断。具体流程如图 2 所示。

![](img/e4200cc4308edaf8913e513b0f96dbb6_447_0.png)

为了验证该方法的有效性，通过 Multisim、Matlab 和 Python 软件进行了仿真实验和计算。以萨伦-凯（Sallen-Key）带通滤波器电路为例，验证了基于变分模态分解和数学形态学分形维数的软故障诊断分析方法。电路图如图 3 所示。

![](img/e4200cc4308edaf8913e513b0f96dbb6_447_1.png)

激励信号 $f = 3 \sin(30) + 3 \sin(20) + \text{noise}$ 用作故障诊断的输入源。电路电阻和电容的容差为 $10\%$，该范围内的元件值被视为正常。在本实验中，当标称值波动 $30\%$ 时设定为软故障状态。本实验配置了 15 种参数故障组合。放大器故障受多种因素影响，因此在此不加以讨论。故障模式设置如表 1 所示，原始信号如图 4 所示，噪声信号如图 5 所示，混合噪声输入信号如图 6 所示。

**表 1. 故障类型描述。**

| 类型编号 | 类型 | 标称值 | 故障区间 |
|---|---|---|---|
| 1 | 正常 | - | - |
| 2 | R$_{1}\uparrow$ 30% | 4 k$\Omega$ | [4.4 k$\Omega$, 5.2 k$\Omega$] |
| 3 | R$_{1}\downarrow$ 30% | 4 k$\Omega$ | [2.8 k$\Omega$, 3.6 k$\Omega$] |
| 4 | R$_{2}\uparrow$ 30% | 3 k$\Omega$ | [3.3 k$\Omega$, 3.9 k$\Omega$] |
| 5 | R$_{2}\downarrow$ 30% | 3 k$\Omega$ | [2.1 k$\Omega$, 2.7 k$\Omega$] |
| 6 | R$_{3}\uparrow$ 30% | 2 k$\Omega$ | [2.2 k$\Omega$, 2.6 k$\Omega$] |
| 7 | R$_{3}\downarrow$ 30% | 2 k$\Omega$ | [1.4 k$\Omega$, 1.8 k$\Omega$] |
| 8 | R$_{4}\uparrow$ 30% | 4 k$\Omega$ | [4.4 k$\Omega$, 5.2 k$\Omega$] |
| 9 | R$_{4}\downarrow$ 30% | 4 k$\Omega$ | [2.8 k$\Omega$, 3.6 k$\Omega$] |
| 10 | R$_{5}\uparrow$ 30% | 4 k$\Omega$ | [4.4 k$\Omega$, 5.2 k$\Omega$] |
| 11 | R$_{5}\downarrow$ 30% | 4 k$\Omega$ | [2.8 k$\Omega$, 3.6 k$\Omega$] |
| 12 | C$_{1}\uparrow$ 30% | 5 nF | [5.5 nF, 6.5 nF] |
| 13 | C$_{1}\downarrow$ 30% | 5 nF | [3.5 nF, 4.5 nF] |
| 14 | C$_{2}\uparrow$ 30% | 5 nF | [5.5 nF, 6.5 nF] |
| 15 | C$_{2}\downarrow$ 30% | 5 nF | [3.5 nF, 4.5 nF] |

![](img/e4200cc4308edaf8913e513b0f96dbb6_448_0.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_448_1.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_448_2.png)

在使用 VMD 分解信号时，预设尺度参数和二次惩罚因子是影响分解精度的主要参数。因此，对于实测信号的 VMD 分解，合理选择其参数是该方法的难点和关键。VMD 信号分解所得各阶 IMF 分量的中心频率从低频分布到高频。如果获得最佳预设尺度参数 $K$，最后一阶 IMF 分量的中心频率应为最大值，且最大中心频率值应保持稳定。基于对大量实测信号 VMD 分解结果的测试和分析以及参考文献 [16]，本文选择二次惩罚因子 $\alpha = 2000$。以故障类型 3 和故障类型 5 的信号为例进行 VMD 分解，如图 7 和图 8 所示，通过分解获得 IMF 分量的中心频率，如图 9 和图 10 所示。由图可知，当 $K = 4$ 时，IMF 分量的中心频率达到最大值并趋于稳定，模式间的频率不重叠，噪声和模式混叠的影响得到有效抑制。当预设尺度参数 $K > 4$ 时，IMF 5 和 IMF 6 分量的中心频率变得不稳定并出现模式混叠。因此，当 $K = 4$ 时，信号的 VMD 分解效果最佳。

![](img/e4200cc4308edaf8913e513b0f96dbb6_449_0.png)

**图 7. 故障 3 信号的 VMD 分解序列图。**

近年来，在电路故障诊断领域，结合经验模态分解与盒维数估计的方法常用于特征提取 [17]。实验将该传统方法与基于变分模态分解和数学形态学的特征提取模型进行比较。以类型 2~5 的四种状态为例，其中 $q$ 为尺度，取值范围为 $[0, 10]$。每种状态对应 10 个分形维数。随着尺度 $q$ 的增加，故障状态从不同维度被描绘出来，$D_q$ 是不同尺度 $q$ 下的分形维数值，并对此进行频谱分析。

在图 11 中，Fault03 的 IMF1 分量与其他分量不重叠，而 Fault02、Fault04 和 Fault05 的 IMF1 分量存在混叠及不同程度的交叉。随着 $q$ 的增加，混叠和交叉现象越来越严重，使得它们难以区分。在图 12 中，Fault02 和 Fault04 的 IMF1 分量存在严重的交叉现象，难以区分故障类型。当 $q$ 值较小时，Fault03 和 Fault05 的 IMF1 没有混叠现象。随着 $q$ 的增加，Fault04 的 IMF1 与 Fault03 和 Fault05 的 IMF1 出现严重交叉现象。在图 13 中，Fault04 和 Fault05 的 IMF1 严重

