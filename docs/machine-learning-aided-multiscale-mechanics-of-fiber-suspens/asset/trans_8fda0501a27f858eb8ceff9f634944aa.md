

在所考虑体积 \(\Omega_t\) 上的线性动量平衡。\(n\) 阶张量场 \(\psi : Y_t \times [0, T] \to (\mathbb{R}^d)^{\otimes n}\) 在体积 \(\Omega_t\) 上的一般平衡方程读作（Liu, 2002）

\[
\frac{\mathrm{d}}{\mathrm{d}t} \int_{\Omega_t} \psi \, \mathrm{d}\Omega_t(\boldsymbol{x}) = \int_{\Omega_t} p_\psi + s_\psi \, \mathrm{d}\Omega_t(\boldsymbol{x}) + \int_{\partial\Omega_t} \boldsymbol{q}_\psi \odot \boldsymbol{n} \, \mathrm{d}A_t(\boldsymbol{x}), \quad (2.15)
\]

其中 \(\odot\) 表示一阶张量收缩。三个张量场 \(p_\psi : \Omega_t \times [0, T] \to (\mathbb{R}^d)^{\otimes n}\)、\(s_\psi : \Omega_t \times [0, T] \to (\mathbb{R}^d)^{\otimes n}\) 和 \(\boldsymbol{q} : \Omega_t \times [0, T] \to (\mathbb{R}^d)^{\otimes (n+1)}\) 分别代表量 \(\psi\) 的内部生成场、外部供给场和非对流通量场。利用雷诺输运定理和散度定理（Bertram, 2012），一般平衡方程（2.15）在常规点的局部形式（Liu, 2002）

\[
\frac{\partial \psi}{\partial t} + \text{div}(\psi \otimes \boldsymbol{v}) = p_\psi + s_\psi + \text{div}(\boldsymbol{q}_\psi), \quad (2.16)
\]

源自方程（2.15）。这里，\(\boldsymbol{v} : \Omega_t \times [0, T] \to \mathbb{R}^d\) 表示速度场。如果体积 \(\Omega_t\) 包含材料奇异面 \(\mathcal{S}_t\)，则材料奇异面 \(\mathcal{S}_t\) 上点 \(\boldsymbol{x} \in \mathcal{S}_t\) 的跳跃条件（Morro and Giorgi, 2023）

\[
[[\boldsymbol{q}_\psi]] \cdot \boldsymbol{n} = \boldsymbol{0} \quad (2.17)
\]

成立。这里，量 \(q\) 跨越具有法向量 \(\boldsymbol{n}\) 的材料奇异面 \(\mathcal{S}_t\) 的跳跃 \([[q]]\) 为

\[
[[q]] = q^+ - q^-, \quad (2.18)
\]

这里，我们用 \(q^+\) 和 \(q^-\) 分别表示量 \(q\) 的左侧和右侧极限。

### 2.3.2 质量平衡

我们将质量密度 \(\rho : \Omega_t \times [0, T] \rightarrow \mathbb{R}\) 作为平衡方程（2.16）的主体 \(\psi\)。由于内部生成 \(p_\rho\)、外部供给 \(s_\rho\) 和非对流通量 \(\mathbf{q}_\rho\) 均消失（Morro and Giorgi, 2023），常规点的质量平衡局部形式读作

\[
\dot{\rho} + \rho \operatorname{div} (\mathbf{v}) = 0. \quad (2.19)
\]

由于我们要求满足跳跃条件（2.17），奇异点 \(\mathbf{x} \in \mathcal{S}_t\) 的质量平衡得到满足。对于不可压缩流动，质量密度 \(\rho\) 的物质导数 \(\dot{\rho}\) 消失，质量平衡简化为（Landau and Lifshitz, 2013）

\[
\operatorname{div} (\mathbf{v}) = 0. \quad (2.20)
\]

特别是，不可压缩流动可能源于具有空间-时间均匀质量密度 \(\rho\) 的不可压缩材料的运动。然而，具有空间-时间不均匀质量密度 \(\rho\) 的可压缩材料也可能发生不可压缩流动，因为物质时间导数

\[
\dot{\rho} = \frac{\partial \rho}{\partial t} + \frac{\partial \rho}{\partial \mathbf{x}} \cdot \mathbf{v} \quad (2.21)
\]

应当消失，而不仅仅是各个单独项 \(\partial \rho / \partial t\) 和 \((\partial \rho / \partial \mathbf{x}) \cdot \mathbf{v}\)（Spurk and Aksel, 2007）。

### 2.3.3 线性和角动量平衡

将线性动量密度 \(\rho \mathbf{v}\) 作为平衡方程（2.16）的主体 \(\psi\)，常规点的线性动量密度 \(\rho \dot{\mathbf{v}}\) 的局部平衡读作（Morro and Giorgi, 2023）

\[
\rho \dot{\mathbf{v}} = \text{div} (\boldsymbol{\sigma}) + \mathbf{b}, \quad (2.22)
\]

其中 \(\boldsymbol{\sigma} : \Omega_t \times [0, T] \to \text{Sym}(d)\) 表示柯西应力张量场，\(\text{Sym}(d)\) 代表维度 \(d\) 的对称二阶张量空间，\(\mathbf{b} : \Omega_t \times [0, T] \to \mathbb{R}^d\) 是体力密度场。牵引场

\[
\mathbf{t} = \boldsymbol{\sigma} \mathbf{n} \quad (2.23)
\]

根据跳跃条件（2.17），牵引场在材料奇异面 \(\mathcal{S}_t\) 上是连续的，因为成立

\[
[\![\boldsymbol{\sigma}]\!]\mathbf{n} = 0 \quad \Longleftrightarrow \quad \boldsymbol{\sigma}^+ \mathbf{n} = \boldsymbol{\sigma}^- \mathbf{n}. \quad (2.24)
\]

在本论文中，我们考虑不含体力密度的稳态过程，因此供给项 \(\mathbf{b}\) 和速度的物质导数 \(\dot{v}\) 均消失，线性动量平衡简化为

\[
\text{div} (\boldsymbol{\sigma}) = 0. \quad (2.25)
\]

为了将应力场 \(\boldsymbol{\sigma}\) 的球形和偏差贡献分离，我们引入加性分解

\[
\boldsymbol{\sigma} = \boldsymbol{\tau} - p\mathbf{I}, \quad (2.26)
\]

为粘应力场 \(\boldsymbol{\tau} : \Omega_t \times [0, T] \to \text{Sym}_0(d)\) 和压力场 \(p : \Omega_t \times [0, T] \to \mathbb{R}\)。这里，\(\mathbf{I}\) 表示二阶单位张量，\(\text{Sym}_0(d)\) 表示维度 \(d\) 的无痕对称二阶张量空间。因此，将加性分解（2.26）代入线性动量平衡（2.25）得到

\[
\text{div} (\boldsymbol{\tau}) = \nabla p. \quad (2.27)
\]

此外，对于参考点 $x_0 \in \Omega_t$，我们将角动量密度 $(x - x_0) \times \rho v$ 作为平衡方程（2.16）的主体 \(\psi\)。此时，角动量平衡归约为（Liu, 2002）

$$
\sigma = \sigma^{\top},
$$

前提是线性动量平衡（2.22）得到满足。因此，柯西应力张量的对称性保证了非极性材料的角动量守恒，即没有动量密度作用于体积 \(\Omega_t\) 的情况。

## 2.4 纤维取向状态描述

由于纤维悬浮液的有效行为取决于悬浮液中的纤维取向统计特性，因此对取向状态进行数学描述对于研究纤维悬浮液至关重要。下文中，我们使用纤维取向分布函数（Kanatani, 1984）

\[
\rho: S^2 \rightarrow \mathbb{R}, \quad n \mapsto \rho(n),
\]

用于编码纤维在 2 球面 $S^2$ 上沿方向 $n$ 取向的概率，从而描述纤维悬浮液的取向状态。取向分布函数 \(\rho\) 的时空演化由偏微分方程，即 Fokker–Planck 方程（Fokker, 1914）所支配。然而，在构件成型模拟中，使用 Fokker–Planck 方程计算取向分布函数 \(\rho\) 的演化需要巨大的计算开销。相反，（Kennedy and Zheng, 2013）中常用二阶纤维取向张量（Kanatani, 1984; Advani and Tucker III, 1987）

\[
N = \int_{S^2} n \otimes n \rho(n) \, dS(n), \quad (2.30)
\]

作为纤维取向状态的度量。张量 N 是对称的、半正定的，且迹为单位，因此

\[
N_{ii} = \lambda_1 + \lambda_2 + \lambda_3 = 1, \quad (2.31)
\]

其中 \(\lambda_1\)、\(\lambda_2\) 和 \(\lambda_3\) 表示张量 N 的特征值。通过对特征值进行排序

\[
\lambda_1 \ge \lambda_2 \ge \lambda_3, \quad (2.32)
\]

并考虑方程（2.31），最大特征值 \(\lambda_1\) 的界限如下

\[
1 \ge \lambda_1 \ge \frac{1}{3}. \quad (2.33)
\]

此外，特征值 \(\lambda_2\) 的上界源于张量 N 的半正定性，下界可通过利用方程（2.31）从方程（2.32）中消去 \(\lambda_3\) 得出，即

\[
\min(\lambda_1, 1 - \lambda_1) \ge \lambda_2 \ge \frac{1 - \lambda_1}{2}. \quad (2.34)
\]

因此，我们可以通过其两个特征值 \(\lambda_1\) 和 \(\lambda_2\) 以及特征分解中的旋转 Q 来参数化张量 N

\[
N = Q \, \text{diag}(\lambda_1, \lambda_2, \lambda_3) \, Q^{\text{T}}, \quad (2.35)
\]

其中 diag 算子在 \(\mathbb{R}^3\) 的标准基下构造一个二阶张量。根据客观性，本论文的结果推广到所有旋转 Q，为简化起见，我们选择

\[
Q = I. \quad (2.36)
\]

