
![](img/ddadb1d3eaa6f9576eea68f95d453bca_33_0.png)

图 1.5 基于 LLE 的特征空间中的聚类质心。一个质心代表稳态解；两个解析相反的瞬态相位；其余八个质心接近极限环。详情参见 Ehlert 等 (2020)。

![](img/ddadb1d3eaa6f9576eea68f95d453bca_33_1.png)

图 1.6 Re = 100 时新模拟轨迹的样本外误差 E_out。实线对应 LLE 表示。红色点划线和蓝色虚线分别指 10 个质心和 10 个 POD 模态的近似。详情参见 Ehlert 等 (2020)。

在 t = 60 到 t = 80 之间。LLE 在最高可达三个数量级上显著优于 POD 和聚类，突出了 Navier–Stokes 动力学的二维流形以及 LLE 的一个特定应用。正如预期，聚类表现最差，因其缺乏内在插值。基于 LLE 的自编码器的低误差表明动力学本质上是二维的。然而，大约需要 50 个 POD 模态才能达到类似的分辨率，这一点由 Loiseau 等 (2018) 对类似流形近似的论证所证实。显然，基于 POD 的表示对于缓慢变化的振荡相干结构并不高效。

数据驱动的 Galerkin 展开已针对多种目的进行了优化。*动态模态分解* (DMD) (Rowley et al. 2009, Schmid 2010) 可以从初始瞬态中提取稳定性模态，并从收敛后的瞬态数据中提取傅里叶模态。然而，对于瞬态尾迹的性能令人失望，而递归 DMD 可以保留 POD 和 DMD 的某些优势 (Noack et al. 2016)。灵活的状态相关模态可以显著提高低阶表示的精度 (Siegel et al. 2008, Tadmor et al. 2011, Babaee & Sapsis 2016)。

## 1.5 动力学模型：从本征正交分解到流形

本节追求瞬态圆柱尾迹的最小阶模型。起点是 POD Galerkin 方法（第 1.5.1 节）。然后（第 1.5.2 节），采用平均场理论显著简化动力学。该简化最终形成以 Landau 方程为动力学的流形模型（第 1.5.3 节）。

### 1.5.1 本征正交分解 Galerkin 方法

传统的 Galerkin 方法 (Fletcher 1984) 从 Navier–Stokes 方程 (1.1) 推导出具有正交归一模态的 Galerkin 近似 (1.14) 的动力学。在弱条件下，得到常数-线性-二次常微分方程组

$$\frac{da_i}{dt} = c_i + \sum_{j=1,\dots,N} l_{ij}a_j + \sum_{j,k=1,\dots,N} q_{ijk}a_j a_k.\tag{1.15}$$

这些条件可能包括流动的不可压缩性、静止域、静止 Dirichlet、周期性或 von Neumann 边界条件，以及流动的光滑性。系数 $c_i$、$l_{ij}$ 和 $q_{ijk}$ 是模态和雷诺数的函数。系数也可以从数值解或实验数据中识别 (Galletti et al. 2004, Cordier et al. 2013)，例如，如果流动域太小或 (1.14) 中未分辨湍流脉动。我们参考精美的教科书 (Fletcher 1984, Holmes et al. 2012) 获取细节。Schlegel 和 Noack (2015) 已推导出有界解的必要充分条件，这可以被视为物理上合理模型的必要条件。

### 1.5.2 平均场模型

Galerkin 系统 (1.15) 可以利用图 1.3 中所示并在第 1.5.1 节中推导的流形动力学显著简化。流动由零阶和一阶谐波分量主导（见 (1.6)）。

零阶分量位于稳态解 $\boldsymbol{u}_s$ 到平均流 $\bar{\boldsymbol{u}}$ 的直线上。该直线近似于一周期的平均流 $\boldsymbol{u}^D$，并由位移模态 $\boldsymbol{u}_3$ 及其振幅 $a_3$ 参数化（见 (1.7)）。位移模态本质上是尾迹中的回流。流线看起来像一只苍蝇，并在图 1.3（左中子图）中示出。

一阶谐波代表 von Kármán 涡脱落，可由余弦 **u₁** 和正弦 **u₂** 模态解析，暂时忽略形状变形：

$$\mathbf{u}'(\mathbf{x},t)=a_1(t)\,\mathbf{u}_1(\mathbf{x})+a_2(t)\,\mathbf{u}_2(\mathbf{x})\tag{1.16}$$

模态可从图 1.3 最右列推断。以下假设 **u₁**、**u₂** 和 **u₃** 已正交归一化。瞬态的前三个 POD 模态已是这些模态的良好近似。

遵循平均场论证 (Noack et al. 2003)，Galerkin 系统 (1.15) 简化为自放大、振幅受限的振荡器，

$$\frac{da_1}{dt}=\sigma a_1-\omega a_2,\qquad \sigma=\sigma_1-\beta a_3,\tag{1.17a}$$
$$\frac{da_2}{dt}=\sigma a_2+\omega a_1,\qquad \omega=\omega_1+\gamma a_3,\tag{1.17b}$$
$$\frac{da_3}{dt}=\sigma_3 a_3+\alpha\left(a_1^2+a_2^2\right).\tag{1.17c}$$

该振荡器具有三个参数 $\sigma_1$、$\omega_1$、$\sigma_3$ 用于线性动力学，以及三个参数 $\alpha$、$\beta$、$\gamma$ 用于雷诺应力的弱非线性效应。有趣的是，*非线性动力学的稀疏识别* (SINDy) 正是从瞬态模拟数据中提取出这一稀疏动力系统 (Brunton, Proctor & Kutz 2016a)。

![](img/ddadb1d3eaa6f9576eea68f95d453bca_35_0.png)

图 1.7 来自 DNS（实线）和平均场 Galerkin 系统 (1.17)（虚线）的圆柱尾迹瞬态动力学。这里，$a_\Delta = a_3$。相图取自 Tadmor 和 Noack (2004)。

图 1.7 显示平均场 Galerkin 系统 (1.17) 与直接数值模拟吻合良好。详细分析 (Tadmor & Noack 2004) 定量证实了流形和时间演化的这一一致性。

### 1.5.3 流形模型

平均场 Galerkin 系统可进一步简化，利用位移模态对波动水平的从属关系。事实上，经校准的 $\sigma_3 \approx -6\sigma_1$ 显示出比波动增长更快地收敛到流形。因此，(1.17c) 可很好地用代数方程近似

$$a_3 = \frac{\alpha_3}{|\sigma_3|}\left(a_1^2 + a_2^2\right),\tag{1.18}$$

解释了图中平均场抛物线形状。将方程 (1.18) 代入 (1.17a)、(1.17b) 并引入极坐标 $a_1 = r \cos \theta$、$a_2 = r \sin \theta$，得到超临界失稳的著名 Landau 方程 (Landau & Lifshitz 1987)，

$$dr/dt = \sigma_1 r - \beta' r^3, \quad d\theta/dt = \omega_1 + \gamma' r^2. \tag{1.19}$$

这些方程显示了由线性不稳定性引起的指数增长，以及由雷诺应力和平均场变形引起的三次阻尼。频率也会发生变化。非线性参数 $\beta'$ 和 $\gamma'$ 可从 (1.17) 轻松推导。有趣的是，该方程即使远离涡脱落起始点也被发现仍然准确。

所得的 Landau 模型不包含高次谐波。更糟的是，我们假设了固定模态 $\boldsymbol{u}_1$、$\boldsymbol{u}_2$。然而，稳态解附近的显著稳定性模态与表征极限环的 POD 模态明显不同。依赖于 $a_3$ 的模态可以纠正这一缺陷 (Morzyński et al. 2006)，但模型仍然对高次谐波视而不见。更精确的模型基于 LLE 特征坐标 $\gamma_1 = r \cos \theta$ 和 $\gamma_2 = r \sin \theta$ 以及 $r$ 和 $\theta$ 动力学的已识别 Landau 方程。LLE 自编码器包含了模态变形和高次谐波 (Ehlert et al. 2020)。Loiseau 等 (2018) 基于类似前提推导了此类模型。平均场 Galerkin 模型可推广至两个（及以上）频率 (Luchtenburg et al. 2009)。

## 1.6 控制：基于模型和无模型方法

本节预览两种流动控制方法。第 1.6.1 节遵循基于模型的控制设计的经典范式，而第 1.6.2 节概述了无模型的机器学习控制优化。

### 1.6.1 基于模型的控制

作为控制基准 (Hinze & Kunisch 2000)，我们旨在用近尾迹中的横向体积力稳定圆柱尾迹（见图 1.8）。这种公认的学术性体积力执行器在计算流动控制文献中出人意料地经常被使用，并显著简化了讨论。作为额外复杂性，实验条件由热线测量的流向速度分量 $s$ 模拟。目标是稳定基于传感器的控制律（再次见图 1.8）。

可以证明体积力会在平均场系统中引入额外项 $g b$ (Gerhard et al. 2003)，

$$da_1/dt = \sigma a_1 - \omega a_2 + g b, \quad \sigma = \sigma_1 - \beta a_3, \tag{1.20a}$$
$$da_2/dt = \sigma a_2 + \omega a_1, \quad \omega = \omega_1 + \gamma a_3, \tag{1.20b}$$
$$a_3 = a' \left(a_1^2 + a_2^2\right), \quad a' = \alpha / |\sigma_1|. \tag{1.20c}$$
